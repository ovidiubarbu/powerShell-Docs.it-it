---
title: Elemento SelectionSetName per EntrySelectedBy per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368320"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="588f6-102">Elemento SelectionSetName per EntrySelectedBy per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="588f6-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="588f6-103">Specifica un set di tipi .NET che utilizzano questa voce della visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="588f6-103">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="588f6-104">Non esiste alcun limite al numero di set di selezione che è possibile specificare per una voce.</span><span class="sxs-lookup"><span data-stu-id="588f6-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="588f6-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) elemento EntrySelectedBy (Format) SelectionSetName elemento per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="588f6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="588f6-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="588f6-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="588f6-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="588f6-107">Attributes and Elements</span></span>

<span data-ttu-id="588f6-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="588f6-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="588f6-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="588f6-109">Attributes</span></span>

<span data-ttu-id="588f6-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="588f6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="588f6-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="588f6-111">Child Elements</span></span>

<span data-ttu-id="588f6-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="588f6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="588f6-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="588f6-113">Parent Elements</span></span>

|<span data-ttu-id="588f6-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="588f6-114">Element</span></span>|<span data-ttu-id="588f6-115">Description</span><span class="sxs-lookup"><span data-stu-id="588f6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="588f6-116">Elemento EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="588f6-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="588f6-117">Definisce i tipi .NET che utilizzano questa voce o la condizione che deve esistere affinché questa voce venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="588f6-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="588f6-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="588f6-118">Text Value</span></span>

<span data-ttu-id="588f6-119">Consente di specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="588f6-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="588f6-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="588f6-120">Remarks</span></span>

<span data-ttu-id="588f6-121">I set di selezione vengono in genere utilizzati quando si desidera definire un gruppo di oggetti utilizzati in più viste.</span><span class="sxs-lookup"><span data-stu-id="588f6-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="588f6-122">Ad esempio, potrebbe essere necessario creare una visualizzazione tabella e una visualizzazione elenco per lo stesso set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="588f6-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="588f6-123">Per ulteriori informazioni sulla definizione di set di selezione, vedere [definizione di set di oggetti per una vista](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="588f6-123">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="588f6-124">Se si specifica un set di selezione per una voce, non è possibile specificare un nome di tipo.</span><span class="sxs-lookup"><span data-stu-id="588f6-124">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="588f6-125">Per ulteriori informazioni su come specificare un tipo .NET, vedere [elemento TypeName per EntrySelectedBy per TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span><span class="sxs-lookup"><span data-stu-id="588f6-125">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="588f6-126">Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="588f6-126">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="588f6-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="588f6-127">See Also</span></span>

[<span data-ttu-id="588f6-128">Elemento EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="588f6-128">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="588f6-129">Definizione di set di oggetti per una vista</span><span class="sxs-lookup"><span data-stu-id="588f6-129">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="588f6-130">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="588f6-130">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="588f6-131">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="588f6-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
