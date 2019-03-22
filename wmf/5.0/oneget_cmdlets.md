---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 042e9a30068d32dc5860255bdec960371121d866
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795097"
---
# <a name="packagemanagement-cmdlets"></a>Cmdlet PackageManagement

Questi sono gli elementi centrali del modulo PackageManagement per il supporto di individuazione, installazione e inventario del software. Provare i cmdlet per queste operazioni:

- `Find-Package`
- `Find-PackageProvider`
- `Get-Package`
- `Get-PackageProvider`
- `Get-PackageSource`
- `Import-PackageProvider`
- `Install-Package`
- `Install-PackageProvider`
- `Register-PackageSource`
- `Save-Package`
- `Set-PackageSource`
- `Uninstall-Package`
- `Unregister-PackageSource`

Dato che PackageManagement è un modulo di PowerShell, è possibile eseguire il comando seguente per aggiornare il modulo PackageManagement stesso:

```powershell
Install-Module PackageManagement –Force
```

In questo caso, è necessario accedere di nuovo alla sessione di PowerShell per passare alla nuova versione di PackageManagement.

## <a name="find-package-cmdletpowershellmodulepackagemanagementfind-package"></a>[Cmdlet Find-Package](/powershell/module/PackageManagement/Find-Package)

Questo cmdlet consente l'individuazione dei pacchetti software in origini pacchetti disponibili tramite provider di pacchetti caricati.

```powershell
# Find all available Windows PowerShell module packages from galleries registered
# with PowerShellGet provider
Find-Package -ProviderName PowerShellGet -Source as source
Find-Package -Name jquery –Provider NuGet -Source http://www.nuget.org/api/v2/

# Find package with name and version
# Here we are assuming that the user already registered nuget.org using
# Register-PackageSource. You can specify either the provider or the source, or
# neither. For the latter, performance may be less optimal as it searches through all
# the providers and registered sources.
Find-Package -Name jquery –Provider NuGet –RequiredVersion 2.1.4 -Source nuget.org
```

## <a name="find-packageprovider-cmdletpowershellmodulepackagemanagementfind-packageprovider"></a>[Cmdlet Find-PackageProvider](/powershell/module/PackageManagement/Find-PackageProvider)

Il cmdlet `Find-PackageProvider` consente di trovare i provider PackageManagement corrispondenti disponibili nelle origini pacchetti registrate con PowerShellGet. Questi sono i provider di pacchetti disponibili per l'installazione con il cmdlet `Install-PackageProvider`. Per impostazione predefinita, sono inclusi i moduli disponibili in PowerShell Gallery con i tag 'PackageManagement' e 'Provider'.

`Find-PackageProvider` consente anche di trovare i provider PackageManagement corrispondenti disponibili nell'archivio BLOB di Azure di PackageManagement, in cui viene usato il provider di boostrapper PackageManagement per la ricerca e l'installazione.

```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

## <a name="get-package-cmdletpowershellmodulepackagemanagementget-package"></a>[Cmdlet Get-Package](/powershell/module/PackageManagement/Get-Package)

Questo cmdlet restituisce un elenco di tutti i pacchetti software installati con PackageManagement.

```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdletpowershellmodulepackagemanagementget-packageprovider"></a>[Cmdlet Get-PackageProvider](/powershell/module/PackageManagement/Get-PackageProvider)

I provider di pacchetti caricati e pronti per l'uso nel computer locale possono essere inclusi nell'inventario tramite il cmdlet.

```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdletpowershellmodulepackagemanagementget-packagesource"></a>[Cmdlet Get-PackageSource](/powershell/module/PackageManagement/Get-PackageSource)

Questo cmdlet consente di ottenere un elenco di origini pacchetti registrate per un provider di pacchetti.

```powershell
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdletpowershellmodulepackagemanagementimport-packageprovider"></a>[Cmdlet Import-PackageProvider](/powershell/module/PackageManagement/Import-PackageProvider)

Questo cmdlet consente di aggiungere provider di pacchetti PackageManagement alla sessione corrente.

```powershell
# Import a package provider from the local machine
Import-PackageProvider –Name MyProvider

#The -Name parameter can be either the name of the provider or the full path to the provider. Currently, we support .dll, .exe and.psm1 for the full path case. If the name of the provider is used for the -Name parameter, then additional version parameters such as -RequiredVersion, -MinimumVersion and -MaximumVersion may be specified. Otherwise, the latest version of the provider will be imported.

#If a package provider is not yet loaded to your system, we can discover and install on-demand. You can use explicit discovery and install cmdlets to do so:
 Find-PackageProvider
 Install-PackageProvider –Name MyProvider

#After installed, follow the Import-PackageProvider to load it to your system.

# Import a specific version of a package provider. PackageManagement supports installations of multiple versions of a package provider using PackageProvider cmdlets (not by bootstrapper provider). You can install another version of a package provider given that you already have one up running by:
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider –ListAvailable
Import-PackageProvider –Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
Import-PackageProvider –Name MyProvider –RequiredVersion xxxx -force
```

## <a name="install-package-cmdletpowershellmodulepackagemanagementinstall-package"></a>[Cmdlet Install-Package](/powershell/module/PackageManagement/Install-Package)

Questo cmdlet consente l'installazione dei pacchetti software in origini pacchetti disponibili tramite provider di pacchetti caricati.

```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## <a name="install-packageprovider-cmdletpowershellmodulepackagemanagementinstall-packageprovider"></a>[Cmdlet Install-PackageProvider](/powershell/module/PackageManagement/Install-PackageProvider)

Questo cmdlet consente di installare uno o più provider di pacchetti PackageManagement.

```powershell
# Install a package provider from the PowerShell Gallery
Install-PackageProvider –Name "Gistprovider" -Verbose

# Install a specified version of a package provider
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force

# Find a provider and install it
Find-PackageProvider –Name "Gistprovider" | Install-PackageProvider -Verbose

# Install a provider to the current user’s module folder
Install-PackageProvider –Name Gistprovider –Verbose –Scope CurrentUser
```

## <a name="register-packagesource-cmdletpowershellmodulepackagemanagementregister-packagesource"></a>[Cmdlet Register-PackageSource](/powershell/module/PackageManagement/Register-PackageSource)

Questo cmdlet consente di aggiungere un'origine pacchetto per un provider di pacchetti specificato.
Ogni provider PackageManagement può avere una o più origini software, o repository. PackageManagement fornisce i cmdlet di PowerShell per aggiungere, rimuovere o recuperare informazioni dall'origine. Ad esempio, è possibile registrare un'origine pacchetto per il provider NuGet:

```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdletpowershellmodulepackagemanagementsave-package"></a>[Cmdlet Save-Package](/powershell/module/PackageManagement/Save-Package)

Questo cmdlet consente di salvare i pacchetti nel computer locale senza eseguirne l'installazione.

```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -Source c:\test
```

## <a name="set-packagesource-cmdletpowershellmodulepackagemanagementset-packagesource"></a>[Cmdlet Set-PackageSource](/powershell/module/PackageManagement/Set-PackageSource)

Questo cmdlet consente di modificare le informazioni su un'origine pacchetto esistente.

```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2
```

## <a name="uninstall-package-cmdletpowershellmodulepackagemanagementuninstall-package"></a>[Cmdlet Uninstall-Package](/powershell/module/PackageManagement/Uninstall-Package)

Questo cmdlet consente di disinstallare i pacchetti installati nel computer locale.

```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdletpowershellmodulepackagemanagementunregister-packagesource"></a>[Cmdlet Unregister-PackageSource](/powershell/module/PackageManagement/Unregister-PackageSource)

```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```