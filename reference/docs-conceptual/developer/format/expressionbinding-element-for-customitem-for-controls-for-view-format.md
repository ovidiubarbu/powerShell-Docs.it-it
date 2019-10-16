---
title: Elemento expressiongroup per CustomItem per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363780"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="2467c-102">Elemento ExpressionBinding per CustomItem per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="2467c-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="2467c-103">Definisce i dati visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="2467c-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="2467c-104">Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="2467c-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="2467c-105">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per la visualizzazione (Format) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato) elemento Expressiongroup per CustomItem per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="2467c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2467c-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2467c-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="2467c-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="2467c-107">Attributes and Elements</span></span>

<span data-ttu-id="2467c-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ExpressionBinding`.</span><span class="sxs-lookup"><span data-stu-id="2467c-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2467c-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="2467c-109">Attributes</span></span>

<span data-ttu-id="2467c-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2467c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2467c-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="2467c-111">Child Elements</span></span>

|<span data-ttu-id="2467c-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="2467c-112">Element</span></span>|<span data-ttu-id="2467c-113">Description</span><span class="sxs-lookup"><span data-stu-id="2467c-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="2467c-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="2467c-114">Optional element.</span></span><br /><br /> <span data-ttu-id="2467c-115">Definisce un controllo utilizzato dal controllo.</span><span class="sxs-lookup"><span data-stu-id="2467c-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="2467c-116">Elemento CustomControlName per Expressiongroup per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="2467c-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="2467c-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="2467c-117">Optional element.</span></span><br /><br /> <span data-ttu-id="2467c-118">Specifica il nome di un controllo comune o di un controllo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="2467c-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="2467c-119">Elemento enumeratorcollection per Expressiongroup per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="2467c-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="2467c-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="2467c-120">Optional element.</span></span><br /><br /> <span data-ttu-id="2467c-121">Specifica che gli elementi delle raccolte vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="2467c-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="2467c-122">Elemento ItemSelectionCondition di Expression per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="2467c-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="2467c-123">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="2467c-123">Optional element.</span></span><br /><br /> <span data-ttu-id="2467c-124">Definisce la condizione che deve esistere per il controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="2467c-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="2467c-125">Elemento PropertyName per ExpressionName per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="2467c-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="2467c-126">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="2467c-126">Optional element.</span></span><br /><br /> <span data-ttu-id="2467c-127">Specifica la proprietà .NET il cui valore viene visualizzato dal controllo.</span><span class="sxs-lookup"><span data-stu-id="2467c-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="2467c-128">Elemento ScriptBlock per Expressiongroup per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="2467c-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="2467c-129">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="2467c-129">Optional element.</span></span><br /><br /> <span data-ttu-id="2467c-130">Specifica lo script il cui valore viene visualizzato dal controllo.</span><span class="sxs-lookup"><span data-stu-id="2467c-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2467c-131">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="2467c-131">Parent Elements</span></span>

|<span data-ttu-id="2467c-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="2467c-132">Element</span></span>|<span data-ttu-id="2467c-133">Description</span><span class="sxs-lookup"><span data-stu-id="2467c-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2467c-134">Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="2467c-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="2467c-135">Definisce quali dati vengono visualizzati dal controllo e come vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="2467c-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2467c-136">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="2467c-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="2467c-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2467c-137">See Also</span></span>

[<span data-ttu-id="2467c-138">Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="2467c-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="2467c-139">Elemento CustomControlName per Expressiongroup per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="2467c-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="2467c-140">Elemento enumeratorcollection per Expressiongroup per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="2467c-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="2467c-141">Elemento ItemSelectionCondition di Expression per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="2467c-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="2467c-142">Elemento PropertyName per ExpressionName per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="2467c-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="2467c-143">Elemento ScriptBlock per Expressiongroup per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="2467c-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="2467c-144">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="2467c-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
