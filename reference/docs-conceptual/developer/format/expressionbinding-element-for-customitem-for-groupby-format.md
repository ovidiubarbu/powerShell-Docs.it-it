---
title: Elemento expressiongroup per CustomItem per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368630"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="b7c23-102">Elemento ExpressionBinding per CustomItem per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="b7c23-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="b7c23-103">Definisce i dati visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="b7c23-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="b7c23-104">Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="b7c23-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="b7c23-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format) elemento CustomItem per CustomEntry per l'elemento di espressione GroupBy (Format) per CustomItem per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b7c23-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b7c23-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b7c23-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="b7c23-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="b7c23-107">Attributes and Elements</span></span>

<span data-ttu-id="b7c23-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ExpressionBinding`.</span><span class="sxs-lookup"><span data-stu-id="b7c23-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b7c23-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="b7c23-109">Attributes</span></span>

<span data-ttu-id="b7c23-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="b7c23-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b7c23-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="b7c23-111">Child Elements</span></span>

|<span data-ttu-id="b7c23-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7c23-112">Element</span></span>|<span data-ttu-id="b7c23-113">Description</span><span class="sxs-lookup"><span data-stu-id="b7c23-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="b7c23-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b7c23-114">Optional element.</span></span><br /><br /> <span data-ttu-id="b7c23-115">Definisce un controllo utilizzato dal controllo.</span><span class="sxs-lookup"><span data-stu-id="b7c23-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="b7c23-116">Elemento CustomControlName per Expressiongroup per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b7c23-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="b7c23-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b7c23-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b7c23-118">Specifica il nome di un controllo comune o di un controllo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="b7c23-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="b7c23-119">[Elemento enumeratorcollection per expressiongroup per GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) Elemento enumeratorcollection per Expressiongroup per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b7c23-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="b7c23-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b7c23-120">Optional element.</span></span><br /><br /> <span data-ttu-id="b7c23-121">Specifica che vengono visualizzati gli elementi delle raccolte.</span><span class="sxs-lookup"><span data-stu-id="b7c23-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="b7c23-122">Elemento ItemSelectionCondition per Expressiongroup per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b7c23-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="b7c23-123">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b7c23-123">Optional element.</span></span><br /><br /> <span data-ttu-id="b7c23-124">Definisce la condizione che deve esistere per il controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="b7c23-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="b7c23-125">Elemento PropertyName per ExpressionName per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b7c23-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="b7c23-126">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b7c23-126">Optional element.</span></span><br /><br /> <span data-ttu-id="b7c23-127">Specifica la proprietà .NET il cui valore viene visualizzato dal controllo.</span><span class="sxs-lookup"><span data-stu-id="b7c23-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="b7c23-128">Elemento ScriptBlock per Expressiongroup per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b7c23-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="b7c23-129">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="b7c23-129">Optional element.</span></span><br /><br /> <span data-ttu-id="b7c23-130">Specifica lo script il cui valore viene visualizzato dal controllo.</span><span class="sxs-lookup"><span data-stu-id="b7c23-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b7c23-131">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="b7c23-131">Parent Elements</span></span>

|<span data-ttu-id="b7c23-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7c23-132">Element</span></span>|<span data-ttu-id="b7c23-133">Description</span><span class="sxs-lookup"><span data-stu-id="b7c23-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7c23-134">Elemento CustomItem per CustomEntry per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b7c23-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="b7c23-135">Definisce quali dati vengono visualizzati dalla visualizzazione controlli personalizzati e come vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="b7c23-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="b7c23-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b7c23-136">See Also</span></span>

[<span data-ttu-id="b7c23-137">Elemento CustomControlName per Expressiongroup per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b7c23-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b7c23-138">Elemento enumeratorcollection per Expressiongroup per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b7c23-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b7c23-139">Elemento ItemSelectionCondition per Expressiongroup per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b7c23-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b7c23-140">Elemento PropertyName per ExpressionName per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b7c23-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b7c23-141">Elemento ScriptBlock per Expressiongroup per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b7c23-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b7c23-142">Elemento CustomItem per CustomEntry per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b7c23-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="b7c23-143">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="b7c23-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
