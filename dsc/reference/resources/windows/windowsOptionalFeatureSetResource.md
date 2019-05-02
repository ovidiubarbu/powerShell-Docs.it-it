---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsOptionalFeatureSet DSC
ms.openlocfilehash: c27d026e01bbb443a82112e37f1d199fb3482e49
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076974"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="d0ccc-103">Risorsa WindowsOptionalFeatureSet DSC</span><span class="sxs-lookup"><span data-stu-id="d0ccc-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="d0ccc-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d0ccc-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="d0ccc-105">La risorsa **WindowsOptionalFeatureSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per specificare le funzionalità facoltative abilitate in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="d0ccc-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>
<span data-ttu-id="d0ccc-106">Questa risorsa è una [risorsa composta](../../../resources/authoringResourceComposite.md) che chiama la [risorsa WindowsOptionalFeature](windowsOptionalFeatureResource.md) per ogni funzionalità specificata nella proprietà `Name`.</span><span class="sxs-lookup"><span data-stu-id="d0ccc-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="d0ccc-107">Usare questa risorsa quando si vogliono configurare diverse istanze di Windows facoltative nello stesso stato.</span><span class="sxs-lookup"><span data-stu-id="d0ccc-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="d0ccc-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d0ccc-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="d0ccc-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="d0ccc-109">Properties</span></span>

|  <span data-ttu-id="d0ccc-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="d0ccc-110">Property</span></span>  |  <span data-ttu-id="d0ccc-111">Description</span><span class="sxs-lookup"><span data-stu-id="d0ccc-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="d0ccc-112">Nome</span><span class="sxs-lookup"><span data-stu-id="d0ccc-112">Name</span></span>| <span data-ttu-id="d0ccc-113">Indica il nome delle funzionalità che si vogliono abilitare o disabilitare.</span><span class="sxs-lookup"><span data-stu-id="d0ccc-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span>|
| <span data-ttu-id="d0ccc-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="d0ccc-114">Ensure</span></span>| <span data-ttu-id="d0ccc-115">Specifica se le funzionalità sono abilitate.</span><span class="sxs-lookup"><span data-stu-id="d0ccc-115">Specifies whether the features are enabled.</span></span> <span data-ttu-id="d0ccc-116">Per specificare che le funzionalità sono abilitate impostare la proprietà su "Enable". Per specificare che le funzionalità sono disabilitate impostare la proprietà su "Disable".</span><span class="sxs-lookup"><span data-stu-id="d0ccc-116">To ensure that the features are enabled, set this property to "Enable" To ensure that the features are disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="d0ccc-117">Source</span><span class="sxs-lookup"><span data-stu-id="d0ccc-117">Source</span></span>| <span data-ttu-id="d0ccc-118">Non implementata.</span><span class="sxs-lookup"><span data-stu-id="d0ccc-118">Not implemented.</span></span>|
| <span data-ttu-id="d0ccc-119">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="d0ccc-119">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="d0ccc-120">Specifica se DISM contatta Windows Update (WU) durante la ricerca dei file di origine per abilitare le funzionalità.</span><span class="sxs-lookup"><span data-stu-id="d0ccc-120">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="d0ccc-121">Se $true, DISM non contatta WU.</span><span class="sxs-lookup"><span data-stu-id="d0ccc-121">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="d0ccc-122">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="d0ccc-122">RemoveFilesOnDisable</span></span>| <span data-ttu-id="d0ccc-123">Se è impostata su **$true** consente di rimuovere tutti i file associati alle funzionalità quando sono disabilitate (ossia, quando **Ensure** è impostata su "Absent").</span><span class="sxs-lookup"><span data-stu-id="d0ccc-123">Set to **$true** to remove all files associated with the features when they are disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="d0ccc-124">LogLevel</span><span class="sxs-lookup"><span data-stu-id="d0ccc-124">LogLevel</span></span>| <span data-ttu-id="d0ccc-125">Livello di output massimo per i log.</span><span class="sxs-lookup"><span data-stu-id="d0ccc-125">The maximum output level shown in the logs.</span></span> <span data-ttu-id="d0ccc-126">I valori accettati sono: "ErrorsOnly" (vengono registrati solo gli errori), "ErrorsAndWarning" (vengono registrati errori e avvisi) ed "ErrorsAndWarningAndInformation" (vengono registrati errori, avvisi e informazioni di debug).</span><span class="sxs-lookup"><span data-stu-id="d0ccc-126">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="d0ccc-127">LogPath</span><span class="sxs-lookup"><span data-stu-id="d0ccc-127">LogPath</span></span>| <span data-ttu-id="d0ccc-128">Percorso di un file di registro in cui si vuole che il provider di risorse registri l'operazione.</span><span class="sxs-lookup"><span data-stu-id="d0ccc-128">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="d0ccc-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d0ccc-129">DependsOn</span></span>| <span data-ttu-id="d0ccc-130">Specifica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="d0ccc-130">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d0ccc-131">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="d0ccc-131">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
