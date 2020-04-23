---
ms.date: 09/26/2017
contributor: keithb
keywords: raccolta,powershell,cmdlet,psget
title: Versioni di modulo non definitive
ms.openlocfilehash: eced067dd21082de0db653daf3b838217154f1dd
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328142"
---
# <a name="prerelease-module-versions"></a><span data-ttu-id="ec0ef-103">Versioni di modulo non definitive</span><span class="sxs-lookup"><span data-stu-id="ec0ef-103">Prerelease Module Versions</span></span>

<span data-ttu-id="ec0ef-104">A partire dalla versione 1.6.0, PowerShellGet e PowerShell Gallery consentono di contrassegnare le versioni successive alla versione 1.0.0 come versioni non definitive.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="ec0ef-105">In precedenza, i pacchetti non definitivi potevano avere solo una versione che iniziava con 0.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-105">Prior to this feature, prerelease packages were limited to having a version beginning with 0.</span></span> <span data-ttu-id="ec0ef-106">L'obiettivo di queste funzionalità è quello di offrire un maggior supporto per la convenzione di controllo delle versioni [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) senza interrompere la compatibilità con le versioni precedenti con PowerShell versioni 3 e successive o le versioni esistenti di PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="ec0ef-107">Questo argomento illustra le funzionalità specifiche dei moduli.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-107">This topic focuses on the module-specific features.</span></span> <span data-ttu-id="ec0ef-108">Le funzionalità equivalenti per gli script sono descritte nell'argomento [Versioni non definitive degli script](script-prerelease-support.md).</span><span class="sxs-lookup"><span data-stu-id="ec0ef-108">The equivalent features for scripts are in the [Prerelease Versions of Scripts](script-prerelease-support.md) topic.</span></span> <span data-ttu-id="ec0ef-109">Usando queste funzionalità, i server di pubblicazione possono identificare un modulo o uno script come versione 2.5.0-alpha e rilasciare in seguito una versione pronta per la produzione 2.5.0 che sostituisce la versione non definitiva.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-109">Using these features, publishers can identify a module or script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="ec0ef-110">In generale, le funzionalità di modulo non definitivo includono:</span><span class="sxs-lookup"><span data-stu-id="ec0ef-110">At a high level, the prerelease module features include:</span></span>

- <span data-ttu-id="ec0ef-111">L'aggiunta di una stringa Prerelease alla sezione PSData del manifesto del modulo identifica il modulo come versione non definitiva.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-111">Adding a Prerelease string to the PSData section of the module manifest identifies the module as a prerelease version.</span></span> <span data-ttu-id="ec0ef-112">Quando il modulo viene pubblicato in PowerShell Gallery, i dati vengono estratti dal manifesto e usati per identificare i pacchetti in versione non definitiva.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-112">When the module is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease packages.</span></span>
- <span data-ttu-id="ec0ef-113">L'acquisizione di pacchetti in versione non definitiva richiede l'aggiunta del flag `-AllowPrerelease` ai comandi di PowerShellGet `Find-Module`, `Install-Module`, `Update-Module` e `Save-Module`.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-113">Acquiring prerelease packages requires adding `-AllowPrerelease` flag to the PowerShellGet commands `Find-Module`, `Install-Module`, `Update-Module`, and `Save-Module`.</span></span> <span data-ttu-id="ec0ef-114">Se il flag non viene specificato, i pacchetti in versione non definitiva non vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-114">If the flag is not specified, prerelease packages will not be shown.</span></span>
- <span data-ttu-id="ec0ef-115">Le versioni di modulo visualizzate da `Find-Module`, `Get-InstalledModule` e in PowerShell Gallery vengono visualizzate come stringa singola con la stringa Prerelease aggiunta alla fine, come nella versione 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-115">Module versions displayed by `Find-Module`, `Get-InstalledModule`, and in the PowerShell Gallery will be displayed as a single string with the Prerelease string appended, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="ec0ef-116">Di seguito sono descritti i dettagli delle funzionalità.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-116">Details for the features are included below.</span></span>

<span data-ttu-id="ec0ef-117">Queste modifiche non influiscono sul supporto della versione di modulo in PowerShell e sono compatibili con PowerShell 3.0, 4.0 e 5.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-117">These changes do not affect the module version support that is built into PowerShell, and are compatible with PowerShell 3.0, 4.0, and 5.</span></span>

## <a name="identifying-a-module-version-as-a-prerelease"></a><span data-ttu-id="ec0ef-118">Identificazione di una versione di modulo come versione non definitiva</span><span class="sxs-lookup"><span data-stu-id="ec0ef-118">Identifying a module version as a prerelease</span></span>

