---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 9efc640dfda7e08e59d2c56746facd9658b1f9de
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222174"
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a><span data-ttu-id="97769-102">Individuazione, installazione e inventario dei moduli di PowerShell con PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="97769-102">PowerShell Module Discovery, Install and Inventory with PowerShellGet</span></span>

<span data-ttu-id="97769-103">PowerShellGet è incluso in questa versione di WMF:</span><span class="sxs-lookup"><span data-stu-id="97769-103">PowerShellGet is included in this release of WMF:</span></span>
-   <span data-ttu-id="97769-104">Find-Module consente di filtrare in base ai metadati del modulo con il parametro -Tag</span><span class="sxs-lookup"><span data-stu-id="97769-104">Find-Module can filter on module metadata with the -Tag parameter</span></span>
-   <span data-ttu-id="97769-105">Find-Module consente di filtrare in base al linguaggio di ricerca specifico del repository con il parametro -Filter</span><span class="sxs-lookup"><span data-stu-id="97769-105">Find-Module can filter on repository-specific search language with the -Filter parameter</span></span>
-   <span data-ttu-id="97769-106">Find-Module consente di filtrare in base al contenuto del modulo con i parametri -Command, -DscResource e -Includes</span><span class="sxs-lookup"><span data-stu-id="97769-106">Find-Module can filter based on module contents with the -Command, -DscResource, and -Includes parameters</span></span>
-   <span data-ttu-id="97769-107">Find-DscResource consente l'individuazione delle singole risorse DSC nei repository</span><span class="sxs-lookup"><span data-stu-id="97769-107">Find-DscResource allows discovery of individual DSC resources in repositories</span></span>
-   <span data-ttu-id="97769-108">Supporto per l'installazione da e la pubblicazione in condivisioni file con NuGet</span><span class="sxs-lookup"><span data-stu-id="97769-108">Support for installing from and publishing to file shares with NuGet</span></span>

## <a name="example-commands"></a><span data-ttu-id="97769-109">Comandi di esempio</span><span class="sxs-lookup"><span data-stu-id="97769-109">Example commands</span></span>
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

## <a name="new-features-in-powershellget"></a><span data-ttu-id="97769-110">Nuove funzionalità di PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="97769-110">New features in PowerShellGet</span></span>
-   <span data-ttu-id="97769-111">Supporto delle versioni side-by-side in Windows PowerShell 5.0 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="97769-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
-   <span data-ttu-id="97769-112">Supporto dell'installazione delle dipendenze del modulo</span><span class="sxs-lookup"><span data-stu-id="97769-112">Module dependency installation support</span></span>
-   <span data-ttu-id="97769-113">Tre nuovi cmdlet</span><span class="sxs-lookup"><span data-stu-id="97769-113">Three new cmdlets</span></span>
    -   <span data-ttu-id="97769-114">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="97769-114">Get-InstalledModule</span></span>
    -   <span data-ttu-id="97769-115">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="97769-115">Uninstall-Module</span></span>
    -   <span data-ttu-id="97769-116">Save-Module</span><span class="sxs-lookup"><span data-stu-id="97769-116">Save-Module</span></span>
