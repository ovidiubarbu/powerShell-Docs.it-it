---
title: Elemento SelectionSetName per EntrySelectedBy per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364740"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="fb11d-102">Elemento SelectionSetName per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="fb11d-102">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="fb11d-103">Specifica un set di oggetti .NET per la voce dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="fb11d-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="fb11d-104">Non esiste alcun limite al numero di set di selezione che è possibile specificare per una voce.</span><span class="sxs-lookup"><span data-stu-id="fb11d-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="fb11d-105">Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="fb11d-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="fb11d-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format) elemento EntrySelectedBy per CustomEntry per GroupBy (Format) SelectionSetName elemento per EntrySelectedBy per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="fb11d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fb11d-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="fb11d-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fb11d-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="fb11d-108">Attributes and Elements</span></span>

<span data-ttu-id="fb11d-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="fb11d-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fb11d-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="fb11d-110">Attributes</span></span>

<span data-ttu-id="fb11d-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="fb11d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fb11d-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="fb11d-112">Child Elements</span></span>

<span data-ttu-id="fb11d-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="fb11d-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fb11d-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="fb11d-114">Parent Elements</span></span>

|<span data-ttu-id="fb11d-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="fb11d-115">Element</span></span>|<span data-ttu-id="fb11d-116">Description</span><span class="sxs-lookup"><span data-stu-id="fb11d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fb11d-117">Elemento EntrySelectedBy per CustomEntry per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="fb11d-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="fb11d-118">Definisce i tipi .NET che utilizzano questa voce personalizzata o la condizione che deve esistere affinché questa voce venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="fb11d-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fb11d-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="fb11d-119">Text Value</span></span>

<span data-ttu-id="fb11d-120">Consente di specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="fb11d-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="fb11d-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="fb11d-121">Remarks</span></span>

<span data-ttu-id="fb11d-122">Per ogni definizione di controllo personalizzato deve essere definito almeno un nome di tipo, un set di selezione o una condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="fb11d-122">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="fb11d-123">I set di selezione vengono in genere utilizzati quando si desidera definire un gruppo di oggetti utilizzati in più viste.</span><span class="sxs-lookup"><span data-stu-id="fb11d-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="fb11d-124">È ad esempio possibile creare una visualizzazione tabella e una visualizzazione elenco per lo stesso set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="fb11d-124">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="fb11d-125">Per ulteriori informazioni sulla definizione di set di selezione, vedere [definizione di set di selezione](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="fb11d-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="fb11d-126">Per ulteriori informazioni sui componenti di una visualizzazione controlli personalizzata, vedere [creazione di controlli personalizzati](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="fb11d-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fb11d-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fb11d-127">See Also</span></span>

[<span data-ttu-id="fb11d-128">Elemento EntrySelectedBy per CustomEntry per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="fb11d-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="fb11d-129">Creazione di controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="fb11d-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="fb11d-130">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb11d-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)