---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Risorsa PackageManagementSource DSC
ms.openlocfilehash: 80d157aff5bf7685a797baaf6a26215f02473096
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="07cc0-103">Risorsa PackageManagementSource DSC</span><span class="sxs-lookup"><span data-stu-id="07cc0-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="07cc0-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="07cc0-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="07cc0-105">La risorsa **PackageManagementSource** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per registrare o annullare la registrazione di origini di Gestione pacchetti in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="07cc0-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="07cc0-106">**Le origini di Gestione pacchetti registrate in questo modo vengono registrate nel contesto del sistema, utilizzabile dall'account di sistema o dal motore di DSC.**</span><span class="sxs-lookup"><span data-stu-id="07cc0-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="07cc0-107">Questa risorsa richiede il modulo **PackageManagement**, disponibile da http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="07cc0-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="07cc0-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="07cc0-108">Syntax</span></span>

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="07cc0-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="07cc0-109">Properties</span></span>
|  <span data-ttu-id="07cc0-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="07cc0-110">Property</span></span>  |  <span data-ttu-id="07cc0-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="07cc0-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="07cc0-112">Nome</span><span class="sxs-lookup"><span data-stu-id="07cc0-112">Name</span></span>| <span data-ttu-id="07cc0-113">Specifica il nome dell'origine del pacchetto da registrare o di cui annullare la registrazione nel sistema.</span><span class="sxs-lookup"><span data-stu-id="07cc0-113">Specifies the name of the package source to be registered or unregistered on your system.</span></span>| 
| <span data-ttu-id="07cc0-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="07cc0-114">Ensure</span></span>| <span data-ttu-id="07cc0-115">Determina se l'origine del pacchetto deve essere registrata oppure se ne deve essere annullata la registrazione.</span><span class="sxs-lookup"><span data-stu-id="07cc0-115">Determines whether the package source is to be registered or unregistered.</span></span>| 
| <span data-ttu-id="07cc0-116">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="07cc0-116">InstallationPolicy</span></span>| <span data-ttu-id="07cc0-117">Determina se considerare attendibile l'origine del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="07cc0-117">Determines whether you trust the package source.</span></span> <span data-ttu-id="07cc0-118">Uno dei valori possibili: "Untrusted", "Trusted".</span><span class="sxs-lookup"><span data-stu-id="07cc0-118">One of: "Untrusted", "Trusted".</span></span>| 
| <span data-ttu-id="07cc0-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="07cc0-119">ProviderName</span></span>| <span data-ttu-id="07cc0-120">Specifica il nome del provider OneGet tramite il quale è possibile l'interoperabilità con l'origine del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="07cc0-120">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>| 
| <span data-ttu-id="07cc0-121">SourceUri</span><span class="sxs-lookup"><span data-stu-id="07cc0-121">SourceUri</span></span>| <span data-ttu-id="07cc0-122">Specifica l'URI dell'origine del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="07cc0-122">Specifies the URI of the package source.</span></span>| 
| <span data-ttu-id="07cc0-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="07cc0-123">SourceCredential</span></span>| <span data-ttu-id="07cc0-124">Fornisce l'accesso al pacchetto in un'origine remota.</span><span class="sxs-lookup"><span data-stu-id="07cc0-124">Provides access to the package on a remote source.</span></span>| 

## <a name="example"></a><span data-ttu-id="07cc0-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="07cc0-125">Example</span></span>

<span data-ttu-id="07cc0-126">Questo esempio registra l'origine del pacchetto http://nuget.org usando la risorsa DSC **PackageManagementSource**.</span><span class="sxs-lookup"><span data-stu-id="07cc0-126">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{    
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }
}
```

