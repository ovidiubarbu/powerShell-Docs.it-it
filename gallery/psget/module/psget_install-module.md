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
# <a name="install-module"></a>Install-Module

Installa i moduli di PowerShell dal repository online nel computer locale.

## <a name="description"></a>Description

Il cmdlet Install-Module scarica uno o più moduli da una raccolta online, li convalida e li installa nell'ambito di installazione specificato nel computer locale.

Il cmdlet Install-Module ottiene da una raccolta online uno o più moduli che soddisfano criteri specificati, verifica che i risultati della ricerca siano moduli validi e copia le cartelle dei moduli nel percorso di installazione.

Quando non viene definito alcun ambito o quando il valore del parametro Scope è AllUsers, il modulo viene installato in %SystemDrive%:\Program Files\WindowsPowerShell\Modules. Quando il valore del parametro Scope è CurrentUser, il modulo viene installato in $home\Documents\WindowsPowerShell\Modules.

È possibile filtrare i risultati in base alle versioni minime o esatte dei moduli specificati.

- Supporto delle versioni side-by-side in Windows PowerShell 5.0 o versione successiva
- Supporto dell'installazione delle dipendenze del modulo
- **Prompt dei comandi non attendibile:** per installare i moduli da un repository non attendibile è necessaria l'accettazione utente.
- Il parametro Force reinstalla il modulo installato
- RequiredVersion installa la versione specificata side-by-side con le versioni esistenti in PowerShell 5.0 o versioni successive.

### <a name="scope"></a>Ambito
Specifica l'ambito di installazione del modulo. I valori accettabili per questo parametro sono AllUsers e CurrentUser.

L'ambito di installazione predefinito è AllUsers.

L'ambito AllUsers permette di installare i moduli in un percorso accessibile a tutti gli utenti del computer, vale a dire "$env:SystemDrive\Program Files\WindowsPowerShell\Modules".

L'ambito CurrentUser permette di installare i moduli solo in "$home\Documents\WindowsPowerShell\Modules", in modo che il modulo sia disponibile solo per l'utente corrente.

## <a name="notes"></a>Note

Questo cmdlet viene eseguito in Windows PowerShell 3.0 o versioni successive di Windows PowerShell, in Windows 7 o Windows 2008 R2 e nelle versioni successive di Windows.

Se non è possibile importare un modulo installato, ovvero se non è presente un file con estensione psm1, psd1 o dll con lo stesso nome nella cartella, l'installazione può riuscire unicamente se si aggiunge il parametro Force al comando.

Se una versione del modulo nel computer corrisponde al valore specificato per il parametro Name e non è stato aggiunto il parametro MinimumVersion o RequiredVersion, Install-Module continua automaticamente senza installare tale modulo. Se vengono specificati i parametri MinimumVersion o RequiredVersion e il modulo esistente non corrisponde ai valori in tale parametro, si verifica un errore. Nello specifico: se la versione del modulo attualmente installato è inferiore al valore del parametro MinimumVersion oppure è diversa dal valore del parametro RequiredVersion, si verifica un errore. Se la versione del modulo installato è maggiore del valore del parametro MinimumVersion oppure è uguale al valore del parametro RequiredVersion, Install-Module continua automaticamente senza installare tale modulo.

Se nella raccolta online non esiste alcun modulo corrispondente al nome specificato, Install-Module restituisce un errore.

Per installare più moduli, specificare una matrice dei nomi di modulo, separati da virgole. Se si specificano più nomi di modulo, non è possibile aggiungere i parametri MinimumVersion o RequiredVersion.

Per impostazione predefinita i moduli vengono installati nella cartella Programmi, per evitare confusione durante l'installazione di risorse DSC (Desired State Configuration) con Windows PowerShell. È anche possibile inviare pipe con più oggetti PSGetItemInfo a Install-Module, come metodo alternativo per specificare più moduli per l'installazione in un unico comando.

Per prevenire l'esecuzione di moduli che contengono malware, i moduli installati non vengono importati automaticamente dall'installazione. Per una sicurezza ottimale, valutare il codice del modulo prima di eseguire qualsiasi cmdlet o funzione in un modulo per la prima volta.


## <a name="cmdlet-syntax"></a>Sintassi del cmdlet
```powershell
Get-Command -Name Install-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Riferimento per la Guida online sui cmdlet

[Install-Module](http://go.microsoft.com/fwlink/?LinkID=398573)

## <a name="example-commands"></a>Comandi di esempio

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

## <a name="install-module-cmdlet-in-pipeline-operations"></a>Cmdlet Install-Module in operazioni di pipeline

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

## <a name="side-by-side-version-support-on-powershell-50-or-newer"></a>Supporto delle versioni side-by-side in PowerShell 5.0 o versione successiva

PowerShellGet supporta versioni side-by-side dei moduli nei cmdlet Install-Module, Update-Module e Publish-Module eseguiti in Windows PowerShell 5.0 o versioni successive.

### <a name="install-module-examples"></a>Esempi di Install-Module

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

## <a name="install-module-with-its-dependencies"></a>Installare un modulo con le relative dipendenze

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

## <a name="error-scenarios"></a>Scenari di errore

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