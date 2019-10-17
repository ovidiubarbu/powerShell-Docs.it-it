---
title: Elemento expressiongroup per CustomItem per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363150"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="d1ce1-102">Elemento ExpressionBinding per CustomItem per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="d1ce1-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="d1ce1-103">Definisce i dati visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="d1ce1-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="d1ce1-104">Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.</span><span class="sxs-lookup"><span data-stu-id="d1ce1-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="d1ce1-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl per View (Format) elemento CustomEntries per CustomControl per la visualizzazione (Format) CustomEntry elemento per CustomEntries per CustomControl per la visualizzazione ( Format) elemento CustomItem per CustomEntry per CustomControl per la visualizzazione (Format) elemento Expressiongroup per CustomItem per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="d1ce1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d1ce1-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d1ce1-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="d1ce1-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="d1ce1-107">Attributes and Elements</span></span>

<span data-ttu-id="d1ce1-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ExpressionBinding`.</span><span class="sxs-lookup"><span data-stu-id="d1ce1-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d1ce1-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="d1ce1-109">Attributes</span></span>

<span data-ttu-id="d1ce1-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="d1ce1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d1ce1-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="d1ce1-111">Child Elements</span></span>

|<span data-ttu-id="d1ce1-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="d1ce1-112">Element</span></span>|<span data-ttu-id="d1ce1-113">Description</span><span class="sxs-lookup"><span data-stu-id="d1ce1-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="d1ce1-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d1ce1-114">Optional element.</span></span><br /><br /> <span data-ttu-id="d1ce1-115">Definisce un controllo utilizzato dal controllo.</span><span class="sxs-lookup"><span data-stu-id="d1ce1-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="d1ce1-116">Elemento CustomControlName per Expression per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="d1ce1-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="d1ce1-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d1ce1-117">Optional element.</span></span><br /><br /> <span data-ttu-id="d1ce1-118">Specifica il nome di un controllo comune o di un controllo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="d1ce1-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="d1ce1-119">Elemento Enumerator per Expression per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="d1ce1-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="d1ce1-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d1ce1-120">Optional element.</span></span><br /><br /> <span data-ttu-id="d1ce1-121">Specifica che vengono visualizzati gli elementi delle raccolte.</span><span class="sxs-lookup"><span data-stu-id="d1ce1-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="d1ce1-122">Elemento ItemSelectionCondition per Expression per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="d1ce1-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="d1ce1-123">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d1ce1-123">Optional element.</span></span><br /><br /> <span data-ttu-id="d1ce1-124">Definisce la condizione che deve esistere per il controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="d1ce1-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="d1ce1-125">Elemento PropertyName per Expression per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="d1ce1-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="d1ce1-126">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d1ce1-126">Optional element.</span></span><br /><br /> <span data-ttu-id="d1ce1-127">Specifica la proprietà .NET il cui valore viene visualizzato dal controllo.</span><span class="sxs-lookup"><span data-stu-id="d1ce1-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="d1ce1-128">Elemento ScriptBlock per Expression per CustomCustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="d1ce1-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="d1ce1-129">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d1ce1-129">Optional element.</span></span><br /><br /> <span data-ttu-id="d1ce1-130">Specifica lo script il cui valore viene visualizzato dal controllo.</span><span class="sxs-lookup"><span data-stu-id="d1ce1-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d1ce1-131">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="d1ce1-131">Parent Elements</span></span>

|<span data-ttu-id="d1ce1-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="d1ce1-132">Element</span></span>|<span data-ttu-id="d1ce1-133">Description</span><span class="sxs-lookup"><span data-stu-id="d1ce1-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d1ce1-134">Elemento CustomItem per CustomEntry per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="d1ce1-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="d1ce1-135">Definisce quali dati vengono visualizzati dalla visualizzazione controlli personalizzati e come vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="d1ce1-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d1ce1-136">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="d1ce1-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="d1ce1-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d1ce1-137">See Also</span></span>

[<span data-ttu-id="d1ce1-138">Elemento CustomControlName per Expression per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="d1ce1-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d1ce1-139">Elemento Enumerator per Expression per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="d1ce1-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d1ce1-140">Elemento ItemSelectionCondition per Expression per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="d1ce1-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="d1ce1-141">Elemento PropertyName per Expression per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="d1ce1-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d1ce1-142">Elemento ScriptBlock per Expression per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="d1ce1-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d1ce1-143">Elemento CustomItem per CustomEntry per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="d1ce1-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d1ce1-144">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1ce1-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)