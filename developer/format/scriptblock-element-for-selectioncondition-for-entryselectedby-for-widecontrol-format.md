---
title: Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862947"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="61076-102">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="61076-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="61076-103">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="61076-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="61076-104">Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene utilizzata la definizione di voce wide.</span><span class="sxs-lookup"><span data-stu-id="61076-104">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="61076-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento di configurazione per elemento SelectionCondition WideEntry (formato) per EntrySelectedBy per elemento ScriptBlock WideEntry (formato) per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="61076-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="61076-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="61076-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="61076-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="61076-107">Attributes and Elements</span></span>

<span data-ttu-id="61076-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="61076-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="61076-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="61076-109">Attributes</span></span>

<span data-ttu-id="61076-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="61076-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="61076-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="61076-111">Child Elements</span></span>

<span data-ttu-id="61076-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="61076-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="61076-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="61076-113">Parent Elements</span></span>

|<span data-ttu-id="61076-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="61076-114">Element</span></span>|<span data-ttu-id="61076-115">Description</span><span class="sxs-lookup"><span data-stu-id="61076-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="61076-116">Elemento SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="61076-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="61076-117">Definisce la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="61076-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="61076-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="61076-118">Text Value</span></span>

<span data-ttu-id="61076-119">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="61076-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="61076-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="61076-120">Remarks</span></span>

<span data-ttu-id="61076-121">La condizione di selezione è necessario specificare almeno un nome di uno script o una proprietà da valutare, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="61076-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="61076-122">Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="61076-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="61076-123">Per altre informazioni sugli altri componenti di una visualizzazione più ampia, vedere [visualizzazione estesa](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="61076-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="61076-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="61076-124">See Also</span></span>

[<span data-ttu-id="61076-125">Creazione di una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="61076-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="61076-126">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="61076-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="61076-127">Elemento PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="61076-127">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="61076-128">Elemento SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="61076-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="61076-129">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="61076-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
