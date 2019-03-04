---
title: Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858287"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="0e4c8-102">Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="0e4c8-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="0e4c8-103">Definisce la condizione che deve essere presente per espandere gli oggetti dell'insieme di questa definizione.</span><span class="sxs-lookup"><span data-stu-id="0e4c8-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="0e4c8-104">Configurazione (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) elemento EnumerableExpansion (formato) EntrySelectedBy elemento per elemento SelectionCondition EnumerableExpansion (formato) per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="0e4c8-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0e4c8-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0e4c8-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0e4c8-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="0e4c8-106">Attributes and Elements</span></span>

<span data-ttu-id="0e4c8-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="0e4c8-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="0e4c8-108">È necessario specificare un unico `PropertyName` o `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="0e4c8-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="0e4c8-109">Il `SelectionSetName` e `TypeName` gli elementi sono facoltativi.</span><span class="sxs-lookup"><span data-stu-id="0e4c8-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="0e4c8-110">È possibile specificare uno dei entrambi gli elementi.</span><span class="sxs-lookup"><span data-stu-id="0e4c8-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0e4c8-111">Attributes</span><span class="sxs-lookup"><span data-stu-id="0e4c8-111">Attributes</span></span>

<span data-ttu-id="0e4c8-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="0e4c8-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0e4c8-113">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="0e4c8-113">Child Elements</span></span>

|<span data-ttu-id="0e4c8-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="0e4c8-114">Element</span></span>|<span data-ttu-id="0e4c8-115">Description</span><span class="sxs-lookup"><span data-stu-id="0e4c8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0e4c8-116">Elemento PropertyName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="0e4c8-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="0e4c8-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="0e4c8-117">Optional element.</span></span><br /><br /> <span data-ttu-id="0e4c8-118">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="0e4c8-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="0e4c8-119">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="0e4c8-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="0e4c8-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="0e4c8-120">Optional element.</span></span><br /><br /> <span data-ttu-id="0e4c8-121">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="0e4c8-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="0e4c8-122">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="0e4c8-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="0e4c8-123">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="0e4c8-123">Optional element.</span></span><br /><br /> <span data-ttu-id="0e4c8-124">Specifica il set di tipi .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="0e4c8-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="0e4c8-125">Elemento TypeName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="0e4c8-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="0e4c8-126">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="0e4c8-126">Optional element.</span></span><br /><br /> <span data-ttu-id="0e4c8-127">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="0e4c8-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0e4c8-128">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="0e4c8-128">Parent Elements</span></span>

|<span data-ttu-id="0e4c8-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="0e4c8-129">Element</span></span>|<span data-ttu-id="0e4c8-130">Description</span><span class="sxs-lookup"><span data-stu-id="0e4c8-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0e4c8-131">Elemento EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="0e4c8-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="0e4c8-132">Definisce quali oggetti della raccolta .NET vengono espanse per questa definizione.</span><span class="sxs-lookup"><span data-stu-id="0e4c8-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0e4c8-133">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="0e4c8-133">Remarks</span></span>

<span data-ttu-id="0e4c8-134">Ogni definizione deve avere almeno un nome di tipo, il set di selezione o condizione di selezione definiti.</span><span class="sxs-lookup"><span data-stu-id="0e4c8-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="0e4c8-135">Quando si definisce una condizione di selezione, si applicano i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="0e4c8-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="0e4c8-136">La condizione di selezione è necessario specificare un nome di una proprietà minimi o un blocco di script, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="0e4c8-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="0e4c8-137">La condizione di selezione può includere un numero qualsiasi di tipi .NET o selezione imposta, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="0e4c8-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="0e4c8-138">Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per i dati Diplaying](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0e4c8-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="0e4c8-139">Per altre informazioni sugli altri componenti di una visualizzazione più ampia, vedere [visualizzazione estesa](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="0e4c8-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0e4c8-140">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0e4c8-140">See Also</span></span>

[<span data-ttu-id="0e4c8-141">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="0e4c8-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="0e4c8-142">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e4c8-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
