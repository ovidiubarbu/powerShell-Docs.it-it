---
title: Elemento ItemSelectionCondition per ExpressionName per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365290"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="b4e7d-102">Elemento ItemSelectionCondition per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="b4e7d-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="b4e7d-103">Definisce la condizione che deve esistere per il controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="b4e7d-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="b4e7d-104">Non esiste alcun limite al numero di condizioni di selezione che è possibile specificare per un elemento di controllo.</span><span class="sxs-lookup"><span data-stu-id="b4e7d-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="b4e7d-105">Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="b4e7d-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="b4e7d-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format) elemento CustomItem per CustomEntry per l'elemento di espressione GroupBy (Format) per CustomItem per l'elemento GroupBy (Format) ItemSelectionCondition per Expression per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b4e7d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b4e7d-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b4e7d-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b4e7d-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="b4e7d-108">Attributes and Elements</span></span>

<span data-ttu-id="b4e7d-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ItemSelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="b4e7d-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b4e7d-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="b4e7d-110">Attributes</span></span>

<span data-ttu-id="b4e7d-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="b4e7d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b4e7d-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="b4e7d-112">Child Elements</span></span>

|<span data-ttu-id="b4e7d-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="b4e7d-113">Element</span></span>|<span data-ttu-id="b4e7d-114">Description</span><span class="sxs-lookup"><span data-stu-id="b4e7d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4e7d-115">Elemento PropertyName per ItemSelectionCondition per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b4e7d-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="b4e7d-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b4e7d-116">Optional element.</span></span><br /><br /> <span data-ttu-id="b4e7d-117">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="b4e7d-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="b4e7d-118">Elemento ScriptBlock per ItemSelectionCondition per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b4e7d-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="b4e7d-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b4e7d-119">Optional element.</span></span><br /><br /> <span data-ttu-id="b4e7d-120">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="b4e7d-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b4e7d-121">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="b4e7d-121">Parent Elements</span></span>

|<span data-ttu-id="b4e7d-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="b4e7d-122">Element</span></span>|<span data-ttu-id="b4e7d-123">Description</span><span class="sxs-lookup"><span data-stu-id="b4e7d-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4e7d-124">Elemento expressiongroup per CustomItem per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b4e7d-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="b4e7d-125">Definisce i dati visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="b4e7d-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b4e7d-126">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="b4e7d-126">Remarks</span></span>

<span data-ttu-id="b4e7d-127">È possibile specificare un nome di proprietà o uno script per questa condizione, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="b4e7d-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4e7d-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b4e7d-128">See Also</span></span>

[<span data-ttu-id="b4e7d-129">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="b4e7d-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="b4e7d-130">Elemento expressiongroup per CustomItem per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b4e7d-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
