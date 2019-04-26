---
title: Elemento ExpressionBinding per CustomItem per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065904"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="7400b-102">Elemento ExpressionBinding per CustomItem per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7400b-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="7400b-103">Definisce i dati che vengano visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="7400b-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="7400b-104">Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="7400b-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="7400b-105">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per elemento CustomItem GroupBy (formato) per CustomEntry per elemento ExpressionBinding GroupBy (formato) per CustomItem per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7400b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7400b-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7400b-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="7400b-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="7400b-107">Attributes and Elements</span></span>

<span data-ttu-id="7400b-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ExpressionBinding` elemento.</span><span class="sxs-lookup"><span data-stu-id="7400b-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7400b-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="7400b-109">Attributes</span></span>

<span data-ttu-id="7400b-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="7400b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7400b-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="7400b-111">Child Elements</span></span>

|<span data-ttu-id="7400b-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="7400b-112">Element</span></span>|<span data-ttu-id="7400b-113">Description</span><span class="sxs-lookup"><span data-stu-id="7400b-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="7400b-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7400b-114">Optional element.</span></span><br /><br /> <span data-ttu-id="7400b-115">Definisce un controllo che viene utilizzato da questo controllo.</span><span class="sxs-lookup"><span data-stu-id="7400b-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="7400b-116">Elemento CustomControlName per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7400b-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="7400b-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7400b-117">Optional element.</span></span><br /><br /> <span data-ttu-id="7400b-118">Specifica il nome di un controllo comune o un controllo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="7400b-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="7400b-119">[Elemento EnumerateCollection per ExpressionBinding per GroupBy (formato)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)elemento EnumerateCollection per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7400b-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="7400b-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7400b-120">Optional element.</span></span><br /><br /> <span data-ttu-id="7400b-121">Specificare che vengano visualizzati gli elementi delle raccolte.</span><span class="sxs-lookup"><span data-stu-id="7400b-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="7400b-122">Elemento ItemSelectionCondition per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7400b-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="7400b-123">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7400b-123">Optional element.</span></span><br /><br /> <span data-ttu-id="7400b-124">Definisce la condizione che deve essere presente per questo controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="7400b-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="7400b-125">Elemento PropertyName per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7400b-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="7400b-126">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7400b-126">Optional element.</span></span><br /><br /> <span data-ttu-id="7400b-127">Specifica la proprietà .NET il cui valore viene visualizzato dal controllo.</span><span class="sxs-lookup"><span data-stu-id="7400b-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="7400b-128">Elemento ScriptBlock per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7400b-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="7400b-129">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7400b-129">Optional element.</span></span><br /><br /> <span data-ttu-id="7400b-130">Specifica lo script il cui valore viene visualizzato dal controllo.</span><span class="sxs-lookup"><span data-stu-id="7400b-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7400b-131">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="7400b-131">Parent Elements</span></span>

|<span data-ttu-id="7400b-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="7400b-132">Element</span></span>|<span data-ttu-id="7400b-133">Description</span><span class="sxs-lookup"><span data-stu-id="7400b-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7400b-134">Elemento CustomItem per CustomEntry per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7400b-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="7400b-135">Definisce i dati visualizzati dalla visualizzazione del controllo personalizzato e modalità di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="7400b-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="7400b-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7400b-136">See Also</span></span>

[<span data-ttu-id="7400b-137">Elemento CustomControlName per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7400b-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="7400b-138">Elemento EnumerateCollection per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7400b-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="7400b-139">Elemento ItemSelectionCondition per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7400b-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="7400b-140">Elemento PropertyName per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7400b-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="7400b-141">Elemento ScriptBlock per ExpressionBinding per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7400b-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="7400b-142">Elemento CustomItem per CustomEntry per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7400b-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="7400b-143">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="7400b-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
