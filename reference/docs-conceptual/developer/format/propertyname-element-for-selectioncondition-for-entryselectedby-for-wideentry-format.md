---
title: Elemento PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362240"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="6ea07-102">Elemento PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="6ea07-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="6ea07-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="6ea07-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="6ea07-104">Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene usata la definizione.</span><span class="sxs-lookup"><span data-stu-id="6ea07-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="6ea07-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) elemento EntrySelectedBy per WideEntry (Format) SelectionCondition elemento per EntrySelectedBy per l'elemento WideEntry (Format) PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6ea07-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6ea07-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6ea07-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="6ea07-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="6ea07-107">Attributes and Elements</span></span>

<span data-ttu-id="6ea07-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="6ea07-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6ea07-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="6ea07-109">Attributes</span></span>

<span data-ttu-id="6ea07-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="6ea07-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6ea07-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="6ea07-111">Child Elements</span></span>

<span data-ttu-id="6ea07-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="6ea07-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6ea07-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="6ea07-113">Parent Elements</span></span>

|<span data-ttu-id="6ea07-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="6ea07-114">Element</span></span>|<span data-ttu-id="6ea07-115">Description</span><span class="sxs-lookup"><span data-stu-id="6ea07-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6ea07-116">Elemento SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6ea07-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="6ea07-117">Definisce la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="6ea07-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6ea07-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="6ea07-118">Text Value</span></span>

<span data-ttu-id="6ea07-119">Specificare il nome della proprietà .NET.</span><span class="sxs-lookup"><span data-stu-id="6ea07-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="6ea07-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="6ea07-120">Remarks</span></span>

<span data-ttu-id="6ea07-121">La condizione di selezione deve specificare almeno un nome di proprietà o uno script da valutare, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="6ea07-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="6ea07-122">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6ea07-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="6ea07-123">Per ulteriori informazioni su altri componenti di una visualizzazione estesa, vedere [visualizzazione estesa](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="6ea07-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6ea07-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6ea07-124">See Also</span></span>

[<span data-ttu-id="6ea07-125">Creazione di una visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="6ea07-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="6ea07-126">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="6ea07-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="6ea07-127">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6ea07-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="6ea07-128">Elemento SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6ea07-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="6ea07-129">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="6ea07-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
