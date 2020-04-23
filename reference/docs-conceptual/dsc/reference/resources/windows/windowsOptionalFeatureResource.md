---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WindowsOptionalFeature DSC
ms.openlocfilehash: 7312edcaeb47427bf4736f466a9ed41bd7c31f6a
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954648"
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="c16cc-103">Risorsa WindowsOptionalFeature DSC</span><span class="sxs-lookup"><span data-stu-id="c16cc-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="c16cc-104">Si applica a: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="c16cc-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="c16cc-105">La risorsa **WindowsOptionalFeature** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per specificare le funzionalità facoltative abilitate in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="c16cc-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c16cc-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c16cc-106">Syntax</span></span>

```Syntax
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Source = [string[]] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="c16cc-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="c16cc-107">Properties</span></span>

|<span data-ttu-id="c16cc-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="c16cc-108">Property</span></span> |<span data-ttu-id="c16cc-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="c16cc-109">Description</span></span> |
|---|---|
|<span data-ttu-id="c16cc-110">Nome</span><span class="sxs-lookup"><span data-stu-id="c16cc-110">Name</span></span> |<span data-ttu-id="c16cc-111">Indica il nome della funzionalità che si vuole abilitare o disabilitare.</span><span class="sxs-lookup"><span data-stu-id="c16cc-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span> |
|<span data-ttu-id="c16cc-112">Source (Sorgente)</span><span class="sxs-lookup"><span data-stu-id="c16cc-112">Source</span></span> |<span data-ttu-id="c16cc-113">Non implementato.</span><span class="sxs-lookup"><span data-stu-id="c16cc-113">Not implemented.</span></span> |
|<span data-ttu-id="c16cc-114">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="c16cc-114">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="c16cc-115">Specifica se DISM contatta Windows Update (WU) durante la ricerca dei file di origine per abilitare una funzionalità.</span><span class="sxs-lookup"><span data-stu-id="c16cc-115">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="c16cc-116">Se `$true`, DISM non contatta WU.</span><span class="sxs-lookup"><span data-stu-id="c16cc-116">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="c16cc-117">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="c16cc-117">RemoveFilesOnDisable</span></span> |<span data-ttu-id="c16cc-118">Impostare su `$true` per rimuovere tutti i file associati alla funzionalità quando **Ensure** è impostata su **Absent**.</span><span class="sxs-lookup"><span data-stu-id="c16cc-118">Set to `$true` to remove all files associated with the feature when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="c16cc-119">LogLevel</span><span class="sxs-lookup"><span data-stu-id="c16cc-119">LogLevel</span></span> |<span data-ttu-id="c16cc-120">Livello di output massimo per i log.</span><span class="sxs-lookup"><span data-stu-id="c16cc-120">The maximum output level shown in the logs.</span></span> <span data-ttu-id="c16cc-121">I valori accettati sono: **ErrorsOnly**, **ErrorsAndWarning** e **ErrorsAndWarningAndInformation**.</span><span class="sxs-lookup"><span data-stu-id="c16cc-121">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="c16cc-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="c16cc-122">LogPath</span></span> |<span data-ttu-id="c16cc-123">Percorso di un file di registro in cui si vuole che il provider di risorse registri l'operazione.</span><span class="sxs-lookup"><span data-stu-id="c16cc-123">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="c16cc-124">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="c16cc-124">Common properties</span></span>

|<span data-ttu-id="c16cc-125">Proprietà</span><span class="sxs-lookup"><span data-stu-id="c16cc-125">Property</span></span> |<span data-ttu-id="c16cc-126">Descrizione</span><span class="sxs-lookup"><span data-stu-id="c16cc-126">Description</span></span> |
|---|---|
|<span data-ttu-id="c16cc-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c16cc-127">DependsOn</span></span> |<span data-ttu-id="c16cc-128">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="c16cc-128">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c16cc-129">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c16cc-129">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="c16cc-130">Ensure</span><span class="sxs-lookup"><span data-stu-id="c16cc-130">Ensure</span></span> |<span data-ttu-id="c16cc-131">Indica se la funzionalità è abilitata.</span><span class="sxs-lookup"><span data-stu-id="c16cc-131">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="c16cc-132">Per assicurarsi che la funzionalità sia abilitata, impostare questa proprietà su _Enable_.</span><span class="sxs-lookup"><span data-stu-id="c16cc-132">To ensure that the feature is enabled, set this property to _Enable_.</span></span> <span data-ttu-id="c16cc-133">Per assicurarsi che la funzionalità sia disabilitata, impostare questa proprietà su _Disable_.</span><span class="sxs-lookup"><span data-stu-id="c16cc-133">To ensure that the feature is disabled, set the property to _Disable_.</span></span> <span data-ttu-id="c16cc-134">Il valore predefinito è _Enable_.</span><span class="sxs-lookup"><span data-stu-id="c16cc-134">The default value is _Enable_.</span></span> |
|<span data-ttu-id="c16cc-135">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="c16cc-135">PsDscRunAsCredential</span></span> |<span data-ttu-id="c16cc-136">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="c16cc-136">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="c16cc-137">La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali.</span><span class="sxs-lookup"><span data-stu-id="c16cc-137">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="c16cc-138">Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="c16cc-138">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>