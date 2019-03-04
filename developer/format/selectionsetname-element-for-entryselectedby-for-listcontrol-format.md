---
title: Elemento SelectionSetName per EntrySelectedBy per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860157"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="dfd29-102">Elemento SelectionSetName per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="dfd29-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="dfd29-103">Specifica un set di oggetti .NET per la voce dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="dfd29-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="dfd29-104">Non sono previsti limiti al numero di set di selezione che è possibile specificare per una voce.</span><span class="sxs-lookup"><span data-stu-id="dfd29-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="dfd29-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) elemento ListEntries (formato) elemento ListEntry (formato) EntrySelectedBy elemento di configurazione per elemento SelectionSetName ListEntry (formato) EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="dfd29-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dfd29-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="dfd29-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dfd29-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="dfd29-107">Attributes and Elements</span></span>

<span data-ttu-id="dfd29-108">Le sezioni seguenti descrivono l'elemento padre di attributi e gli elementi figlio di `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="dfd29-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dfd29-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="dfd29-109">Attributes</span></span>

<span data-ttu-id="dfd29-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="dfd29-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dfd29-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="dfd29-111">Child Elements</span></span>

<span data-ttu-id="dfd29-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="dfd29-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dfd29-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="dfd29-113">Parent Elements</span></span>

|<span data-ttu-id="dfd29-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="dfd29-114">Element</span></span>|<span data-ttu-id="dfd29-115">Description</span><span class="sxs-lookup"><span data-stu-id="dfd29-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dfd29-116">Elemento EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="dfd29-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="dfd29-117">Definisce i tipi .NET che usano questa voce di elenco o la condizione che deve essere presente per questa voce da usare.</span><span class="sxs-lookup"><span data-stu-id="dfd29-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dfd29-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="dfd29-118">Text Value</span></span>

<span data-ttu-id="dfd29-119">Specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="dfd29-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="dfd29-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="dfd29-120">Remarks</span></span>

<span data-ttu-id="dfd29-121">Ogni voce dell'elenco deve avere almeno un nome di tipo, il set di selezione o condizione di selezione definiti.</span><span class="sxs-lookup"><span data-stu-id="dfd29-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="dfd29-122">Set di selezione vengono usati quando si desidera definire un gruppo di oggetti utilizzati in più viste.</span><span class="sxs-lookup"><span data-stu-id="dfd29-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="dfd29-123">Ad esempio, è possibile creare una visualizzazione tabella e una visualizzazione elenco per lo stesso set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="dfd29-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="dfd29-124">Per altre informazioni sulla definizione di set di selezione, vedere [definizione di set di oggetti per una visualizzazione](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="dfd29-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="dfd29-125">Per altre informazioni sui componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="dfd29-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="dfd29-126">Esempio</span><span class="sxs-lookup"><span data-stu-id="dfd29-126">Example</span></span>

<span data-ttu-id="dfd29-127">Nell'esempio seguente viene illustrato come specificare un insieme di una voce di una visualizzazione elenco di selezione.</span><span class="sxs-lookup"><span data-stu-id="dfd29-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="dfd29-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="dfd29-128">See Also</span></span>

[<span data-ttu-id="dfd29-129">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="dfd29-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="dfd29-130">Elemento EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="dfd29-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="dfd29-131">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="dfd29-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
