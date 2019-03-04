---
title: Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858017"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="ec7b7-102">Elemento SelectionCondition per EntrySelectedBy per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="ec7b7-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="ec7b7-103">Definisce una condizione che deve essere presente per la definizione di controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="ec7b7-104">Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="ec7b7-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl per i controlli elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) EntrySelectedBy per CustomEntry per i controlli elemento di visualizzazione (formato) SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione ( Formato)</span><span class="sxs-lookup"><span data-stu-id="ec7b7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ec7b7-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ec7b7-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ec7b7-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="ec7b7-107">Attributes and Elements</span></span>

<span data-ttu-id="ec7b7-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ec7b7-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="ec7b7-109">Attributes</span></span>

<span data-ttu-id="ec7b7-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ec7b7-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="ec7b7-111">Child Elements</span></span>

|<span data-ttu-id="ec7b7-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="ec7b7-112">Element</span></span>|<span data-ttu-id="ec7b7-113">Description</span><span class="sxs-lookup"><span data-stu-id="ec7b7-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ec7b7-114">Elemento PropertyName per SelectionCondition per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ec7b7-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="ec7b7-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-115">Optional element.</span></span><br /><br /> <span data-ttu-id="ec7b7-116">Specifica una proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="ec7b7-117">Elemento ScriptBlock per SelectionCondition per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ec7b7-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="ec7b7-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-118">Optional element.</span></span><br /><br /> <span data-ttu-id="ec7b7-119">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="ec7b7-120">Elemento SelectionSetName per SelectionCondition per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ec7b7-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="ec7b7-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-121">Optional element.</span></span><br /><br /> <span data-ttu-id="ec7b7-122">Specifica il set di tipi .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="ec7b7-123">Elemento TypeName per SelectionCondition per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ec7b7-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="ec7b7-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-124">Optional element.</span></span><br /><br /> <span data-ttu-id="ec7b7-125">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ec7b7-126">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="ec7b7-126">Parent Elements</span></span>

|<span data-ttu-id="ec7b7-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="ec7b7-127">Element</span></span>|<span data-ttu-id="ec7b7-128">Description</span><span class="sxs-lookup"><span data-stu-id="ec7b7-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ec7b7-129">Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ec7b7-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="ec7b7-130">Definisce i tipi .NET che usano questa definizione di controllo o la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ec7b7-131">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="ec7b7-131">Remarks</span></span>

<span data-ttu-id="ec7b7-132">Quando si definisce una condizione di selezione, si applicano i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="ec7b7-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="ec7b7-133">La condizione di selezione è necessario specificare un nome di una proprietà minimi o un blocco di script, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="ec7b7-134">La condizione di selezione può includere un numero qualsiasi di tipi .NET o selezione imposta, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="ec7b7-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="ec7b7-135">Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ec7b7-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ec7b7-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ec7b7-136">See Also</span></span>

[<span data-ttu-id="ec7b7-137">Elemento PropertyName per SelectionCondition per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ec7b7-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="ec7b7-138">Elemento ScriptBlock per SelectionCondition per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ec7b7-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="ec7b7-139">Elemento SelectionSetName per SelectionCondition per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ec7b7-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="ec7b7-140">Elemento TypeName per SelectionCondition per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ec7b7-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="ec7b7-141">Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ec7b7-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="ec7b7-142">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec7b7-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