<span data-ttu-id="ec0ef-119">Il supporto di PowerShellGet per le versioni non definitive richiede l'uso di due campi all'interno del manifesto del modulo:</span><span class="sxs-lookup"><span data-stu-id="ec0ef-119">PowerShellGet support for prerelease versions requires the use of two fields within the Module Manifest:</span></span>

- <span data-ttu-id="ec0ef-120">ModuleVersion incluso nel manifesto del modulo deve essere una versione di 3 parti se viene usata una versione non definitiva e deve essere conforme al controllo delle versioni di PowerShell esistente.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-120">The ModuleVersion included in the module manifest must be a 3-part version if a prerelease version is used, and must comply with existing PowerShell versioning.</span></span> <span data-ttu-id="ec0ef-121">Il formato della versione è A.B.C, dove A, B e C sono tutti numeri interi.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-121">The version format would be A.B.C, where A, B, and C are all integers.</span></span>
- <span data-ttu-id="ec0ef-122">La stringa Prerelease è specificata nel manifesto del modulo, nella sezione PSData di PrivateData.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-122">The Prerelease string is specified in the module manifest, in the PSData section of PrivateData.</span></span>

<span data-ttu-id="ec0ef-123">Di seguito sono descritti nel dettaglio i requisiti della stringa Prerelease.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-123">Detailed requirements on the Prerelease string are below.</span></span>

<span data-ttu-id="ec0ef-124">Una sezione di esempio del manifesto di un modulo che definisce il modulo come versione non definitiva sarà simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="ec0ef-124">An example section of a module manifest that defines a module as a prerelease would look like the following:</span></span>

```powershell
@{
    ModuleVersion = '2.5.0'
    #---
    PrivateData = @{
        PSData = @{
            Prerelease = 'alpha'
        }
    }
}
```

<span data-ttu-id="ec0ef-125">I requisiti della stringa Prerelease sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="ec0ef-125">The detailed requirements for Prerelease string are:</span></span>

- <span data-ttu-id="ec0ef-126">È possibile specificare una stringa Prerelease solo quando ModuleVersion è 3 segmenti per Major.Minor.Build.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-126">Prerelease string may only be specified when the ModuleVersion is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="ec0ef-127">Ciò è conforme alla convenzione SemVer v1.0.0.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-127">This aligns with SemVer v1.0.0.</span></span>
- <span data-ttu-id="ec0ef-128">Un segno meno è il delimitatore tra il numero di build e la stringa Prerelease.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-128">A hyphen is the delimiter between the Build number and the Prerelease string.</span></span> <span data-ttu-id="ec0ef-129">È possibile includere un segno meno nella stringa Prerelease solo come primo carattere.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-129">A hyphen may be included in the Prerelease string as the first character, only.</span></span>
- <span data-ttu-id="ec0ef-130">La stringa Prerelease può contenere solo caratteri alfanumerici ASCII [0-9A-Za-z-].</span><span class="sxs-lookup"><span data-stu-id="ec0ef-130">The Prerelease string may contain only ASCII alphanumerics [0-9A-Za-z-].</span></span> <span data-ttu-id="ec0ef-131">È consigliabile fare in modo che la stringa Prerelease inizi con un carattere alfabetico per rendere più semplice l'identificazione di una versione non definitiva durante la ricerca in un elenco di pacchetti.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-131">It is a best practice to begin the Prerelease string with an alpha character, as it will be easier to identify that this is a prerelease version when scanning a list of packages.</span></span>
- <span data-ttu-id="ec0ef-132">Attualmente sono supportate solo stringhe Prerelease SemVer v1.0.0.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-132">Only SemVer v1.0.0 prerelease strings are supported at this time.</span></span> <span data-ttu-id="ec0ef-133">La stringa Prerelease **non deve** contenere punti o + [.+], consentiti in SemVer 2.0.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-133">Prerelease string **must not** contain either period or + [.+], which are allowed in SemVer 2.0.</span></span>
- <span data-ttu-id="ec0ef-134">Esempi di stringhe Prerelease supportate includono: -alpha, -alpha1, -BETA, -update20171020</span><span class="sxs-lookup"><span data-stu-id="ec0ef-134">Examples of supported Prerelease string are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="ec0ef-135">Impatto del controllo delle versioni non definitive sull'ordinamento e sulle cartelle di installazione</span><span class="sxs-lookup"><span data-stu-id="ec0ef-135">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="ec0ef-136">Quando viene usata una versione non definitiva l'ordinamento viene modificato, un aspetto importante durante la pubblicazione in PowerShell Gallery e l'installazione di moduli con i comandi di PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-136">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing modules using PowerShellGet commands.</span></span> <span data-ttu-id="ec0ef-137">Se la stringa Prerelease è specificata per due moduli, l'ordinamento è basato sulla parte di stringa che segue il segno meno.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-137">If the Prerelease string is specified for two modules, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="ec0ef-138">Di conseguenza, la versione 2.5.0-alpha è precedente alla versione 2.5.0-beta che è a sua volta precedente alla versione 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-138">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="ec0ef-139">Se due moduli hanno lo stesso ModuleVersion e uno solo include una stringa Prerelease, il modulo senza la stringa Prerelease viene considerato la versione pronta per la produzione e viene ordinato come versione successiva alla versione non definitiva (che include la stringa Prerelease).</span><span class="sxs-lookup"><span data-stu-id="ec0ef-139">If two modules have the same ModuleVersion, and only one has a Prerelease string, the module without the Prerelease string is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version (which includes the Prerelease string).</span></span> <span data-ttu-id="ec0ef-140">Ad esempio, quando viene eseguito il confronto delle versioni 2.5.0 e 2.5.0-beta, la versione 2.5.0 viene considerata la più recente.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-140">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="ec0ef-141">Durante la pubblicazione in PowerShell Gallery, per impostazione predefinita la versione del modulo in fase di pubblicazione deve essere successiva a qualsiasi versione pubblicata precedentemente presente in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-141">When publishing to the PowerShell Gallery, by default the version of the module being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a><span data-ttu-id="ec0ef-142">Ricerca e acquisizione di pacchetti in versione non definitiva mediante i comandi di PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="ec0ef-142">Finding and acquiring prerelease packages using PowerShellGet commands</span></span>

