---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: raccolta,powershell,cmdlet,psget
title: Get-PSRepository
ms.openlocfilehash: 96f87428312c233757aa5fcae405a192aadff385
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="get-psrepository" class="xliff"></a>
# Get-PSRepository

Ottiene i repository registrati in un computer.

<a id="description" class="xliff"></a>
## Descrizione

Il cmdlet Get-PSRepository ottiene i repository del modulo di PowerShell registrati per l'utente corrente in un computer.

Per ogni repository registrato, Get-PSRepository restituisce un oggetto PSRepository che facoltativamente può essere inviato tramite pipe a Unregister-PSRepository per l'annullamento della registrazione di un repository registrato.

<a id="cmdlet-syntax" class="xliff"></a>
## Sintassi del cmdlet
```powershell
Get-Command -Name Get-PSRepository -Module PowerShellGet -Syntax
```

<a id="cmdlet-online-help-reference" class="xliff"></a>
## Riferimento per la Guida online sui cmdlet

[Get-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517127)

<a id="example-commands" class="xliff"></a>
## Comandi di esempio

```powershell

# Properties of Get-PSRepository returned object
Get-PSRepository PSGallery | Format-List * -Force

Name                      : PSGallery
SourceLocation            : https://www.powershellgallery.com/api/v2/
Trusted                   : False
Registered                : True
InstallationPolicy        : Untrusted
PackageManagementProvider : NuGet
PublishLocation           : https://www.powershellgallery.com/api/v2/package/
ScriptSourceLocation      : https://www.powershellgallery.com/api/v2/items/psscript/
ScriptPublishLocation     : https://www.powershellgallery.com/api/v2/package/
ProviderOptions           : {}

# Get all registered repositories
Get-PSRepository

# Get a specific registered repository
Get-PSRepository PSGallery

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
PSGallery                 Untrusted            https://www.powershellgallery.com/api/v2/

# Get registered repository with wildcards
Get-PSRepository *Gallery*

```

