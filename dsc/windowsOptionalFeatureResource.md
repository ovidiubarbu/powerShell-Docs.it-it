---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsOptionalFeature DSC
ms.openlocfilehash: 388fbe1bc430098d6680902e0b5643243fbf7f4c
ms.sourcegitcommit: 79e8f03afb8d0b0bb0a167e56464929b27f51990
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2017
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="bf138-103">Risorsa WindowsOptionalFeature DSC</span><span class="sxs-lookup"><span data-stu-id="bf138-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="bf138-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bf138-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="bf138-105">La risorsa **WindowsOptionalFeature** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per specificare le funzionalità facoltative abilitate in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="bf138-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="bf138-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="bf138-106">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a><span data-ttu-id="bf138-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="bf138-107">Properties</span></span>

|  <span data-ttu-id="bf138-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="bf138-108">Property</span></span>  |  <span data-ttu-id="bf138-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="bf138-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="bf138-110">Name</span><span class="sxs-lookup"><span data-stu-id="bf138-110">Name</span></span>| <span data-ttu-id="bf138-111">Indica il nome della funzionalità che si vuole abilitare o disabilitare.</span><span class="sxs-lookup"><span data-stu-id="bf138-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span>| 
| <span data-ttu-id="bf138-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="bf138-112">Ensure</span></span>| <span data-ttu-id="bf138-113">Specifica se la funzionalità è abilitata.</span><span class="sxs-lookup"><span data-stu-id="bf138-113">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="bf138-114">Per specificare che la funzionalità è abilitata impostare la proprietà su "Enable". Per specificare che la funzionalità è disabilitata impostare la proprietà su "Disable".</span><span class="sxs-lookup"><span data-stu-id="bf138-114">To ensure that the feature is enabled, set this property to "Enable" To ensure that the feature is disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="bf138-115">Source</span><span class="sxs-lookup"><span data-stu-id="bf138-115">Source</span></span>| <span data-ttu-id="bf138-116">Non implementata.</span><span class="sxs-lookup"><span data-stu-id="bf138-116">Not implemented.</span></span>|
| <span data-ttu-id="bf138-117">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="bf138-117">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="bf138-118">Specifica se DISM contatta Windows Update (WU) durante la ricerca dei file di origine per abilitare una funzionalità.</span><span class="sxs-lookup"><span data-stu-id="bf138-118">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="bf138-119">Se $true, DISM non contatta WU.</span><span class="sxs-lookup"><span data-stu-id="bf138-119">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="bf138-120">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="bf138-120">RemoveFilesOnDisable</span></span>| <span data-ttu-id="bf138-121">Se è impostata su **$true** consente di rimuovere tutti i file associati alla funzionalità quando è disabilitata (ossia, quando **Ensure** è impostata su "Absent").</span><span class="sxs-lookup"><span data-stu-id="bf138-121">Set to **$true** to remove all files associated with the feature when it is disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="bf138-122">LogLevel</span><span class="sxs-lookup"><span data-stu-id="bf138-122">LogLevel</span></span>| <span data-ttu-id="bf138-123">Livello di output massimo per i log.</span><span class="sxs-lookup"><span data-stu-id="bf138-123">The maximum output level shown in the logs.</span></span> <span data-ttu-id="bf138-124">I valori consentiti sono: "ErrorsOnly" (vengono registrati solo gli errori), "ErrorsAndWarning" (vengono registrati errori e avvisi) e "ErrorsAndWarningAndInformation" (vengono registrati errori, avvisi e informazioni di debug).</span><span class="sxs-lookup"><span data-stu-id="bf138-124">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="bf138-125">LogPath</span><span class="sxs-lookup"><span data-stu-id="bf138-125">LogPath</span></span>| <span data-ttu-id="bf138-126">Percorso di un file di registro in cui si vuole che il provider di risorse registri l'operazione.</span><span class="sxs-lookup"><span data-stu-id="bf138-126">The path to a log file where you want the resource provider to log the operation.</span></span>| 
| <span data-ttu-id="bf138-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="bf138-127">DependsOn</span></span>| <span data-ttu-id="bf138-128">Specifica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="bf138-128">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="bf138-129">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="bf138-129">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
 



