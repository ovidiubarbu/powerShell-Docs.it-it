---
title: Elemento SelectionCondition per EntrySelectedBy per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364780"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="9b9dd-102">Elemento SelectionCondition per EntrySelectedBy per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="9b9dd-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="9b9dd-103">Definisce la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="9b9dd-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="9b9dd-104">Non esiste alcun limite al numero di condizioni di selezione che è possibile specificare per una definizione di voce ampia.</span><span class="sxs-lookup"><span data-stu-id="9b9dd-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="9b9dd-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) elemento EntrySelectedBy per WideEntry (Format) SelectionCondition elemento per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9b9dd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9b9dd-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9b9dd-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9b9dd-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="9b9dd-107">Attributes and Elements</span></span>

<span data-ttu-id="9b9dd-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="9b9dd-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="9b9dd-109">È necessario specificare un singolo elemento `PropertyName` o `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="9b9dd-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="9b9dd-110">Gli elementi `SelectionSetName` e `TypeName` sono facoltativi.</span><span class="sxs-lookup"><span data-stu-id="9b9dd-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="9b9dd-111">È possibile specificare uno dei due elementi.</span><span class="sxs-lookup"><span data-stu-id="9b9dd-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9b9dd-112">Attributi</span><span class="sxs-lookup"><span data-stu-id="9b9dd-112">Attributes</span></span>

<span data-ttu-id="9b9dd-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="9b9dd-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9b9dd-114">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="9b9dd-114">Child Elements</span></span>

|<span data-ttu-id="9b9dd-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="9b9dd-115">Element</span></span>|<span data-ttu-id="9b9dd-116">Description</span><span class="sxs-lookup"><span data-stu-id="9b9dd-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9b9dd-117">Elemento PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9b9dd-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="9b9dd-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="9b9dd-118">Optional element.</span></span><br /><br /> <span data-ttu-id="9b9dd-119">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="9b9dd-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="9b9dd-120">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9b9dd-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="9b9dd-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="9b9dd-121">Optional element.</span></span><br /><br /> <span data-ttu-id="9b9dd-122">Specifica il blocco di script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="9b9dd-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="9b9dd-123">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9b9dd-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="9b9dd-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="9b9dd-124">Optional element.</span></span><br /><br /> <span data-ttu-id="9b9dd-125">Specifica il set di tipi .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="9b9dd-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="9b9dd-126">Elemento TypeName per SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9b9dd-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="9b9dd-127">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="9b9dd-127">Optional element.</span></span><br /><br /> <span data-ttu-id="9b9dd-128">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="9b9dd-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9b9dd-129">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="9b9dd-129">Parent Elements</span></span>

|<span data-ttu-id="9b9dd-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="9b9dd-130">Element</span></span>|<span data-ttu-id="9b9dd-131">Description</span><span class="sxs-lookup"><span data-stu-id="9b9dd-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9b9dd-132">Elemento EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9b9dd-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="9b9dd-133">Definisce i tipi .NET che utilizzano questa voce estesa o la condizione che deve esistere affinché questa voce venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="9b9dd-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9b9dd-134">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="9b9dd-134">Remarks</span></span>

<span data-ttu-id="9b9dd-135">Per ogni voce di tipo Wide è necessario definire almeno un nome di tipo, un set di selezione o una condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="9b9dd-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="9b9dd-136">Quando si definisce una condizione di selezione, si applicano i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="9b9dd-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="9b9dd-137">La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="9b9dd-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="9b9dd-138">La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="9b9dd-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="9b9dd-139">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per l'utilizzo di una voce o di un elemento della visualizzazione](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="9b9dd-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="9b9dd-140">Per ulteriori informazioni su altri componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="9b9dd-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9b9dd-141">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9b9dd-141">See Also</span></span>

[<span data-ttu-id="9b9dd-142">Creazione di una visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="9b9dd-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="9b9dd-143">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="9b9dd-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9b9dd-144">Elemento EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9b9dd-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="9b9dd-145">Elemento PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9b9dd-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="9b9dd-146">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9b9dd-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="9b9dd-147">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9b9dd-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="9b9dd-148">Elemento TypeName per SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9b9dd-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="9b9dd-149">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="9b9dd-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
