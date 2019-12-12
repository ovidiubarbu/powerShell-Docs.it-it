---
title: Elemento SelectionCondition per EntrySelectedBy per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368390"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="c8bf9-102">Elemento SelectionCondition per EntrySelectedBy per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c8bf9-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="c8bf9-103">Definisce la condizione che deve esistere per utilizzare per questa definizione della visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="c8bf9-103">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="c8bf9-104">Non esiste alcun limite al numero di condizioni di selezione che è possibile specificare per una definizione di tabella.</span><span class="sxs-lookup"><span data-stu-id="c8bf9-104">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="c8bf9-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) elemento EntrySelectedBy per TableRowEntry (Format) Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c8bf9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c8bf9-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c8bf9-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c8bf9-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="c8bf9-107">Attributes and Elements</span></span>

<span data-ttu-id="c8bf9-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento SelectionCondition.</span><span class="sxs-lookup"><span data-stu-id="c8bf9-108">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c8bf9-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="c8bf9-109">Attributes</span></span>

<span data-ttu-id="c8bf9-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c8bf9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c8bf9-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="c8bf9-111">Child Elements</span></span>

|<span data-ttu-id="c8bf9-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="c8bf9-112">Element</span></span>|<span data-ttu-id="c8bf9-113">Description</span><span class="sxs-lookup"><span data-stu-id="c8bf9-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c8bf9-114">Elemento PropertyName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c8bf9-114">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="c8bf9-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="c8bf9-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c8bf9-116">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="c8bf9-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="c8bf9-117">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c8bf9-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="c8bf9-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="c8bf9-118">Optional element.</span></span><br /><br /> <span data-ttu-id="c8bf9-119">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="c8bf9-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="c8bf9-120">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c8bf9-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="c8bf9-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="c8bf9-121">Optional element.</span></span><br /><br /> <span data-ttu-id="c8bf9-122">Specifica il set di tipi .NET che attivano la condizione.</span><span class="sxs-lookup"><span data-stu-id="c8bf9-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="c8bf9-123">Elemento TypeName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c8bf9-123">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="c8bf9-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="c8bf9-124">Optional element.</span></span><br /><br /> <span data-ttu-id="c8bf9-125">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="c8bf9-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c8bf9-126">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="c8bf9-126">Parent Elements</span></span>

|<span data-ttu-id="c8bf9-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="c8bf9-127">Element</span></span>|<span data-ttu-id="c8bf9-128">Description</span><span class="sxs-lookup"><span data-stu-id="c8bf9-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c8bf9-129">Elemento EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c8bf9-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="c8bf9-130">Definisce i tipi .NET che utilizzano questa voce di tabella o la condizione che deve esistere affinché questa voce venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="c8bf9-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c8bf9-131">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c8bf9-131">Remarks</span></span>

<span data-ttu-id="c8bf9-132">Per ogni voce di elenco è necessario definire almeno un nome di tipo, un set di selezione o una condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="c8bf9-132">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="c8bf9-133">Quando si definisce una condizione di selezione, si applicano i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="c8bf9-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="c8bf9-134">La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="c8bf9-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="c8bf9-135">La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="c8bf9-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="c8bf9-136">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per l'utilizzo di una voce o di un elemento della visualizzazione](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c8bf9-136">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="c8bf9-137">Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="c8bf9-137">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c8bf9-138">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c8bf9-138">See Also</span></span>

[<span data-ttu-id="c8bf9-139">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="c8bf9-139">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c8bf9-140">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="c8bf9-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c8bf9-141">Elemento EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c8bf9-141">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="c8bf9-142">Elemento PropertyName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c8bf9-142">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="c8bf9-143">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c8bf9-143">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="c8bf9-144">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c8bf9-144">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="c8bf9-145">Elemento TypeName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c8bf9-145">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="c8bf9-146">Scrittura di un file di formattazione e di tipi di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c8bf9-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
