---
title: Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368610"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="37ae7-102">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="37ae7-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="37ae7-103">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="37ae7-103">Specifies the script that triggers the condition.</span></span>

<span data-ttu-id="37ae7-104">Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format) elemento EntrySelectedBy per EnumerableExpansion (Format) SelectionCondition elemento per EntrySelectedBy per EnumerableExpansion (Format) elemento ScriptBlock per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="37ae7-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="37ae7-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="37ae7-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="37ae7-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="37ae7-106">Attributes and Elements</span></span>

<span data-ttu-id="37ae7-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="37ae7-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="37ae7-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="37ae7-108">Attributes</span></span>

<span data-ttu-id="37ae7-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="37ae7-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="37ae7-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="37ae7-110">Child Elements</span></span>

<span data-ttu-id="37ae7-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="37ae7-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="37ae7-112">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="37ae7-112">Parent Elements</span></span>

|<span data-ttu-id="37ae7-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="37ae7-113">Element</span></span>|<span data-ttu-id="37ae7-114">Description</span><span class="sxs-lookup"><span data-stu-id="37ae7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="37ae7-115">Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="37ae7-115">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="37ae7-116">Definisce la condizione che deve esistere per espandere gli oggetti della raccolta di questa definizione.</span><span class="sxs-lookup"><span data-stu-id="37ae7-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="37ae7-117">Valore testo</span><span class="sxs-lookup"><span data-stu-id="37ae7-117">Text Value</span></span>

<span data-ttu-id="37ae7-118">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="37ae7-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="37ae7-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="37ae7-119">Remarks</span></span>

<span data-ttu-id="37ae7-120">La condizione di selezione deve specificare almeno un nome di script o di proprietà da valutare, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="37ae7-120">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="37ae7-121">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="37ae7-121">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="37ae7-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="37ae7-122">See Also</span></span>

[<span data-ttu-id="37ae7-123">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="37ae7-123">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="37ae7-124">Elemento PropertyName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="37ae7-124">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="37ae7-125">Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="37ae7-125">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="37ae7-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="37ae7-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
