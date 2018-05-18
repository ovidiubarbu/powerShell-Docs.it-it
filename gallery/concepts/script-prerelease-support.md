---
ms.date: 10/17/2017
contributor: keithb
ms.topic: reference
keywords: raccolta,powershell,cmdlet,psget
title: Versioni non definitive degli script
ms.openlocfilehash: 2c7e1cbc352f8dc39fef9cd968b2f0c1964c30b3
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="prerelease-versions-of-scripts"></a><span data-ttu-id="28938-103">Versioni non definitive degli script</span><span class="sxs-lookup"><span data-stu-id="28938-103">Prerelease versions of scripts</span></span>

<span data-ttu-id="28938-104">A partire dalla versione 1.6.0, PowerShellGet e PowerShell Gallery consentono di contrassegnare le versioni successive alla versione 1.0.0 come versioni non definitive.</span><span class="sxs-lookup"><span data-stu-id="28938-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="28938-105">In precedenza, gli elementi non definitivi potevano avere solo una versione che iniziasse con 0.</span><span class="sxs-lookup"><span data-stu-id="28938-105">Prior to this feature, prerelease items were limited to having a version beginning with 0.</span></span> <span data-ttu-id="28938-106">L'obiettivo di queste funzionalità è quello di offrire un maggior supporto per la convenzione di controllo delle versioni [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) senza interrompere la compatibilità con le versioni precedenti con PowerShell versioni 3 e successive o le versioni esistenti di PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="28938-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="28938-107">Questo argomento illustra le funzionalità specifiche degli script.</span><span class="sxs-lookup"><span data-stu-id="28938-107">This topic focuses on the script-specific features.</span></span> <span data-ttu-id="28938-108">Le funzionalità equivalenti per i moduli sono descritte nell'argomento [Versioni di modulo non definitive](module-prerelease-support.md).</span><span class="sxs-lookup"><span data-stu-id="28938-108">The equivalent features for modules are in the [Prerelease Module Versions](module-prerelease-support.md) topic.</span></span> <span data-ttu-id="28938-109">Usando queste funzionalità, i server di pubblicazione possono identificare uno script come versione 2.5.0-alpha e rilasciare in seguito una versione pronta per la produzione 2.5.0 che sostituisce la versione non definitiva.</span><span class="sxs-lookup"><span data-stu-id="28938-109">Using these features, publishers can identify a script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="28938-110">In generale, le funzionalità di script non definitivo includono:</span><span class="sxs-lookup"><span data-stu-id="28938-110">At a high level, the prerelease script features include:</span></span>

- <span data-ttu-id="28938-111">Aggiunta di un suffisso PrereleaseString alla stringa di versione nel manifesto dello script.</span><span class="sxs-lookup"><span data-stu-id="28938-111">Adding a PrereleaseString suffix to the version string in the script manifest.</span></span> <span data-ttu-id="28938-112">Quando gli script vengono pubblicati in PowerShell Gallery, i dati vengono estratti dal manifesto e usati per identificare gli elementi di versione non definitiva.</span><span class="sxs-lookup"><span data-stu-id="28938-112">When the scripts is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease items.</span></span>
- <span data-ttu-id="28938-113">L'acquisizione degli elementi di versione non definitiva richiede l'aggiunta del flag -AllowPrerelease ai comandi di PowerShellGet Find-Script, Install-Script, Update-Script e Save-Script.</span><span class="sxs-lookup"><span data-stu-id="28938-113">Acquiring prerelease items requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Script, Install-Script, Update-Script, and Save-Script.</span></span> <span data-ttu-id="28938-114">Se il flag non viene specificato, gli elementi di versione non definitiva non vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="28938-114">If the flag is not specified, prerelease items will not be shown.</span></span>
- <span data-ttu-id="28938-115">Le versioni di script visualizzate da Find-Script, Get-InstalledScript e in PowerShell Gallery vengono visualizzate con PrereleaseString, come in 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="28938-115">Script versions displayed by Find-Script, Get-InstalledScript, and in the PowerShell Gallery will be displayed with the PrereleaseString, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="28938-116">Di seguito sono descritti i dettagli delle funzionalità.</span><span class="sxs-lookup"><span data-stu-id="28938-116">Details for the features are included below.</span></span>

