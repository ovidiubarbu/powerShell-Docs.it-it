---
title: Elemento SelectionCondition per EntrySelectedBy per CustomControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075750"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="37832-102">Elemento SelectionCondition per EntrySelectedBy per CustomControl (formato)</span><span class="sxs-lookup"><span data-stu-id="37832-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="37832-103">Definisce una condizione che deve essere presente per una definizione di controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="37832-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="37832-104">Questo elemento viene usato quando si definisce una vista di controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="37832-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="37832-105">Elemento di CustomControl elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) elemento di visualizzazione (formato) CustomEntries per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per CustomControl per visualizzazione ( Elemento CustomItem Format) per CustomEntry per CustomControl elemento di visualizzazione (formato) EntrySelectedBy per CustomEntry per CustomControl elemento di visualizzazione (formato) SelectionCondition per EntrySelectedBy per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="37832-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="37832-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="37832-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="37832-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="37832-107">Attributes and Elements</span></span>

<span data-ttu-id="37832-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="37832-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="37832-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="37832-109">Attributes</span></span>

<span data-ttu-id="37832-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="37832-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="37832-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="37832-111">Child Elements</span></span>

|<span data-ttu-id="37832-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="37832-112">Element</span></span>|<span data-ttu-id="37832-113">Description</span><span class="sxs-lookup"><span data-stu-id="37832-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="37832-114">Elemento PropertyName per SelectionCondition per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="37832-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="37832-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="37832-115">Optional element.</span></span><br /><br /> <span data-ttu-id="37832-116">Specifica una proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="37832-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="37832-117">Elemento ScriptBlock per SelectionCondition per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="37832-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="37832-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="37832-118">Optional element.</span></span><br /><br /> <span data-ttu-id="37832-119">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="37832-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="37832-120">Elemento SelectionSetName per SelectionCondition per un controllo personalizzato per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="37832-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="37832-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="37832-121">Optional element.</span></span><br /><br /> <span data-ttu-id="37832-122">Specifica il set di tipi .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="37832-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="37832-123">Elemento TypeName per SelectionCondition per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="37832-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="37832-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="37832-124">Optional element.</span></span><br /><br /> <span data-ttu-id="37832-125">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="37832-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="37832-126">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="37832-126">Parent Elements</span></span>

|<span data-ttu-id="37832-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="37832-127">Element</span></span>|<span data-ttu-id="37832-128">Description</span><span class="sxs-lookup"><span data-stu-id="37832-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="37832-129">Elemento EntrySelectedBy per CustomEntry per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="37832-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="37832-130">Definisce i tipi .NET che usano questa definizione di controllo o la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="37832-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="37832-131">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="37832-131">Remarks</span></span>

<span data-ttu-id="37832-132">Quando si definisce una condizione di selezione, si applicano i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="37832-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="37832-133">La condizione di selezione è necessario specificare un nome di una proprietà minimi o un blocco di script, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="37832-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="37832-134">La condizione di selezione può includere un numero qualsiasi di tipi .NET o selezione imposta, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="37832-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="37832-135">Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="37832-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="37832-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="37832-136">See Also</span></span>

[<span data-ttu-id="37832-137">Elemento PropertyName per SelectionCondition per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="37832-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="37832-138">Elemento ScriptBlock per SelectionCondition per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="37832-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="37832-139">Elemento SelectionSetName per SelectionCondition per un controllo personalizzato per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="37832-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="37832-140">Elemento TypeName per SelectionCondition per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="37832-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="37832-141">Elemento EntrySelectedBy per CustomEntry per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="37832-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="37832-142">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="37832-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
