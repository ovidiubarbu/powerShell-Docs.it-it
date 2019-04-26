---
title: Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064374"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="58f9f-102">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="58f9f-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="58f9f-103">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="58f9f-103">Specifies the script that triggers the condition.</span></span>

<span data-ttu-id="58f9f-104">Configurazione (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) elemento EnumerableExpansion (formato) EntrySelectedBy elemento per elemento SelectionCondition EnumerableExpansion (formato) per EntrySelectedBy per Elemento ScriptBlock EnumerableExpansion (formato) per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="58f9f-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="58f9f-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="58f9f-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="58f9f-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="58f9f-106">Attributes and Elements</span></span>

<span data-ttu-id="58f9f-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="58f9f-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="58f9f-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="58f9f-108">Attributes</span></span>

<span data-ttu-id="58f9f-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="58f9f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="58f9f-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="58f9f-110">Child Elements</span></span>

<span data-ttu-id="58f9f-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="58f9f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="58f9f-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="58f9f-112">Parent Elements</span></span>

|<span data-ttu-id="58f9f-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="58f9f-113">Element</span></span>|<span data-ttu-id="58f9f-114">Description</span><span class="sxs-lookup"><span data-stu-id="58f9f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="58f9f-115">Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="58f9f-115">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="58f9f-116">Definisce la condizione che deve essere presente per espandere gli oggetti dell'insieme di questa definizione.</span><span class="sxs-lookup"><span data-stu-id="58f9f-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="58f9f-117">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="58f9f-117">Text Value</span></span>

<span data-ttu-id="58f9f-118">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="58f9f-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="58f9f-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="58f9f-119">Remarks</span></span>

<span data-ttu-id="58f9f-120">La condizione di selezione è necessario specificare almeno un nome di uno script o una proprietà da valutare, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="58f9f-120">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="58f9f-121">Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="58f9f-121">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="58f9f-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="58f9f-122">See Also</span></span>

[<span data-ttu-id="58f9f-123">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="58f9f-123">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="58f9f-124">Elemento PropertyName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="58f9f-124">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="58f9f-125">Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="58f9f-125">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="58f9f-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="58f9f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
