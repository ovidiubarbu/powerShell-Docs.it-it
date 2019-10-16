---
title: Elemento EntrySelectedBy per ListEntry per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363830"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="6cf74-102">Elemento EntrySelectedBy per ListEntry per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="6cf74-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="6cf74-103">Definisce i tipi .NET che utilizzano questa definizione di visualizzazione elenco o la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="6cf74-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="6cf74-104">Nella maggior parte dei casi è necessaria una sola definizione per una visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="6cf74-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="6cf74-105">È tuttavia possibile specificare più definizioni per la visualizzazione elenco se si desidera utilizzare la stessa visualizzazione elenco per visualizzare dati diversi per oggetti diversi.</span><span class="sxs-lookup"><span data-stu-id="6cf74-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="6cf74-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries per ListControl (Format) elemento ListEntry per ListEntry per l'elemento ListControl (Format) EntrySelectedBy per ListEntry per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="6cf74-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6cf74-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6cf74-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6cf74-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="6cf74-108">Attributes and Elements</span></span>

<span data-ttu-id="6cf74-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="6cf74-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6cf74-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="6cf74-110">Attributes</span></span>

<span data-ttu-id="6cf74-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="6cf74-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6cf74-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="6cf74-112">Child Elements</span></span>

|<span data-ttu-id="6cf74-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="6cf74-113">Element</span></span>|<span data-ttu-id="6cf74-114">Description</span><span class="sxs-lookup"><span data-stu-id="6cf74-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6cf74-115">Elemento SelectionCondition per EntrySelectedBy per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6cf74-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="6cf74-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="6cf74-116">Optional element.</span></span><br /><br /> <span data-ttu-id="6cf74-117">Definisce la condizione che deve esistere affinché questa definizione di visualizzazione elenco venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="6cf74-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="6cf74-118">Elemento SelectionSetName per EntrySelectedBy per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6cf74-118">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="6cf74-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="6cf74-119">Optional element.</span></span><br /><br /> <span data-ttu-id="6cf74-120">Specifica un set di tipi .NET che utilizzano questa definizione della vista elenco.</span><span class="sxs-lookup"><span data-stu-id="6cf74-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="6cf74-121">Elemento TypeName per EntrySelectedBy per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6cf74-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="6cf74-122">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="6cf74-122">Optional element.</span></span><br /><br /> <span data-ttu-id="6cf74-123">Specifica un tipo .NET che usa questa definizione di visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="6cf74-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6cf74-124">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="6cf74-124">Parent Elements</span></span>

|<span data-ttu-id="6cf74-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="6cf74-125">Element</span></span>|<span data-ttu-id="6cf74-126">Description</span><span class="sxs-lookup"><span data-stu-id="6cf74-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6cf74-127">Elemento ListEntry per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6cf74-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="6cf74-128">Definisce la modalità di visualizzazione delle righe dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="6cf74-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6cf74-129">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="6cf74-129">Remarks</span></span>

<span data-ttu-id="6cf74-130">È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per una definizione di visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="6cf74-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="6cf74-131">Non esiste un limite massimo per il numero di elementi figlio che è possibile usare.</span><span class="sxs-lookup"><span data-stu-id="6cf74-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="6cf74-132">Le condizioni di selezione vengono usate per definire una condizione che deve esistere per la definizione da usare, ad esempio quando un oggetto ha una proprietà specifica o che un valore di proprietà o uno script specifico restituisce `true`.</span><span class="sxs-lookup"><span data-stu-id="6cf74-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="6cf74-133">Per ulteriori informazioni sulle condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6cf74-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="6cf74-134">Per ulteriori informazioni sui componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="6cf74-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6cf74-135">Esempio</span><span class="sxs-lookup"><span data-stu-id="6cf74-135">Example</span></span>

<span data-ttu-id="6cf74-136">Nell'esempio seguente viene illustrato come definire gli oggetti per una visualizzazione elenco utilizzando il relativo nome di tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="6cf74-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="6cf74-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6cf74-137">See Also</span></span>

[<span data-ttu-id="6cf74-138">Elemento ListEntry per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6cf74-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="6cf74-139">Elemento SelectionCondition per EntrySelectedBy per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6cf74-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="6cf74-140">Elemento SelectionSetName per EntrySelectedBy per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6cf74-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="6cf74-141">Elemento TypeName per EntrySelectedBy per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6cf74-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="6cf74-142">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="6cf74-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="6cf74-143">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="6cf74-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="6cf74-144">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="6cf74-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
