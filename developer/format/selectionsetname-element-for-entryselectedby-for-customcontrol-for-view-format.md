---
title: Elemento SelectionSetName per EntrySelectedBy per CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855027"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="02b40-102">Elemento SelectionSetName per EntrySelectedBy per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="02b40-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="02b40-103">Specifica un set di oggetti .NET per la voce dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="02b40-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="02b40-104">Non sono previsti limiti al numero di set di selezione che è possibile specificare per una voce.</span><span class="sxs-lookup"><span data-stu-id="02b40-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="02b40-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per EntrySelectedBy visualizzazione (formato) Elemento per CustomEntry elemento di visualizzazione (formato) SelectionSetName per EntrySelectedBy per CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="02b40-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="02b40-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="02b40-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="02b40-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="02b40-107">Attributes and Elements</span></span>

<span data-ttu-id="02b40-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="02b40-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="02b40-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="02b40-109">Attributes</span></span>

<span data-ttu-id="02b40-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="02b40-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="02b40-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="02b40-111">Child Elements</span></span>

<span data-ttu-id="02b40-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="02b40-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="02b40-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="02b40-113">Parent Elements</span></span>

|<span data-ttu-id="02b40-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="02b40-114">Element</span></span>|<span data-ttu-id="02b40-115">Description</span><span class="sxs-lookup"><span data-stu-id="02b40-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="02b40-116">Elemento EntrySelectedBy per CustomEntry per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="02b40-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="02b40-117">Definisce i tipi .NET che usano questa voce personalizzata o la condizione che deve essere presente per questa voce da usare.</span><span class="sxs-lookup"><span data-stu-id="02b40-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="02b40-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="02b40-118">Text Value</span></span>

<span data-ttu-id="02b40-119">Specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="02b40-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="02b40-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="02b40-120">Remarks</span></span>

<span data-ttu-id="02b40-121">Ogni voce di controllo personalizzato deve avere almeno un nome di tipo, il set di selezione o condizione di selezione definiti.</span><span class="sxs-lookup"><span data-stu-id="02b40-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="02b40-122">Set di selezione vengono usati quando si desidera definire un gruppo di oggetti utilizzati in più viste.</span><span class="sxs-lookup"><span data-stu-id="02b40-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="02b40-123">Ad esempio, è possibile creare una visualizzazione tabella e una visualizzazione elenco per lo stesso set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="02b40-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="02b40-124">Per altre informazioni sulla definizione di set di selezione, vedere [definizione di selezione imposta](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="02b40-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="02b40-125">Per altre informazioni sui componenti di una vista di controllo personalizzato, vedere [Creating Custom Controls](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="02b40-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="02b40-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="02b40-126">See Also</span></span>

[<span data-ttu-id="02b40-127">Elemento EntrySelectedBy per CustomEntry per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="02b40-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="02b40-128">Visualizzazione controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="02b40-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="02b40-129">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="02b40-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
