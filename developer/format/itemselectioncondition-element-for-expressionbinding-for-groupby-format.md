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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065462"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="bdd03-102">Elemento ItemSelectionCondition per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="bdd03-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="bdd03-103">Definisce la condizione che deve essere presente per questo controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="bdd03-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="bdd03-104">Non sono previsti limiti al numero di condizioni di selezione che possono essere specificati per un elemento del controllo.</span><span class="sxs-lookup"><span data-stu-id="bdd03-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="bdd03-105">Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="bdd03-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="bdd03-106">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per elemento CustomItem GroupBy (formato) per CustomEntry per elemento ExpressionBinding GroupBy (formato) per CustomItem per elemento ItemSelectionCondition GroupBy (formato) per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="bdd03-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bdd03-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="bdd03-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bdd03-108">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="bdd03-108">Attributes and Elements</span></span>

<span data-ttu-id="bdd03-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ItemSelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="bdd03-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bdd03-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="bdd03-110">Attributes</span></span>

<span data-ttu-id="bdd03-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="bdd03-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bdd03-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="bdd03-112">Child Elements</span></span>

|<span data-ttu-id="bdd03-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="bdd03-113">Element</span></span>|<span data-ttu-id="bdd03-114">Description</span><span class="sxs-lookup"><span data-stu-id="bdd03-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bdd03-115">Elemento PropertyName per ItemSelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="bdd03-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="bdd03-116">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="bdd03-116">Optional element.</span></span><br /><br /> <span data-ttu-id="bdd03-117">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="bdd03-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="bdd03-118">Elemento ScriptBlock per ItemSelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="bdd03-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="bdd03-119">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="bdd03-119">Optional element.</span></span><br /><br /> <span data-ttu-id="bdd03-120">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="bdd03-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bdd03-121">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="bdd03-121">Parent Elements</span></span>

|<span data-ttu-id="bdd03-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="bdd03-122">Element</span></span>|<span data-ttu-id="bdd03-123">Description</span><span class="sxs-lookup"><span data-stu-id="bdd03-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bdd03-124">Elemento ExpressionBinding per CustomItem per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="bdd03-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="bdd03-125">Definisce i dati che vengano visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="bdd03-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bdd03-126">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="bdd03-126">Remarks</span></span>

<span data-ttu-id="bdd03-127">È possibile specificare un nome di proprietà o uno script per questa condizione, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="bdd03-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="bdd03-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bdd03-128">See Also</span></span>

[<span data-ttu-id="bdd03-129">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="bdd03-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="bdd03-130">Elemento ExpressionBinding per CustomItem per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="bdd03-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
