---
title: Elemento ScriptBlock per SelectionCondition per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08512496-5682-4539-ab56-0c5394ce1f01
caps.latest.revision: 6
ms.openlocfilehash: 0137886437f01518f396613c564517e7910e657a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364800"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="fbbee-102">Elemento ScriptBlock per SelectionCondition per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="fbbee-102">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="fbbee-103">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="fbbee-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="fbbee-104">Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene usata la definizione.</span><span class="sxs-lookup"><span data-stu-id="fbbee-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="fbbee-105">Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="fbbee-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="fbbee-106">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per i controlli per la visualizzazione (formato) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) EntrySelectedBy elemento per CustomEntry per i controlli per la visualizzazione (formato) SelectionCondition elemento per EntrySelectedBy per i controlli per la visualizzazione ( Format) elemento ScriptBlock per SelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="fbbee-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fbbee-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="fbbee-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fbbee-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="fbbee-108">Attributes and Elements</span></span>

<span data-ttu-id="fbbee-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="fbbee-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fbbee-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="fbbee-110">Attributes</span></span>

<span data-ttu-id="fbbee-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="fbbee-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fbbee-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="fbbee-112">Child Elements</span></span>

<span data-ttu-id="fbbee-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="fbbee-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fbbee-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="fbbee-114">Parent Elements</span></span>

|<span data-ttu-id="fbbee-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="fbbee-115">Element</span></span>|<span data-ttu-id="fbbee-116">Description</span><span class="sxs-lookup"><span data-stu-id="fbbee-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fbbee-117">Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="fbbee-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="fbbee-118">Definisce una condizione che deve esistere per la definizione del controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="fbbee-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fbbee-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="fbbee-119">Text Value</span></span>

<span data-ttu-id="fbbee-120">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="fbbee-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="fbbee-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="fbbee-121">Remarks</span></span>

<span data-ttu-id="fbbee-122">Per valutare la condizione di selezione, è necessario specificare almeno uno script o un nome di proprietà, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="fbbee-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="fbbee-123">Per ulteriori informazioni sul modo in cui è possibile utilizzare le condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="fbbee-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fbbee-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fbbee-124">See Also</span></span>

[<span data-ttu-id="fbbee-125">Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="fbbee-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="fbbee-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="fbbee-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
