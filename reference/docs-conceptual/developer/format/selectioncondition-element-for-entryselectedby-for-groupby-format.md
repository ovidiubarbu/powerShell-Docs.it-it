---
title: Elemento SelectionCondition per EntrySelectedBy per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368430"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="86f86-102">Elemento SelectionCondition per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="86f86-102">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="86f86-103">Definisce una condizione che deve esistere per la definizione di un controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="86f86-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="86f86-104">Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="86f86-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="86f86-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format) elemento EntrySelectedBy per CustomEntry per GroupBy (Format) SelectionCondition elemento per EntrySelectedBy per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="86f86-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="86f86-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="86f86-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="86f86-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="86f86-107">Attributes and Elements</span></span>

<span data-ttu-id="86f86-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="86f86-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="86f86-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="86f86-109">Attributes</span></span>

<span data-ttu-id="86f86-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="86f86-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="86f86-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="86f86-111">Child Elements</span></span>

|<span data-ttu-id="86f86-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="86f86-112">Element</span></span>|<span data-ttu-id="86f86-113">Description</span><span class="sxs-lookup"><span data-stu-id="86f86-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86f86-114">Elemento PropertyName per SelectionCondition per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="86f86-114">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="86f86-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="86f86-115">Optional element.</span></span><br /><br /> <span data-ttu-id="86f86-116">Specifica una proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="86f86-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="86f86-117">Elemento ScriptBlock per SelectionCondition per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="86f86-117">ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="86f86-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="86f86-118">Optional element.</span></span><br /><br /> <span data-ttu-id="86f86-119">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="86f86-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="86f86-120">Elemento SelectionSetName per SelectionCondition per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="86f86-120">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="86f86-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="86f86-121">Optional element.</span></span><br /><br /> <span data-ttu-id="86f86-122">Specifica il set di tipi .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="86f86-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="86f86-123">Elemento TypeName per SelectionCondition per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="86f86-123">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="86f86-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="86f86-124">Optional element.</span></span><br /><br /> <span data-ttu-id="86f86-125">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="86f86-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="86f86-126">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="86f86-126">Parent Elements</span></span>

|<span data-ttu-id="86f86-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="86f86-127">Element</span></span>|<span data-ttu-id="86f86-128">Description</span><span class="sxs-lookup"><span data-stu-id="86f86-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86f86-129">Elemento EntrySelectedBy per CustomEntry per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="86f86-129">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="86f86-130">Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="86f86-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="86f86-131">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="86f86-131">Remarks</span></span>

<span data-ttu-id="86f86-132">Quando si definisce una condizione di selezione, si applicano i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="86f86-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="86f86-133">La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="86f86-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="86f86-134">La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="86f86-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="86f86-135">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="86f86-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="86f86-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="86f86-136">See Also</span></span>

[<span data-ttu-id="86f86-137">Elemento PropertyName per SelectionCondition per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="86f86-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="86f86-138">Elemento ScriptBlock per SelectionCondition per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="86f86-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="86f86-139">Elemento SelectionSetName per SelectionCondition per il controllo personalizzato per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="86f86-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="86f86-140">Elemento TypeName per SelectionCondition per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="86f86-140">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="86f86-141">Elemento EntrySelectedBy per CustomEntry per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="86f86-141">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="86f86-142">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="86f86-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
