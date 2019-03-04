---
title: Elemento PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860417"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="155ef-102">Elemento PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="155ef-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="155ef-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="155ef-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="155ef-104">Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene utilizzata la definizione.</span><span class="sxs-lookup"><span data-stu-id="155ef-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="155ef-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento di configurazione per elemento SelectionCondition WideEntry (formato) per EntrySelectedBy per elemento PropertyName WideEntry (formato) per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="155ef-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="155ef-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="155ef-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="155ef-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="155ef-107">Attributes and Elements</span></span>

<span data-ttu-id="155ef-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="155ef-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="155ef-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="155ef-109">Attributes</span></span>

<span data-ttu-id="155ef-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="155ef-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="155ef-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="155ef-111">Child Elements</span></span>

<span data-ttu-id="155ef-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="155ef-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="155ef-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="155ef-113">Parent Elements</span></span>

|<span data-ttu-id="155ef-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="155ef-114">Element</span></span>|<span data-ttu-id="155ef-115">Description</span><span class="sxs-lookup"><span data-stu-id="155ef-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="155ef-116">Elemento SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="155ef-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="155ef-117">Definisce la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="155ef-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="155ef-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="155ef-118">Text Value</span></span>

<span data-ttu-id="155ef-119">Specificare il nome della proprietà .NET.</span><span class="sxs-lookup"><span data-stu-id="155ef-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="155ef-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="155ef-120">Remarks</span></span>

<span data-ttu-id="155ef-121">La condizione di selezione è necessario specificare almeno un nome di proprietà o uno script per valutare, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="155ef-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="155ef-122">Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="155ef-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="155ef-123">Per altre informazioni sugli altri componenti di una visualizzazione più ampia, vedere [visualizzazione estesa](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="155ef-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="155ef-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="155ef-124">See Also</span></span>

[<span data-ttu-id="155ef-125">Creazione di una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="155ef-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="155ef-126">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="155ef-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="155ef-127">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="155ef-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="155ef-128">Elemento SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="155ef-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="155ef-129">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="155ef-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
