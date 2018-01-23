---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsPackageCab DSC
ms.openlocfilehash: 1d7c8d9bf45d2eda8734daa8877315d219662c75
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="770a3-103">Risorsa WindowsPackageCab DSC</span><span class="sxs-lookup"><span data-stu-id="770a3-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="770a3-104">Si applica a: Windows PowerShell 5.1 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="770a3-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="770a3-105">La risorsa **WindowsPackageCab** in Windows PowerShell DSC (Desired State Configuration) offre un meccanismo per installare o disinstallare pacchetti CAB in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="770a3-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="770a3-106">È necessario che nel nodo di destinazione sia installato il modulo PowerShell Gestione e manutenzione immagini distribuzione.</span><span class="sxs-lookup"><span data-stu-id="770a3-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="770a3-107">Per informazioni, vedere [Usare Gestione e manutenzione immagini distribuzione in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span><span class="sxs-lookup"><span data-stu-id="770a3-107">For information, see [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span> 


## <a name="syntax"></a><span data-ttu-id="770a3-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="770a3-108">Syntax</span></span>

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="770a3-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="770a3-109">Properties</span></span>

|  <span data-ttu-id="770a3-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="770a3-110">Property</span></span>  |  <span data-ttu-id="770a3-111">Description</span><span class="sxs-lookup"><span data-stu-id="770a3-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="770a3-112">Nome</span><span class="sxs-lookup"><span data-stu-id="770a3-112">Name</span></span>| <span data-ttu-id="770a3-113">Indica il nome del pacchetto per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="770a3-113">Indicates the name of the package for you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="770a3-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="770a3-114">Ensure</span></span>| <span data-ttu-id="770a3-115">Indica se il pacchetto è installato.</span><span class="sxs-lookup"><span data-stu-id="770a3-115">Indicates if the package is installed.</span></span> <span data-ttu-id="770a3-116">Impostare questa proprietà su "Absent" per specificare che il pacchetto non è installato (o disinstallare il pacchetto se è installato).</span><span class="sxs-lookup"><span data-stu-id="770a3-116">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="770a3-117">Impostarla su "Present" (valore predefinito) per specificare che il pacchetto è installato.</span><span class="sxs-lookup"><span data-stu-id="770a3-117">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="770a3-118">Path</span><span class="sxs-lookup"><span data-stu-id="770a3-118">Path</span></span>| <span data-ttu-id="770a3-119">Percorso in cui si trova il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="770a3-119">Indicates the path where the package resides.</span></span>| 
| <span data-ttu-id="770a3-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="770a3-120">LogPath</span></span>| <span data-ttu-id="770a3-121">Indica il percorso completo in cui il provider deve salvare un file di log per installare o disinstallare il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="770a3-121">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>| 
| <span data-ttu-id="770a3-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="770a3-122">DependsOn</span></span> | <span data-ttu-id="770a3-123">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="770a3-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="770a3-124">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è \`DependsOn = "[ResourceType]ResourceName"\`\`.</span><span class="sxs-lookup"><span data-stu-id="770a3-124">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>| 

## <a name="example"></a><span data-ttu-id="770a3-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="770a3-125">Example</span></span>

<span data-ttu-id="770a3-126">La configurazione di esempio seguente accetta parametri di input e assicura che venga installato il file con estensione cab specificato dal parametro `$Name`.</span><span class="sxs-lookup"><span data-stu-id="770a3-126">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```

