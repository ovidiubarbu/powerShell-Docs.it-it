---
title: Elemento ScriptBlock per ItemSelectionCondition per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856737"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="7eb0e-102">Elemento ScriptBlock per ItemSelectionCondition per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="7eb0e-102">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="7eb0e-103">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="7eb0e-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="7eb0e-104">Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene utilizzato il controllo.</span><span class="sxs-lookup"><span data-stu-id="7eb0e-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="7eb0e-105">Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.</span><span class="sxs-lookup"><span data-stu-id="7eb0e-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="7eb0e-106">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) CustomItem per CustomEntry per i controlli elemento di visualizzazione (formato) ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato) Elemento ItemSelectionCondition ExpressionBinding per i controlli elemento di visualizzazione (formato) ScriptBlock per ItemSelectionCondition per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="7eb0e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7eb0e-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7eb0e-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7eb0e-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="7eb0e-108">Attributes and Elements</span></span>

<span data-ttu-id="7eb0e-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="7eb0e-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7eb0e-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="7eb0e-110">Attributes</span></span>

<span data-ttu-id="7eb0e-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="7eb0e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7eb0e-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="7eb0e-112">Child Elements</span></span>

<span data-ttu-id="7eb0e-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="7eb0e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7eb0e-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="7eb0e-114">Parent Elements</span></span>

|<span data-ttu-id="7eb0e-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="7eb0e-115">Element</span></span>|<span data-ttu-id="7eb0e-116">Description</span><span class="sxs-lookup"><span data-stu-id="7eb0e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7eb0e-117">Elemento ItemSelectionCondition ExpressionBinding per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="7eb0e-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="7eb0e-118">Definisce la condizione che deve essere presente per questo controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="7eb0e-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7eb0e-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="7eb0e-119">Text Value</span></span>

<span data-ttu-id="7eb0e-120">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="7eb0e-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="7eb0e-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="7eb0e-121">Remarks</span></span>

<span data-ttu-id="7eb0e-122">Se questo elemento viene usato, è possibile specificare il [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) elemento quando si definisce la condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="7eb0e-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="7eb0e-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7eb0e-123">See Also</span></span>

[<span data-ttu-id="7eb0e-124">Elemento PropertyName per ItemSelectionCondition per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="7eb0e-124">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="7eb0e-125">Elemento ItemSelectionCondition ExpressionBinding per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="7eb0e-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="7eb0e-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="7eb0e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
