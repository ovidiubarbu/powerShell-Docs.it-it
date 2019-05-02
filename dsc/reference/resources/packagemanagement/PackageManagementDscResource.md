---
ms.date: 06/20/2018
keywords: dsc,powershell,configurazione,installazione
title: Risorsa PackageManagement DSC
ms.openlocfilehash: 18cbbfe0715c82dcfdf4a5fb6ee36ee814e43d3b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077620"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="70680-103">Risorsa PackageManagement DSC</span><span class="sxs-lookup"><span data-stu-id="70680-103">DSC PackageManagement Resource</span></span>

<span data-ttu-id="70680-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="70680-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="70680-105">La risorsa **PackageManagement** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per installare o disinstallare pacchetti di Gestione pacchetti in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="70680-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="70680-106">Questa risorsa richiede il modulo **PackageManagement**, disponibile da [http://PowerShellGallery.com](http://PowerShellGallery.com).</span><span class="sxs-lookup"><span data-stu-id="70680-106">This resource requires the **PackageManagement** module, available from [http://PowerShellGallery.com](http://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="70680-107">La versione del modulo **PackageManagement** deve essere almeno la 1.1.7.0 affinché le informazioni sulle proprietà seguenti siano corrette.</span><span class="sxs-lookup"><span data-stu-id="70680-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="70680-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="70680-108">Syntax</span></span>

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [AdditionalParameters = [HashTable]]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [MaximumVersion = [string]]
    [MinimumVersion = [string]]
    [ProviderName = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [RequiredVersion = [string]]
    [Source = [string]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a><span data-ttu-id="70680-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="70680-109">Properties</span></span>

| <span data-ttu-id="70680-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="70680-110">Property</span></span> | <span data-ttu-id="70680-111">Description</span><span class="sxs-lookup"><span data-stu-id="70680-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="70680-112">Nome</span><span class="sxs-lookup"><span data-stu-id="70680-112">Name</span></span>| <span data-ttu-id="70680-113">Specifica il nome del pacchetto da installare o disinstallare.</span><span class="sxs-lookup"><span data-stu-id="70680-113">Specifies the name of the Package to be installed or uninstalled.</span></span>|
| <span data-ttu-id="70680-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="70680-114">AdditionalParameters</span></span>| <span data-ttu-id="70680-115">Tabella hash specifica del provider dei parametri passati a `Get-Package -AdditionalArguments`.</span><span class="sxs-lookup"><span data-stu-id="70680-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="70680-116">Ad esempio, per il provider NuGet è possibile passare parametri aggiuntivi come DestinationPath.</span><span class="sxs-lookup"><span data-stu-id="70680-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>|
| <span data-ttu-id="70680-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="70680-117">Ensure</span></span>| <span data-ttu-id="70680-118">Determina se il pacchetto deve essere installato o disinstallato.</span><span class="sxs-lookup"><span data-stu-id="70680-118">Determines whether the package is to be installed or uninstalled.</span></span>|
| <span data-ttu-id="70680-119">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="70680-119">MaximumVersion</span></span>|<span data-ttu-id="70680-120">Specifica la versione massima consentita del pacchetto da trovare.</span><span class="sxs-lookup"><span data-stu-id="70680-120">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="70680-121">Se non si aggiunge questo parametro, la risorsa trova la versione disponibile più recente del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="70680-121">If you do not add this parameter, the resource finds the highest available version of the package.</span></span>|
| <span data-ttu-id="70680-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="70680-122">MinimumVersion</span></span>|<span data-ttu-id="70680-123">Specifica la versione minima consentita del pacchetto da trovare.</span><span class="sxs-lookup"><span data-stu-id="70680-123">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="70680-124">Se non si aggiunge questo parametro, la risorsa trova la versione disponibile più recente del pacchetto che soddisfa anche l'eventuale requisito di versione massima specificato dal parametro _MaximumVersion_.</span><span class="sxs-lookup"><span data-stu-id="70680-124">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="70680-125">ProviderName</span><span class="sxs-lookup"><span data-stu-id="70680-125">ProviderName</span></span>| <span data-ttu-id="70680-126">Specifica il nome di un provider di pacchetti entro il cui ambito limitare la ricerca di pacchetti.</span><span class="sxs-lookup"><span data-stu-id="70680-126">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="70680-127">Per ottenere i nomi di provider di pacchetti, è possibile eseguire il cmdlet `Get-PackageProvider`.</span><span class="sxs-lookup"><span data-stu-id="70680-127">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>|
| <span data-ttu-id="70680-128">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="70680-128">RequiredVersion</span></span>| <span data-ttu-id="70680-129">Specifica la versione esatta del pacchetto da installare.</span><span class="sxs-lookup"><span data-stu-id="70680-129">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="70680-130">Se non si specifica questo parametro, la risorsa DSC installa la versione disponibile più recente del pacchetto che soddisfa anche l'eventuale requisito di versione massima specificato dal parametro _MaximumVersion_.</span><span class="sxs-lookup"><span data-stu-id="70680-130">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="70680-131">Source</span><span class="sxs-lookup"><span data-stu-id="70680-131">Source</span></span>| <span data-ttu-id="70680-132">Specifica il nome dell'origine del pacchetto in cui è possibile trovare il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="70680-132">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="70680-133">Può trattarsi di un URI o di un'origine registrata con la risorsa DSC `Register-PackageSource` o PackageManagementSource.</span><span class="sxs-lookup"><span data-stu-id="70680-133">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span>|
| <span data-ttu-id="70680-134">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="70680-134">SourceCredential</span></span> | <span data-ttu-id="70680-135">Specifica un account utente con i diritti per installare un pacchetto per un'origine o un provider di pacchetti specificato.</span><span class="sxs-lookup"><span data-stu-id="70680-135">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>|

## <a name="additional-parameters"></a><span data-ttu-id="70680-136">Parametri aggiuntivi</span><span class="sxs-lookup"><span data-stu-id="70680-136">Additional Parameters</span></span>

<span data-ttu-id="70680-137">Nella tabella seguente sono elencate le opzioni per la proprietà AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="70680-137">The following table lists options for the AdditionalParameters property.</span></span>

| <span data-ttu-id="70680-138">Parametro</span><span class="sxs-lookup"><span data-stu-id="70680-138">Parameter</span></span> | <span data-ttu-id="70680-139">Description</span><span class="sxs-lookup"><span data-stu-id="70680-139">Description</span></span> |
| --- | --- |
| <span data-ttu-id="70680-140">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="70680-140">DestinationPath</span></span>| <span data-ttu-id="70680-141">Usato dai provider, ad esempio il provider NuGet predefinito.</span><span class="sxs-lookup"><span data-stu-id="70680-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="70680-142">Specifica un percorso di file in cui si vuole installare il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="70680-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="70680-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="70680-143">InstallationPolicy</span></span>| <span data-ttu-id="70680-144">Usato dai provider, ad esempio il provider NuGet predefinito.</span><span class="sxs-lookup"><span data-stu-id="70680-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="70680-145">Determina se considerare attendibile l'origine del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="70680-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="70680-146">Uno dei valori `Untrusted` o `Trusted`.</span><span class="sxs-lookup"><span data-stu-id="70680-146">One of: `Untrusted`, `Trusted`.</span></span>|

## <a name="example"></a><span data-ttu-id="70680-147">Esempio</span><span class="sxs-lookup"><span data-stu-id="70680-147">Example</span></span>

<span data-ttu-id="70680-148">Questo esempio installa il pacchetto NuGet **JQuery** e il modulo di PowerShell **GistProvider** usando la risorsa DSC **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="70680-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="70680-149">Questo esempio verifica innanzitutto che siano disponibili le origini di pacchetti richieste e quindi definisce lo stato previsto dei pacchetti **JQuery** e **GistProvider** (rispettivamente, NuGet e PowerShell).</span><span class="sxs-lookup"><span data-stu-id="70680-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2/"
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