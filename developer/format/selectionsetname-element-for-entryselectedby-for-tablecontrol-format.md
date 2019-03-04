---
title: Elemento SelectionSetName per EntrySelectedBy per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856097"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="25078-102">Elemento SelectionSetName per EntrySelectedBy per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="25078-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="25078-103">Specifica che un set di .NET tipi l'uso di questa voce della visualizzazione della tabella.</span><span class="sxs-lookup"><span data-stu-id="25078-103">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="25078-104">Non sono previsti limiti al numero di set di selezione che è possibile specificare per una voce.</span><span class="sxs-lookup"><span data-stu-id="25078-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="25078-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) elemento EntrySelectedBy (formato) SelectionSetName elemento di configurazione per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="25078-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="25078-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="25078-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="25078-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="25078-107">Attributes and Elements</span></span>

<span data-ttu-id="25078-108">Le sezioni seguenti descrivono gli attributi, elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="25078-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="25078-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="25078-109">Attributes</span></span>

<span data-ttu-id="25078-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="25078-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="25078-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="25078-111">Child Elements</span></span>

<span data-ttu-id="25078-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="25078-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="25078-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="25078-113">Parent Elements</span></span>

|<span data-ttu-id="25078-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="25078-114">Element</span></span>|<span data-ttu-id="25078-115">Description</span><span class="sxs-lookup"><span data-stu-id="25078-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="25078-116">Elemento EntrySelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="25078-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="25078-117">Definisce i tipi .NET che usano questa voce o la condizione che deve essere presente per questa voce da usare.</span><span class="sxs-lookup"><span data-stu-id="25078-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="25078-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="25078-118">Text Value</span></span>

<span data-ttu-id="25078-119">Specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="25078-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="25078-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="25078-120">Remarks</span></span>

<span data-ttu-id="25078-121">Set di selezione vengono usati quando si desidera definire un gruppo di oggetti utilizzati in più viste.</span><span class="sxs-lookup"><span data-stu-id="25078-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="25078-122">Ad esempio, è possibile creare una visualizzazione tabella e una visualizzazione elenco per lo stesso set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="25078-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="25078-123">Per altre informazioni sulla definizione di set di selezione, vedere [definizione di set di oggetti per una visualizzazione](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="25078-123">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="25078-124">Se si specifica una selezione impostato per una voce, è possibile specificare un nome di tipo.</span><span class="sxs-lookup"><span data-stu-id="25078-124">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="25078-125">Per altre informazioni su come specificare un tipo .NET, vedere [elemento TypeName per EntrySelectedBy per TableRowEntry (formato)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span><span class="sxs-lookup"><span data-stu-id="25078-125">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="25078-126">Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="25078-126">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="25078-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="25078-127">See Also</span></span>

[<span data-ttu-id="25078-128">Elemento EntrySelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="25078-128">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="25078-129">La definizione di set di oggetti per una visualizzazione</span><span class="sxs-lookup"><span data-stu-id="25078-129">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="25078-130">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="25078-130">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="25078-131">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="25078-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
