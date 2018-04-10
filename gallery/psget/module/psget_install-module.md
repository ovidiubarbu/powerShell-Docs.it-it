---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: raccolta,powershell,cmdlet,psget
title: Install-Module
ms.openlocfilehash: 960e3a85a0f915dd9da00f6456550a335c619cea
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="install-module"></a><span data-ttu-id="c60c7-103">Install-Module</span><span class="sxs-lookup"><span data-stu-id="c60c7-103">Install-Module</span></span>

<span data-ttu-id="c60c7-104">Installa i moduli di PowerShell dal repository online nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="c60c7-104">Installs the PowerShell modules from online repositories to the local computer.</span></span>

## <a name="description"></a><span data-ttu-id="c60c7-105">Description</span><span class="sxs-lookup"><span data-stu-id="c60c7-105">Description</span></span>

<span data-ttu-id="c60c7-106">Il cmdlet Install-Module scarica uno o più moduli da una raccolta online, li convalida e li installa nell'ambito di installazione specificato nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="c60c7-106">Install-Module cmdlet downloads one or more modules from an online gallery, validates and installs them on the local computer to the specified installation scope.</span></span>

<span data-ttu-id="c60c7-107">Il cmdlet Install-Module ottiene da una raccolta online uno o più moduli che soddisfano criteri specificati, verifica che i risultati della ricerca siano moduli validi e copia le cartelle dei moduli nel percorso di installazione.</span><span class="sxs-lookup"><span data-stu-id="c60c7-107">The Install-Module cmdlet gets one or more modules that meet specified criteria from an online gallery, verifies that search results are valid modules, and copies module folders to the installation location.</span></span>

<span data-ttu-id="c60c7-108">Quando non viene definito alcun ambito o quando il valore del parametro Scope è AllUsers, il modulo viene installato in %SystemDrive%:\Program Files\WindowsPowerShell\Modules.</span><span class="sxs-lookup"><span data-stu-id="c60c7-108">When no scope is defined, or when the value of the Scope parameter is AllUsers, the module is installed to %systemdrive%:\Program Files\WindowsPowerShell\Modules.</span></span> <span data-ttu-id="c60c7-109">Quando il valore del parametro Scope è CurrentUser, il modulo viene installato in $home\Documents\WindowsPowerShell\Modules.</span><span class="sxs-lookup"><span data-stu-id="c60c7-109">When the value of Scope is CurrentUser, the module is installed to $home\Documents\WindowsPowerShell\Modules.</span></span>

<span data-ttu-id="c60c7-110">È possibile filtrare i risultati in base alle versioni minime o esatte dei moduli specificati.</span><span class="sxs-lookup"><span data-stu-id="c60c7-110">You can filter your results based on minimum and exact versions of specified modules.</span></span>

- <span data-ttu-id="c60c7-111">Supporto delle versioni side-by-side in Windows PowerShell 5.0 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="c60c7-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
- <span data-ttu-id="c60c7-112">Supporto dell'installazione delle dipendenze del modulo</span><span class="sxs-lookup"><span data-stu-id="c60c7-112">Module dependency installation support</span></span>
- <span data-ttu-id="c60c7-113">**Prompt dei comandi non attendibile:** per installare i moduli da un repository non attendibile è necessaria l'accettazione utente.</span><span class="sxs-lookup"><span data-stu-id="c60c7-113">**Untrusted prompt:**User acceptance is required for installing the modules from an untrusted repository.</span></span>
- <span data-ttu-id="c60c7-114">Il parametro Force reinstalla il modulo installato</span><span class="sxs-lookup"><span data-stu-id="c60c7-114">-Force reinstalls the installed module</span></span>
- <span data-ttu-id="c60c7-115">RequiredVersion installa la versione specificata side-by-side con le versioni esistenti in PowerShell 5.0 o versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c60c7-115">RequiredVersion installs the specified version in SxS with existing versions on PowerShell version 5.0 or newer.</span></span>

### <a name="scope"></a><span data-ttu-id="c60c7-116">Ambito</span><span class="sxs-lookup"><span data-stu-id="c60c7-116">Scope</span></span>
<span data-ttu-id="c60c7-117">Specifica l'ambito di installazione del modulo.</span><span class="sxs-lookup"><span data-stu-id="c60c7-117">Specifies the installation scope of the module.</span></span> <span data-ttu-id="c60c7-118">I valori accettabili per questo parametro sono AllUsers e CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="c60c7-118">The acceptable values for this parameter are: AllUsers and CurrentUser.</span></span>

