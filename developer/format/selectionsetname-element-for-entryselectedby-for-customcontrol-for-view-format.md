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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063975"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="086d7-102">Elemento SelectionSetName per EntrySelectedBy per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="086d7-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="086d7-103">Specifica un set di oggetti .NET per la voce dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="086d7-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="086d7-104">Non sono previsti limiti al numero di set di selezione che è possibile specificare per una voce.</span><span class="sxs-lookup"><span data-stu-id="086d7-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="086d7-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per EntrySelectedBy visualizzazione (formato) Elemento per CustomEntry elemento di visualizzazione (formato) SelectionSetName per EntrySelectedBy per CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="086d7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="086d7-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="086d7-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="086d7-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="086d7-107">Attributes and Elements</span></span>

<span data-ttu-id="086d7-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="086d7-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="086d7-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="086d7-109">Attributes</span></span>

<span data-ttu-id="086d7-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="086d7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="086d7-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="086d7-111">Child Elements</span></span>

<span data-ttu-id="086d7-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="086d7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="086d7-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="086d7-113">Parent Elements</span></span>

|<span data-ttu-id="086d7-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="086d7-114">Element</span></span>|<span data-ttu-id="086d7-115">Description</span><span class="sxs-lookup"><span data-stu-id="086d7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="086d7-116">Elemento EntrySelectedBy per CustomEntry per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="086d7-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="086d7-117">Definisce i tipi .NET che usano questa voce personalizzata o la condizione che deve essere presente per questa voce da usare.</span><span class="sxs-lookup"><span data-stu-id="086d7-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="086d7-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="086d7-118">Text Value</span></span>

<span data-ttu-id="086d7-119">Specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="086d7-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="086d7-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="086d7-120">Remarks</span></span>

<span data-ttu-id="086d7-121">Ogni voce di controllo personalizzato deve avere almeno un nome di tipo, il set di selezione o condizione di selezione definiti.</span><span class="sxs-lookup"><span data-stu-id="086d7-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="086d7-122">Set di selezione vengono usati quando si desidera definire un gruppo di oggetti utilizzati in più viste.</span><span class="sxs-lookup"><span data-stu-id="086d7-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="086d7-123">Ad esempio, è possibile creare una visualizzazione tabella e una visualizzazione elenco per lo stesso set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="086d7-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="086d7-124">Per altre informazioni sulla definizione di set di selezione, vedere [definizione di selezione imposta](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="086d7-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="086d7-125">Per altre informazioni sui componenti di una vista di controllo personalizzato, vedere [Creating Custom Controls](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="086d7-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="086d7-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="086d7-126">See Also</span></span>

[<span data-ttu-id="086d7-127">Elemento EntrySelectedBy per CustomEntry per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="086d7-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="086d7-128">Visualizzazione controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="086d7-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="086d7-129">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="086d7-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
