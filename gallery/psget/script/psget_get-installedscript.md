---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: raccolta,powershell,cmdlet,psget
title: Get-InstalledScript
ms.openlocfilehash: 668327905b0dab40119940a3134b674c452f538d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="get-installedscript"></a><span data-ttu-id="a66cf-103">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="a66cf-103">Get-InstalledScript</span></span>

<span data-ttu-id="a66cf-104">Ottiene gli script installati in un computer.</span><span class="sxs-lookup"><span data-stu-id="a66cf-104">Gets installed scripts on a computer.</span></span>

## <a name="description"></a><span data-ttu-id="a66cf-105">Description</span><span class="sxs-lookup"><span data-stu-id="a66cf-105">Description</span></span>

<span data-ttu-id="a66cf-106">Il cmdlet Get-InstalledScript ottiene gli script di PowerShell installati in un computer.</span><span class="sxs-lookup"><span data-stu-id="a66cf-106">The Get-InstalledScript cmdlet gets installed PowerShell scripts on a computer.</span></span>

<span data-ttu-id="a66cf-107">Per ogni script installato, Get-InstalledScript restituisce un oggetto PSRepositoryItemInfo che facoltativamente può essere inviato tramite pipe al cmdlet Uninstall-Script per la disinstallazione degli script installati.</span><span class="sxs-lookup"><span data-stu-id="a66cf-107">For each installed script, Get-InstalledScript returns a PSRepositoryItemInfo object which can optionally be piped to Uninstall-Script for uninstalling the installed scripts.</span></span>

- <span data-ttu-id="a66cf-108">Get-InstalledScript consente di filtrare gli script installati in base ai parametri di nome e versione.</span><span class="sxs-lookup"><span data-stu-id="a66cf-108">Get-InstalledScript can filter installed scripts based on name, version parameters.</span></span>
- <span data-ttu-id="a66cf-109">Get-InstalledScript consente di filtrare usando i parametri di versione MinimumVersion, MaximumVersion, RequiredVersion e AllVersions.</span><span class="sxs-lookup"><span data-stu-id="a66cf-109">Get-InstalledScript can filter with version parameters: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="a66cf-110">Questi parametri si escludono a vicenda, ad eccezione di MinimumVersion e MaximumVersion.</span><span class="sxs-lookup"><span data-stu-id="a66cf-110">These parameters are mutually exclusive, except MinmimumVersion and MaximumVersion.</span></span>
  - <span data-ttu-id="a66cf-111">I parametri di versione sono consentiti solo con il nome del singolo script senza caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="a66cf-111">These version parameters are allowed only with the single script name without any wildcards.</span></span>
  - <span data-ttu-id="a66cf-112">Se il parametro RequiredVersion non è specificato, Get-InstalledScript restituisce la versione più recente dello script installato maggiore o uguale alla versione minima specificata. Se la versione minima non è specificata, restituisce la versione più recente dello script.</span><span class="sxs-lookup"><span data-stu-id="a66cf-112">If the RequiredVersion parameter is not specified, Get-InstalledScript returns the latest version of the installed script that is equal to or greater than the minimum version specified or the latest version of the script if no minimum version is specified.</span></span>
  - <span data-ttu-id="a66cf-113">Se il parametro RequiredVersion è specificato, Get-InstalledScript restituisce unicamente la versione dello script installato che corrisponde esattamente alla versione specificata.</span><span class="sxs-lookup"><span data-stu-id="a66cf-113">If the RequiredVersion parameter is specified, Get-InstalledScript only returns the version of installed script that exactly matches the specified version.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="a66cf-114">Sintassi del cmdlet</span><span class="sxs-lookup"><span data-stu-id="a66cf-114">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Get-InstalledScript -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="a66cf-115">Riferimento per la Guida online sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="a66cf-115">Cmdlet online help reference</span></span>

[<span data-ttu-id="a66cf-116">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="a66cf-116">Get-InstalledScript</span></span>](http://go.microsoft.com/fwlink/?LinkId=619790)

## <a name="example-commands"></a><span data-ttu-id="a66cf-117">Comandi di esempio</span><span class="sxs-lookup"><span data-stu-id="a66cf-117">Example commands</span></span>

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