---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: raccolta,powershell,cmdlet,psget
title: Find-DscResource
ms.openlocfilehash: 522a44e25c57a7dd75a098a1f34e53e74d96f4a6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="find-dscresource"></a><span data-ttu-id="27893-103">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="27893-103">Find-DscResource</span></span>

<span data-ttu-id="27893-104">Trova le risorse DSC nei moduli.</span><span class="sxs-lookup"><span data-stu-id="27893-104">Finds DSC Resources in modules.</span></span>

## <a name="description"></a><span data-ttu-id="27893-105">Description</span><span class="sxs-lookup"><span data-stu-id="27893-105">Description</span></span>

<span data-ttu-id="27893-106">Il cmdlet Find--DscResource trova le risorse [DSC (Desired State Configuration)](https://msdn.microsoft.com/PowerShell/dsc/overview) contenute nei moduli che corrispondono ai criteri specificati nei repository registrati.</span><span class="sxs-lookup"><span data-stu-id="27893-106">The Find-DscResource cmdlet finds [Desired State Configuration (DSC)](https://msdn.microsoft.com/PowerShell/dsc/overview) resources contained in modules that match the specified criteria from registered repositories.</span></span>
<span data-ttu-id="27893-107">Per ogni modulo trovato da questo cmdlet, Find-DscResource restituisce un oggetto PSGetDscResourceInfo che è possibile inviare tramite pipe a Install-Module per installare i moduli contenenti le risorse restituite da questo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="27893-107">For each module that this cmdlet finds, Find-DscResource returns a PSGetDscResourceInfo object that you can pipe to Install-Module to install the modules containing the resources that this cmdlet returns.</span></span>

<span data-ttu-id="27893-108">DSC è una nuova piattaforma di gestione di Windows PowerShell che consente di distribuire e gestire dati di configurazione per i servizi software, nonché di gestire l'ambiente in cui vengono eseguiti questi servizi.</span><span class="sxs-lookup"><span data-stu-id="27893-108">DSC is a new management platform in Windows PowerShell that enables deploying and managing configuration data for software services and managing the environment in which these services run.</span></span>

<span data-ttu-id="27893-109">Le risorse DSC (Desired State Configuration) forniscono i blocchi predefiniti per una configurazione DSC.</span><span class="sxs-lookup"><span data-stu-id="27893-109">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="27893-110">Una risorsa espone le proprietà che possono essere configurate (schema) e contiene le funzioni di script di PowerShell chiamate da Gestione configurazione locale per assicurare il risultato desiderato.</span><span class="sxs-lookup"><span data-stu-id="27893-110">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="27893-111">Una risorsa può modellare un elemento generico come un file o uno specifico come un'impostazione del server IIS.</span><span class="sxs-lookup"><span data-stu-id="27893-111">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span> <span data-ttu-id="27893-112">I gruppi di tali risorse sono combinati in un modulo DSC, che organizza tutti i file necessari in una struttura portatile che include i metadati che permettono di identificare il modo in cui si intende usare le risorse.</span><span class="sxs-lookup"><span data-stu-id="27893-112">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

- <span data-ttu-id="27893-113">Find-DscResource consente di filtrare usando i parametri di versione MinimumVersion, RequiredVersion e AllVersions.</span><span class="sxs-lookup"><span data-stu-id="27893-113">Find-DscResource can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="27893-114">Questi parametri si escludono a vicenda.</span><span class="sxs-lookup"><span data-stu-id="27893-114">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="27893-115">Questi parametri di versione sono consentiti solo con il nome del modulo singolo senza caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="27893-115">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="27893-116">Se il parametro RequiredVersion non è specificato, Find-DscResource restituisce la versione più recente del modulo maggiore o uguale alla versione minima specificata. Se la versione minima non è specificata, restituisce la versione più recente del modulo.</span><span class="sxs-lookup"><span data-stu-id="27893-116">If the RequiredVersion parameter is not specified, Find-DscResource returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="27893-117">Se il parametro RequiredVersion è specificato, Find-DscResource restituisce unicamente la versione del modulo che corrisponde esattamente alla versione specificata.</span><span class="sxs-lookup"><span data-stu-id="27893-117">If the RequiredVersion parameter is specified, Find-DscResource only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="27893-118">Find-DscResource consente di filtrare in base ai metadati del modulo usando il parametro -Tag</span><span class="sxs-lookup"><span data-stu-id="27893-118">Find-DscResource can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="27893-119">Find-DscResource consente di filtrare in base al linguaggio di ricerca specifico del repository usando il parametro -Filter.</span><span class="sxs-lookup"><span data-stu-id="27893-119">Find-DscResource can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="27893-120">Find-DscResource consente di filtrare in base ai moduli di tutti o alcuni dei repository registrati.</span><span class="sxs-lookup"><span data-stu-id="27893-120">Find-DscResource can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="27893-121">Sintassi del cmdlet</span><span class="sxs-lookup"><span data-stu-id="27893-121">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="27893-122">Riferimento per la Guida online sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="27893-122">Cmdlet online help reference</span></span>

[<span data-ttu-id="27893-123">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="27893-123">Find-DscResource</span></span>](http://go.microsoft.com/fwlink/?LinkId=517196)

## <a name="example-commands"></a><span data-ttu-id="27893-124">Comandi di esempio</span><span class="sxs-lookup"><span data-stu-id="27893-124">Example commands</span></span>
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```