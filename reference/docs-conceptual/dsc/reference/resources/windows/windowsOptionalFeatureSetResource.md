---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsOptionalFeatureSet DSC
ms.openlocfilehash: f378006a6c362ee9890d70dd76fb552dd262a544
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71952868"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="9e28f-103">Risorsa WindowsOptionalFeatureSet DSC</span><span class="sxs-lookup"><span data-stu-id="9e28f-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="9e28f-104">Si applica a: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="9e28f-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="9e28f-105">La risorsa **WindowsOptionalFeatureSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per specificare le funzionalità facoltative abilitate in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="9e28f-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span> <span data-ttu-id="9e28f-106">Questa risorsa è una [risorsa composita](../../../resources/authoringResourceComposite.md) che chiama la [risorsa WindowsOptionalFeature](windowsOptionalFeatureResource.md) per ogni funzionalità specificata nella proprietà **Name**.</span><span class="sxs-lookup"><span data-stu-id="9e28f-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="9e28f-107">Usare questa risorsa quando si vogliono configurare diverse istanze di Windows facoltative nello stesso stato.</span><span class="sxs-lookup"><span data-stu-id="9e28f-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="9e28f-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9e28f-108">Syntax</span></span>

```Syntax
WindowsOptionalFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="9e28f-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="9e28f-109">Properties</span></span>

|<span data-ttu-id="9e28f-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="9e28f-110">Property</span></span> |<span data-ttu-id="9e28f-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9e28f-111">Description</span></span> |
|---|---|
|<span data-ttu-id="9e28f-112">Nome</span><span class="sxs-lookup"><span data-stu-id="9e28f-112">Name</span></span> |<span data-ttu-id="9e28f-113">Indica il nome delle funzionalità che si vogliono abilitare o disabilitare.</span><span class="sxs-lookup"><span data-stu-id="9e28f-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span> |
|<span data-ttu-id="9e28f-114">Source (Sorgente)</span><span class="sxs-lookup"><span data-stu-id="9e28f-114">Source</span></span> |<span data-ttu-id="9e28f-115">Non implementato.</span><span class="sxs-lookup"><span data-stu-id="9e28f-115">Not implemented.</span></span> |
|<span data-ttu-id="9e28f-116">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="9e28f-116">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="9e28f-117">Specifica se DISM contatta Windows Update (WU) durante la ricerca dei file di origine per abilitare le funzionalità.</span><span class="sxs-lookup"><span data-stu-id="9e28f-117">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="9e28f-118">Se `$true`, DISM non contatta WU.</span><span class="sxs-lookup"><span data-stu-id="9e28f-118">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="9e28f-119">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="9e28f-119">RemoveFilesOnDisable</span></span> |<span data-ttu-id="9e28f-120">Impostare su `$true` per rimuovere tutti i file associati alle funzionalità quando **Ensure** è impostata su **Absent**.</span><span class="sxs-lookup"><span data-stu-id="9e28f-120">Set to `$true` to remove all files associated with the features when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="9e28f-121">LogLevel</span><span class="sxs-lookup"><span data-stu-id="9e28f-121">LogLevel</span></span> |<span data-ttu-id="9e28f-122">Livello di output massimo per i log.</span><span class="sxs-lookup"><span data-stu-id="9e28f-122">The maximum output level shown in the logs.</span></span> <span data-ttu-id="9e28f-123">I valori accettati sono: **ErrorsOnly**, **ErrorsAndWarning** e **ErrorsAndWarningAndInformation**.</span><span class="sxs-lookup"><span data-stu-id="9e28f-123">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="9e28f-124">LogPath</span><span class="sxs-lookup"><span data-stu-id="9e28f-124">LogPath</span></span> |<span data-ttu-id="9e28f-125">Percorso di un file di registro in cui si vuole che il provider di risorse registri l'operazione.</span><span class="sxs-lookup"><span data-stu-id="9e28f-125">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="9e28f-126">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="9e28f-126">Common properties</span></span>

|<span data-ttu-id="9e28f-127">Proprietà</span><span class="sxs-lookup"><span data-stu-id="9e28f-127">Property</span></span> |<span data-ttu-id="9e28f-128">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9e28f-128">Description</span></span> |
|---|---|
|<span data-ttu-id="9e28f-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="9e28f-129">DependsOn</span></span> |<span data-ttu-id="9e28f-130">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="9e28f-130">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="9e28f-131">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="9e28f-131">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="9e28f-132">Ensure</span><span class="sxs-lookup"><span data-stu-id="9e28f-132">Ensure</span></span> |<span data-ttu-id="9e28f-133">Specifica se le funzionalità sono abilitate.</span><span class="sxs-lookup"><span data-stu-id="9e28f-133">Specifies whether the features are enabled.</span></span> <span data-ttu-id="9e28f-134">Per assicurarsi che le funzionalità siano abilitate, impostare questa proprietà su **Enable**.</span><span class="sxs-lookup"><span data-stu-id="9e28f-134">To ensure that the features are enabled, set this property to **Enable**.</span></span> <span data-ttu-id="9e28f-135">Per assicurarsi che le funzionalità siano disabilitate, impostare la proprietà su **Disable**.</span><span class="sxs-lookup"><span data-stu-id="9e28f-135">To ensure that the features are disabled, set the property to **Disable**.</span></span> <span data-ttu-id="9e28f-136">Il valore predefinito è **Enable**.</span><span class="sxs-lookup"><span data-stu-id="9e28f-136">The default value is **Enable**.</span></span> |
|<span data-ttu-id="9e28f-137">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="9e28f-137">PsDscRunAsCredential</span></span> |<span data-ttu-id="9e28f-138">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="9e28f-138">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="9e28f-139">La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali.</span><span class="sxs-lookup"><span data-stu-id="9e28f-139">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="9e28f-140">Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="9e28f-140">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>