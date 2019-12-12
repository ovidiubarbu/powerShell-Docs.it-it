---
title: Elemento ScriptBlock per ItemSelectionCondition per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362070"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="c8493-102">Elemento ScriptBlock per ItemSelectionCondition per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="c8493-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="c8493-103">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="c8493-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="c8493-104">Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzato il controllo.</span><span class="sxs-lookup"><span data-stu-id="c8493-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="c8493-105">Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.</span><span class="sxs-lookup"><span data-stu-id="c8493-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="c8493-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per la vista (Format) CustomEntry elemento per CustomEntries per la visualizzazione (Format) CustomItem elemento per CustomEntry per la visualizzazione (formato) elemento Expressiongroup per CustomItem per CustomControl per la visualizzazione (Format) ItemSelectionCondition elemento per l'associazione di espressioni per CustomControl per la visualizzazione (formato) ScriptBlock elemento per ItemSelectionCondition per CustomControl per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c8493-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c8493-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c8493-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c8493-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="c8493-108">Attributes and Elements</span></span>

<span data-ttu-id="c8493-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="c8493-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c8493-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="c8493-110">Attributes</span></span>

<span data-ttu-id="c8493-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c8493-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c8493-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="c8493-112">Child Elements</span></span>

<span data-ttu-id="c8493-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c8493-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c8493-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="c8493-114">Parent Elements</span></span>

|<span data-ttu-id="c8493-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="c8493-115">Element</span></span>|<span data-ttu-id="c8493-116">Description</span><span class="sxs-lookup"><span data-stu-id="c8493-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c8493-117">Elemento ItemSelectionCondition per l'associazione di espressioni per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="c8493-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="c8493-118">Definisce la condizione che deve esistere per il controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="c8493-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c8493-119">Valore testo</span><span class="sxs-lookup"><span data-stu-id="c8493-119">Text Value</span></span>

<span data-ttu-id="c8493-120">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="c8493-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="c8493-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c8493-121">Remarks</span></span>

<span data-ttu-id="c8493-122">Se viene usato questo elemento, non è possibile specificare l'elemento [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) quando si definisce la condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="c8493-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8493-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c8493-123">See Also</span></span>

[<span data-ttu-id="c8493-124">Elemento PropertyName per ItemSelectionCondition per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="c8493-124">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c8493-125">Elemento ItemSelectionCondition per l'associazione di espressioni per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="c8493-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="c8493-126">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c8493-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
