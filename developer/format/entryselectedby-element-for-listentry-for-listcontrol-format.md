---
title: Elemento EntrySelectedBy per ListEntry per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054936"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="b33f0-102">Elemento EntrySelectedBy per ListEntry per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b33f0-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="b33f0-103">Definisce i tipi .NET che usano questa definizione di visualizzazione elenco o la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="b33f0-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="b33f0-104">Nella maggior parte dei casi è necessaria una sola definizione per una visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="b33f0-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="b33f0-105">Tuttavia, è possibile fornire più definizioni per la visualizzazione elenco se si desidera utilizzare la stessa visualizzazione elenco per visualizzare dati diversi per oggetti diversi.</span><span class="sxs-lookup"><span data-stu-id="b33f0-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="b33f0-106">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) ListEntries elemento di configurazione per elemento dell'oggetto ListControl (formato) ListEntry ListEntry per elemento EntrySelectedBy ListControl (formato) per ListEntry per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b33f0-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b33f0-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b33f0-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b33f0-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="b33f0-108">Attributes and Elements</span></span>

<span data-ttu-id="b33f0-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="b33f0-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b33f0-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="b33f0-110">Attributes</span></span>

<span data-ttu-id="b33f0-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="b33f0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b33f0-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="b33f0-112">Child Elements</span></span>

|<span data-ttu-id="b33f0-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="b33f0-113">Element</span></span>|<span data-ttu-id="b33f0-114">Description</span><span class="sxs-lookup"><span data-stu-id="b33f0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b33f0-115">Elemento SelectionCondition per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b33f0-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="b33f0-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b33f0-116">Optional element.</span></span><br /><br /> <span data-ttu-id="b33f0-117">Definisce la condizione che deve essere presente per questa definizione della vista elenco da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="b33f0-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="b33f0-118">Elemento SelectionSetName per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b33f0-118">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="b33f0-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b33f0-119">Optional element.</span></span><br /><br /> <span data-ttu-id="b33f0-120">Specifica un set di tipi .NET che usano questa definizione della vista elenco.</span><span class="sxs-lookup"><span data-stu-id="b33f0-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="b33f0-121">Elemento TypeName per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b33f0-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="b33f0-122">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b33f0-122">Optional element.</span></span><br /><br /> <span data-ttu-id="b33f0-123">Specifica un tipo .NET che usa questa definizione della vista elenco.</span><span class="sxs-lookup"><span data-stu-id="b33f0-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b33f0-124">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="b33f0-124">Parent Elements</span></span>

|<span data-ttu-id="b33f0-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="b33f0-125">Element</span></span>|<span data-ttu-id="b33f0-126">Description</span><span class="sxs-lookup"><span data-stu-id="b33f0-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b33f0-127">Elemento ListEntry per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b33f0-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="b33f0-128">Definisce come vengono visualizzate le righe dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="b33f0-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b33f0-129">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="b33f0-129">Remarks</span></span>

<span data-ttu-id="b33f0-130">È necessario specificare almeno un tipo, il set di selezione o condizione di selezione per una definizione della vista elenco.</span><span class="sxs-lookup"><span data-stu-id="b33f0-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="b33f0-131">Non è definito alcun limite massimo al numero di elementi figlio che è possibile usare.</span><span class="sxs-lookup"><span data-stu-id="b33f0-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="b33f0-132">Condizioni di selezione vengono usate per definire una condizione che deve essere presente per la definizione da usare, ad esempio quando un oggetto dispone di una proprietà specifica o che restituisce un valore della proprietà specifica o uno script `true`.</span><span class="sxs-lookup"><span data-stu-id="b33f0-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="b33f0-133">Per altre informazioni sulle condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b33f0-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b33f0-134">Per altre informazioni sui componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="b33f0-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b33f0-135">Esempio</span><span class="sxs-lookup"><span data-stu-id="b33f0-135">Example</span></span>

<span data-ttu-id="b33f0-136">Nell'esempio seguente viene illustrato come definire gli oggetti per una visualizzazione elenco utilizzando il nome del tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="b33f0-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="b33f0-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b33f0-137">See Also</span></span>

[<span data-ttu-id="b33f0-138">Elemento ListEntry per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b33f0-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="b33f0-139">Elemento SelectionCondition per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b33f0-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="b33f0-140">Elemento SelectionSetName per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b33f0-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="b33f0-141">Elemento TypeName per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b33f0-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="b33f0-142">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="b33f0-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="b33f0-143">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="b33f0-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b33f0-144">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="b33f0-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
