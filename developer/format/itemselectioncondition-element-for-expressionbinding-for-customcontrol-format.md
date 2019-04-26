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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065825"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="84a3e-102">Elemento ItemSelectionCondition per ExpressionBinding per CustomControl (formato)</span><span class="sxs-lookup"><span data-stu-id="84a3e-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="84a3e-103">Definisce la condizione che deve essere presente per questo controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="84a3e-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="84a3e-104">Non sono previsti limiti al numero di condizioni di selezione che possono essere specificati per un elemento del controllo.</span><span class="sxs-lookup"><span data-stu-id="84a3e-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="84a3e-105">Questo elemento viene usato quando si definisce una vista di controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="84a3e-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="84a3e-106">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per elemento CustomItem visualizzazione (formato) CustomEntry elemento di visualizzazione (formato) ExpressionBinding per CustomItem per CustomControl elemento di visualizzazione (formato) ItemSelectionCondition per associazione di espressioni per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="84a3e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="84a3e-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="84a3e-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="84a3e-108">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="84a3e-108">Attributes and Elements</span></span>

<span data-ttu-id="84a3e-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ItemSelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="84a3e-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="84a3e-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="84a3e-110">Attributes</span></span>

<span data-ttu-id="84a3e-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="84a3e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="84a3e-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="84a3e-112">Child Elements</span></span>

|<span data-ttu-id="84a3e-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="84a3e-113">Element</span></span>|<span data-ttu-id="84a3e-114">Description</span><span class="sxs-lookup"><span data-stu-id="84a3e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="84a3e-115">Elemento PropertyName per ItemSelectionCondition per CustomControl per visualizzazione (formato</span><span class="sxs-lookup"><span data-stu-id="84a3e-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="84a3e-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="84a3e-116">Optional element.</span></span><br /><br /> <span data-ttu-id="84a3e-117">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="84a3e-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="84a3e-118">Elemento ScriptBlock per ItemSelectionCondition per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="84a3e-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="84a3e-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="84a3e-119">Optional element.</span></span><br /><br /> <span data-ttu-id="84a3e-120">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="84a3e-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="84a3e-121">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="84a3e-121">Parent Elements</span></span>

|<span data-ttu-id="84a3e-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="84a3e-122">Element</span></span>|<span data-ttu-id="84a3e-123">Description</span><span class="sxs-lookup"><span data-stu-id="84a3e-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="84a3e-124">Elemento ExpressionBinding per CustomItem per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="84a3e-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="84a3e-125">Definisce i dati che vengano visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="84a3e-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="84a3e-126">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="84a3e-126">Remarks</span></span>

<span data-ttu-id="84a3e-127">È possibile specificare un nome di proprietà o uno script per questa condizione, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="84a3e-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="84a3e-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="84a3e-128">See Also</span></span>

[<span data-ttu-id="84a3e-129">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="84a3e-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="84a3e-130">Elemento ExpressionBinding per CustomItem per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="84a3e-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
