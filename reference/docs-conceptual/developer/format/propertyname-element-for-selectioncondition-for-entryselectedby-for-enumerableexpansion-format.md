---
title: Elemento PropertyName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ae11924-0072-451e-bf70-c5ffb25dccc0
caps.latest.revision: 13
ms.openlocfilehash: 0c20512e660c8d2b61d063dbd7078b55b23efeb8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362320"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="e84e2-102">Elemento PropertyName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="e84e2-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="e84e2-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="e84e2-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="e84e2-104">Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene usata la definizione.</span><span class="sxs-lookup"><span data-stu-id="e84e2-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="e84e2-105">Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format) elemento EntrySelectedBy per EnumerableExpansion (Format) SelectionCondition elemento per EntrySelectedBy per Elemento EnumerableExpansion (Format) PropertyName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="e84e2-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e84e2-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e84e2-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e84e2-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="e84e2-107">Attributes and Elements</span></span>

<span data-ttu-id="e84e2-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="e84e2-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e84e2-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="e84e2-109">Attributes</span></span>

<span data-ttu-id="e84e2-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e84e2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e84e2-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="e84e2-111">Child Elements</span></span>

<span data-ttu-id="e84e2-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e84e2-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e84e2-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="e84e2-113">Parent Elements</span></span>

|<span data-ttu-id="e84e2-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="e84e2-114">Element</span></span>|<span data-ttu-id="e84e2-115">Description</span><span class="sxs-lookup"><span data-stu-id="e84e2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e84e2-116">Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="e84e2-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="e84e2-117">Definisce la condizione che deve esistere per espandere gli oggetti della raccolta di questa definizione.</span><span class="sxs-lookup"><span data-stu-id="e84e2-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e84e2-118">Valore testo</span><span class="sxs-lookup"><span data-stu-id="e84e2-118">Text Value</span></span>

<span data-ttu-id="e84e2-119">Specificare il nome della proprietà .NET.</span><span class="sxs-lookup"><span data-stu-id="e84e2-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="e84e2-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e84e2-120">Remarks</span></span>

<span data-ttu-id="e84e2-121">La condizione di selezione deve specificare almeno un nome di proprietà o uno script da valutare, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="e84e2-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="e84e2-122">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e84e2-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e84e2-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e84e2-123">See Also</span></span>

[<span data-ttu-id="e84e2-124">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="e84e2-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e84e2-125">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="e84e2-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="e84e2-126">Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="e84e2-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="e84e2-127">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e84e2-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
