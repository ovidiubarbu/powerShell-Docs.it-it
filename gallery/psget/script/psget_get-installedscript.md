---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Get-InstalledScript
ms.openlocfilehash: f35e57cdadd1448bd9032ab007d692003c4cf4a2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="get-installedscript" class="xliff"></a>
# Get-InstalledScript

Ottiene gli script installati in un computer.

<a id="description" class="xliff"></a>
## Descrizione

Il cmdlet Get-InstalledScript ottiene gli script di PowerShell installati in un computer.

Per ogni script installato, Get-InstalledScript restituisce un oggetto PSRepositoryItemInfo che facoltativamente può essere inviato tramite pipe al cmdlet Uninstall-Script per la disinstallazione degli script installati.

- Get-InstalledScript consente di filtrare gli script installati in base ai parametri di nome e versione.
- Get-InstalledScript consente di filtrare usando i parametri di versione MinimumVersion, MaximumVersion, RequiredVersion e AllVersions.
  - Questi parametri si escludono a vicenda, ad eccezione di MinimumVersion e MaximumVersion.
  - I parametri di versione sono consentiti solo con il nome del singolo script senza caratteri jolly.
  - Se il parametro RequiredVersion non è specificato, Get-InstalledScript restituisce la versione più recente dello script installato maggiore o uguale alla versione minima specificata. Se la versione minima non è specificata, restituisce la versione più recente dello script. 
  - Se il parametro RequiredVersion è specificato, Get-InstalledScript restituisce unicamente la versione dello script installato che corrisponde esattamente alla versione specificata.

<a id="cmdlet-syntax" class="xliff"></a>
## Sintassi del cmdlet

```powershell
Get-Command -Name Get-InstalledScript -Module PowerShellGet -Syntax
```

<a id="cmdlet-online-help-reference" class="xliff"></a>
## Riferimento per la Guida online sui cmdlet

[Get-InstalledScript](http://go.microsoft.com/fwlink/?LinkId=619790)

<a id="example-commands" class="xliff"></a>
## Comandi di esempio

```powershell

# Get all scripts installed using PowerShellGet cmdlets
Get-InstalledScript

# Get a specific installed script
Get-InstalledScript Show-Tree

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.0      Show-Tree                           PSGallery            Script to show the layout of PowerShell namespaces (Tr...

# Get installed script with wildcards
Get-InstalledScript -Name *Azure*

# Get all versions of an installed script
Get-InstalledScript -Name Connect-O365 -AllVersions

# Get installed script with MinimumVersion
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1

# Get installed script with MaximumVersion
Get-InstalledScript -Name Connect-O365 -MaximumVersion 1.6.3

# Get installed script with version range
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.3

# Get installed script with RequiredVersion
Get-InstalledScript -Name Connect-O365 -RequiredVersion 1.4

# Properties of Get-InstalledScript returned object
Get-InstalledScript Show-Tree | Format-List * -Force

Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              : 5/4/2016 11:44:13 PM
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSScript}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {description, installeddate, tags, PackageManagementProvider...}
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts


```

