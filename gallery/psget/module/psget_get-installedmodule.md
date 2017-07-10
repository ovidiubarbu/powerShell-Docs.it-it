---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: raccolta,powershell,cmdlet,psget
title: Get-InstalledModule
ms.openlocfilehash: 6f485d04503ea6d9a51a68ae7ec3d0dc2e6facab
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="get-installedmodule" class="xliff"></a>
# Get-InstalledModule

Ottiene i moduli installati in un computer.

<a id="description" class="xliff"></a>
## Descrizione

Il cmdlet Get-InstalledModule ottiene i moduli di PowerShell installati in un computer installati con il cmdlet Install-Module.

Per ogni modulo installato, Get-InstalledModule restituisce un oggetto PSRepositoryItemInfo che facoltativamente può essere inviato tramite pipe al cmdlet Uninstall-Module per la disinstallazione dei moduli installati.

- Get-InstalledModule consente di filtrare i moduli installati in base ai parametri di nome e versione.
- Get-InstalledModule consente di filtrare usando i parametri di versione MinimumVersion, MaximumVersion, RequiredVersion e AllVersions.
  - Questi parametri si escludono a vicenda, ad eccezione di MinimumVersion e MaximumVersion.
  - Questi parametri di versione sono consentiti solo con il nome del modulo singolo senza caratteri jolly.
  - Se il parametro RequiredVersion non è specificato, Get-InstalledModule restituisce la versione più recente del modulo installato maggiore o uguale alla versione minima specificata. Se la versione minima non è specificata, restituisce la versione più recente del modulo. 
  - Se il parametro RequiredVersion è specificato, Get-InstalledModule restituisce unicamente la versione del modulo installato che corrisponde esattamente alla versione specificata.

<a id="cmdlet-syntax" class="xliff"></a>
## Sintassi del cmdlet
```powershell
Get-Command -Name Get-InstalledModule -Module PowerShellGet -Syntax
```

<a id="cmdlet-online-help-reference" class="xliff"></a>
## Riferimento per la Guida online sui cmdlet

[Get-InstalledModule](http://go.microsoft.com/fwlink/?LinkId=526863)

<a id="example-commands" class="xliff"></a>
## Comandi di esempio

```powershell

# Get all modules installed using PowerShellGet cmdlets
Get-InstalledModule

# Get a specific installed module
Get-InstalledModule DJoin

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        DJoin                               PSGallery            This is a PowerShell frontend to the DJOIN.exe c...

# Get installed module with wildcards
Get-InstalledModule -Name AzureRM*

# Get all versions of an installed module
Get-InstalledModule -Name AzureRM.Automation -AllVersions

# Get installed module with MinimumVersion
Get-InstalledModule -Name AzureRM.Automation -MinimumVersion 1.0.0

# Get installed module with MaximumVersion
Get-InstalledModule -Name AzureRM.Automation -MaximumVersion 1.0.8

# Get installed module with version range
Get-InstalledModule -Name AzureRM.Automation -MinimumVersion 1.0.0 -MaximumVersion 1.0.8

# Get installed module with RequiredVersion
Get-InstalledScript -Name AzureRM.Automation -RequiredVersion 1.0.3

# Properties of Get-InstalledModule returned object
Get-InstalledModule DJoin | Format-List * -Force

Name                       : DJoin
Version                    : 1.0
Type                       : Module
Description                : This is a PowerShell frontend to the DJOIN.exe command which provides better
                             discoverability and usability.
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 7:12:37 PM
InstalledDate              : 4/5/2016 4:13:39 PM
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSModule}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {description, installeddate, tags, PackageManagementProvider...}
InstalledLocation          : C:\Program Files\WindowsPowerShell\Modules\DJoin\1.0

```



<a id="installeddate-and-updateddate-properties-in-psgetrepositoryiteminfo-object" class="xliff"></a>
## Proprietà InstalledDate e UpdatedDate nell'oggetto PSGetRepositoryItemInfo

    During the install operation:
        InstalledDate: current DateTime (Get-Date) value
        UpdatedDate: null

    During the Update operation:
        InstalledDate: InstalledDate from the previous installation otherwise current DateTime (Get-Date) value
        UpdatedDate: current DateTime (Get-Date) value

```powershell
Install-Module -Name ContosoServer -RequiredVersion 1.0 -Repository INT
Get-InstalledModule -Name ContosoServer | Format-Table Name, InstalledDate, UpdatedDate

Name          InstalledDate         UpdatedDate
----          -------------         -----------
ContosoServer 2/29/2016 11:59:14 AM


\Update-Module -Name ContosoServer
Get-InstalledModule -Name ContosoServer | Format-Table Name, InstalledDate, UpdatedDate

Name          InstalledDate         UpdatedDate
----          -------------         -----------
ContosoServer 2/29/2016 11:59:14 AM 2/29/2016 12:00:15 PM
```

