---
title: Elemento ItemSelectionCondition per ExpressionName per CustomControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362910"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="66269-102">Elemento ItemSelectionCondition per ExpressionBinding per CustomControl (formato)</span><span class="sxs-lookup"><span data-stu-id="66269-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="66269-103">Definisce la condizione che deve esistere per il controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="66269-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="66269-104">Non esiste alcun limite al numero di condizioni di selezione che è possibile specificare per un elemento di controllo.</span><span class="sxs-lookup"><span data-stu-id="66269-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="66269-105">Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.</span><span class="sxs-lookup"><span data-stu-id="66269-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="66269-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per la vista (Format) CustomEntry elemento per CustomEntries per la visualizzazione (Format) CustomItem elemento per Elemento CustomEntry per la vista (Format) espressione per CustomItem per CustomControl per la visualizzazione (Format) ItemSelectionCondition elemento per l'associazione di espressioni per CustomControl per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="66269-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="66269-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="66269-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="66269-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="66269-108">Attributes and Elements</span></span>

<span data-ttu-id="66269-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ItemSelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="66269-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="66269-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="66269-110">Attributes</span></span>

<span data-ttu-id="66269-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="66269-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="66269-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="66269-112">Child Elements</span></span>

|<span data-ttu-id="66269-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="66269-113">Element</span></span>|<span data-ttu-id="66269-114">Description</span><span class="sxs-lookup"><span data-stu-id="66269-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="66269-115">Elemento PropertyName per ItemSelectionCondition per CustomControl per View (format</span><span class="sxs-lookup"><span data-stu-id="66269-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="66269-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="66269-116">Optional element.</span></span><br /><br /> <span data-ttu-id="66269-117">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="66269-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="66269-118">Elemento ScriptBlock per ItemSelectionCondition per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="66269-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="66269-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="66269-119">Optional element.</span></span><br /><br /> <span data-ttu-id="66269-120">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="66269-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="66269-121">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="66269-121">Parent Elements</span></span>

|<span data-ttu-id="66269-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="66269-122">Element</span></span>|<span data-ttu-id="66269-123">Description</span><span class="sxs-lookup"><span data-stu-id="66269-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="66269-124">Elemento expressiongroup per CustomItem per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="66269-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="66269-125">Definisce i dati visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="66269-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="66269-126">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="66269-126">Remarks</span></span>

<span data-ttu-id="66269-127">È possibile specificare un nome di proprietà o uno script per questa condizione, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="66269-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="66269-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="66269-128">See Also</span></span>

[<span data-ttu-id="66269-129">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="66269-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="66269-130">Elemento expressiongroup per CustomItem per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="66269-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
