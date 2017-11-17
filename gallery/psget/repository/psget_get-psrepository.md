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
# <a name="get-psrepository"></a><span data-ttu-id="86125-103">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="86125-103">Get-PSRepository</span></span>

<span data-ttu-id="86125-104">Ottiene i repository registrati in un computer.</span><span class="sxs-lookup"><span data-stu-id="86125-104">Gets the registered repositories on a computer.</span></span>

## <a name="description"></a><span data-ttu-id="86125-105">Descrizione</span><span class="sxs-lookup"><span data-stu-id="86125-105">Description</span></span>

<span data-ttu-id="86125-106">Il cmdlet Get-PSRepository ottiene i repository del modulo di PowerShell registrati per l'utente corrente in un computer.</span><span class="sxs-lookup"><span data-stu-id="86125-106">The Get-PSRepository cmdlet gets PowerShell module repositories that are registered for the current user on a computer.</span></span>

<span data-ttu-id="86125-107">Per ogni repository registrato, Get-PSRepository restituisce un oggetto PSRepository che facoltativamente può essere inviato tramite pipe a Unregister-PSRepository per l'annullamento della registrazione di un repository registrato.</span><span class="sxs-lookup"><span data-stu-id="86125-107">For each registered repository, Get-PSRepository returns a PSRepository object which can optionally be piped to Unregister-PSRepository for unregistering a registered repository.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="86125-108">Sintassi del cmdlet</span><span class="sxs-lookup"><span data-stu-id="86125-108">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Get-PSRepository -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="86125-109">Riferimento per la Guida online sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="86125-109">Cmdlet online help reference</span></span>

[<span data-ttu-id="86125-110">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="86125-110">Get-PSRepository</span></span>](http://go.microsoft.com/fwlink/?LinkID=517127)

## <a name="example-commands"></a><span data-ttu-id="86125-111">Comandi di esempio</span><span class="sxs-lookup"><span data-stu-id="86125-111">Example commands</span></span>

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

