---
title: Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362050"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="54dfc-102">Elemento SelectionCondition per EntrySelectedBy per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="54dfc-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="54dfc-103">Definisce una condizione che deve esistere per la definizione del controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="54dfc-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="54dfc-104">Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="54dfc-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="54dfc-105">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per i controlli per la visualizzazione (formato) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) EntrySelectedBy elemento per CustomEntry per i controlli per la visualizzazione (formato) SelectionCondition elemento per EntrySelectedBy per i controlli per la visualizzazione ( Formato</span><span class="sxs-lookup"><span data-stu-id="54dfc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="54dfc-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="54dfc-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="54dfc-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="54dfc-107">Attributes and Elements</span></span>

<span data-ttu-id="54dfc-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="54dfc-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="54dfc-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="54dfc-109">Attributes</span></span>

<span data-ttu-id="54dfc-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="54dfc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="54dfc-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="54dfc-111">Child Elements</span></span>

|<span data-ttu-id="54dfc-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="54dfc-112">Element</span></span>|<span data-ttu-id="54dfc-113">Description</span><span class="sxs-lookup"><span data-stu-id="54dfc-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="54dfc-114">Elemento PropertyName per SelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="54dfc-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="54dfc-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="54dfc-115">Optional element.</span></span><br /><br /> <span data-ttu-id="54dfc-116">Specifica una proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="54dfc-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="54dfc-117">Elemento ScriptBlock per SelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="54dfc-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="54dfc-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="54dfc-118">Optional element.</span></span><br /><br /> <span data-ttu-id="54dfc-119">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="54dfc-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="54dfc-120">Elemento SelectionSetName per SelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="54dfc-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="54dfc-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="54dfc-121">Optional element.</span></span><br /><br /> <span data-ttu-id="54dfc-122">Specifica il set di tipi .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="54dfc-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="54dfc-123">Elemento TypeName per SelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="54dfc-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="54dfc-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="54dfc-124">Optional element.</span></span><br /><br /> <span data-ttu-id="54dfc-125">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="54dfc-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="54dfc-126">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="54dfc-126">Parent Elements</span></span>

|<span data-ttu-id="54dfc-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="54dfc-127">Element</span></span>|<span data-ttu-id="54dfc-128">Description</span><span class="sxs-lookup"><span data-stu-id="54dfc-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="54dfc-129">Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="54dfc-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="54dfc-130">Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="54dfc-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="54dfc-131">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="54dfc-131">Remarks</span></span>

<span data-ttu-id="54dfc-132">Quando si definisce una condizione di selezione, si applicano i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="54dfc-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="54dfc-133">La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="54dfc-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="54dfc-134">La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="54dfc-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="54dfc-135">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="54dfc-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="54dfc-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="54dfc-136">See Also</span></span>

[<span data-ttu-id="54dfc-137">Elemento PropertyName per SelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="54dfc-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="54dfc-138">Elemento ScriptBlock per SelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="54dfc-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="54dfc-139">Elemento SelectionSetName per SelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="54dfc-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="54dfc-140">Elemento TypeName per SelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="54dfc-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="54dfc-141">Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="54dfc-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="54dfc-142">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="54dfc-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
