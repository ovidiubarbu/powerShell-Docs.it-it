---
title: Elemento SelectionCondition per EntrySelectedBy per CustomControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368440"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="3cebd-102">Elemento SelectionCondition per EntrySelectedBy per CustomControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3cebd-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="3cebd-103">Definisce una condizione che deve esistere per la definizione di un controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="3cebd-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="3cebd-104">Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.</span><span class="sxs-lookup"><span data-stu-id="3cebd-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="3cebd-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl per View (Format) elemento CustomEntries per CustomControl per la visualizzazione (Format) CustomEntry elemento per CustomEntries per CustomControl per la visualizzazione ( Format) elemento CustomItem per CustomEntry per CustomControl per la visualizzazione (Format) EntrySelectedBy elemento per CustomEntry per CustomControl per la visualizzazione (Format) SelectionCondition elemento per EntrySelectedBy per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3cebd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3cebd-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3cebd-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3cebd-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="3cebd-107">Attributes and Elements</span></span>

<span data-ttu-id="3cebd-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="3cebd-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3cebd-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="3cebd-109">Attributes</span></span>

<span data-ttu-id="3cebd-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="3cebd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3cebd-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="3cebd-111">Child Elements</span></span>

|<span data-ttu-id="3cebd-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="3cebd-112">Element</span></span>|<span data-ttu-id="3cebd-113">Description</span><span class="sxs-lookup"><span data-stu-id="3cebd-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3cebd-114">Elemento PropertyName per SelectionCondition per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3cebd-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="3cebd-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="3cebd-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3cebd-116">Specifica una proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="3cebd-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="3cebd-117">Elemento ScriptBlock per SelectionCondition per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3cebd-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="3cebd-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="3cebd-118">Optional element.</span></span><br /><br /> <span data-ttu-id="3cebd-119">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="3cebd-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="3cebd-120">Elemento SelectionSetName per SelectionCondition per il controllo personalizzato per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="3cebd-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="3cebd-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="3cebd-121">Optional element.</span></span><br /><br /> <span data-ttu-id="3cebd-122">Specifica il set di tipi .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="3cebd-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="3cebd-123">Elemento TypeName per SelectionCondition per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3cebd-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="3cebd-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="3cebd-124">Optional element.</span></span><br /><br /> <span data-ttu-id="3cebd-125">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="3cebd-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3cebd-126">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="3cebd-126">Parent Elements</span></span>

|<span data-ttu-id="3cebd-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="3cebd-127">Element</span></span>|<span data-ttu-id="3cebd-128">Description</span><span class="sxs-lookup"><span data-stu-id="3cebd-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3cebd-129">Elemento EntrySelectedBy per CustomEntry per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3cebd-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="3cebd-130">Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="3cebd-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3cebd-131">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="3cebd-131">Remarks</span></span>

<span data-ttu-id="3cebd-132">Quando si definisce una condizione di selezione, si applicano i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="3cebd-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="3cebd-133">La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="3cebd-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="3cebd-134">La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="3cebd-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="3cebd-135">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3cebd-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3cebd-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3cebd-136">See Also</span></span>

[<span data-ttu-id="3cebd-137">Elemento PropertyName per SelectionCondition per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3cebd-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3cebd-138">Elemento ScriptBlock per SelectionCondition per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3cebd-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3cebd-139">Elemento SelectionSetName per SelectionCondition per il controllo personalizzato per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="3cebd-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3cebd-140">Elemento TypeName per SelectionCondition per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3cebd-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3cebd-141">Elemento EntrySelectedBy per CustomEntry per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="3cebd-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3cebd-142">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="3cebd-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