<span data-ttu-id="ec0ef-143">L'uso di pacchetti in versione non definitiva con i comandi di PowerShellGet Find-Module, Install-Module, Update-Module e Save-Module richiede l'aggiunta del flag -AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-143">Dealing with prerelease packages using PowerShellGet Find-Module, Install-Module, Update-Module, and Save-Module commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="ec0ef-144">Se il flag -AllowPrerelease è specificato, i pacchetti in versione non definitiva verranno inclusi, se presenti.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-144">If -AllowPrerelease is specified, prerelease packages will be included if they are present.</span></span> <span data-ttu-id="ec0ef-145">Se il flag -AllowPrerelease non è specificato, i pacchetti in versione non definitiva non verranno visualizzati.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-145">If -AllowPrerelease flag is not specified, prerelease packages will not be shown.</span></span>

<span data-ttu-id="ec0ef-146">Le uniche eccezioni nei comandi di modulo di PowerShellGet sono rappresentate da Get-InstalledModule e da alcuni casi di utilizzo di Uninstall-Module.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-146">The only exceptions to this in the PowerShellGet module commands are Get-InstalledModule, and some cases with Uninstall-Module.</span></span>

- <span data-ttu-id="ec0ef-147">Get-InstalledModule visualizza sempre automaticamente le informazioni di versione non definitiva nella stringa di versione per i moduli.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-147">Get-InstalledModule always will automatically show the prerelease information in the version string for modules.</span></span>
- <span data-ttu-id="ec0ef-148">Uninstall-Module disinstalla per impostazione predefinita la versione più recente di un modulo, se non è specificata __alcuna versione__.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-148">Uninstall-Module will by default uninstall the most recent version of a module, if __no version__ is specified.</span></span> <span data-ttu-id="ec0ef-149">Questo comportamento non è stato modificato.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-149">That behavior has not changed.</span></span> <span data-ttu-id="ec0ef-150">Tuttavia, se una versione non definitiva viene specificata usando -RequiredVersion, è necessario specificare -AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-150">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="ec0ef-151">Esempi</span><span class="sxs-lookup"><span data-stu-id="ec0ef-151">Examples</span></span>

<span data-ttu-id="ec0ef-152">Si supponga che PowerShell Gallery includa le versioni del modulo TestPackage 1.8.0 e 1.9.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-152">Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.</span></span> <span data-ttu-id="ec0ef-153">Se non si specifica `-AllowPrerelease`, verrà restituita solo la versione 1.8.0.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-153">If `-AllowPrerelease` is not specified, only version 1.8.0 will be returned.</span></span>