<span data-ttu-id="c60c7-119">L'ambito di installazione predefinito è AllUsers.</span><span class="sxs-lookup"><span data-stu-id="c60c7-119">The default installation scope is AllUsers.</span></span>

<span data-ttu-id="c60c7-120">L'ambito AllUsers permette di installare i moduli in un percorso accessibile a tutti gli utenti del computer, vale a dire "$env:SystemDrive\Program Files\WindowsPowerShell\Modules".</span><span class="sxs-lookup"><span data-stu-id="c60c7-120">The AllUsers scope lets modules be installed in a location that is accessible to all users of the computer, that is, "$env:SystemDrive\Program Files\WindowsPowerShell\Modules".</span></span>

<span data-ttu-id="c60c7-121">L'ambito CurrentUser permette di installare i moduli solo in "$home\Documents\WindowsPowerShell\Modules", in modo che il modulo sia disponibile solo per l'utente corrente.</span><span class="sxs-lookup"><span data-stu-id="c60c7-121">The CurrentUser scope lets modules be installed only to "$home\Documents\WindowsPowerShell\Modules", so that the module is available only to the current user.</span></span>

## <a name="notes"></a><span data-ttu-id="c60c7-122">Note</span><span class="sxs-lookup"><span data-stu-id="c60c7-122">Notes</span></span>

<span data-ttu-id="c60c7-123">Questo cmdlet viene eseguito in Windows PowerShell 3.0 o versioni successive di Windows PowerShell, in Windows 7 o Windows 2008 R2 e nelle versioni successive di Windows.</span><span class="sxs-lookup"><span data-stu-id="c60c7-123">This cmdlet runs on Windows PowerShell 3.0 or later releases of Windows PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="c60c7-124">Se non è possibile importare un modulo installato, ovvero se non è presente un file con estensione psm1, psd1 o dll con lo stesso nome nella cartella, l'installazione può riuscire unicamente se si aggiunge il parametro Force al comando.</span><span class="sxs-lookup"><span data-stu-id="c60c7-124">If an installed module cannot be imported (that is, if it does not have a .psm1, .psd1, or .dll of the same name within the folder), installation fails unless you add the Force parameter to your command.</span></span>

<span data-ttu-id="c60c7-125">Se una versione del modulo nel computer corrisponde al valore specificato per il parametro Name e non è stato aggiunto il parametro MinimumVersion o RequiredVersion, Install-Module continua automaticamente senza installare tale modulo.</span><span class="sxs-lookup"><span data-stu-id="c60c7-125">If a version of the module on the computer matches the value specified for the Name parameter, and you have not added the MinimumVersion or RequiredVersion parameter, Install-Module silently continues without installing that module.</span></span> <span data-ttu-id="c60c7-126">Se vengono specificati i parametri MinimumVersion o RequiredVersion e il modulo esistente non corrisponde ai valori in tale parametro, si verifica un errore.</span><span class="sxs-lookup"><span data-stu-id="c60c7-126">If the MinimumVersion or RequiredVersion parameters are specified, and the existing module does not match the values in that parameter, then an error occurs.</span></span> <span data-ttu-id="c60c7-127">Nello specifico: se la versione del modulo attualmente installato è inferiore al valore del parametro MinimumVersion oppure è diversa dal valore del parametro RequiredVersion, si verifica un errore.</span><span class="sxs-lookup"><span data-stu-id="c60c7-127">To be more specific: if the version of the currently-installed module is either lower than the value of the MinimumVersion parameter, or not equal to the value of the RequiredVersion parameter, an error occurs.</span></span> <span data-ttu-id="c60c7-128">Se la versione del modulo installato è maggiore del valore del parametro MinimumVersion oppure è uguale al valore del parametro RequiredVersion, Install-Module continua automaticamente senza installare tale modulo.</span><span class="sxs-lookup"><span data-stu-id="c60c7-128">If the version of the installed module is greater than the value of the MinimumVersion parameter, or equal to the value of the RequiredVersion parameter, Install-Module silently continues without installing that module.</span></span>

<span data-ttu-id="c60c7-129">Se nella raccolta online non esiste alcun modulo corrispondente al nome specificato, Install-Module restituisce un errore.</span><span class="sxs-lookup"><span data-stu-id="c60c7-129">Install-Module returns an error if no module exists in the online gallery that matches the specified name.</span></span>

<span data-ttu-id="c60c7-130">Per installare più moduli, specificare una matrice dei nomi di modulo, separati da virgole.</span><span class="sxs-lookup"><span data-stu-id="c60c7-130">To install multiple modules, specify an array of the module names, separated by commas.</span></span> <span data-ttu-id="c60c7-131">Se si specificano più nomi di modulo, non è possibile aggiungere i parametri MinimumVersion o RequiredVersion.</span><span class="sxs-lookup"><span data-stu-id="c60c7-131">You cannot add MinimumVersion or RequiredVersion if you specify multiple module names.</span></span>

