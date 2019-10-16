---
title: Elemento ItemSelectionCondition per Expressiongroup per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362940"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="2d6f6-102">Elemento ItemSelectionCondition per ExpressionBinding per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="2d6f6-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="2d6f6-103">Definisce la condizione che deve esistere per il controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="2d6f6-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="2d6f6-104">Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="2d6f6-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="2d6f6-105">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per la visualizzazione (Format) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato) elemento Expressiongroup per CustomItem per i controlli per la visualizzazione (formato) Elemento ItemSelectionCondition di Expression per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="2d6f6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2d6f6-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2d6f6-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2d6f6-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="2d6f6-107">Attributes and Elements</span></span>

<span data-ttu-id="2d6f6-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ItemSelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="2d6f6-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2d6f6-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="2d6f6-109">Attributes</span></span>

<span data-ttu-id="2d6f6-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2d6f6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2d6f6-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="2d6f6-111">Child Elements</span></span>

|<span data-ttu-id="2d6f6-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="2d6f6-112">Element</span></span>|<span data-ttu-id="2d6f6-113">Description</span><span class="sxs-lookup"><span data-stu-id="2d6f6-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2d6f6-114">Elemento PropertyName per ItemSelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="2d6f6-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="2d6f6-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="2d6f6-115">Optional element.</span></span><br /><br /> <span data-ttu-id="2d6f6-116">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="2d6f6-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="2d6f6-117">Elemento ScriptBlock per ItemSelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="2d6f6-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="2d6f6-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="2d6f6-118">Optional element.</span></span><br /><br /> <span data-ttu-id="2d6f6-119">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="2d6f6-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2d6f6-120">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="2d6f6-120">Parent Elements</span></span>

|<span data-ttu-id="2d6f6-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="2d6f6-121">Element</span></span>|<span data-ttu-id="2d6f6-122">Description</span><span class="sxs-lookup"><span data-stu-id="2d6f6-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2d6f6-123">Elemento expressiongroup per CustomItem per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="2d6f6-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="2d6f6-124">Definisce i dati visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="2d6f6-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2d6f6-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="2d6f6-125">Remarks</span></span>

<span data-ttu-id="2d6f6-126">È possibile specificare un nome di proprietà o uno script per questa condizione, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="2d6f6-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d6f6-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2d6f6-127">See Also</span></span>

[<span data-ttu-id="2d6f6-128">Elemento PropertyName per ItemSelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="2d6f6-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="2d6f6-129">Elemento ScriptBlock per ItemSelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="2d6f6-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="2d6f6-130">Elemento expressiongroup per CustomItem per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="2d6f6-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="2d6f6-131">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="2d6f6-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
