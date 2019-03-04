---
title: Elemento PropertyName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ae11924-0072-451e-bf70-c5ffb25dccc0
caps.latest.revision: 13
ms.openlocfilehash: 0c20512e660c8d2b61d063dbd7078b55b23efeb8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859627"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="e9a9a-102">Elemento PropertyName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="e9a9a-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="e9a9a-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="e9a9a-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="e9a9a-104">Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene utilizzata la definizione.</span><span class="sxs-lookup"><span data-stu-id="e9a9a-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="e9a9a-105">Configurazione (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) elemento EnumerableExpansion (formato) EntrySelectedBy elemento per elemento SelectionCondition EnumerableExpansion (formato) per EntrySelectedBy per Elemento PropertyName EnumerableExpansion (formato) per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="e9a9a-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e9a9a-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e9a9a-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e9a9a-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="e9a9a-107">Attributes and Elements</span></span>

<span data-ttu-id="e9a9a-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="e9a9a-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e9a9a-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="e9a9a-109">Attributes</span></span>

<span data-ttu-id="e9a9a-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e9a9a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e9a9a-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="e9a9a-111">Child Elements</span></span>

<span data-ttu-id="e9a9a-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e9a9a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e9a9a-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="e9a9a-113">Parent Elements</span></span>

|<span data-ttu-id="e9a9a-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="e9a9a-114">Element</span></span>|<span data-ttu-id="e9a9a-115">Description</span><span class="sxs-lookup"><span data-stu-id="e9a9a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e9a9a-116">Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="e9a9a-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="e9a9a-117">Definisce la condizione che deve essere presente per espandere gli oggetti dell'insieme di questa definizione.</span><span class="sxs-lookup"><span data-stu-id="e9a9a-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e9a9a-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="e9a9a-118">Text Value</span></span>

<span data-ttu-id="e9a9a-119">Specificare il nome della proprietà .NET.</span><span class="sxs-lookup"><span data-stu-id="e9a9a-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="e9a9a-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e9a9a-120">Remarks</span></span>

<span data-ttu-id="e9a9a-121">La condizione di selezione è necessario specificare almeno un nome di proprietà o uno script per valutare, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="e9a9a-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="e9a9a-122">Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e9a9a-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e9a9a-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e9a9a-123">See Also</span></span>

[<span data-ttu-id="e9a9a-124">La definizione delle condizioni per i dati quando viene visualizzata</span><span class="sxs-lookup"><span data-stu-id="e9a9a-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e9a9a-125">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="e9a9a-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="e9a9a-126">Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="e9a9a-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="e9a9a-127">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e9a9a-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
