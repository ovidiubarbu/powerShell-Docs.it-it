---
title: Elemento ScriptBlock per ItemSelectionCondition per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364920"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="8ac08-102">Elemento ScriptBlock per ItemSelectionCondition per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="8ac08-102">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="8ac08-103">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="8ac08-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="8ac08-104">Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzato il controllo.</span><span class="sxs-lookup"><span data-stu-id="8ac08-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="8ac08-105">Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="8ac08-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="8ac08-106">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per la visualizzazione (Format) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato) elemento Expressiongroup per CustomItem per i controlli per la visualizzazione (formato) Elemento ItemSelectionCondition di Expression per i controlli per la visualizzazione (Format) elemento ScriptBlock per ItemSelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="8ac08-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8ac08-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8ac08-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8ac08-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="8ac08-108">Attributes and Elements</span></span>

<span data-ttu-id="8ac08-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="8ac08-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8ac08-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="8ac08-110">Attributes</span></span>

<span data-ttu-id="8ac08-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="8ac08-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8ac08-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="8ac08-112">Child Elements</span></span>

<span data-ttu-id="8ac08-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="8ac08-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8ac08-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="8ac08-114">Parent Elements</span></span>

|<span data-ttu-id="8ac08-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="8ac08-115">Element</span></span>|<span data-ttu-id="8ac08-116">Description</span><span class="sxs-lookup"><span data-stu-id="8ac08-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8ac08-117">Elemento ItemSelectionCondition di Expression per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="8ac08-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="8ac08-118">Definisce la condizione che deve esistere per il controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="8ac08-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8ac08-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="8ac08-119">Text Value</span></span>

<span data-ttu-id="8ac08-120">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="8ac08-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="8ac08-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="8ac08-121">Remarks</span></span>

<span data-ttu-id="8ac08-122">Se viene usato questo elemento, non è possibile specificare l'elemento [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) quando si definisce la condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="8ac08-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ac08-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8ac08-123">See Also</span></span>

[<span data-ttu-id="8ac08-124">Elemento PropertyName per ItemSelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="8ac08-124">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8ac08-125">Elemento ItemSelectionCondition di Expression per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="8ac08-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="8ac08-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="8ac08-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
