---
title: Elemento ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858297"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="7687e-102">Elemento ExpressionBinding per CustomItem per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="7687e-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="7687e-103">Definisce i dati che vengano visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="7687e-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="7687e-104">Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.</span><span class="sxs-lookup"><span data-stu-id="7687e-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="7687e-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) CustomItem per CustomEntry per i controlli elemento di visualizzazione (formato) ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="7687e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7687e-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7687e-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="7687e-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="7687e-107">Attributes and Elements</span></span>

<span data-ttu-id="7687e-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ExpressionBinding` elemento.</span><span class="sxs-lookup"><span data-stu-id="7687e-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7687e-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="7687e-109">Attributes</span></span>

<span data-ttu-id="7687e-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="7687e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7687e-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="7687e-111">Child Elements</span></span>

|<span data-ttu-id="7687e-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="7687e-112">Element</span></span>|<span data-ttu-id="7687e-113">Description</span><span class="sxs-lookup"><span data-stu-id="7687e-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="7687e-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7687e-114">Optional element.</span></span><br /><br /> <span data-ttu-id="7687e-115">Definisce un controllo che viene utilizzato da questo controllo.</span><span class="sxs-lookup"><span data-stu-id="7687e-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="7687e-116">Elemento CustomControlName per ExpressionBinding per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="7687e-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="7687e-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7687e-117">Optional element.</span></span><br /><br /> <span data-ttu-id="7687e-118">Specifica il nome di un controllo comune o un controllo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="7687e-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="7687e-119">Elemento EnumerateCollection per ExpressionBinding per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="7687e-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="7687e-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7687e-120">Optional element.</span></span><br /><br /> <span data-ttu-id="7687e-121">Specifica che vengono visualizzati gli elementi delle raccolte.</span><span class="sxs-lookup"><span data-stu-id="7687e-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="7687e-122">Elemento ItemSelectionCondition ExpressionBinding per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="7687e-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="7687e-123">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7687e-123">Optional element.</span></span><br /><br /> <span data-ttu-id="7687e-124">Definisce la condizione che deve essere presente per questo controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="7687e-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="7687e-125">Elemento PropertyName per ExpressionBinding per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="7687e-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="7687e-126">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7687e-126">Optional element.</span></span><br /><br /> <span data-ttu-id="7687e-127">Specifica la proprietà .NET il cui valore viene visualizzato dal controllo.</span><span class="sxs-lookup"><span data-stu-id="7687e-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="7687e-128">Elemento ScriptBlock per ExpressionBinding per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="7687e-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="7687e-129">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7687e-129">Optional element.</span></span><br /><br /> <span data-ttu-id="7687e-130">Specifica lo script il cui valore viene visualizzato dal controllo.</span><span class="sxs-lookup"><span data-stu-id="7687e-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7687e-131">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="7687e-131">Parent Elements</span></span>

|<span data-ttu-id="7687e-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="7687e-132">Element</span></span>|<span data-ttu-id="7687e-133">Description</span><span class="sxs-lookup"><span data-stu-id="7687e-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7687e-134">Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="7687e-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="7687e-135">Definisce i dati che vengano visualizzati dal controllo e la modalità di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="7687e-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7687e-136">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="7687e-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="7687e-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7687e-137">See Also</span></span>

[<span data-ttu-id="7687e-138">Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="7687e-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="7687e-139">Elemento CustomControlName per ExpressionBinding per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="7687e-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="7687e-140">Elemento EnumerateCollection per ExpressionBinding per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="7687e-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="7687e-141">Elemento ItemSelectionCondition ExpressionBinding per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="7687e-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="7687e-142">Elemento PropertyName per ExpressionBinding per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="7687e-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="7687e-143">Elemento ScriptBlock per ExpressionBinding per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="7687e-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="7687e-144">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="7687e-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
