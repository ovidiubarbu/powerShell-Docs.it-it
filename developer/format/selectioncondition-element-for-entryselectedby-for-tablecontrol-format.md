---
title: Elemento SelectionCondition per EntrySelectedBy per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075665"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="b4071-102">Elemento SelectionCondition per EntrySelectedBy per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b4071-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="b4071-103">Definisce la condizione che deve essere presente per l'utilizzo per questa definizione della visualizzazione della tabella.</span><span class="sxs-lookup"><span data-stu-id="b4071-103">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="b4071-104">Non sono previsti limiti al numero di condizioni di selezione che è possibile specificare per una definizione di tabella.</span><span class="sxs-lookup"><span data-stu-id="b4071-104">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="b4071-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento di configurazione per TableRowEntry (formato) Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b4071-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b4071-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b4071-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b4071-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="b4071-107">Attributes and Elements</span></span>

<span data-ttu-id="b4071-108">Le sezioni seguenti descrivono gli attributi, elementi figlio e l'elemento padre dell'elemento SelectionCondition.</span><span class="sxs-lookup"><span data-stu-id="b4071-108">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b4071-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="b4071-109">Attributes</span></span>

<span data-ttu-id="b4071-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="b4071-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b4071-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="b4071-111">Child Elements</span></span>

|<span data-ttu-id="b4071-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="b4071-112">Element</span></span>|<span data-ttu-id="b4071-113">Description</span><span class="sxs-lookup"><span data-stu-id="b4071-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4071-114">Elemento PropertyName per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b4071-114">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="b4071-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b4071-115">Optional element.</span></span><br /><br /> <span data-ttu-id="b4071-116">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="b4071-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="b4071-117">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b4071-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="b4071-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b4071-118">Optional element.</span></span><br /><br /> <span data-ttu-id="b4071-119">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="b4071-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="b4071-120">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b4071-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="b4071-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b4071-121">Optional element.</span></span><br /><br /> <span data-ttu-id="b4071-122">Specifica il set di tipi .NET che attivano la condizione.</span><span class="sxs-lookup"><span data-stu-id="b4071-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="b4071-123">Elemento TypeName per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b4071-123">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="b4071-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b4071-124">Optional element.</span></span><br /><br /> <span data-ttu-id="b4071-125">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="b4071-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b4071-126">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="b4071-126">Parent Elements</span></span>

|<span data-ttu-id="b4071-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="b4071-127">Element</span></span>|<span data-ttu-id="b4071-128">Description</span><span class="sxs-lookup"><span data-stu-id="b4071-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4071-129">Elemento EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b4071-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="b4071-130">Definisce i tipi .NET che usano la voce della tabella o la condizione che deve essere presente per questa voce da usare.</span><span class="sxs-lookup"><span data-stu-id="b4071-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b4071-131">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="b4071-131">Remarks</span></span>

<span data-ttu-id="b4071-132">Ogni voce dell'elenco deve avere almeno un nome di tipo, il set di selezione o condizione di selezione definiti.</span><span class="sxs-lookup"><span data-stu-id="b4071-132">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="b4071-133">Quando si definisce una condizione di selezione, si applicano i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="b4071-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="b4071-134">La condizione di selezione è necessario specificare un nome di una proprietà minimi o un blocco di script, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="b4071-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="b4071-135">La condizione di selezione può includere un numero qualsiasi di tipi .NET o selezione imposta, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="b4071-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="b4071-136">Per altre informazioni su come usare le condizioni di selezione, vedere [definizione di condizioni per quando una voce di visualizzazione o viene usato l'elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b4071-136">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b4071-137">Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="b4071-137">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4071-138">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b4071-138">See Also</span></span>

[<span data-ttu-id="b4071-139">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="b4071-139">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b4071-140">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="b4071-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b4071-141">Elemento EntrySelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="b4071-141">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="b4071-142">Elemento PropertyName per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b4071-142">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="b4071-143">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b4071-143">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="b4071-144">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b4071-144">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="b4071-145">Elemento TypeName per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b4071-145">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="b4071-146">La scrittura di un metodo di formattazione di Windows PowerShell e i tipi di File</span><span class="sxs-lookup"><span data-stu-id="b4071-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
