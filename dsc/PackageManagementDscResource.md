---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa PackageManagement DSC
ms.openlocfilehash: 4cd7625af7ed0bb3fe971c826ac2075841cdfdc5
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="e8624-103">Risorsa PackageManagement DSC</span><span class="sxs-lookup"><span data-stu-id="e8624-103">DSC PackageManagement Resource</span></span>

> <span data-ttu-id="e8624-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e8624-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="e8624-105">La risorsa **PackageManagement** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per installare o disinstallare pacchetti di Gestione pacchetti in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="e8624-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="e8624-106">Questa risorsa richiede il modulo **PackageManagement**, disponibile da http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="e8624-106">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="e8624-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e8624-107">Syntax</span></span>

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ Source = [string] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ RequiredVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ MaximumVersion = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ ProviderName = [string] ]
    [ AdditionalParameters = [Microsoft.Management.Infrastructure.CimInstance[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="e8624-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="e8624-108">Properties</span></span>
|  <span data-ttu-id="e8624-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="e8624-109">Property</span></span>  |  <span data-ttu-id="e8624-110">Description</span><span class="sxs-lookup"><span data-stu-id="e8624-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="e8624-111">Nome</span><span class="sxs-lookup"><span data-stu-id="e8624-111">Name</span></span>| <span data-ttu-id="e8624-112">Specifica il nome del pacchetto da installare o disinstallare.</span><span class="sxs-lookup"><span data-stu-id="e8624-112">Specifies the name of the Package to be installed or uninstalled.</span></span>| 
| <span data-ttu-id="e8624-113">Source</span><span class="sxs-lookup"><span data-stu-id="e8624-113">Source</span></span>| <span data-ttu-id="e8624-114">Specifica il nome dell'origine del pacchetto in cui è possibile trovare il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="e8624-114">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="e8624-115">Può trattarsi di un URI o di un'origine registrata con la risorsa DSC Register-PackageSource o PackageManagementSource.</span><span class="sxs-lookup"><span data-stu-id="e8624-115">This can either be a URI or a source registered with Register-PackageSource or PackageManagementSource DSC resource.</span></span> <span data-ttu-id="e8624-116">La risorsa DSC MSFT_PackageManagementSource può anche registrare un'origine del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="e8624-116">The DSC resource MSFT_PackageManagementSource can also register a package source.</span></span>| 
| <span data-ttu-id="e8624-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="e8624-117">Ensure</span></span>| <span data-ttu-id="e8624-118">Determina se il pacchetto deve essere installato o disinstallato.</span><span class="sxs-lookup"><span data-stu-id="e8624-118">Determines whether the package is to be installed or uninstalled.</span></span>| 
| <span data-ttu-id="e8624-119">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="e8624-119">RequiredVersion</span></span>| <span data-ttu-id="e8624-120">Specifica la versione esatta del pacchetto da installare.</span><span class="sxs-lookup"><span data-stu-id="e8624-120">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="e8624-121">Se non si specifica questo parametro, la risorsa DSC installa la versione disponibile più recente del pacchetto che soddisfa anche l'eventuale requisito di versione massima specificato dal parametro MaximumVersion.</span><span class="sxs-lookup"><span data-stu-id="e8624-121">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the MaximumVersion parameter.</span></span>| 
| <span data-ttu-id="e8624-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="e8624-122">MinimumVersion</span></span>| <span data-ttu-id="e8624-123">Specifica la versione minima consentita del pacchetto da installare.</span><span class="sxs-lookup"><span data-stu-id="e8624-123">Specifies the minimum allowed version of the package that you want to install.</span></span> <span data-ttu-id="e8624-124">Se non si aggiunge questo parametro, la risorsa DSC installa la versione disponibile più recente del pacchetto che soddisfa anche l'eventuale requisito di versione massima specificato dal parametro MaximumVersion.</span><span class="sxs-lookup"><span data-stu-id="e8624-124">If you do not add this parameter, this DSC resource intalls the highest available version of the package that also satisfies any maximum specified version specified by the MaximumVersion parameter.</span></span>| 
| <span data-ttu-id="e8624-125">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="e8624-125">MaximumVersion</span></span>| <span data-ttu-id="e8624-126">Specifica la versione massima consentita del pacchetto da installare.</span><span class="sxs-lookup"><span data-stu-id="e8624-126">Specifies the maximum allowed version of the package that you want to install.</span></span> <span data-ttu-id="e8624-127">Se non si specifica questo parametro, questa risorsa DSC installa la versione disponibile con numero più alto del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="e8624-127">If you do not specify this parameter, this DSC resource installs the highest-numbered available version of the package.</span></span>| 
| <span data-ttu-id="e8624-128">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="e8624-128">SourceCredential</span></span> | <span data-ttu-id="e8624-129">Specifica un account utente con i diritti per installare un pacchetto per un'origine o un provider di pacchetti specificato.</span><span class="sxs-lookup"><span data-stu-id="e8624-129">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>| 
| <span data-ttu-id="e8624-130">ProviderName</span><span class="sxs-lookup"><span data-stu-id="e8624-130">ProviderName</span></span>| <span data-ttu-id="e8624-131">Specifica il nome di un provider di pacchetti entro il cui ambito limitare la ricerca di pacchetti.</span><span class="sxs-lookup"><span data-stu-id="e8624-131">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="e8624-132">Per ottenere i nomi di provider di pacchetti, è possibile eseguire il cmdlet Get-PackageProvider.</span><span class="sxs-lookup"><span data-stu-id="e8624-132">You can get package provider names by running the Get-PackageProvider cmdlet.</span></span>| 
| <span data-ttu-id="e8624-133">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="e8624-133">AdditionalParameters</span></span>| <span data-ttu-id="e8624-134">Parametri specifici del provider che vengono passati come una tabella hash.</span><span class="sxs-lookup"><span data-stu-id="e8624-134">Provider specific parameters that are passed as an Hashtable.</span></span> <span data-ttu-id="e8624-135">Ad esempio, per il provider NuGet è possibile passare parametri aggiuntivi come DestinationPath.</span><span class="sxs-lookup"><span data-stu-id="e8624-135">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>| 

## <a name="additional-parameters"></a><span data-ttu-id="e8624-136">Parametri aggiuntivi</span><span class="sxs-lookup"><span data-stu-id="e8624-136">Additional Parameters</span></span>
<span data-ttu-id="e8624-137">Nella tabella seguente sono elencate le opzioni per la proprietà AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="e8624-137">The following table lists options for the AdditionalParameters property.</span></span>
|  <span data-ttu-id="e8624-138">Parametro</span><span class="sxs-lookup"><span data-stu-id="e8624-138">Parameter</span></span>  | <span data-ttu-id="e8624-139">Description</span><span class="sxs-lookup"><span data-stu-id="e8624-139">Description</span></span>   | 
|---|---|
| <span data-ttu-id="e8624-140">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="e8624-140">DestinationPath</span></span>| <span data-ttu-id="e8624-141">Usato dai provider, ad esempio il provider NuGet predefinito.</span><span class="sxs-lookup"><span data-stu-id="e8624-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="e8624-142">Specifica un percorso di file in cui si vuole installare il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="e8624-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="e8624-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="e8624-143">InstallationPolicy</span></span>| <span data-ttu-id="e8624-144">Usato dai provider, ad esempio il provider NuGet predefinito.</span><span class="sxs-lookup"><span data-stu-id="e8624-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="e8624-145">Determina se considerare attendibile l'origine del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="e8624-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="e8624-146">Uno dei valori possibili: "Untrusted", "Trusted".</span><span class="sxs-lookup"><span data-stu-id="e8624-146">One of: "Untrusted", "Trusted".</span></span>|

## <a name="example"></a><span data-ttu-id="e8624-147">Esempio</span><span class="sxs-lookup"><span data-stu-id="e8624-147">Example</span></span>

<span data-ttu-id="e8624-148">Questo esempio installa il pacchetto NuGet **JQuery** e il modulo di PowerShell **GistProvider** usando la risorsa DSC **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="e8624-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="e8624-149">Questo esempio verifica innanzitutto che siano disponibili le origini di pacchetti richieste e quindi definisce lo stato previsto dei pacchetti **JQuery** e **GistProvider** (rispettivamente, NuGet e PowerShell).</span><span class="sxs-lookup"><span data-stu-id="e8624-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{    
    PackageManagementSource SourceRepository 
    { 
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }    
    
    PackageManagementSource PSGallery 
    { 
        Ensure      = "Present" 
        Name        = "psgallery" 
        ProviderName= "PowerShellGet" 
        SourceUri   = "https://www.powershellgallery.com/api/v2/"   
        InstallationPolicy ="Trusted" 
    } 
          
    PackageManagement NugetPackage 
    { 
        Ensure               = "Present"  
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1" 
        DependsOn            = "[PackageManagementSource]SourceRepository" 
    }
    
    PackageManagement PSModule 
    { 
        Ensure               = "Present"  
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery" 
    }
}
```

