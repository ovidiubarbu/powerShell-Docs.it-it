---
title: Elemento SelectionSetName per EntrySelectedBy per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362000"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="33986-102">Elemento SelectionSetName per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="33986-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="33986-103">Specifica un set di oggetti .NET per la voce dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="33986-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="33986-104">Non esiste alcun limite al numero di set di selezione che è possibile specificare per una voce.</span><span class="sxs-lookup"><span data-stu-id="33986-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="33986-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento EntrySelectedBy per ListEntry (Format) SelectionSetName elemento per EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="33986-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="33986-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="33986-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="33986-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="33986-107">Attributes and Elements</span></span>

<span data-ttu-id="33986-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="33986-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="33986-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="33986-109">Attributes</span></span>

<span data-ttu-id="33986-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="33986-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="33986-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="33986-111">Child Elements</span></span>

<span data-ttu-id="33986-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="33986-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="33986-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="33986-113">Parent Elements</span></span>

|<span data-ttu-id="33986-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="33986-114">Element</span></span>|<span data-ttu-id="33986-115">Description</span><span class="sxs-lookup"><span data-stu-id="33986-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33986-116">Elemento EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="33986-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="33986-117">Definisce i tipi .NET che utilizzano questa voce di elenco o la condizione che deve esistere affinché questa voce venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="33986-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="33986-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="33986-118">Text Value</span></span>

<span data-ttu-id="33986-119">Consente di specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="33986-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="33986-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="33986-120">Remarks</span></span>

<span data-ttu-id="33986-121">Per ogni voce di elenco è necessario definire almeno un nome di tipo, un set di selezione o una condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="33986-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="33986-122">I set di selezione vengono in genere utilizzati quando si desidera definire un gruppo di oggetti utilizzati in più viste.</span><span class="sxs-lookup"><span data-stu-id="33986-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="33986-123">Ad esempio, potrebbe essere necessario creare una visualizzazione tabella e una visualizzazione elenco per lo stesso set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="33986-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="33986-124">Per ulteriori informazioni sulla definizione di set di selezione, vedere [definizione di set di oggetti per una vista](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="33986-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="33986-125">Per ulteriori informazioni sui componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="33986-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="33986-126">Esempio</span><span class="sxs-lookup"><span data-stu-id="33986-126">Example</span></span>

<span data-ttu-id="33986-127">Nell'esempio seguente viene illustrato come specificare un set di selezione per una voce di una visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="33986-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="33986-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="33986-128">See Also</span></span>

[<span data-ttu-id="33986-129">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="33986-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="33986-130">Elemento EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="33986-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="33986-131">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="33986-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
