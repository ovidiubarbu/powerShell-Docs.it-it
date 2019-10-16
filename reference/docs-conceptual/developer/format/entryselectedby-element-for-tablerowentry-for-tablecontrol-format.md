---
title: Elemento EntrySelectedBy per TableRowEntry per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363340"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="1e5a7-102">Elemento EntrySelectedBy per TableRowEntry per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1e5a7-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="1e5a7-103">Definisce i tipi .NET che utilizzano questa definizione della vista tabella o la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="1e5a7-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="1e5a7-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) elemento EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1e5a7-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1e5a7-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1e5a7-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1e5a7-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="1e5a7-106">Attributes and Elements</span></span>

<span data-ttu-id="1e5a7-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="1e5a7-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1e5a7-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="1e5a7-108">Attributes</span></span>

<span data-ttu-id="1e5a7-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="1e5a7-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1e5a7-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="1e5a7-110">Child Elements</span></span>

|<span data-ttu-id="1e5a7-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="1e5a7-111">Element</span></span>|<span data-ttu-id="1e5a7-112">Description</span><span class="sxs-lookup"><span data-stu-id="1e5a7-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1e5a7-113">Elemento SelectionCondition per EntrySelectedBy per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="1e5a7-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="1e5a7-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="1e5a7-114">Optional element.</span></span><br /><br /> <span data-ttu-id="1e5a7-115">Definisce la condizione che deve esistere per la definizione della vista tabella da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="1e5a7-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="1e5a7-116">Elemento SelectionSetName per EntrySelectedBy per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="1e5a7-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="1e5a7-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="1e5a7-117">Optional element.</span></span><br /><br /> <span data-ttu-id="1e5a7-118">Specifica un set di tipi .NET che utilizzano questa definizione della vista tabella.</span><span class="sxs-lookup"><span data-stu-id="1e5a7-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="1e5a7-119">Elemento TypeName per EntrySelectedBy per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="1e5a7-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="1e5a7-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="1e5a7-120">Optional element.</span></span><br /><br /> <span data-ttu-id="1e5a7-121">Specifica un tipo .NET che usa questa definizione della vista tabella.</span><span class="sxs-lookup"><span data-stu-id="1e5a7-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1e5a7-122">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="1e5a7-122">Parent Elements</span></span>

|<span data-ttu-id="1e5a7-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="1e5a7-123">Element</span></span>|<span data-ttu-id="1e5a7-124">Description</span><span class="sxs-lookup"><span data-stu-id="1e5a7-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1e5a7-125">Elemento TableRowEntry per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="1e5a7-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="1e5a7-126">Definisce i dati visualizzati in una riga della tabella.</span><span class="sxs-lookup"><span data-stu-id="1e5a7-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1e5a7-127">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="1e5a7-127">Remarks</span></span>

<span data-ttu-id="1e5a7-128">È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per una definizione di vista tabella.</span><span class="sxs-lookup"><span data-stu-id="1e5a7-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="1e5a7-129">Non esiste un limite massimo per il numero di elementi figlio che è possibile usare.</span><span class="sxs-lookup"><span data-stu-id="1e5a7-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="1e5a7-130">Le condizioni di selezione vengono usate per definire una condizione che deve esistere per la definizione da usare, ad esempio quando un oggetto ha una proprietà specifica o che un valore di proprietà o uno script specifico restituisce `true`.</span><span class="sxs-lookup"><span data-stu-id="1e5a7-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="1e5a7-131">Per ulteriori informazioni sulle condizioni di selezione, vedere [definizione di condizioni per l'utilizzo di una voce o di un elemento della visualizzazione](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1e5a7-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1e5a7-132">Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="1e5a7-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1e5a7-133">Esempio</span><span class="sxs-lookup"><span data-stu-id="1e5a7-133">Example</span></span>

<span data-ttu-id="1e5a7-134">Nell'esempio seguente viene illustrato un elemento `TableRowEntry` utilizzato per visualizzare le proprietà dell'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="1e5a7-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a><span data-ttu-id="1e5a7-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1e5a7-135">See Also</span></span>

[<span data-ttu-id="1e5a7-136">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="1e5a7-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="1e5a7-137">Elemento SelectionCondition per EntrySelectedBy per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="1e5a7-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="1e5a7-138">Elemento SelectionSetName per EntrySelectedBy per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="1e5a7-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="1e5a7-139">Elemento TableRowEntry per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="1e5a7-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="1e5a7-140">Elemento TypeName per EntrySelectedBy per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="1e5a7-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="1e5a7-141">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="1e5a7-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
