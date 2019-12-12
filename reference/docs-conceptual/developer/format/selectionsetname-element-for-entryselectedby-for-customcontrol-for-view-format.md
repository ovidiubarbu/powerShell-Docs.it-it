---
title: Elemento SelectionSetName per EntrySelectedBy per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364750"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="43c2d-102">Elemento SelectionSetName per EntrySelectedBy per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="43c2d-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="43c2d-103">Specifica un set di oggetti .NET per la voce dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="43c2d-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="43c2d-104">Non esiste alcun limite al numero di set di selezione che è possibile specificare per una voce.</span><span class="sxs-lookup"><span data-stu-id="43c2d-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="43c2d-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per l'elemento View (Format) CustomEntry per CustomEntries per View (Format) EntrySelectedBy Elemento per CustomEntry per la visualizzazione (Format) elemento SelectionSetName per EntrySelectedBy per CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="43c2d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="43c2d-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="43c2d-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="43c2d-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="43c2d-107">Attributes and Elements</span></span>

<span data-ttu-id="43c2d-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="43c2d-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="43c2d-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="43c2d-109">Attributes</span></span>

<span data-ttu-id="43c2d-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="43c2d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="43c2d-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="43c2d-111">Child Elements</span></span>

<span data-ttu-id="43c2d-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="43c2d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="43c2d-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="43c2d-113">Parent Elements</span></span>

|<span data-ttu-id="43c2d-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="43c2d-114">Element</span></span>|<span data-ttu-id="43c2d-115">Description</span><span class="sxs-lookup"><span data-stu-id="43c2d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="43c2d-116">Elemento EntrySelectedBy per CustomEntry per View (Format)</span><span class="sxs-lookup"><span data-stu-id="43c2d-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="43c2d-117">Definisce i tipi .NET che utilizzano questa voce personalizzata o la condizione che deve esistere affinché questa voce venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="43c2d-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="43c2d-118">Valore testo</span><span class="sxs-lookup"><span data-stu-id="43c2d-118">Text Value</span></span>

<span data-ttu-id="43c2d-119">Consente di specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="43c2d-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="43c2d-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="43c2d-120">Remarks</span></span>

<span data-ttu-id="43c2d-121">Per ogni voce di controllo personalizzata è necessario definire almeno un nome di tipo, un set di selezione o una condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="43c2d-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="43c2d-122">I set di selezione vengono in genere utilizzati quando si desidera definire un gruppo di oggetti utilizzati in più viste.</span><span class="sxs-lookup"><span data-stu-id="43c2d-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="43c2d-123">Ad esempio, potrebbe essere necessario creare una visualizzazione tabella e una visualizzazione elenco per lo stesso set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="43c2d-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="43c2d-124">Per ulteriori informazioni sulla definizione di set di selezione, vedere [definizione di set di selezione](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="43c2d-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="43c2d-125">Per ulteriori informazioni sui componenti di una visualizzazione controlli personalizzata, vedere [creazione di controlli personalizzati](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="43c2d-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="43c2d-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="43c2d-126">See Also</span></span>

[<span data-ttu-id="43c2d-127">Elemento EntrySelectedBy per CustomEntry per View (Format)</span><span class="sxs-lookup"><span data-stu-id="43c2d-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="43c2d-128">Visualizzazione controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="43c2d-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="43c2d-129">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="43c2d-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