<span data-ttu-id="c60c7-132">Per impostazione predefinita i moduli vengono installati nella cartella Programmi, per evitare confusione durante l'installazione di risorse DSC (Desired State Configuration) con Windows PowerShell. È anche possibile inviare pipe con più oggetti PSGetItemInfo a Install-Module, come metodo alternativo per specificare più moduli per l'installazione in un unico comando.</span><span class="sxs-lookup"><span data-stu-id="c60c7-132">By default, modules are installed to the Program Files folder, to prevent confusion when you are installing Windows PowerShell Desired State Configuration (DSC) resources.You can pipe multiple PSGetItemInfo objects to Install-Module; this is another way of specifying multiple modules to install in a single command.</span></span>

<span data-ttu-id="c60c7-133">Per prevenire l'esecuzione di moduli che contengono malware, i moduli installati non vengono importati automaticamente dall'installazione.</span><span class="sxs-lookup"><span data-stu-id="c60c7-133">To help prevent running modules that contain malicious code, installed modules are not automatically imported by installation.</span></span> <span data-ttu-id="c60c7-134">Per una sicurezza ottimale, valutare il codice del modulo prima di eseguire qualsiasi cmdlet o funzione in un modulo per la prima volta.</span><span class="sxs-lookup"><span data-stu-id="c60c7-134">As a security best practice, evaluate module code before running any cmdlets or functions in a module for the first time.</span></span>


## <a name="cmdlet-syntax"></a><span data-ttu-id="c60c7-135">Sintassi del cmdlet</span><span class="sxs-lookup"><span data-stu-id="c60c7-135">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Install-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="c60c7-136">Riferimento per la Guida online sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="c60c7-136">Cmdlet online help reference</span></span>

[<span data-ttu-id="c60c7-137">Install-Module</span><span class="sxs-lookup"><span data-stu-id="c60c7-137">Install-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398573)

## <a name="example-commands"></a><span data-ttu-id="c60c7-138">Comandi di esempio</span><span class="sxs-lookup"><span data-stu-id="c60c7-138">Example commands</span></span>

```powershell

# Install a module by name
Install-Module -Name MyDscModule

# Install multiple modules
Install-Module ContosoClient,ContosoServer

# Install a module using its minimum version
Install-Module -Name ContosoServer -MinimumVersion 1.0

# Install a specific version of a module
Install-Module -Name ContosoServer -RequiredVersion 1.1.3

# Install a specific prerelease version of a module
Install-Module -Name ContosoServer -RequiredVersion 1.1.3-alpha -AllowPrerelease

# Install the latest version of a module by name, including prelrelease versions if one exists
Install-Module -Name ContosoServer -AllowPrerelease

# Install the latest version of a module to $home\Documents\WindowsPowerShell\Modules.
Install-Module -Name ContosoServer -Scope CurrentUser

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Module ContosoServer -RequiredVersion 1.5

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Module ContosoServer -MinimumVersion 2.5

# Install multiple modules from multiple registered repositories
Install-Module ContosoClient,ContosoServer -Repository PSGallery, PrivatePSGallery

# Install a module with -WhatIf
Install-Module ContosoClient -WhatIf

# Install a module with -Confirm. A prompt will be displayed to confirm the installation.
Install-Module ContosoClient -WhatIf

# -Force option reinstalls the installed module
Install-Module ContosoClient -Force

# Install a module with dependencies
Install-Module -Name
```

## <a name="install-module-cmdlet-in-pipeline-operations"></a><span data-ttu-id="c60c7-139">Cmdlet Install-Module in operazioni di pipeline</span><span class="sxs-lookup"><span data-stu-id="c60c7-139">Install-Module cmdlet in pipeline operations</span></span>

```powershell

# Find a module and install it
Find-Module -Name "MyDSC*" | Install-Module

# Find a module and install it to the CurrentUser scope
Find-Module -Name "MyDSC*" | Install-Module -Scope CurrentUser

# Find commands by name and install them
# The first command finds the specified commands in the INT repository, and then uses the pipeline operator to pass them to Install-Module to install them.
# The second command uses Get-InstalledModule to verify the modules from the prior command are installed.
Find-Command -Repository "INT" -Name Get-ContosoClient,Get-ContosoServer | Install-Module
Get-InstalledModule

# This command finds the resource named MyResource and passes it to the Install-Module cmdlet by using the pipeline operator. The Install-Module cmdlet installs the module for the resource.
# If you pipe multiple resources to the Install-Module cmdlet from the same module, Install-Module attempts to install the module only once.
Find-DscResource -Name "MyResource" | Install-Module
Get-InstalledModule

# Find multiple role capabilities and install them
Find-RoleCapability -Name MyJeaRole, Maintenance | Install-Module
Get-InstalledModule

```

