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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064323"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="41109-102">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="41109-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="41109-103">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="41109-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="41109-104">Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene utilizzata la definizione di voce wide.</span><span class="sxs-lookup"><span data-stu-id="41109-104">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="41109-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento di configurazione per elemento SelectionCondition WideEntry (formato) per EntrySelectedBy per elemento ScriptBlock WideEntry (formato) per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="41109-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="41109-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="41109-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="41109-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="41109-107">Attributes and Elements</span></span>

<span data-ttu-id="41109-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="41109-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="41109-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="41109-109">Attributes</span></span>

<span data-ttu-id="41109-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="41109-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="41109-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="41109-111">Child Elements</span></span>

<span data-ttu-id="41109-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="41109-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="41109-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="41109-113">Parent Elements</span></span>

|<span data-ttu-id="41109-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="41109-114">Element</span></span>|<span data-ttu-id="41109-115">Description</span><span class="sxs-lookup"><span data-stu-id="41109-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="41109-116">Elemento SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="41109-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="41109-117">Definisce la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="41109-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="41109-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="41109-118">Text Value</span></span>

<span data-ttu-id="41109-119">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="41109-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="41109-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="41109-120">Remarks</span></span>

<span data-ttu-id="41109-121">La condizione di selezione è necessario specificare almeno un nome di uno script o una proprietà da valutare, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="41109-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="41109-122">Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="41109-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="41109-123">Per altre informazioni sugli altri componenti di una visualizzazione più ampia, vedere [visualizzazione estesa](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="41109-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="41109-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="41109-124">See Also</span></span>

[<span data-ttu-id="41109-125">Creazione di una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="41109-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="41109-126">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="41109-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="41109-127">Elemento PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="41109-127">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="41109-128">Elemento SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="41109-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="41109-129">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="41109-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
