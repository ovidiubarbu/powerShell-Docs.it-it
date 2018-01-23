---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsOptionalFeatureSet DSC
ms.openlocfilehash: 6912e5cf92f23058342bc566bd66dc4be3357a30
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="84908-103">Risorsa WindowsOptionalFeatureSet DSC</span><span class="sxs-lookup"><span data-stu-id="84908-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="84908-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="84908-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="84908-105">La risorsa **WindowsOptionalFeatureSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per specificare le funzionalità facoltative abilitate in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="84908-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span> <span data-ttu-id="84908-106">Questa risorsa è una [risorsa composta](authoringResourceComposite.md) che chiama la [risorsa WindowsOptionalFeature](windowsOptionalFeatureResource.md) per ogni funzionalità specificata nella proprietà `Name`.</span><span class="sxs-lookup"><span data-stu-id="84908-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="84908-107">Usare questa risorsa quando si vogliono configurare diverse istanze di Windows facoltative nello stesso stato.</span><span class="sxs-lookup"><span data-stu-id="84908-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="84908-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="84908-108">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ] 
    [ RemoveFilesOnDisable = [bool] ]  
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a><span data-ttu-id="84908-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="84908-109">Properties</span></span>

|  <span data-ttu-id="84908-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="84908-110">Property</span></span>  |  <span data-ttu-id="84908-111">Description</span><span class="sxs-lookup"><span data-stu-id="84908-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="84908-112">Nome</span><span class="sxs-lookup"><span data-stu-id="84908-112">Name</span></span>| <span data-ttu-id="84908-113">Indica il nome delle funzionalità che si vogliono abilitare o disabilitare.</span><span class="sxs-lookup"><span data-stu-id="84908-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span>| 
| <span data-ttu-id="84908-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="84908-114">Ensure</span></span>| <span data-ttu-id="84908-115">Specifica se le funzionalità sono abilitate.</span><span class="sxs-lookup"><span data-stu-id="84908-115">Specifies whether the features are enabled.</span></span> <span data-ttu-id="84908-116">Per specificare che le funzionalità sono abilitate impostare la proprietà su "Enable". Per specificare che le funzionalità sono disabilitate impostare la proprietà su "Disable".</span><span class="sxs-lookup"><span data-stu-id="84908-116">To ensure that the features are enabled, set this property to "Enable" To ensure that the features are disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="84908-117">Source</span><span class="sxs-lookup"><span data-stu-id="84908-117">Source</span></span>| <span data-ttu-id="84908-118">Non implementata.</span><span class="sxs-lookup"><span data-stu-id="84908-118">Not implemented.</span></span>|
| <span data-ttu-id="84908-119">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="84908-119">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="84908-120">Specifica se DISM contatta Windows Update (WU) durante la ricerca dei file di origine per abilitare le funzionalità.</span><span class="sxs-lookup"><span data-stu-id="84908-120">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="84908-121">Se $true, DISM non contatta WU.</span><span class="sxs-lookup"><span data-stu-id="84908-121">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="84908-122">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="84908-122">RemoveFilesOnDisable</span></span>| <span data-ttu-id="84908-123">Se è impostata su **$true** consente di rimuovere tutti i file associati alle funzionalità quando sono disabilitate (ossia, quando **Ensure** è impostata su "Absent").</span><span class="sxs-lookup"><span data-stu-id="84908-123">Set to **$true** to remove all files associated with the features when they are disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="84908-124">LogLevel</span><span class="sxs-lookup"><span data-stu-id="84908-124">LogLevel</span></span>| <span data-ttu-id="84908-125">Livello di output massimo per i log.</span><span class="sxs-lookup"><span data-stu-id="84908-125">The maximum output level shown in the logs.</span></span> <span data-ttu-id="84908-126">I valori consentiti sono: "ErrorsOnly" (vengono registrati solo gli errori), "ErrorsAndWarning" (vengono registrati errori e avvisi) e "ErrorsAndWarningAndInformation" (vengono registrati errori, avvisi e informazioni di debug).</span><span class="sxs-lookup"><span data-stu-id="84908-126">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="84908-127">LogPath</span><span class="sxs-lookup"><span data-stu-id="84908-127">LogPath</span></span>| <span data-ttu-id="84908-128">Percorso di un file di registro in cui si vuole che il provider di risorse registri l'operazione.</span><span class="sxs-lookup"><span data-stu-id="84908-128">The path to a log file where you want the resource provider to log the operation.</span></span>| 
| <span data-ttu-id="84908-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="84908-129">DependsOn</span></span>| <span data-ttu-id="84908-130">Specifica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="84908-130">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="84908-131">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="84908-131">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
 



