---
title: Elemento PropertyName per ItemSelectionCondition per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064765"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="98020-102">Elemento PropertyName per ItemSelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="98020-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="98020-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="98020-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="98020-104">Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene utilizzato il controllo.</span><span class="sxs-lookup"><span data-stu-id="98020-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="98020-105">Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="98020-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="98020-106">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per elemento CustomItem GroupBy (formato) per CustomEntry per elemento ExpressionBinding GroupBy (formato) per CustomItem per elemento ItemSelectionCondition GroupBy (formato) per ExpressionBinding per elemento PropertyName GroupBy (formato) ItemSelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="98020-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="98020-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="98020-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="98020-108">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="98020-108">Attributes and Elements</span></span>

<span data-ttu-id="98020-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="98020-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="98020-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="98020-110">Attributes</span></span>

<span data-ttu-id="98020-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="98020-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="98020-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="98020-112">Child Elements</span></span>

<span data-ttu-id="98020-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="98020-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="98020-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="98020-114">Parent Elements</span></span>

|<span data-ttu-id="98020-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="98020-115">Element</span></span>|<span data-ttu-id="98020-116">Description</span><span class="sxs-lookup"><span data-stu-id="98020-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="98020-117">Elemento ItemSelectionCondition per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="98020-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="98020-118">Definisce la condizione che deve essere presente per questo controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="98020-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="98020-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="98020-119">Text Value</span></span>

<span data-ttu-id="98020-120">Specificare il nome della proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="98020-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="98020-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="98020-121">Remarks</span></span>

<span data-ttu-id="98020-122">Se questo elemento viene usato, è possibile specificare il [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) elemento quando si definisce la condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="98020-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="98020-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="98020-123">See Also</span></span>

[<span data-ttu-id="98020-124">Elemento ScriptBlock per ItemSelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="98020-124">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="98020-125">Elemento ItemSelectionCondition per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="98020-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="98020-126">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="98020-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
