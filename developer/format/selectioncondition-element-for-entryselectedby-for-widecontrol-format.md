---
title: Elemento SelectionCondition per EntrySelectedBy per WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063993"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="d9908-102">Elemento SelectionCondition per EntrySelectedBy per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d9908-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="d9908-103">Definisce la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="d9908-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="d9908-104">Non sono previsti limiti al numero di condizioni di selezione che è possibile specificare per una definizione di voce wide.</span><span class="sxs-lookup"><span data-stu-id="d9908-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="d9908-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento di configurazione per elemento SelectionCondition WideEntry (formato) per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="d9908-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d9908-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d9908-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d9908-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="d9908-107">Attributes and Elements</span></span>

<span data-ttu-id="d9908-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="d9908-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="d9908-109">È necessario specificare un unico `PropertyName` o `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="d9908-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="d9908-110">Il `SelectionSetName` e `TypeName` gli elementi sono facoltativi.</span><span class="sxs-lookup"><span data-stu-id="d9908-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="d9908-111">È possibile specificare uno dei entrambi gli elementi.</span><span class="sxs-lookup"><span data-stu-id="d9908-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d9908-112">Attributes</span><span class="sxs-lookup"><span data-stu-id="d9908-112">Attributes</span></span>

<span data-ttu-id="d9908-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="d9908-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d9908-114">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="d9908-114">Child Elements</span></span>

|<span data-ttu-id="d9908-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="d9908-115">Element</span></span>|<span data-ttu-id="d9908-116">Description</span><span class="sxs-lookup"><span data-stu-id="d9908-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d9908-117">Elemento PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="d9908-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="d9908-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d9908-118">Optional element.</span></span><br /><br /> <span data-ttu-id="d9908-119">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="d9908-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="d9908-120">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="d9908-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="d9908-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d9908-121">Optional element.</span></span><br /><br /> <span data-ttu-id="d9908-122">Specifica il blocco di script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="d9908-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="d9908-123">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="d9908-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="d9908-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d9908-124">Optional element.</span></span><br /><br /> <span data-ttu-id="d9908-125">Specifica il set di tipi .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="d9908-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="d9908-126">Elemento TypeName per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="d9908-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="d9908-127">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d9908-127">Optional element.</span></span><br /><br /> <span data-ttu-id="d9908-128">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="d9908-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d9908-129">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="d9908-129">Parent Elements</span></span>

|<span data-ttu-id="d9908-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="d9908-130">Element</span></span>|<span data-ttu-id="d9908-131">Description</span><span class="sxs-lookup"><span data-stu-id="d9908-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d9908-132">Elemento EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="d9908-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="d9908-133">Definisce i tipi .NET che usano questa voce ampia o la condizione che deve essere presente per questa voce da usare.</span><span class="sxs-lookup"><span data-stu-id="d9908-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d9908-134">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="d9908-134">Remarks</span></span>

<span data-ttu-id="d9908-135">Ogni voce wide deve avere almeno un nome di tipo, il set di selezione o condizione di selezione definiti.</span><span class="sxs-lookup"><span data-stu-id="d9908-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="d9908-136">Quando si definisce una condizione di selezione, si applicano i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="d9908-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="d9908-137">La condizione di selezione è necessario specificare un nome di una proprietà minimi o un blocco di script, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="d9908-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="d9908-138">La condizione di selezione può includere un numero qualsiasi di tipi .NET o selezione imposta, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="d9908-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="d9908-139">Per altre informazioni su come usare le condizioni di selezione, vedere [definizione di condizioni per quando una voce di visualizzazione o viene usato l'elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d9908-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="d9908-140">Per altre informazioni sugli altri componenti di una visualizzazione più ampia, vedere [creazione di una visualizzazione più ampia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="d9908-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d9908-141">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d9908-141">See Also</span></span>

[<span data-ttu-id="d9908-142">Creazione di una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="d9908-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d9908-143">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="d9908-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d9908-144">Elemento EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="d9908-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="d9908-145">Elemento PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="d9908-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="d9908-146">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="d9908-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="d9908-147">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="d9908-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="d9908-148">Elemento TypeName per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="d9908-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="d9908-149">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="d9908-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
