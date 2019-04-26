---
title: Elemento ScriptBlock per ItemSelectionCondition per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064544"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="2d514-102">Elemento ScriptBlock per ItemSelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="2d514-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="2d514-103">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="2d514-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="2d514-104">Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene utilizzato il controllo.</span><span class="sxs-lookup"><span data-stu-id="2d514-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="2d514-105">Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="2d514-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="2d514-106">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per elemento CustomItem GroupBy (formato) per CustomEntry per elemento ExpressionBinding GroupBy (formato) per CustomItem per elemento ItemSelectionCondition GroupBy (formato) per ExpressionBinding per elemento ScriptBlock GroupBy (formato) ItemSelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="2d514-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2d514-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2d514-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2d514-108">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="2d514-108">Attributes and Elements</span></span>

<span data-ttu-id="2d514-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="2d514-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2d514-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="2d514-110">Attributes</span></span>

<span data-ttu-id="2d514-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2d514-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2d514-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="2d514-112">Child Elements</span></span>

<span data-ttu-id="2d514-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2d514-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2d514-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="2d514-114">Parent Elements</span></span>

|<span data-ttu-id="2d514-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="2d514-115">Element</span></span>|<span data-ttu-id="2d514-116">Description</span><span class="sxs-lookup"><span data-stu-id="2d514-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2d514-117">Elemento ItemSelectionCondition per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="2d514-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="2d514-118">Definisce la condizione che deve essere presente per questo controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="2d514-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2d514-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="2d514-119">Text Value</span></span>

<span data-ttu-id="2d514-120">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="2d514-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="2d514-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="2d514-121">Remarks</span></span>

<span data-ttu-id="2d514-122">Se questo elemento viene usato, è possibile specificare il [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) elemento quando si definisce la condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="2d514-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d514-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2d514-123">See Also</span></span>

[<span data-ttu-id="2d514-124">Elemento ItemSelectionCondition per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="2d514-124">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="2d514-125">Elemento PropertyName per ItemSelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="2d514-125">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="2d514-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="2d514-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
