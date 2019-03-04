---
title: Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e01344bd-ad69-4789-8e9f-2e79880c3a33
caps.latest.revision: 6
ms.openlocfilehash: cb79fb942111cee89c6b2abba75de4c494082b7e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853077"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="1bd34-102">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="1bd34-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="1bd34-103">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="1bd34-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="1bd34-104">Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene utilizzata la definizione.</span><span class="sxs-lookup"><span data-stu-id="1bd34-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="1bd34-105">Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="1bd34-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="1bd34-106">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per elemento EntrySelectedBy GroupBy (formato) per CustomEntry per elemento SelectionCondition GroupBy (formato) per EntrySelectedBy per elemento ScriptBlock GroupBy (formato) per SelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="1bd34-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1bd34-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1bd34-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1bd34-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="1bd34-108">Attributes and Elements</span></span>

<span data-ttu-id="1bd34-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="1bd34-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1bd34-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="1bd34-110">Attributes</span></span>

<span data-ttu-id="1bd34-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="1bd34-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1bd34-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="1bd34-112">Child Elements</span></span>

<span data-ttu-id="1bd34-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="1bd34-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1bd34-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="1bd34-114">Parent Elements</span></span>

|<span data-ttu-id="1bd34-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="1bd34-115">Element</span></span>|<span data-ttu-id="1bd34-116">Description</span><span class="sxs-lookup"><span data-stu-id="1bd34-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1bd34-117">Elemento SelectionCondition per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="1bd34-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="1bd34-118">Definisce una condizione che deve essere presente per la definizione di controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="1bd34-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1bd34-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="1bd34-119">Text Value</span></span>

<span data-ttu-id="1bd34-120">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="1bd34-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="1bd34-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="1bd34-121">Remarks</span></span>

<span data-ttu-id="1bd34-122">La condizione di selezione è necessario specificare un nome di script o proprietà uno minimi per valutare, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="1bd34-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="1bd34-123">Per altre informazioni sull'utilizzo di condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1bd34-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1bd34-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1bd34-124">See Also</span></span>

[<span data-ttu-id="1bd34-125">Elemento SelectionCondition per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="1bd34-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="1bd34-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="1bd34-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
