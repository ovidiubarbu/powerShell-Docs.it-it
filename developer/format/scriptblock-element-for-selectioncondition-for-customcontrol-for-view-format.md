---
title: Elemento ScriptBlock per SelectionCondition per CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857417"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="975b4-102">Elemento ScriptBlock per SelectionCondition per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="975b4-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="975b4-103">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="975b4-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="975b4-104">Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene utilizzata la definizione.</span><span class="sxs-lookup"><span data-stu-id="975b4-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="975b4-105">Questo elemento viene usato quando si definisce una vista di controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="975b4-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="975b4-106">Elemento di CustomControl elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) elemento di visualizzazione (formato) CustomEntries per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per CustomControl per visualizzazione ( Elemento CustomItem Format) per CustomEntry per CustomControl elemento di visualizzazione (formato) SelectionCondition per EntrySelectedBy per CustomControl elemento di visualizzazione (formato) ScriptBlock per SelectionCondition per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="975b4-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="975b4-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="975b4-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="975b4-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="975b4-108">Attributes and Elements</span></span>

<span data-ttu-id="975b4-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="975b4-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="975b4-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="975b4-110">Attributes</span></span>

<span data-ttu-id="975b4-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="975b4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="975b4-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="975b4-112">Child Elements</span></span>

<span data-ttu-id="975b4-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="975b4-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="975b4-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="975b4-114">Parent Elements</span></span>

|<span data-ttu-id="975b4-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="975b4-115">Element</span></span>|<span data-ttu-id="975b4-116">Description</span><span class="sxs-lookup"><span data-stu-id="975b4-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="975b4-117">Elemento SelectionCondition per EntrySelectedBy per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="975b4-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="975b4-118">Definisce una condizione che deve essere presente per la definizione di controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="975b4-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="975b4-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="975b4-119">Text Value</span></span>

<span data-ttu-id="975b4-120">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="975b4-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="975b4-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="975b4-121">Remarks</span></span>

<span data-ttu-id="975b4-122">La condizione di selezione è necessario specificare un nome di script o proprietà uno minimi per valutare, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="975b4-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="975b4-123">Per altre informazioni sull'utilizzo di condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="975b4-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="975b4-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="975b4-124">See Also</span></span>

[<span data-ttu-id="975b4-125">Elemento SelectionCondition per EntrySelectedBy per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="975b4-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="975b4-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="975b4-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
