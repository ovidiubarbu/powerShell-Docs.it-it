---
title: Elemento SelectionSetName per EntrySelectedBy per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064068"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="d51b6-102">Elemento SelectionSetName per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d51b6-102">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="d51b6-103">Specifica un set di oggetti .NET per la voce dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="d51b6-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="d51b6-104">Non sono previsti limiti al numero di set di selezione che è possibile specificare per una voce.</span><span class="sxs-lookup"><span data-stu-id="d51b6-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="d51b6-105">Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="d51b6-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="d51b6-106">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per elemento EntrySelectedBy GroupBy (formato) per CustomEntry per elemento SelectionSetName GroupBy (formato) per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d51b6-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d51b6-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d51b6-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d51b6-108">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="d51b6-108">Attributes and Elements</span></span>

<span data-ttu-id="d51b6-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="d51b6-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d51b6-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="d51b6-110">Attributes</span></span>

<span data-ttu-id="d51b6-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="d51b6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d51b6-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="d51b6-112">Child Elements</span></span>

<span data-ttu-id="d51b6-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="d51b6-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d51b6-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="d51b6-114">Parent Elements</span></span>

|<span data-ttu-id="d51b6-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="d51b6-115">Element</span></span>|<span data-ttu-id="d51b6-116">Description</span><span class="sxs-lookup"><span data-stu-id="d51b6-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d51b6-117">Elemento EntrySelectedBy per CustomEntry per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d51b6-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="d51b6-118">Definisce i tipi .NET che usano questa voce personalizzata o la condizione che deve essere presente per questa voce da usare.</span><span class="sxs-lookup"><span data-stu-id="d51b6-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d51b6-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="d51b6-119">Text Value</span></span>

<span data-ttu-id="d51b6-120">Specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="d51b6-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="d51b6-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="d51b6-121">Remarks</span></span>

<span data-ttu-id="d51b6-122">Ogni definizione di controllo personalizzato deve avere almeno un nome di tipo, il set di selezione o condizione di selezione definiti.</span><span class="sxs-lookup"><span data-stu-id="d51b6-122">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="d51b6-123">Set di selezione vengono usati quando si desidera definire un gruppo di oggetti utilizzati in più viste.</span><span class="sxs-lookup"><span data-stu-id="d51b6-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="d51b6-124">Ad esempio, è possibile creare una visualizzazione tabella e una visualizzazione elenco per lo stesso set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="d51b6-124">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="d51b6-125">Per altre informazioni sulla definizione di set di selezione, vedere [definizione di selezione imposta](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="d51b6-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="d51b6-126">Per altre informazioni sui componenti di una vista di controllo personalizzato, vedere [Creating Custom Controls](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d51b6-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d51b6-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d51b6-127">See Also</span></span>

[<span data-ttu-id="d51b6-128">Elemento EntrySelectedBy per CustomEntry per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d51b6-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="d51b6-129">Creazione di controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="d51b6-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="d51b6-130">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="d51b6-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