## <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="c60c7-140">Supporto delle versioni side-by-side in PowerShell 5.0 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="c60c7-140">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="c60c7-141">PowerShellGet supporta versioni side-by-side dei moduli nei cmdlet Install-Module, Update-Module e Publish-Module eseguiti in Windows PowerShell 5.0 o versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c60c7-141">PowerShellGet supports the side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>

### <a name="install-module-examples"></a><span data-ttu-id="c60c7-142">Esempi di Install-Module</span><span class="sxs-lookup"><span data-stu-id="c60c7-142">Install-Module examples</span></span>

```powershell
# Install a version of the module
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Install another version of the module in Side-by-Side with already installed version.
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name       : PSScriptAnalyzer
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Get all versions of an installed module
Get-InstalledModule -Name PSScriptAnalyzer -AllVersions
Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1.0      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis...
1.1.1      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis...


```

## <a name="install-module-with-its-dependencies"></a><span data-ttu-id="c60c7-143">Installare un modulo con le relative dipendenze</span><span class="sxs-lookup"><span data-stu-id="c60c7-143">Install module with its dependencies</span></span>

```powershell

# Find a module
Find-Module -Name TypePx -Repository PSGallery

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

# Find a module and its dependencies
Find-Module -Name TypePx -Repository PSGallery -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...

# Discover the dependencies list without adding -IncludeDependencies
$result = Find-Module -Name TypePx -Repository PSGallery
$result.Dependencies

Name                           Value
----                           -----
Name                           SnippetPx
CanonicalId                    powershellget:SnippetPx/#https://www.powershellgallery.com/api/v2/


# Now install the module along with its dependencies
Install-Module -Name TypePx -Repository PSGallery -Verbose

VERBOSE: Repository details, Name = 'PSGallery', Location = 'https://www.powershellgallery.com/api/v2/'; IsTrusted =
'False'; IsRegistered = 'True'.
VERBOSE: Using the provider 'PowerShellGet' for searching packages.
VERBOSE: Using the specified source names : 'PSGallery'.
VERBOSE: Getting the provider object for the PackageManagement Provider 'NuGet'.
VERBOSE: The specified Location is 'https://www.powershellgallery.com/api/v2/' and PackageManagementProvider is
'NuGet'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Total package yield:'1' for the specified package 'TypePx'.
VERBOSE: Performing the operation "Install-Module" on target "Version '2.0.1.20' of module 'TypePx'".

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
VERBOSE: The installation scope is specified to be 'AllUsers'.
VERBOSE: The specified module will be installed in 'C:\Program Files\WindowsPowerShell\Modules'.
VERBOSE: The specified Location is 'NuGet' and PackageManagementProvider is 'NuGet'.
VERBOSE: Downloading module 'TypePx' with version '2.0.1.20' from the repository
'https://www.powershellgallery.com/api/v2/'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='SnippetPx'' for ''.
VERBOSE: InstallPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\SnippetPx\SnippetPx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'SnippetPx'.
VERBOSE: Hash for package 'SnippetPx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: InstallPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\TypePx\TypePx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'TypePx'.
VERBOSE: Hash for package 'TypePx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: Installing the dependency module 'SnippetPx' with version '1.0.5.18' for the module 'TypePx'.
VERBOSE: Module 'SnippetPx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\SnippetPx\1.0.5.18'.
VERBOSE: Module 'TypePx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\TypePx\2.0.1.20'.


# Get the installed modules
Get-InstalledModule

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

```

## <a name="error-scenarios"></a><span data-ttu-id="c60c7-144">Scenari di errore</span><span class="sxs-lookup"><span data-stu-id="c60c7-144">Error scenarios</span></span>

```powershell

# Below command fails with 'NameShouldNotContainWildcardCharacters,Install-Module'
Install-Module ContosoServe*

# Below command fails with 'VersionRangeAndRequiredVersionCannotBeSpecifiedTogether,Install-Module'
Install-Module ContosoServer -MinimumVersion 1.0 -RequiredVersion 5.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Module'
Install-Module ContosoClient,ContosoServer -RequiredVersion 2.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Module'
Install-Module ContosoClient,ContosoServer -MinimumVersion 2.0

```