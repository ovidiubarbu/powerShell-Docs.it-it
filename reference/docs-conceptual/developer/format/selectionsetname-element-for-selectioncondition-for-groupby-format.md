---
title: Elemento SelectionSetName per SelectionCondition per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361860"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="67d85-102">Elemento SelectionSetName per SelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="67d85-102">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="67d85-103">Specifica il set di tipi .NET che attivano la condizione.</span><span class="sxs-lookup"><span data-stu-id="67d85-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="67d85-104">Quando uno dei tipi in questo set è presente, la condizione viene soddisfatta e l'oggetto viene visualizzato tramite questo controllo.</span><span class="sxs-lookup"><span data-stu-id="67d85-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="67d85-105">Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="67d85-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="67d85-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format) elemento EntrySelectedBy per CustomEntry per l'elemento SelectionCondition di GroupBy (Format) per EntrySelectedBy per SelectionSetName per l'elemento SelectionCondition di GroupBy (Format) per per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="67d85-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="67d85-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="67d85-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="67d85-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="67d85-108">Attributes and Elements</span></span>

<span data-ttu-id="67d85-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="67d85-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="67d85-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="67d85-110">Attributes</span></span>

<span data-ttu-id="67d85-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="67d85-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="67d85-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="67d85-112">Child Elements</span></span>

<span data-ttu-id="67d85-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="67d85-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="67d85-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="67d85-114">Parent Elements</span></span>

|<span data-ttu-id="67d85-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="67d85-115">Element</span></span>|<span data-ttu-id="67d85-116">Description</span><span class="sxs-lookup"><span data-stu-id="67d85-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67d85-117">Elemento SelectionCondition per EntrySelectedBy per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="67d85-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="67d85-118">Definisce una condizione che deve esistere per la definizione del controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="67d85-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="67d85-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="67d85-119">Text Value</span></span>

<span data-ttu-id="67d85-120">Consente di specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="67d85-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="67d85-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="67d85-121">Remarks</span></span>

<span data-ttu-id="67d85-122">I set di selezione sono gruppi comuni di oggetti .NET che possono essere utilizzati da qualsiasi visualizzazione definita dal file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="67d85-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="67d85-123">Per ulteriori informazioni sulla creazione e il riferimento a set di selezione, vedere [definizione di set di selezione](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="67d85-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="67d85-124">Quando questo elemento viene specificato, non è possibile specificare l'elemento [typeName](./typename-element-for-selectioncondition-for-groupby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="67d85-124">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="67d85-125">Per ulteriori informazioni sulla definizione delle condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="67d85-125">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="67d85-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="67d85-126">See Also</span></span>

[<span data-ttu-id="67d85-127">Elemento TypeName per SelectionCondition per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="67d85-127">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="67d85-128">Elemento SelectionCondition per EntrySelectedBy per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="67d85-128">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="67d85-129">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="67d85-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="67d85-130">Definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="67d85-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="67d85-131">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="67d85-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)