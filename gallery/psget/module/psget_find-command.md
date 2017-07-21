---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Find-Command
ms.openlocfilehash: f867f12b1c6efad30a04581c6f36c5a77a2fb2ae
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="find-command"></a><span data-ttu-id="19271-103">Find-Command</span><span class="sxs-lookup"><span data-stu-id="19271-103">Find-Command</span></span>

<span data-ttu-id="19271-104">Trova i comandi di PowerShell nei moduli.</span><span class="sxs-lookup"><span data-stu-id="19271-104">Finds PowerShell commands in modules.</span></span>

## <a name="description"></a><span data-ttu-id="19271-105">Descrizione</span><span class="sxs-lookup"><span data-stu-id="19271-105">Description</span></span>
<span data-ttu-id="19271-106">Il cmdlet Find-Command trova i comandi di PowerShell, ad esempio cmdlet, alias, funzioni e flussi di lavoro.</span><span class="sxs-lookup"><span data-stu-id="19271-106">The Find-Command cmdlet finds PowerShell commands such as cmdlets, aliases, functions, and workflows.</span></span> <span data-ttu-id="19271-107">Find-Command cerca nei moduli dei repository registrati.</span><span class="sxs-lookup"><span data-stu-id="19271-107">Find-Command searches modules in registered repositories.</span></span>
<span data-ttu-id="19271-108">Per ogni comando trovato da questo cmdlet, viene restituito un oggetto PSGetCommandInfo.</span><span class="sxs-lookup"><span data-stu-id="19271-108">For each command that this cmdlet finds, it returns a PSGetCommandInfo object.</span></span> <span data-ttu-id="19271-109">È possibile passare un oggetto PSGetCommandInfo al cmdlet Install-Module per installare il modulo che contiene il comando.</span><span class="sxs-lookup"><span data-stu-id="19271-109">You can pass a PSGetCommandInfo object to the Install-Module cmdlet to install the module that contains the command.</span></span>

- <span data-ttu-id="19271-110">Find-Command consente di filtrare usando i parametri di versione MinimumVersion, RequiredVersion e AllVersions.</span><span class="sxs-lookup"><span data-stu-id="19271-110">Find-Command can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="19271-111">Questi parametri si escludono a vicenda.</span><span class="sxs-lookup"><span data-stu-id="19271-111">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="19271-112">Questi parametri di versione sono consentiti solo con il nome del modulo singolo senza caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="19271-112">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="19271-113">Se il parametro RequiredVersion non è specificato, Find-Command restituisce la versione più recente del modulo maggiore o uguale alla versione minima specificata. Se la versione minima non è specificata, restituisce la versione più recente del modulo.</span><span class="sxs-lookup"><span data-stu-id="19271-113">If the RequiredVersion parameter is not specified, Find-Command returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="19271-114">Se il parametro RequiredVersion è specificato, Find-Command restituisce unicamente la versione del modulo che corrisponde esattamente alla versione specificata.</span><span class="sxs-lookup"><span data-stu-id="19271-114">If the RequiredVersion parameter is specified, Find-Command only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="19271-115">Find-Command consente di filtrare in base ai metadati del modulo usando il parametro -Tag</span><span class="sxs-lookup"><span data-stu-id="19271-115">Find-Command can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="19271-116">Find-Command consente di filtrare in base al linguaggio di ricerca specifico del repository usando il parametro -Filter.</span><span class="sxs-lookup"><span data-stu-id="19271-116">Find-Command can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="19271-117">Find-Command consente di filtrare in base ai moduli di tutti o alcuni dei repository registrati.</span><span class="sxs-lookup"><span data-stu-id="19271-117">Find-Command can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="19271-118">Sintassi del cmdlet</span><span class="sxs-lookup"><span data-stu-id="19271-118">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="19271-119">Riferimento per la Guida online sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="19271-119">Cmdlet online help reference</span></span>

[<span data-ttu-id="19271-120">Find-Command</span><span class="sxs-lookup"><span data-stu-id="19271-120">Find-Command</span></span>](http://go.microsoft.com/fwlink/?LinkId=733636)

## <a name="example-commands"></a><span data-ttu-id="19271-121">Comandi di esempio</span><span class="sxs-lookup"><span data-stu-id="19271-121">Example commands</span></span>
```powershell

# Find a specific command
Find-Command -Name Get-ScriptAnalyzerRule

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Get-ScriptAnalyzerRule              1.5.0      PSScriptAnalyzer                    PSGallery

# Find multiple commands
Find-Command -Name Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

# Find all available commands from all registered repositories
Find-Command

# Find available commands from few registered repositories
Find-Command -Repository PSGallery,PrivatePSGallery

# Find all commands in a specified repository
Find-Command -Repository PSGallery

# Find a command defined in a specific module
Find-Command -Name Get-ScriptAnalyzerRule -Module PSScriptAnalyzer

# Find commands from all versions of a module
Find-Command -ModuleName PSReadline -AllVersions

# Find commands with module name and MinimumVersion.
Find-Command -ModuleName PSReadline -MinimumVersion 1.1

# Find commands with module name and exact version
Find-Command -ModuleName AzureRM -RequiredVersion 1.4.0

# Find commands defined modules with -Filter based search. -Filter searches in description and module names
Find-Command -Filter Cookbook
Find-Command -Filter RBAC

# Find all commands with tags Azure or DSC in module metadata
Find-Command -Tag Azure, DSC

```

