---
title: Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368450"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="0c669-102">Elemento SelectionCondition per EntrySelectedBy per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="0c669-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="0c669-103">Definisce una condizione che deve esistere per la definizione di un controllo comune da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="0c669-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="0c669-104">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="0c669-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="0c669-105">Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per i controlli per Configuration (Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (Format) SelectionCondition elemento per EntrySelectedBy per CustomEntry per Configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="0c669-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0c669-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0c669-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0c669-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="0c669-107">Attributes and Elements</span></span>

<span data-ttu-id="0c669-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="0c669-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0c669-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="0c669-109">Attributes</span></span>

<span data-ttu-id="0c669-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="0c669-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0c669-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="0c669-111">Child Elements</span></span>

|<span data-ttu-id="0c669-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="0c669-112">Element</span></span>|<span data-ttu-id="0c669-113">Description</span><span class="sxs-lookup"><span data-stu-id="0c669-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0c669-114">Elemento PropertyName per SelectionCondition per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0c669-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="0c669-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="0c669-115">Optional element.</span></span><br /><br /> <span data-ttu-id="0c669-116">Specifica una proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="0c669-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="0c669-117">Elemento ScriptBlock per SelectionCondition per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0c669-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="0c669-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="0c669-118">Optional element.</span></span><br /><br /> <span data-ttu-id="0c669-119">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="0c669-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="0c669-120">Elemento SelectionSetName per SelectionCondition per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0c669-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="0c669-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="0c669-121">Optional element.</span></span><br /><br /> <span data-ttu-id="0c669-122">Specifica il set di tipi .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="0c669-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="0c669-123">Elemento TypeName per SelectionCondition per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0c669-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="0c669-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="0c669-124">Optional element.</span></span><br /><br /> <span data-ttu-id="0c669-125">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="0c669-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0c669-126">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="0c669-126">Parent Elements</span></span>

|<span data-ttu-id="0c669-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="0c669-127">Element</span></span>|<span data-ttu-id="0c669-128">Description</span><span class="sxs-lookup"><span data-stu-id="0c669-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0c669-129">Elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0c669-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="0c669-130">Definisce i tipi .NET che utilizzano questa voce della definizione del controllo comune.</span><span class="sxs-lookup"><span data-stu-id="0c669-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0c669-131">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="0c669-131">Remarks</span></span>

<span data-ttu-id="0c669-132">Quando si definisce una condizione di selezione, è necessario attenersi alle linee guida seguenti:</span><span class="sxs-lookup"><span data-stu-id="0c669-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="0c669-133">La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="0c669-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="0c669-134">La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="0c669-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="0c669-135">Per ulteriori informazioni sul modo in cui è possibile utilizzare le condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0c669-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0c669-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0c669-136">See Also</span></span>

[<span data-ttu-id="0c669-137">Elemento PropertyName per SelectionCondition per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0c669-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="0c669-138">Elemento ScriptBlock per SelectionCondition per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0c669-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="0c669-139">Elemento SelectionSetName per SelectionCondition per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0c669-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="0c669-140">Elemento TypeName per SelectionCondition per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0c669-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="0c669-141">Elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="0c669-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="0c669-142">Scrittura di un file di formattazione e di tipi di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c669-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
