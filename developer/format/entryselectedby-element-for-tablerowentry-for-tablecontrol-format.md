---
title: Elemento EntrySelectedBy per TableRowEntry per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058760"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="f9f8a-102">Elemento EntrySelectedBy per TableRowEntry per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f9f8a-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="f9f8a-103">Definisce i tipi .NET che usano questa definizione di visualizzazione della tabella o la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="f9f8a-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="f9f8a-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento di configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f9f8a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f9f8a-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f9f8a-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f9f8a-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="f9f8a-106">Attributes and Elements</span></span>

<span data-ttu-id="f9f8a-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="f9f8a-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f9f8a-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="f9f8a-108">Attributes</span></span>

<span data-ttu-id="f9f8a-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f9f8a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f9f8a-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f9f8a-110">Child Elements</span></span>

|<span data-ttu-id="f9f8a-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="f9f8a-111">Element</span></span>|<span data-ttu-id="f9f8a-112">Description</span><span class="sxs-lookup"><span data-stu-id="f9f8a-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f9f8a-113">Elemento SelectionCondition per EntrySelectedBy per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="f9f8a-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="f9f8a-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="f9f8a-114">Optional element.</span></span><br /><br /> <span data-ttu-id="f9f8a-115">Definisce la condizione che deve essere presente per questa definizione di visualizzazione tabella da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="f9f8a-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="f9f8a-116">Elemento SelectionSetName per EntrySelectedBy per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="f9f8a-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="f9f8a-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="f9f8a-117">Optional element.</span></span><br /><br /> <span data-ttu-id="f9f8a-118">Specifica un set di tipi .NET che usano questa definizione di vista della tabella.</span><span class="sxs-lookup"><span data-stu-id="f9f8a-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="f9f8a-119">Elemento TypeName per EntrySelectedBy per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="f9f8a-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="f9f8a-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="f9f8a-120">Optional element.</span></span><br /><br /> <span data-ttu-id="f9f8a-121">Specifica un tipo .NET che usa questa definizione di vista della tabella.</span><span class="sxs-lookup"><span data-stu-id="f9f8a-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f9f8a-122">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f9f8a-122">Parent Elements</span></span>

|<span data-ttu-id="f9f8a-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="f9f8a-123">Element</span></span>|<span data-ttu-id="f9f8a-124">Description</span><span class="sxs-lookup"><span data-stu-id="f9f8a-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f9f8a-125">Elemento TableRowEntry per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="f9f8a-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="f9f8a-126">Definisce i dati che viene visualizzati in una riga della tabella.</span><span class="sxs-lookup"><span data-stu-id="f9f8a-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f9f8a-127">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f9f8a-127">Remarks</span></span>

<span data-ttu-id="f9f8a-128">È necessario specificare almeno un tipo, set di selezione o condizione di selezione per una definizione di vista della tabella.</span><span class="sxs-lookup"><span data-stu-id="f9f8a-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="f9f8a-129">Non è definito alcun limite massimo al numero di elementi figlio che è possibile usare.</span><span class="sxs-lookup"><span data-stu-id="f9f8a-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="f9f8a-130">Condizioni di selezione vengono usate per definire una condizione che deve essere presente per la definizione da usare, ad esempio quando un oggetto dispone di una proprietà specifica o che restituisce un valore della proprietà specifica o uno script `true`.</span><span class="sxs-lookup"><span data-stu-id="f9f8a-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="f9f8a-131">Per altre informazioni sulle condizioni di selezione, vedere [definizione di condizioni per quando una voce di visualizzazione o viene usato l'elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f9f8a-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f9f8a-132">Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f9f8a-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f9f8a-133">Esempio</span><span class="sxs-lookup"><span data-stu-id="f9f8a-133">Example</span></span>

<span data-ttu-id="f9f8a-134">L'esempio seguente mostra una `TableRowEntry` elemento utilizzato per visualizzare le proprietà del [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto.</span><span class="sxs-lookup"><span data-stu-id="f9f8a-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f9f8a-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f9f8a-135">See Also</span></span>

[<span data-ttu-id="f9f8a-136">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="f9f8a-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f9f8a-137">Elemento SelectionCondition per EntrySelectedBy per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="f9f8a-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="f9f8a-138">Elemento SelectionSetName per EntrySelectedBy per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="f9f8a-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="f9f8a-139">Elemento TableRowEntry per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="f9f8a-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="f9f8a-140">Elemento TypeName per EntrySelectedBy per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="f9f8a-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="f9f8a-141">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f9f8a-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