## <a name="identifying-a-script-version-as-a-prerelease"></a><span data-ttu-id="28938-117">Identificazione di una versione di script come versione non definitiva</span><span class="sxs-lookup"><span data-stu-id="28938-117">Identifying a script version as a prerelease</span></span>

<span data-ttu-id="28938-118">Il supporto di PowerShellGet per le versioni non definitive è più semplice per gli script rispetto ai moduli.</span><span class="sxs-lookup"><span data-stu-id="28938-118">PowerShellGet support for prerelease versions is easier for scripts than modules.</span></span> <span data-ttu-id="28938-119">Poiché il controllo delle versioni degli script è supportato solo da PowerShellGet, non si verificano problemi di compatibilità causati dall'aggiunta della stringa di versione non definitiva.</span><span class="sxs-lookup"><span data-stu-id="28938-119">Script versioning is only supported by PowerShellGet, so there are no compatibility issues caused by adding the prerelease string.</span></span> <span data-ttu-id="28938-120">Per identificare uno script in PowerShell Gallery come versione non definitiva, aggiungere un suffisso di versione non definitiva a una stringa di versione formattata correttamente nei metadati dello script.</span><span class="sxs-lookup"><span data-stu-id="28938-120">To identify a script in the PowerShell Gallery as a prerelease, add a prerelease suffix to a properly-formatted version string in the script metadata.</span></span>

<span data-ttu-id="28938-121">Una sezione di esempio del manifesto di uno script con una versione non definitiva apparirà come segue:</span><span class="sxs-lookup"><span data-stu-id="28938-121">An example section of a script manifest with a prerelease version would look like the following:</span></span>

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>

