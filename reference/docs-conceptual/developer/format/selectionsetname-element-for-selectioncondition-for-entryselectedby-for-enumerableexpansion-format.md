---
title: Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361990"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="7f04c-102">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="7f04c-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="7f04c-103">Specifica il set di tipi .NET che attivano la condizione.</span><span class="sxs-lookup"><span data-stu-id="7f04c-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="7f04c-104">Quando uno dei tipi in questo set è presente, viene soddisfatta la condizione.</span><span class="sxs-lookup"><span data-stu-id="7f04c-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="7f04c-105">Elemento di configurazione elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansions (Format) elemento EntrySelectedBy per EnumerableExpansion (Format) SelectionCondition elemento per EntrySelectedBy per EnumerableExpansion (Format) elemento SelectionSetName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7f04c-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7f04c-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7f04c-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7f04c-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="7f04c-107">Attributes and Elements</span></span>

<span data-ttu-id="7f04c-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="7f04c-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7f04c-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="7f04c-109">Attributes</span></span>

<span data-ttu-id="7f04c-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="7f04c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7f04c-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="7f04c-111">Child Elements</span></span>

<span data-ttu-id="7f04c-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="7f04c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7f04c-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="7f04c-113">Parent Elements</span></span>

|<span data-ttu-id="7f04c-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="7f04c-114">Element</span></span>|<span data-ttu-id="7f04c-115">Description</span><span class="sxs-lookup"><span data-stu-id="7f04c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7f04c-116">Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7f04c-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="7f04c-117">Definisce la condizione che deve esistere per espandere gli oggetti della raccolta di questa definizione.</span><span class="sxs-lookup"><span data-stu-id="7f04c-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7f04c-118">Valore testo</span><span class="sxs-lookup"><span data-stu-id="7f04c-118">Text Value</span></span>

<span data-ttu-id="7f04c-119">Consente di specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="7f04c-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="7f04c-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="7f04c-120">Remarks</span></span>

<span data-ttu-id="7f04c-121">La condizione di selezione può specificare un set di selezione o un tipo .NET, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="7f04c-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="7f04c-122">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="7f04c-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="7f04c-123">I set di selezione sono gruppi comuni di oggetti .NET che possono essere utilizzati da qualsiasi visualizzazione definita dal file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="7f04c-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="7f04c-124">Per ulteriori informazioni sulla creazione e il riferimento a set di selezione, vedere [definizione di set di selezione](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="7f04c-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7f04c-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7f04c-125">See Also</span></span>

[<span data-ttu-id="7f04c-126">Definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="7f04c-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="7f04c-127">Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7f04c-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="7f04c-128">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="7f04c-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
