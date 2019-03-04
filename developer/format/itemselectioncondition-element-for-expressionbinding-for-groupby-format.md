---
title: Elemento ItemSelectionCondition per ExpressionBinding per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853137"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="d3f81-102">Elemento ItemSelectionCondition per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d3f81-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="d3f81-103">Definisce la condizione che deve essere presente per questo controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="d3f81-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="d3f81-104">Non sono previsti limiti al numero di condizioni di selezione che possono essere specificati per un elemento del controllo.</span><span class="sxs-lookup"><span data-stu-id="d3f81-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="d3f81-105">Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="d3f81-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="d3f81-106">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per elemento CustomItem GroupBy (formato) per CustomEntry per elemento ExpressionBinding GroupBy (formato) per CustomItem per elemento ItemSelectionCondition GroupBy (formato) per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d3f81-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d3f81-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d3f81-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d3f81-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="d3f81-108">Attributes and Elements</span></span>

<span data-ttu-id="d3f81-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ItemSelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="d3f81-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d3f81-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="d3f81-110">Attributes</span></span>

<span data-ttu-id="d3f81-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="d3f81-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d3f81-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="d3f81-112">Child Elements</span></span>

|<span data-ttu-id="d3f81-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="d3f81-113">Element</span></span>|<span data-ttu-id="d3f81-114">Description</span><span class="sxs-lookup"><span data-stu-id="d3f81-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d3f81-115">Elemento PropertyName per ItemSelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d3f81-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="d3f81-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d3f81-116">Optional element.</span></span><br /><br /> <span data-ttu-id="d3f81-117">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="d3f81-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="d3f81-118">Elemento ScriptBlock per ItemSelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d3f81-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="d3f81-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d3f81-119">Optional element.</span></span><br /><br /> <span data-ttu-id="d3f81-120">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="d3f81-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d3f81-121">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="d3f81-121">Parent Elements</span></span>

|<span data-ttu-id="d3f81-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="d3f81-122">Element</span></span>|<span data-ttu-id="d3f81-123">Description</span><span class="sxs-lookup"><span data-stu-id="d3f81-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d3f81-124">Elemento ExpressionBinding per CustomItem per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d3f81-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="d3f81-125">Definisce i dati che vengano visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="d3f81-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d3f81-126">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="d3f81-126">Remarks</span></span>

<span data-ttu-id="d3f81-127">È possibile specificare un nome di proprietà o uno script per questa condizione, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="d3f81-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3f81-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d3f81-128">See Also</span></span>

[<span data-ttu-id="d3f81-129">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="d3f81-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="d3f81-130">Elemento ExpressionBinding per CustomItem per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d3f81-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
