---
title: Elemento ScriptBlock per SelectionCondition per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368640"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="70128-102">Elemento ScriptBlock per SelectionCondition per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="70128-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="70128-103">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="70128-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="70128-104">Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzata la definizione.</span><span class="sxs-lookup"><span data-stu-id="70128-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="70128-105">Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.</span><span class="sxs-lookup"><span data-stu-id="70128-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="70128-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl per View (Format) elemento CustomEntries per CustomControl per la visualizzazione (Format) CustomEntry elemento per CustomEntries per CustomControl per la visualizzazione ( Format) elemento CustomItem per CustomEntry per CustomControl per la visualizzazione (Format) SelectionCondition elemento per EntrySelectedBy per CustomControl per la visualizzazione (Format) ScriptBlock elemento per SelectionCondition per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="70128-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="70128-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="70128-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="70128-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="70128-108">Attributes and Elements</span></span>

<span data-ttu-id="70128-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="70128-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="70128-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="70128-110">Attributes</span></span>

<span data-ttu-id="70128-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="70128-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="70128-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="70128-112">Child Elements</span></span>

<span data-ttu-id="70128-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="70128-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="70128-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="70128-114">Parent Elements</span></span>

|<span data-ttu-id="70128-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="70128-115">Element</span></span>|<span data-ttu-id="70128-116">Description</span><span class="sxs-lookup"><span data-stu-id="70128-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70128-117">Elemento SelectionCondition per EntrySelectedBy per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="70128-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="70128-118">Definisce una condizione che deve esistere per la definizione del controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="70128-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="70128-119">Valore testo</span><span class="sxs-lookup"><span data-stu-id="70128-119">Text Value</span></span>

<span data-ttu-id="70128-120">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="70128-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="70128-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="70128-121">Remarks</span></span>

<span data-ttu-id="70128-122">Per valutare la condizione di selezione, è necessario specificare almeno uno script o un nome di proprietà, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="70128-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="70128-123">Per ulteriori informazioni sul modo in cui è possibile utilizzare le condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="70128-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="70128-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="70128-124">See Also</span></span>

[<span data-ttu-id="70128-125">Elemento SelectionCondition per EntrySelectedBy per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="70128-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="70128-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="70128-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
