---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa PackageManagement DSC
ms.openlocfilehash: 28ae8772170bd4559c8a19c3a1df8c9118734857
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995973"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="9a5bb-103">Risorsa PackageManagement DSC</span><span class="sxs-lookup"><span data-stu-id="9a5bb-103">DSC PackageManagement Resource</span></span>

<span data-ttu-id="9a5bb-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="9a5bb-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="9a5bb-105">La risorsa **PackageManagement** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per installare o disinstallare pacchetti di Gestione pacchetti in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="9a5bb-106">Questa risorsa richiede il modulo **PackageManagement**, disponibile da [https://PowerShellGallery.com](https://PowerShellGallery.com).</span><span class="sxs-lookup"><span data-stu-id="9a5bb-106">This resource requires the **PackageManagement** module, available from [https://PowerShellGallery.com](https://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a5bb-107">La versione del modulo **PackageManagement** deve essere almeno la 1.1.7.0 affinché le informazioni sulle proprietà seguenti siano corrette.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="9a5bb-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9a5bb-108">Syntax</span></span>

```Syntax
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ AdditionalParameters = [HashTable] ]
    [ MaximumVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ ProviderName = [string] ]
    [ RequiredVersion = [string] ]
    [ Source = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="9a5bb-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="9a5bb-109">Properties</span></span>

|<span data-ttu-id="9a5bb-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="9a5bb-110">Property</span></span> |<span data-ttu-id="9a5bb-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9a5bb-111">Description</span></span> |
|---|---|
|<span data-ttu-id="9a5bb-112">Nome</span><span class="sxs-lookup"><span data-stu-id="9a5bb-112">Name</span></span> |<span data-ttu-id="9a5bb-113">Specifica il nome del pacchetto da installare o disinstallare.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-113">Specifies the name of the Package to be installed or uninstalled.</span></span> |
|<span data-ttu-id="9a5bb-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="9a5bb-114">AdditionalParameters</span></span> |<span data-ttu-id="9a5bb-115">Tabella hash specifica del provider dei parametri passati a `Get-Package -AdditionalArguments`.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="9a5bb-116">Ad esempio, per il provider NuGet è possibile passare parametri aggiuntivi come DestinationPath.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span> |
|<span data-ttu-id="9a5bb-117">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="9a5bb-117">MaximumVersion</span></span> |<span data-ttu-id="9a5bb-118">Specifica la versione massima consentita del pacchetto da trovare.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-118">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="9a5bb-119">Se non si aggiunge questo parametro, la risorsa trova la versione disponibile più recente del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-119">If you do not add this parameter, the resource finds the highest available version of the package.</span></span> |
|<span data-ttu-id="9a5bb-120">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="9a5bb-120">MinimumVersion</span></span> |<span data-ttu-id="9a5bb-121">Specifica la versione minima consentita del pacchetto da trovare.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-121">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="9a5bb-122">Se non si aggiunge questo parametro, la risorsa trova la versione disponibile più recente del pacchetto che soddisfa anche l'eventuale requisito di versione massima specificato dal parametro **MaximumVersion**.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-122">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the **MaximumVersion** parameter.</span></span> |
|<span data-ttu-id="9a5bb-123">ProviderName</span><span class="sxs-lookup"><span data-stu-id="9a5bb-123">ProviderName</span></span> |<span data-ttu-id="9a5bb-124">Specifica il nome di un provider di pacchetti entro il cui ambito limitare la ricerca di pacchetti.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-124">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="9a5bb-125">Per ottenere i nomi di provider di pacchetti, è possibile eseguire il cmdlet `Get-PackageProvider`.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-125">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span> |
|<span data-ttu-id="9a5bb-126">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="9a5bb-126">RequiredVersion</span></span> |<span data-ttu-id="9a5bb-127">Specifica la versione esatta del pacchetto da installare.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-127">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="9a5bb-128">Se non si specifica questo parametro, la risorsa DSC installa la versione disponibile più recente del pacchetto che soddisfa anche l'eventuale requisito di versione massima specificato dal parametro **MaximumVersion**.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-128">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the **MaximumVersion** parameter.</span></span> |
|<span data-ttu-id="9a5bb-129">Source (Sorgente)</span><span class="sxs-lookup"><span data-stu-id="9a5bb-129">Source</span></span> |<span data-ttu-id="9a5bb-130">Specifica il nome dell'origine del pacchetto in cui è possibile trovare il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-130">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="9a5bb-131">Può trattarsi di un URI o di un'origine registrata con la risorsa DSC `Register-PackageSource` o PackageManagementSource.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-131">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span> |
|<span data-ttu-id="9a5bb-132">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="9a5bb-132">SourceCredential</span></span> |<span data-ttu-id="9a5bb-133">Specifica un account utente con i diritti per installare un pacchetto per un'origine o un provider di pacchetti specificato.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-133">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span> |

## <a name="additional-parameters"></a><span data-ttu-id="9a5bb-134">Parametri aggiuntivi</span><span class="sxs-lookup"><span data-stu-id="9a5bb-134">Additional Parameters</span></span>

<span data-ttu-id="9a5bb-135">Nella tabella seguente sono elencate le opzioni per la proprietà AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-135">The following table lists options for the AdditionalParameters property.</span></span>

|<span data-ttu-id="9a5bb-136">Parametro</span><span class="sxs-lookup"><span data-stu-id="9a5bb-136">Parameter</span></span> |<span data-ttu-id="9a5bb-137">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9a5bb-137">Description</span></span> |
|---|---|
|<span data-ttu-id="9a5bb-138">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="9a5bb-138">DestinationPath</span></span> |<span data-ttu-id="9a5bb-139">Usato dai provider, ad esempio il provider NuGet predefinito.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-139">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="9a5bb-140">Specifica un percorso di file in cui si vuole installare il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-140">Specifies a file location where you want the package to be installed.</span></span> |
|<span data-ttu-id="9a5bb-141">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="9a5bb-141">InstallationPolicy</span></span> |<span data-ttu-id="9a5bb-142">Usato dai provider, ad esempio il provider NuGet predefinito.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-142">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="9a5bb-143">Determina se considerare attendibile l'origine del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-143">Determines whether you trust the package's source.</span></span> <span data-ttu-id="9a5bb-144">Uno dei valori possibili: **Untrusted** o **Trusted**.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-144">One of: **Untrusted** or **Trusted**.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="9a5bb-145">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="9a5bb-145">Common properties</span></span>

|<span data-ttu-id="9a5bb-146">Proprietà</span><span class="sxs-lookup"><span data-stu-id="9a5bb-146">Property</span></span> |<span data-ttu-id="9a5bb-147">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9a5bb-147">Description</span></span> |
|---|---|
|<span data-ttu-id="9a5bb-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="9a5bb-148">DependsOn</span></span> |<span data-ttu-id="9a5bb-149">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-149">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="9a5bb-150">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-150">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="9a5bb-151">Ensure</span><span class="sxs-lookup"><span data-stu-id="9a5bb-151">Ensure</span></span> |<span data-ttu-id="9a5bb-152">Determina se il pacchetto deve essere installato o disinstallato.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-152">Determines whether the package is to be installed or uninstalled.</span></span> <span data-ttu-id="9a5bb-153">Il valore predefinito è **Present**.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-153">The default value is **Present**.</span></span> |
|<span data-ttu-id="9a5bb-154">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="9a5bb-154">PsDscRunAsCredential</span></span> |<span data-ttu-id="9a5bb-155">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-155">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="9a5bb-156">La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-156">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="9a5bb-157">Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="9a5bb-157">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="9a5bb-158">Esempio</span><span class="sxs-lookup"><span data-stu-id="9a5bb-158">Example</span></span>

<span data-ttu-id="9a5bb-159">Questo esempio installa il pacchetto NuGet **JQuery** e il modulo di PowerShell **GistProvider** usando la risorsa DSC **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="9a5bb-159">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="9a5bb-160">Questo esempio verifica innanzitutto che siano disponibili le origini di pacchetti richieste e quindi definisce lo stato previsto dei pacchetti **JQuery** e **GistProvider** (rispettivamente, NuGet e PowerShell).</span><span class="sxs-lookup"><span data-stu-id="9a5bb-160">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

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
        SourceLocation   = "https://www.powershellgallery.com/api/v2"
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