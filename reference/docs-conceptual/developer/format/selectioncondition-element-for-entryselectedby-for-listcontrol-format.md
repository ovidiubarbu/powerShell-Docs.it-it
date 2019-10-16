---
title: Elemento SelectionCondition per EntrySelectedBy per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: f04a07c241268566eaedfe2b299c33d5be4dc19d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364820"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="71014-102">Elemento SelectionCondition per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="71014-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="71014-103">Definisce la condizione che deve esistere per utilizzare questa definizione della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="71014-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="71014-104">Non esiste alcun limite al numero di condizioni di selezione che è possibile specificare per una definizione di elenco.</span><span class="sxs-lookup"><span data-stu-id="71014-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="71014-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento EntrySelectedBy per ListEntry (Format) SelectionCondition elemento per EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="71014-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="71014-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="71014-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="71014-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="71014-107">Attributes and Elements</span></span>

<span data-ttu-id="71014-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="71014-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="71014-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="71014-109">Attributes</span></span>

<span data-ttu-id="71014-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="71014-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="71014-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="71014-111">Child Elements</span></span>

|<span data-ttu-id="71014-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="71014-112">Element</span></span>|<span data-ttu-id="71014-113">Description</span><span class="sxs-lookup"><span data-stu-id="71014-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="71014-114">Elemento PropertyName per SelectionCondition per EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="71014-114">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="71014-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="71014-115">Optional element.</span></span><br /><br /> <span data-ttu-id="71014-116">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="71014-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="71014-117">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="71014-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="71014-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="71014-118">Optional element.</span></span><br /><br /> <span data-ttu-id="71014-119">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="71014-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="71014-120">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="71014-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="71014-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="71014-121">Optional element.</span></span><br /><br /> <span data-ttu-id="71014-122">Specifica il set di tipi .NET che attivano la condizione.</span><span class="sxs-lookup"><span data-stu-id="71014-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="71014-123">Elemento TypeName per SelectionCondition per EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="71014-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="71014-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="71014-124">Optional element.</span></span><br /><br /> <span data-ttu-id="71014-125">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="71014-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="71014-126">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="71014-126">Parent Elements</span></span>

|<span data-ttu-id="71014-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="71014-127">Element</span></span>|<span data-ttu-id="71014-128">Description</span><span class="sxs-lookup"><span data-stu-id="71014-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="71014-129">Elemento EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="71014-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="71014-130">Definisce i tipi .NET che utilizzano questa voce di tabella o la condizione che deve esistere affinché questa voce venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="71014-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="71014-131">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="71014-131">Remarks</span></span>

<span data-ttu-id="71014-132">lWhen si definisce una condizione di selezione, si applicano i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="71014-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="71014-133">La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="71014-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="71014-134">La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="71014-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="71014-135">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="71014-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="71014-136">Per ulteriori informazioni sugli altri componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="71014-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="71014-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="71014-137">See Also</span></span>

[<span data-ttu-id="71014-138">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="71014-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="71014-139">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="71014-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="71014-140">Elemento ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="71014-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="71014-141">Elemento SelectionSetName per EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="71014-141">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="71014-142">Elemento TypeName per EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="71014-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](/powershell/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[<span data-ttu-id="71014-143">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="71014-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