```

<span data-ttu-id="28938-122">Per usare un suffisso di versione non definitiva, la stringa di versione deve soddisfare i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="28938-122">To use a prerelease suffix, the version string must meet the following requirements:</span></span>

- <span data-ttu-id="28938-123">È possibile specificare un suffisso di versione non definitiva solo quando la versione è 3 segmenti per Major.Minor.Build.</span><span class="sxs-lookup"><span data-stu-id="28938-123">A prerelease suffix may only be specified when the Version is 3 segments for Major.Minor.Build.</span></span>
  <span data-ttu-id="28938-124">Ciò è conforme alla convenzione SemVer v1.0.0</span><span class="sxs-lookup"><span data-stu-id="28938-124">This aligns with SemVer v1.0.0</span></span>
- <span data-ttu-id="28938-125">Il suffisso di versione non definitiva è una stringa che inizia con un segno meno e può contenere caratteri alfanumerici ASCII [0-9A-Za-z-]</span><span class="sxs-lookup"><span data-stu-id="28938-125">The prerelease suffix is a string which begins with a hyphen, and may contain ASCII alphanumerics [0-9A-Za-z-]</span></span>
- <span data-ttu-id="28938-126">Poiché attualmente sono supportate solo stringhe di versione non definitiva SemVer v1.0.0, il suffisso di versione non definitiva __non deve__ contenere punti o + [. +], consentiti in SemVer 2.0</span><span class="sxs-lookup"><span data-stu-id="28938-126">Only SemVer v1.0.0 prerelease strings are supported at this time, so the prerelease suffix __must not__ contain either period or + [.+], which are allowed in SemVer 2.0</span></span>
- <span data-ttu-id="28938-127">Esempi di stringhe PrereleaseString supportate includono: -alpha, -alpha1, -BETA, -update20171020</span><span class="sxs-lookup"><span data-stu-id="28938-127">Examples of supported PrereleaseString strings are: -alpha, -alpha1, -BETA, -update20171020</span></span>

<span data-ttu-id="28938-128">__Impatto del controllo delle versioni non definitive sull'ordinamento e sulle cartelle di installazione__</span><span class="sxs-lookup"><span data-stu-id="28938-128">__Prerelease versioning impact on sort order and installation folders__</span></span>

<span data-ttu-id="28938-129">Quando viene usata una versione non definitiva l'ordinamento viene modificato, un aspetto importante durante la pubblicazione in PowerShell Gallery e l'installazione di script con i comandi di PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="28938-129">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing scripts using PowerShellGet commands.</span></span> <span data-ttu-id="28938-130">Se sono presenti due versioni di script con numero di versione, l'ordinamento è basato sulla parte della stringa che segue il segno meno.</span><span class="sxs-lookup"><span data-stu-id="28938-130">If two scripts versions with the version number exist, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="28938-131">Di conseguenza, la versione 2.5.0-alpha è precedente alla versione 2.5.0-beta che è a sua volta precedente alla versione 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="28938-131">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="28938-132">Se due script hanno lo stesso numero di versione e uno solo include PrereleaseString, lo script __senza__ il suffisso di versione non definitiva viene considerato la versione pronta per la produzione e viene ordinato come versione successiva alla versione non definitiva.</span><span class="sxs-lookup"><span data-stu-id="28938-132">If two scripts have the same version number, and only one has a PrereleaseString, the script __without__ the prerelease suffix is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version.</span></span> <span data-ttu-id="28938-133">Ad esempio, quando viene eseguito il confronto delle versioni 2.5.0 e 2.5.0-beta, la versione 2.5.0 viene considerata la più recente.</span><span class="sxs-lookup"><span data-stu-id="28938-133">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="28938-134">Durante la pubblicazione in PowerShell Gallery, per impostazione predefinita la versione dello script in fase di pubblicazione deve essere successiva a qualsiasi versione pubblicata precedentemente presente in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="28938-134">When publishing to the PowerShell Gallery, by default the version of the script being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span> <span data-ttu-id="28938-135">Un server di pubblicazione può aggiornare la versione 2.5.0-alpha con la versione 2.5.0-beta o con la versione 2.5.0 (senza suffisso di versione non definitiva).</span><span class="sxs-lookup"><span data-stu-id="28938-135">A publisher may update version 2.5.0-alpha with 2.5.0-beta, or with 2.5.0 (with no prerelease suffix).</span></span>

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a><span data-ttu-id="28938-136">Ricerca e acquisizione di elementi di versione non definitiva mediante i comandi di PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="28938-136">Finding and acquiring prerelease items using PowerShellGet commands</span></span>

<span data-ttu-id="28938-137">L'uso di elementi di versione non definitiva con i comandi di PowerShellGet Find-Script, Install-Script, Update-Script e Save-Script richiede l'aggiunta del flag -AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="28938-137">Dealing with prerelease items using PowerShellGet Find-Script, Install-Script, Update-Script, and Save-Script commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="28938-138">Se il flag -AllowPrerelease è specificato, gli elementi di versione non definitiva, se presenti, vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="28938-138">If -AllowPrerelease is specified, prerelease items will be included if they are present.</span></span> <span data-ttu-id="28938-139">Se il flag -AllowPrerelease non è specificato, gli elementi di versione non definitiva non vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="28938-139">If -AllowPrerelease flag is not specified, prerelease items will not be shown.</span></span>

<span data-ttu-id="28938-140">Le uniche eccezioni nei comandi di script di PowerShellGet sono rappresentate da Get-InstalledScript e da alcuni casi di utilizzo di Uninstall-Script.</span><span class="sxs-lookup"><span data-stu-id="28938-140">The only exceptions to this in the PowerShellGet script commands are Get-InstalledScript, and some cases with Uninstall-Script.</span></span>

- <span data-ttu-id="28938-141">Get-InstalledScript visualizza sempre automaticamente le informazioni di versione non definitiva nella stringa di versione, se presente.</span><span class="sxs-lookup"><span data-stu-id="28938-141">Get-InstalledScript always will automatically show the prerelease information in the version string if it is present.</span></span>
- <span data-ttu-id="28938-142">Uninstall-Script disinstalla per impostazione predefinita la versione più recente di uno script, se non è specificata __alcuna versione__.</span><span class="sxs-lookup"><span data-stu-id="28938-142">Uninstall-Script will by default uninstall the most recent version of a script, if __no version__ is specified.</span></span> <span data-ttu-id="28938-143">Questo comportamento non è stato modificato.</span><span class="sxs-lookup"><span data-stu-id="28938-143">That behavior has not changed.</span></span> <span data-ttu-id="28938-144">Tuttavia, se una versione non definitiva viene specificata usando -RequiredVersion, è necessario specificare -AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="28938-144">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="28938-145">Esempi</span><span class="sxs-lookup"><span data-stu-id="28938-145">Examples</span></span>

```powershell
# Assume the PowerShell Gallery has TestPackage versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> Find-Script TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Find-Script TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# To install a prerelease, you must specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and script name 'TestPackage'.
Try Get-PSRepository to see all available registered script repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# Note that Get-InstalledScript shows the prerelease version.
# If -RequiredVersion is not specified, all installed scripts will be displayed by Get-InstalledScript
```

<span data-ttu-id="28938-146">Uninstall-Script rimuove la versione corrente di uno script quando non viene specificato -RequiredVersion.</span><span class="sxs-lookup"><span data-stu-id="28938-146">Uninstall-Script will remove the current version of a script when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="28938-147">Se -RequiredVersion è specificato e si tratta di una versione non definitiva, è necessario aggiungere -AllowPrerelease al comando.</span><span class="sxs-lookup"><span data-stu-id="28938-147">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha
Uninstall-Script: The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Script TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Script], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-script


C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
# Since script versions are not installed side-by-side, the above could be simply "Uninstall-Script TestPackage"

C:\windows\system32> Get-Installedscript TestPackage
PackageManagement\Get-Package : No match was found for the specified search criteria and script names 'testpackage'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.5.0.0\PSModule.psm1:4088 char:9
+         PackageManagement\Get-Package @PSBoundParameters | Microsoft. ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...lets.GetPackage:GetPackage) [Get-Package], Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.GetPackage
```

