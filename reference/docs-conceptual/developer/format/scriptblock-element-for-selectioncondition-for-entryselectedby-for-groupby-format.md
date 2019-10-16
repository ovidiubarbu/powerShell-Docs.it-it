---
title: Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e01344bd-ad69-4789-8e9f-2e79880c3a33
caps.latest.revision: 6
ms.openlocfilehash: cb79fb942111cee89c6b2abba75de4c494082b7e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368600"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="56914-102">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="56914-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="56914-103">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="56914-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="56914-104">Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene usata la definizione.</span><span class="sxs-lookup"><span data-stu-id="56914-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="56914-105">Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="56914-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="56914-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format) elemento EntrySelectedBy per CustomEntry per l'elemento SelectionCondition di GroupBy (Format) per EntrySelectedBy per ScriptBlock per l'elemento SelectionCondition di GroupBy (Format) per per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="56914-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="56914-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="56914-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="56914-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="56914-108">Attributes and Elements</span></span>

<span data-ttu-id="56914-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="56914-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="56914-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="56914-110">Attributes</span></span>

<span data-ttu-id="56914-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="56914-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="56914-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="56914-112">Child Elements</span></span>

<span data-ttu-id="56914-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="56914-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="56914-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="56914-114">Parent Elements</span></span>

|<span data-ttu-id="56914-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="56914-115">Element</span></span>|<span data-ttu-id="56914-116">Description</span><span class="sxs-lookup"><span data-stu-id="56914-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="56914-117">Elemento SelectionCondition per EntrySelectedBy per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="56914-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="56914-118">Definisce una condizione che deve esistere per la definizione del controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="56914-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="56914-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="56914-119">Text Value</span></span>

<span data-ttu-id="56914-120">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="56914-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="56914-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="56914-121">Remarks</span></span>

<span data-ttu-id="56914-122">Per valutare la condizione di selezione, è necessario specificare almeno uno script o un nome di proprietà, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="56914-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="56914-123">Per ulteriori informazioni sul modo in cui è possibile utilizzare le condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="56914-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="56914-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="56914-124">See Also</span></span>

[<span data-ttu-id="56914-125">Elemento SelectionCondition per EntrySelectedBy per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="56914-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="56914-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="56914-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
