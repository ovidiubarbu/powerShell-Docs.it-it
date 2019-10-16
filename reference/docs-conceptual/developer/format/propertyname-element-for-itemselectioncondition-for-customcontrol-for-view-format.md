---
title: Elemento PropertyName per ItemSelectionCondition per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362440"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="f545d-102">Elemento PropertyName per ItemSelectionCondition per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="f545d-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="f545d-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="f545d-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="f545d-104">Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene utilizzato il controllo.</span><span class="sxs-lookup"><span data-stu-id="f545d-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="f545d-105">Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.</span><span class="sxs-lookup"><span data-stu-id="f545d-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="f545d-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per la vista (Format) CustomEntry elemento per CustomEntries per la visualizzazione (Format) CustomItem elemento per CustomEntry per la visualizzazione (formato) elemento Expressiongroup per CustomItem per CustomControl per la visualizzazione (Format) ItemSelectionCondition elemento per l'associazione di espressioni per CustomControl per la visualizzazione (Format) PropertyName elemento per ItemSelectionCondition per CustomControl per la visualizzazione (formato</span><span class="sxs-lookup"><span data-stu-id="f545d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="f545d-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f545d-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f545d-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="f545d-108">Attributes and Elements</span></span>

<span data-ttu-id="f545d-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="f545d-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f545d-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="f545d-110">Attributes</span></span>

<span data-ttu-id="f545d-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f545d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f545d-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f545d-112">Child Elements</span></span>

<span data-ttu-id="f545d-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f545d-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f545d-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f545d-114">Parent Elements</span></span>

|<span data-ttu-id="f545d-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="f545d-115">Element</span></span>|<span data-ttu-id="f545d-116">Description</span><span class="sxs-lookup"><span data-stu-id="f545d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f545d-117">Elemento ItemSelectionCondition per l'associazione di espressioni per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="f545d-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="f545d-118">Definisce la condizione che deve esistere per il controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="f545d-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f545d-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="f545d-119">Text Value</span></span>

<span data-ttu-id="f545d-120">Specificare il nome della proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="f545d-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="f545d-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f545d-121">Remarks</span></span>

<span data-ttu-id="f545d-122">Se viene usato questo elemento, non è possibile specificare l'elemento [scriptblock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) quando si definisce la condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="f545d-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="f545d-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f545d-123">See Also</span></span>

[<span data-ttu-id="f545d-124">Elemento ScriptBlock per ItemSelectionCondition per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="f545d-124">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f545d-125">Elemento ItemSelectionCondition per l'associazione di espressioni per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="f545d-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="f545d-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f545d-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
