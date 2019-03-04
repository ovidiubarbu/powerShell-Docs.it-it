---
title: Elemento SelectionCondition per EntrySelectedBy per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: ec75945c5517c02fa001f0a38573c045ffcdbfd3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857487"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="04c0d-102">Elemento SelectionCondition per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="04c0d-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="04c0d-103">Definisce la condizione che deve essere presente per usare questa definizione della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="04c0d-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="04c0d-104">Non sono previsti limiti al numero di condizioni di selezione che è possibile specificare per una definizione di elenco.</span><span class="sxs-lookup"><span data-stu-id="04c0d-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="04c0d-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) elemento ListEntries (formato) elemento ListEntry (formato) EntrySelectedBy elemento di configurazione per elemento SelectionCondition ListEntry (formato) EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="04c0d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="04c0d-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="04c0d-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="04c0d-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="04c0d-107">Attributes and Elements</span></span>

<span data-ttu-id="04c0d-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="04c0d-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="04c0d-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="04c0d-109">Attributes</span></span>

<span data-ttu-id="04c0d-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="04c0d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="04c0d-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="04c0d-111">Child Elements</span></span>

|<span data-ttu-id="04c0d-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="04c0d-112">Element</span></span>|<span data-ttu-id="04c0d-113">Description</span><span class="sxs-lookup"><span data-stu-id="04c0d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="04c0d-114">Elemento PropertyName per SelectionCondition per EmtrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="04c0d-114">PropertyName Element for SelectionCondition for EmtrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="04c0d-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="04c0d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="04c0d-116">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="04c0d-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="04c0d-117">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="04c0d-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="04c0d-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="04c0d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="04c0d-119">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="04c0d-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="04c0d-120">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="04c0d-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="04c0d-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="04c0d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="04c0d-122">Specifica il set di tipi .NET che attivano la condizione.</span><span class="sxs-lookup"><span data-stu-id="04c0d-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="04c0d-123">Elemento TypeName per SelectionCondition per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="04c0d-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="04c0d-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="04c0d-124">Optional element.</span></span><br /><br /> <span data-ttu-id="04c0d-125">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="04c0d-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="04c0d-126">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="04c0d-126">Parent Elements</span></span>

|<span data-ttu-id="04c0d-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="04c0d-127">Element</span></span>|<span data-ttu-id="04c0d-128">Description</span><span class="sxs-lookup"><span data-stu-id="04c0d-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="04c0d-129">Elemento EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="04c0d-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="04c0d-130">Definisce i tipi .NET che usano la voce della tabella o la condizione che deve essere presente per questa voce da usare.</span><span class="sxs-lookup"><span data-stu-id="04c0d-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="04c0d-131">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="04c0d-131">Remarks</span></span>

<span data-ttu-id="04c0d-132">lWhen si sta definendo una condizione di selezione, applicano i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="04c0d-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="04c0d-133">La condizione di selezione è necessario specificare un nome di una proprietà minimi o un blocco di script, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="04c0d-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="04c0d-134">La condizione di selezione può includere un numero qualsiasi di tipi .NET o selezione imposta, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="04c0d-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="04c0d-135">Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="04c0d-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="04c0d-136">Per altre informazioni sugli altri componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="04c0d-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="04c0d-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="04c0d-137">See Also</span></span>

[<span data-ttu-id="04c0d-138">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="04c0d-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="04c0d-139">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="04c0d-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="04c0d-140">Elemento ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="04c0d-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="04c0d-141">Elemento SelectionSetName per EnrtySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="04c0d-141">SelectionSetName Element for EnrtySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="04c0d-142">Elemento TypeName per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="04c0d-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](http://msdn.microsoft.com/en-us/fcd4daa6-f3fd-43f7-a468-03c582d34533)

[<span data-ttu-id="04c0d-143">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="04c0d-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
