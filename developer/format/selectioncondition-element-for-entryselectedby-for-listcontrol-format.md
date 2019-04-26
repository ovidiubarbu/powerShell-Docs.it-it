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
ms.openlocfilehash: 633204f3b181316761746ea2679910216fb74657
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064102"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="56626-102">Elemento SelectionCondition per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="56626-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="56626-103">Definisce la condizione che deve essere presente per usare questa definizione della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="56626-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="56626-104">Non sono previsti limiti al numero di condizioni di selezione che è possibile specificare per una definizione di elenco.</span><span class="sxs-lookup"><span data-stu-id="56626-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="56626-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) elemento ListEntries (formato) elemento ListEntry (formato) EntrySelectedBy elemento di configurazione per elemento SelectionCondition ListEntry (formato) EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="56626-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="56626-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="56626-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="56626-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="56626-107">Attributes and Elements</span></span>

<span data-ttu-id="56626-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="56626-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="56626-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="56626-109">Attributes</span></span>

<span data-ttu-id="56626-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="56626-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="56626-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="56626-111">Child Elements</span></span>

|<span data-ttu-id="56626-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="56626-112">Element</span></span>|<span data-ttu-id="56626-113">Description</span><span class="sxs-lookup"><span data-stu-id="56626-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="56626-114">Elemento PropertyName per SelectionCondition per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="56626-114">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="56626-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="56626-115">Optional element.</span></span><br /><br /> <span data-ttu-id="56626-116">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="56626-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="56626-117">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="56626-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="56626-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="56626-118">Optional element.</span></span><br /><br /> <span data-ttu-id="56626-119">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="56626-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="56626-120">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="56626-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="56626-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="56626-121">Optional element.</span></span><br /><br /> <span data-ttu-id="56626-122">Specifica il set di tipi .NET che attivano la condizione.</span><span class="sxs-lookup"><span data-stu-id="56626-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="56626-123">Elemento TypeName per SelectionCondition per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="56626-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="56626-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="56626-124">Optional element.</span></span><br /><br /> <span data-ttu-id="56626-125">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="56626-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="56626-126">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="56626-126">Parent Elements</span></span>

|<span data-ttu-id="56626-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="56626-127">Element</span></span>|<span data-ttu-id="56626-128">Description</span><span class="sxs-lookup"><span data-stu-id="56626-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="56626-129">Elemento EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="56626-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="56626-130">Definisce i tipi .NET che usano la voce della tabella o la condizione che deve essere presente per questa voce da usare.</span><span class="sxs-lookup"><span data-stu-id="56626-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="56626-131">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="56626-131">Remarks</span></span>

<span data-ttu-id="56626-132">lWhen si sta definendo una condizione di selezione, applicano i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="56626-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="56626-133">La condizione di selezione è necessario specificare un nome di una proprietà minimi o un blocco di script, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="56626-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="56626-134">La condizione di selezione può includere un numero qualsiasi di tipi .NET o selezione imposta, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="56626-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="56626-135">Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="56626-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="56626-136">Per altre informazioni sugli altri componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="56626-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="56626-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="56626-137">See Also</span></span>

[<span data-ttu-id="56626-138">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="56626-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="56626-139">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="56626-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="56626-140">Elemento ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="56626-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="56626-141">Elemento SelectionSetName per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="56626-141">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="56626-142">Elemento TypeName per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="56626-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](http://msdn.microsoft.com/en-us/fcd4daa6-f3fd-43f7-a468-03c582d34533)

[<span data-ttu-id="56626-143">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="56626-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