```powershell
find-module TestPackage
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.8.0          TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

```powershell
find-module TestPackage -AllowPrerelease
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.9.0-alpha    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="ec0ef-154">Per installare una versione non definitiva, specificare sempre -AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-154">To install a prerelease, always specify -AllowPrerelease.</span></span> <span data-ttu-id="ec0ef-155">Non è sufficiente specificare una stringa di versione non definitiva.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-155">Specifying a prerelease version string is not sufficient.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha
```

```output
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage
```

<span data-ttu-id="ec0ef-156">Il comando precedente non riesce perché non viene specificato -AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-156">The previous command failed because -AllowPrerelease was not specified.</span></span> <span data-ttu-id="ec0ef-157">L'aggiunta di `-AllowPrerelease` consentirà di completare correttamente l'operazione.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-157">Adding `-AllowPrerelease` will result in success.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="ec0ef-158">L'installazione side-by-side di versioni di un modulo che si differenziano solo per la versione non definitiva specificata non è supportata.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-158">Side-by-side installation of versions of a module that differ only due to the prerelease specified is not supported.</span></span> <span data-ttu-id="ec0ef-159">Quando si installa un modulo con PowerShellGet, versioni diverse dello stesso modulo vengono installate side-by-side creando un nome di cartella con ModuleVersion.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-159">When installing a module using PowerShellGet, different versions of the same module are installed side-by-side by creating a folder name using the ModuleVersion.</span></span> <span data-ttu-id="ec0ef-160">Per il nome di cartella viene usato ModuleVersion, senza la stringa Prerelease.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-160">The ModuleVersion, without the prerelease string, is used for the folder name.</span></span> <span data-ttu-id="ec0ef-161">Se un utente installa MyModule versione 2.5.0-alpha, il modulo viene installato nella cartella `MyModule\2.5.0`.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-161">If a user installs MyModule version 2.5.0-alpha, it will be installed to the `MyModule\2.5.0` folder.</span></span> <span data-ttu-id="ec0ef-162">Se l'utente installa quindi la versione 2.5.0-beta, la versione 2.5.0-beta **sovrascriverà** il contenuto della cartella `MyModule\2.5.0`.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-162">If the user then installs 2.5.0-beta, the 2.5.0-beta version will **overwrite** the contents of the folder `MyModule\2.5.0`.</span></span> <span data-ttu-id="ec0ef-163">Uno dei vantaggi di questo approccio è rappresentato dal fatto che non è necessario disinstallare la versione non definitiva dopo aver installato la versione pronta per la produzione.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-163">One advantage to this approach is that there is no need to un-install the prerelease version after installing the production-ready version.</span></span> <span data-ttu-id="ec0ef-164">L'esempio seguente mostra cosa accade:</span><span class="sxs-lookup"><span data-stu-id="ec0ef-164">The example below shows what to expect:</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-alpha     TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name            Repository  Description
-------        ----            ----------  -----------
1.9.0-beta     TestPackage     PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

```

<span data-ttu-id="ec0ef-165">Uninstall-Module rimuove la versione più recente di un modulo quando non viene specificato -RequiredVersion.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-165">Uninstall-Module will remove the latest version of a module when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="ec0ef-166">Se -RequiredVersion è specificato e si tratta di una versione non definitiva, è necessario aggiungere -AllowPrerelease al comando.</span><span class="sxs-lookup"><span data-stu-id="ec0ef-166">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
2.0.0-alpha1    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta

Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-Module

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
2.0.0-alpha1    TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...
```

## <a name="more-details"></a><span data-ttu-id="ec0ef-167">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="ec0ef-167">More details</span></span>

- [<span data-ttu-id="ec0ef-168">Versioni non definitive degli script</span><span class="sxs-lookup"><span data-stu-id="ec0ef-168">Prerelease Script Versions</span></span>](script-prerelease-support.md)
- [<span data-ttu-id="ec0ef-169">Find-Module</span><span class="sxs-lookup"><span data-stu-id="ec0ef-169">Find-Module</span></span>](/powershell/module/powershellget/find-module)
- [<span data-ttu-id="ec0ef-170">Install-Module</span><span class="sxs-lookup"><span data-stu-id="ec0ef-170">Install-Module</span></span>](/powershell/module/powershellget/install-module)
- [<span data-ttu-id="ec0ef-171">Save-Module</span><span class="sxs-lookup"><span data-stu-id="ec0ef-171">Save-Module</span></span>](/powershell/module/powershellget/save-module)
- [<span data-ttu-id="ec0ef-172">Update-Module</span><span class="sxs-lookup"><span data-stu-id="ec0ef-172">Update-Module</span></span>](/powershell/module/powershellget/Update-Module)
- [<span data-ttu-id="ec0ef-173">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="ec0ef-173">Get-InstalledModule</span></span>](/powershell/module/powershellget/get-installedmodule)
- [<span data-ttu-id="ec0ef-174">UnInstall-Module</span><span class="sxs-lookup"><span data-stu-id="ec0ef-174">UnInstall-Module</span></span>](/powershell/module/powershellget/uninstall-module)
