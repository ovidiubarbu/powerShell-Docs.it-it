---
title: Elemento di configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856327"
---
# <a name="configuration-element-format"></a><span data-ttu-id="270ae-102">Elemento Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="270ae-102">Configuration Element (Format)</span></span>

<span data-ttu-id="270ae-103">Rappresenta l'elemento di livello superiore di un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="270ae-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="270ae-104">Elemento di configurazione</span><span class="sxs-lookup"><span data-stu-id="270ae-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="270ae-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="270ae-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="270ae-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="270ae-106">Attributes and Elements</span></span>

<span data-ttu-id="270ae-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Configuration` elemento.</span><span class="sxs-lookup"><span data-stu-id="270ae-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="270ae-108">Questo elemento deve essere l'elemento radice per ogni file di formattazione e questo elemento deve contenere almeno un elemento figlio.</span><span class="sxs-lookup"><span data-stu-id="270ae-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="270ae-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="270ae-109">Attributes</span></span>

<span data-ttu-id="270ae-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="270ae-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="270ae-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="270ae-111">Child Elements</span></span>

|<span data-ttu-id="270ae-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="270ae-112">Element</span></span>|<span data-ttu-id="270ae-113">Description</span><span class="sxs-lookup"><span data-stu-id="270ae-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="270ae-114">I controlli elemento di configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="270ae-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="270ae-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="270ae-115">Optional element.</span></span><br /><br /> <span data-ttu-id="270ae-116">Definisce i controlli comuni che possono essere usati da tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="270ae-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="270ae-117">Elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="270ae-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="270ae-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="270ae-118">Optional element.</span></span><br /><br /> <span data-ttu-id="270ae-119">Definisce le impostazioni comuni che si applicano a tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="270ae-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="270ae-120">Formato elemento SelectionSets</span><span class="sxs-lookup"><span data-stu-id="270ae-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="270ae-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="270ae-121">Optional element.</span></span><br /><br /> <span data-ttu-id="270ae-122">Definisce il set di oggetti .NET che possono essere usati da tutte le visualizzazioni del file di formattazione comuni.</span><span class="sxs-lookup"><span data-stu-id="270ae-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="270ae-123">Elemento ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="270ae-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="270ae-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="270ae-124">Optional element.</span></span><br /><br /> <span data-ttu-id="270ae-125">Definisce le viste utilizzate per visualizzare gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="270ae-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="270ae-126">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="270ae-126">Parent Elements</span></span>

<span data-ttu-id="270ae-127">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="270ae-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="270ae-128">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="270ae-128">Remarks</span></span>

<span data-ttu-id="270ae-129">File di formattazione definiscono come gli oggetti vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="270ae-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="270ae-130">Nella maggior parte dei casi, questo elemento radice contiene un [ViewDefinitions](./viewdefinitions-element-format.md) elemento che definisce la tabella, elenco e visualizzazioni ampie del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="270ae-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="270ae-131">Oltre alle definizioni delle viste, è possibile definire il file di formattazione comuni selezione set, impostazioni e i controlli che è possono utilizzare tali viste.</span><span class="sxs-lookup"><span data-stu-id="270ae-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="270ae-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="270ae-132">See Also</span></span>

[<span data-ttu-id="270ae-133">I controlli elemento di configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="270ae-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="270ae-134">Elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="270ae-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="270ae-135">Elemento SelectionSets (formato)</span><span class="sxs-lookup"><span data-stu-id="270ae-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="270ae-136">Elemento ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="270ae-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="270ae-137">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="270ae-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
