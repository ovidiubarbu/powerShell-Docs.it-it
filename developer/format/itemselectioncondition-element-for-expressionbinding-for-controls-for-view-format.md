---
title: Elemento ItemSelectionCondition per ExpressionBinding per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861847"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="3241a-102">Elemento ItemSelectionCondition per ExpressionBinding per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="3241a-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="3241a-103">Definisce la condizione che deve essere presente per questo controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="3241a-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="3241a-104">Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.</span><span class="sxs-lookup"><span data-stu-id="3241a-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="3241a-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) CustomItem per CustomEntry per i controlli elemento di visualizzazione (formato) ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato) Elemento ItemSelectionCondition ExpressionBinding per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="3241a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3241a-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3241a-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3241a-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="3241a-107">Attributes and Elements</span></span>

<span data-ttu-id="3241a-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ItemSelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="3241a-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3241a-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="3241a-109">Attributes</span></span>

<span data-ttu-id="3241a-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="3241a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3241a-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="3241a-111">Child Elements</span></span>

|<span data-ttu-id="3241a-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="3241a-112">Element</span></span>|<span data-ttu-id="3241a-113">Description</span><span class="sxs-lookup"><span data-stu-id="3241a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3241a-114">Elemento PropertyName per ItemSelectionCondition per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="3241a-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="3241a-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="3241a-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3241a-116">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="3241a-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="3241a-117">Elemento ScriptBlock per ItemSelectionCondition per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="3241a-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="3241a-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="3241a-118">Optional element.</span></span><br /><br /> <span data-ttu-id="3241a-119">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="3241a-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3241a-120">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="3241a-120">Parent Elements</span></span>

|<span data-ttu-id="3241a-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="3241a-121">Element</span></span>|<span data-ttu-id="3241a-122">Description</span><span class="sxs-lookup"><span data-stu-id="3241a-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3241a-123">Elemento ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="3241a-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="3241a-124">Definisce i dati che vengano visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="3241a-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3241a-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="3241a-125">Remarks</span></span>

<span data-ttu-id="3241a-126">È possibile specificare un nome di proprietà o uno script per questa condizione, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="3241a-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="3241a-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3241a-127">See Also</span></span>

[<span data-ttu-id="3241a-128">Elemento PropertyName per ItemSelectionCondition per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="3241a-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="3241a-129">Elemento ScriptBlock per ItemSelectionCondition per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="3241a-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="3241a-130">Elemento ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="3241a-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="3241a-131">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="3241a-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
