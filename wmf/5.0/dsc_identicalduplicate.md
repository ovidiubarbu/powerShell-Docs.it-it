---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 28f4f8ae2bbddc8fb5ef9d95d3061a91fcc8ffe2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058727"
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="8a01f-102">Consentire risorse duplicate identiche in una configurazione</span><span class="sxs-lookup"><span data-stu-id="8a01f-102">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="8a01f-103">DSC non consente o non gestisce definizioni di risorse in conflitto all'interno di una configurazione.</span><span class="sxs-lookup"><span data-stu-id="8a01f-103">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="8a01f-104">Anziché tentare di risolvere il conflitto, l'esito è semplicemente negativo.</span><span class="sxs-lookup"><span data-stu-id="8a01f-104">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="8a01f-105">Dato che il riutilizzo delle configurazioni diventa sempre più comune tramite risorse composite, i conflitti si verificheranno sempre più spesso.</span><span class="sxs-lookup"><span data-stu-id="8a01f-105">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="8a01f-106">Quando le definizioni delle risorse in conflitto sono identiche, DSC dovrebbe essere intelligente e consentire questa situazione.</span><span class="sxs-lookup"><span data-stu-id="8a01f-106">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="8a01f-107">In questa versione è supportata la presenza di più istanze di risorse con definizioni identiche:</span><span class="sxs-lookup"><span data-stu-id="8a01f-107">With this release, we support having multiple resource instances that have identical definitions:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="8a01f-108">Nelle versioni precedenti, il risultato sarebbe la non riuscita della compilazione a causa di un conflitto tra le istanze di WindowsFeature FE_IIS e WindowsFeature Worker_IIS nel tentativo di assicurarsi che il ruolo 'Web-Server' sia installato.</span><span class="sxs-lookup"><span data-stu-id="8a01f-108">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="8a01f-109">Si noti che *tutte* le proprietà da configurare in queste due configurazioni sono identiche.</span><span class="sxs-lookup"><span data-stu-id="8a01f-109">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="8a01f-110">Dato che *tutte* le proprietà in queste due risorse sono identiche, il risultato sarà ora una compilazione corretta.</span><span class="sxs-lookup"><span data-stu-id="8a01f-110">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="8a01f-111">In presenza di differenze per qualsiasi proprietà tra le due risorse, non verranno considerate identiche e la compilazione avrà esito negativo:</span><span class="sxs-lookup"><span data-stu-id="8a01f-111">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS
    {
        Ensure = 'Present'     # Ensure is Present here
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS
    {
        Ensure = 'Absent'      # Ensure property is Absent instead of Present
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="8a01f-112">Questa configurazione molto simile non riuscirà perché le risorse WindowsFeature FE_IIS e WindowsFeature Worker_II non sono più identiche e pertanto sono in conflitto.</span><span class="sxs-lookup"><span data-stu-id="8a01f-112">This very similar configuration will fail because the WindowsFeature FE_IIS and the WindowsFeature Worker_IIS resources are no longer identical and therefore conflict.</span></span>
