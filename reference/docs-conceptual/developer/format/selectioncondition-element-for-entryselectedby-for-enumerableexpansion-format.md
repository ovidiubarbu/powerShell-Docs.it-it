---
title: Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362010"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="9c826-102">Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="9c826-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="9c826-103">Definisce la condizione che deve esistere per espandere gli oggetti della raccolta di questa definizione.</span><span class="sxs-lookup"><span data-stu-id="9c826-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="9c826-104">Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format) elemento EntrySelectedBy per EnumerableExpansion (Format) SelectionCondition elemento per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="9c826-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9c826-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9c826-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9c826-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="9c826-106">Attributes and Elements</span></span>

<span data-ttu-id="9c826-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="9c826-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="9c826-108">È necessario specificare un singolo elemento `PropertyName` o `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="9c826-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="9c826-109">Gli elementi `SelectionSetName` e `TypeName` sono facoltativi.</span><span class="sxs-lookup"><span data-stu-id="9c826-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="9c826-110">È possibile specificare uno dei due elementi.</span><span class="sxs-lookup"><span data-stu-id="9c826-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9c826-111">Attributi</span><span class="sxs-lookup"><span data-stu-id="9c826-111">Attributes</span></span>

<span data-ttu-id="9c826-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="9c826-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9c826-113">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="9c826-113">Child Elements</span></span>

|<span data-ttu-id="9c826-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="9c826-114">Element</span></span>|<span data-ttu-id="9c826-115">Description</span><span class="sxs-lookup"><span data-stu-id="9c826-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9c826-116">Elemento PropertyName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="9c826-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="9c826-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="9c826-117">Optional element.</span></span><br /><br /> <span data-ttu-id="9c826-118">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="9c826-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="9c826-119">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="9c826-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="9c826-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="9c826-120">Optional element.</span></span><br /><br /> <span data-ttu-id="9c826-121">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="9c826-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="9c826-122">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="9c826-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="9c826-123">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="9c826-123">Optional element.</span></span><br /><br /> <span data-ttu-id="9c826-124">Specifica il set di tipi .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="9c826-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="9c826-125">Elemento TypeName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="9c826-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="9c826-126">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="9c826-126">Optional element.</span></span><br /><br /> <span data-ttu-id="9c826-127">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="9c826-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9c826-128">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="9c826-128">Parent Elements</span></span>

|<span data-ttu-id="9c826-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="9c826-129">Element</span></span>|<span data-ttu-id="9c826-130">Description</span><span class="sxs-lookup"><span data-stu-id="9c826-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9c826-131">Elemento EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="9c826-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="9c826-132">Definisce gli oggetti della raccolta .NET espansi da questa definizione.</span><span class="sxs-lookup"><span data-stu-id="9c826-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9c826-133">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="9c826-133">Remarks</span></span>

<span data-ttu-id="9c826-134">Per ogni definizione è necessario definire almeno un nome di tipo, un set di selezione o una condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="9c826-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="9c826-135">Quando si definisce una condizione di selezione, si applicano i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="9c826-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="9c826-136">La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="9c826-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="9c826-137">La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="9c826-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="9c826-138">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la riproduzione di dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="9c826-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="9c826-139">Per ulteriori informazioni su altri componenti di una visualizzazione estesa, vedere [visualizzazione estesa](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="9c826-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9c826-140">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9c826-140">See Also</span></span>

[<span data-ttu-id="9c826-141">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="9c826-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9c826-142">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="9c826-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
