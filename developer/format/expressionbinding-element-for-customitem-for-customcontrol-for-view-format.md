---
title: Elemento ExpressionBinding per CustomItem per CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065921"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="20987-102">Elemento ExpressionBinding per CustomItem per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="20987-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="20987-103">Definisce i dati che vengano visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="20987-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="20987-104">Questo elemento viene usato quando si definisce una vista di controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="20987-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="20987-105">Elemento di CustomControl elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) elemento di visualizzazione (formato) CustomEntries per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per CustomControl per visualizzazione ( Elemento CustomItem Format) per CustomEntry per CustomControl elemento di visualizzazione (formato) ExpressionBinding per CustomItem per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="20987-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="20987-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="20987-106">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="20987-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="20987-107">Attributes and Elements</span></span>

<span data-ttu-id="20987-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ExpressionBinding` elemento.</span><span class="sxs-lookup"><span data-stu-id="20987-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="20987-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="20987-109">Attributes</span></span>

<span data-ttu-id="20987-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="20987-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="20987-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="20987-111">Child Elements</span></span>

|<span data-ttu-id="20987-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="20987-112">Element</span></span>|<span data-ttu-id="20987-113">Description</span><span class="sxs-lookup"><span data-stu-id="20987-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="20987-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="20987-114">Optional element.</span></span><br /><br /> <span data-ttu-id="20987-115">Definisce un controllo che viene utilizzato da questo controllo.</span><span class="sxs-lookup"><span data-stu-id="20987-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="20987-116">Elemento CustomControlName per ExpressionBinding per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="20987-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="20987-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="20987-117">Optional element.</span></span><br /><br /> <span data-ttu-id="20987-118">Specifica il nome di un controllo comune o un controllo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="20987-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="20987-119">Elemento EnumerateCollection per ExpressionBinding per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="20987-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="20987-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="20987-120">Optional element.</span></span><br /><br /> <span data-ttu-id="20987-121">Specificare che vengano visualizzati gli elementi delle raccolte.</span><span class="sxs-lookup"><span data-stu-id="20987-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="20987-122">Elemento ItemSelectionCondition per ExpressionBinding per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="20987-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="20987-123">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="20987-123">Optional element.</span></span><br /><br /> <span data-ttu-id="20987-124">Definisce la condizione che deve essere presente per questo controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="20987-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="20987-125">Elemento PropertyName per ExpressionBinding per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="20987-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="20987-126">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="20987-126">Optional element.</span></span><br /><br /> <span data-ttu-id="20987-127">Specifica la proprietà .NET il cui valore viene visualizzato dal controllo.</span><span class="sxs-lookup"><span data-stu-id="20987-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="20987-128">Elemento ScriptBlock per ExpressionBinding per CustomCustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="20987-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="20987-129">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="20987-129">Optional element.</span></span><br /><br /> <span data-ttu-id="20987-130">Specifica lo script il cui valore viene visualizzato dal controllo.</span><span class="sxs-lookup"><span data-stu-id="20987-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="20987-131">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="20987-131">Parent Elements</span></span>

|<span data-ttu-id="20987-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="20987-132">Element</span></span>|<span data-ttu-id="20987-133">Description</span><span class="sxs-lookup"><span data-stu-id="20987-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="20987-134">Elemento CustomItem per CustomEntry per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="20987-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="20987-135">Definisce i dati visualizzati dalla visualizzazione del controllo personalizzato e modalità di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="20987-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="20987-136">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="20987-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="20987-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="20987-137">See Also</span></span>

[<span data-ttu-id="20987-138">Elemento CustomControlName per ExpressionBinding per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="20987-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="20987-139">Elemento EnumerateCollection per ExpressionBinding per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="20987-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="20987-140">Elemento ItemSelectionCondition per ExpressionBinding per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="20987-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="20987-141">Elemento PropertyName per ExpressionBinding per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="20987-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="20987-142">Elemento ScriptBlock per ExpressionBinding per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="20987-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="20987-143">Elemento CustomItem per CustomEntry per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="20987-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="20987-144">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="20987-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