## <a name="more-details"></a><span data-ttu-id="28938-148">Altri dettagli</span><span class="sxs-lookup"><span data-stu-id="28938-148">More details</span></span>

- [<span data-ttu-id="28938-149">Versioni di modulo non definitive</span><span class="sxs-lookup"><span data-stu-id="28938-149">Prerelease Module Versions</span></span>](module-prerelease-support.md)
- [<span data-ttu-id="28938-150">Find-script</span><span class="sxs-lookup"><span data-stu-id="28938-150">Find-script</span></span>](/powershell/module/powershellget/find-script)
- [<span data-ttu-id="28938-151">Install-script</span><span class="sxs-lookup"><span data-stu-id="28938-151">Install-script</span></span>](/powershell/module/powershellget/install-script)
- [<span data-ttu-id="28938-152">Save-script</span><span class="sxs-lookup"><span data-stu-id="28938-152">Save-script</span></span>](/powershell/module/powershellget/save-script)
- [<span data-ttu-id="28938-153">Update-script</span><span class="sxs-lookup"><span data-stu-id="28938-153">Update-script</span></span>](/powershell/module/powershellget/update-script)
- [<span data-ttu-id="28938-154">Get-Installedscript</span><span class="sxs-lookup"><span data-stu-id="28938-154">Get-Installedscript</span></span>](/powershell/module/powershellget/get-installedscript)
- [<span data-ttu-id="28938-155">UnInstall-script</span><span class="sxs-lookup"><span data-stu-id="28938-155">UnInstall-script</span></span>](/powershell/module/powershellget/uninstall-script)