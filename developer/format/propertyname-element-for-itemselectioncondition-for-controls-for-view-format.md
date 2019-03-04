---
title: Elemento PropertyName per ItemSelectionCondition per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857627"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="e4663-102">Elemento PropertyName per ItemSelectionCondition per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="e4663-102">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="e4663-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="e4663-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="e4663-104">Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene utilizzato il controllo.</span><span class="sxs-lookup"><span data-stu-id="e4663-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="e4663-105">Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.</span><span class="sxs-lookup"><span data-stu-id="e4663-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e4663-106">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) CustomItem per CustomEntry per i controlli elemento di visualizzazione (formato) ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato) Elemento ItemSelectionCondition ExpressionBinding per i controlli elemento di visualizzazione (formato) PropertyName per ItemSelectionCondition per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="e4663-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e4663-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e4663-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e4663-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="e4663-108">Attributes and Elements</span></span>

<span data-ttu-id="e4663-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="e4663-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e4663-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="e4663-110">Attributes</span></span>

<span data-ttu-id="e4663-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e4663-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e4663-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="e4663-112">Child Elements</span></span>

<span data-ttu-id="e4663-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e4663-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e4663-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="e4663-114">Parent Elements</span></span>

|<span data-ttu-id="e4663-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="e4663-115">Element</span></span>|<span data-ttu-id="e4663-116">Description</span><span class="sxs-lookup"><span data-stu-id="e4663-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e4663-117">Elemento ItemSelectionCondition ExpressionBinding per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="e4663-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="e4663-118">Definisce la condizione che deve essere presente per questo controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="e4663-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e4663-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="e4663-119">Text Value</span></span>

<span data-ttu-id="e4663-120">Specificare il nome della proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="e4663-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="e4663-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e4663-121">Remarks</span></span>

<span data-ttu-id="e4663-122">Se questo elemento viene usato, è possibile specificare il [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) elemento quando si definisce la condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="e4663-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4663-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e4663-123">See Also</span></span>

[<span data-ttu-id="e4663-124">Elemento ScriptBlock per ItemSelectionCondition per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="e4663-124">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="e4663-125">Elemento ItemSelectionCondition ExpressionBinding per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="e4663-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="e4663-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4663-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
