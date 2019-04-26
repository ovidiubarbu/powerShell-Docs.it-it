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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064952"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="5246e-102">Elemento PropertyName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="5246e-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="5246e-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="5246e-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="5246e-104">Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene utilizzata la definizione.</span><span class="sxs-lookup"><span data-stu-id="5246e-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="5246e-105">Configurazione (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) elemento EnumerableExpansion (formato) EntrySelectedBy elemento per elemento SelectionCondition EnumerableExpansion (formato) per EntrySelectedBy per Elemento PropertyName EnumerableExpansion (formato) per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="5246e-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5246e-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5246e-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5246e-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="5246e-107">Attributes and Elements</span></span>

<span data-ttu-id="5246e-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="5246e-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5246e-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="5246e-109">Attributes</span></span>

<span data-ttu-id="5246e-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="5246e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5246e-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="5246e-111">Child Elements</span></span>

<span data-ttu-id="5246e-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="5246e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5246e-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="5246e-113">Parent Elements</span></span>

|<span data-ttu-id="5246e-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="5246e-114">Element</span></span>|<span data-ttu-id="5246e-115">Description</span><span class="sxs-lookup"><span data-stu-id="5246e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5246e-116">Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="5246e-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="5246e-117">Definisce la condizione che deve essere presente per espandere gli oggetti dell'insieme di questa definizione.</span><span class="sxs-lookup"><span data-stu-id="5246e-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5246e-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="5246e-118">Text Value</span></span>

<span data-ttu-id="5246e-119">Specificare il nome della proprietà .NET.</span><span class="sxs-lookup"><span data-stu-id="5246e-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="5246e-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="5246e-120">Remarks</span></span>

<span data-ttu-id="5246e-121">La condizione di selezione è necessario specificare almeno un nome di proprietà o uno script per valutare, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="5246e-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="5246e-122">Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5246e-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5246e-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5246e-123">See Also</span></span>

[<span data-ttu-id="5246e-124">La definizione delle condizioni per i dati quando viene visualizzata</span><span class="sxs-lookup"><span data-stu-id="5246e-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="5246e-125">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="5246e-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="5246e-126">Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="5246e-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="5246e-127">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="5246e-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
