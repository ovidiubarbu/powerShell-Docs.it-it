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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362050"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="f024c-102">Elemento SelectionCondition per EntrySelectedBy per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="f024c-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="f024c-103">Definisce una condizione che deve esistere per la definizione del controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="f024c-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="f024c-104">Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="f024c-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="f024c-105">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per i controlli per la visualizzazione (formato) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) EntrySelectedBy elemento per CustomEntry per i controlli per la visualizzazione (formato) SelectionCondition elemento per EntrySelectedBy per i controlli per la visualizzazione ( Formato</span><span class="sxs-lookup"><span data-stu-id="f024c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f024c-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f024c-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f024c-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="f024c-107">Attributes and Elements</span></span>

<span data-ttu-id="f024c-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="f024c-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f024c-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="f024c-109">Attributes</span></span>

<span data-ttu-id="f024c-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f024c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f024c-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f024c-111">Child Elements</span></span>

|<span data-ttu-id="f024c-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="f024c-112">Element</span></span>|<span data-ttu-id="f024c-113">Description</span><span class="sxs-lookup"><span data-stu-id="f024c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f024c-114">Elemento PropertyName per SelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="f024c-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f024c-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="f024c-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f024c-116">Specifica una proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="f024c-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f024c-117">Elemento ScriptBlock per SelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="f024c-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f024c-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="f024c-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f024c-119">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="f024c-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="f024c-120">Elemento SelectionSetName per SelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="f024c-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f024c-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="f024c-121">Optional element.</span></span><br /><br /> <span data-ttu-id="f024c-122">Specifica il set di tipi .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="f024c-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="f024c-123">Elemento TypeName per SelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="f024c-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f024c-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="f024c-124">Optional element.</span></span><br /><br /> <span data-ttu-id="f024c-125">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="f024c-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f024c-126">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f024c-126">Parent Elements</span></span>

|<span data-ttu-id="f024c-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="f024c-127">Element</span></span>|<span data-ttu-id="f024c-128">Description</span><span class="sxs-lookup"><span data-stu-id="f024c-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f024c-129">Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="f024c-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="f024c-130">Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="f024c-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f024c-131">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f024c-131">Remarks</span></span>

<span data-ttu-id="f024c-132">Quando si definisce una condizione di selezione, si applicano i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="f024c-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="f024c-133">La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="f024c-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="f024c-134">La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="f024c-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="f024c-135">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f024c-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f024c-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f024c-136">See Also</span></span>

[<span data-ttu-id="f024c-137">Elemento PropertyName per SelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="f024c-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f024c-138">Elemento ScriptBlock per SelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="f024c-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f024c-139">Elemento SelectionSetName per SelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="f024c-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f024c-140">Elemento TypeName per SelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="f024c-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f024c-141">Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="f024c-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="f024c-142">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f024c-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
