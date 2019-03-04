---
title: Elemento ItemSelectionCondition per ExpressionBinding per CustomControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858187"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="454df-102">Elemento ItemSelectionCondition per ExpressionBinding per CustomControl (formato)</span><span class="sxs-lookup"><span data-stu-id="454df-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="454df-103">Definisce la condizione che deve essere presente per questo controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="454df-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="454df-104">Non sono previsti limiti al numero di condizioni di selezione che possono essere specificati per un elemento del controllo.</span><span class="sxs-lookup"><span data-stu-id="454df-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="454df-105">Questo elemento viene usato quando si definisce una vista di controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="454df-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="454df-106">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per elemento CustomItem visualizzazione (formato) CustomEntry elemento di visualizzazione (formato) ExpressionBinding per CustomItem per CustomControl elemento di visualizzazione (formato) ItemSelectionCondition per associazione di espressioni per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="454df-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="454df-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="454df-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="454df-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="454df-108">Attributes and Elements</span></span>

<span data-ttu-id="454df-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ItemSelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="454df-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="454df-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="454df-110">Attributes</span></span>

<span data-ttu-id="454df-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="454df-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="454df-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="454df-112">Child Elements</span></span>

|<span data-ttu-id="454df-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="454df-113">Element</span></span>|<span data-ttu-id="454df-114">Description</span><span class="sxs-lookup"><span data-stu-id="454df-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="454df-115">Elemento PropertyName per ItemSelectionCondition per CustomControl per visualizzazione (formato</span><span class="sxs-lookup"><span data-stu-id="454df-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="454df-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="454df-116">Optional element.</span></span><br /><br /> <span data-ttu-id="454df-117">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="454df-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="454df-118">Elemento ScriptBlock per ItemSelectionCondition per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="454df-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="454df-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="454df-119">Optional element.</span></span><br /><br /> <span data-ttu-id="454df-120">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="454df-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="454df-121">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="454df-121">Parent Elements</span></span>

|<span data-ttu-id="454df-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="454df-122">Element</span></span>|<span data-ttu-id="454df-123">Description</span><span class="sxs-lookup"><span data-stu-id="454df-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="454df-124">Elemento ExpressionBinding per CustomItem per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="454df-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="454df-125">Definisce i dati che vengano visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="454df-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="454df-126">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="454df-126">Remarks</span></span>

<span data-ttu-id="454df-127">È possibile specificare un nome di proprietà o uno script per questa condizione, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="454df-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="454df-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="454df-128">See Also</span></span>

[<span data-ttu-id="454df-129">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="454df-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="454df-130">Elemento ExpressionBinding per CustomItem per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="454df-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
