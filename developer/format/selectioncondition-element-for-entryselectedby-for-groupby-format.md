---
title: Elemento SelectionCondition per EntrySelectedBy per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855167"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="43a2c-102">Elemento SelectionCondition per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="43a2c-102">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="43a2c-103">Definisce una condizione che deve essere presente per una definizione di controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="43a2c-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="43a2c-104">Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="43a2c-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="43a2c-105">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per elemento EntrySelectedBy GroupBy (formato) per CustomEntry per elemento SelectionCondition GroupBy (formato) per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="43a2c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="43a2c-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="43a2c-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="43a2c-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="43a2c-107">Attributes and Elements</span></span>

<span data-ttu-id="43a2c-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="43a2c-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="43a2c-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="43a2c-109">Attributes</span></span>

<span data-ttu-id="43a2c-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="43a2c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="43a2c-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="43a2c-111">Child Elements</span></span>

|<span data-ttu-id="43a2c-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="43a2c-112">Element</span></span>|<span data-ttu-id="43a2c-113">Description</span><span class="sxs-lookup"><span data-stu-id="43a2c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="43a2c-114">Elemento PropertyName per SelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="43a2c-114">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="43a2c-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="43a2c-115">Optional element.</span></span><br /><br /> <span data-ttu-id="43a2c-116">Specifica una proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="43a2c-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="43a2c-117">Elemento ScriptBlock per SelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="43a2c-117">ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="43a2c-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="43a2c-118">Optional element.</span></span><br /><br /> <span data-ttu-id="43a2c-119">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="43a2c-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="43a2c-120">Elemento SelectionSetName per SelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="43a2c-120">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="43a2c-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="43a2c-121">Optional element.</span></span><br /><br /> <span data-ttu-id="43a2c-122">Specifica il set di tipi .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="43a2c-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="43a2c-123">Elemento TypeName per SelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="43a2c-123">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="43a2c-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="43a2c-124">Optional element.</span></span><br /><br /> <span data-ttu-id="43a2c-125">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="43a2c-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="43a2c-126">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="43a2c-126">Parent Elements</span></span>

|<span data-ttu-id="43a2c-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="43a2c-127">Element</span></span>|<span data-ttu-id="43a2c-128">Description</span><span class="sxs-lookup"><span data-stu-id="43a2c-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="43a2c-129">Elemento EntrySelectedBy per CustomEntry per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="43a2c-129">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="43a2c-130">Definisce i tipi .NET che usano questa definizione di controllo o la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="43a2c-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="43a2c-131">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="43a2c-131">Remarks</span></span>

<span data-ttu-id="43a2c-132">Quando si definisce una condizione di selezione, si applicano i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="43a2c-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="43a2c-133">La condizione di selezione è necessario specificare un nome di una proprietà minimi o un blocco di script, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="43a2c-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="43a2c-134">La condizione di selezione può includere un numero qualsiasi di tipi .NET o selezione imposta, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="43a2c-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="43a2c-135">Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="43a2c-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="43a2c-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="43a2c-136">See Also</span></span>

[<span data-ttu-id="43a2c-137">Elemento PropertyName per SelectionCondition per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="43a2c-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="43a2c-138">Elemento ScriptBlock per SelectionCondition per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="43a2c-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="43a2c-139">Elemento SelectionSetName per SelectionCondition per un controllo personalizzato per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="43a2c-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="43a2c-140">Elemento TypeName per SelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="43a2c-140">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="43a2c-141">Elemento EntrySelectedBy per CustomEntry per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="43a2c-141">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="43a2c-142">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="43a2c-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
