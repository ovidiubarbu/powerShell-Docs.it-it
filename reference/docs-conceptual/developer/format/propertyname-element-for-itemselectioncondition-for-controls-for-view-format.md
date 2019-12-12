---
title: Elemento PropertyName per ItemSelectionCondition per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362480"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="c7248-102">Elemento PropertyName per ItemSelectionCondition per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="c7248-102">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="c7248-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="c7248-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="c7248-104">Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene utilizzato il controllo.</span><span class="sxs-lookup"><span data-stu-id="c7248-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="c7248-105">Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="c7248-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="c7248-106">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per la visualizzazione (Format) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato) elemento Expressiongroup per CustomItem per i controlli per la visualizzazione (formato) Elemento ItemSelectionCondition di Expression per i controlli per la visualizzazione (Format) PropertyName per ItemSelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="c7248-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c7248-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c7248-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c7248-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="c7248-108">Attributes and Elements</span></span>

<span data-ttu-id="c7248-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="c7248-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c7248-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="c7248-110">Attributes</span></span>

<span data-ttu-id="c7248-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c7248-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c7248-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="c7248-112">Child Elements</span></span>

<span data-ttu-id="c7248-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c7248-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c7248-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="c7248-114">Parent Elements</span></span>

|<span data-ttu-id="c7248-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="c7248-115">Element</span></span>|<span data-ttu-id="c7248-116">Description</span><span class="sxs-lookup"><span data-stu-id="c7248-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c7248-117">Elemento ItemSelectionCondition di Expression per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="c7248-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="c7248-118">Definisce la condizione che deve esistere per il controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="c7248-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c7248-119">Valore testo</span><span class="sxs-lookup"><span data-stu-id="c7248-119">Text Value</span></span>

<span data-ttu-id="c7248-120">Specificare il nome della proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="c7248-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="c7248-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c7248-121">Remarks</span></span>

<span data-ttu-id="c7248-122">Se viene usato questo elemento, non è possibile specificare l'elemento [scriptblock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) quando si definisce la condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="c7248-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7248-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c7248-123">See Also</span></span>

[<span data-ttu-id="c7248-124">Elemento ScriptBlock per ItemSelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="c7248-124">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="c7248-125">Elemento ItemSelectionCondition di Expression per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="c7248-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="c7248-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7248-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
