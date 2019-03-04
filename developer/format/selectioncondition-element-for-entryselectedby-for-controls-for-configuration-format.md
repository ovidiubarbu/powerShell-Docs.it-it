---
title: Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854147"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="f87df-102">Elemento SelectionCondition per EntrySelectedBy per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="f87df-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="f87df-103">Definisce una condizione che deve essere presente per la definizione di un controllo comune da usare.</span><span class="sxs-lookup"><span data-stu-id="f87df-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="f87df-104">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="f87df-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="f87df-105">Configurazione (formato) i controlli elemento dell'elemento di controllo di configurazione (formato) per i controlli per Configuration (formato) CustomControl elemento per elemento Configuration (formato) CustomEntries CustomControl dei controlli per il controllo Elemento CustomEntry di configurazione (formato) per CustomControl per i controlli per elemento di configurazione (formato) EntrySelectedBy per CustomEntry per i controlli per elemento di configurazione (formato) SelectionCondition per EntrySelectedBy per CustomEntry per Configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f87df-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f87df-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f87df-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f87df-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="f87df-107">Attributes and Elements</span></span>

<span data-ttu-id="f87df-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="f87df-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f87df-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="f87df-109">Attributes</span></span>

<span data-ttu-id="f87df-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f87df-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f87df-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f87df-111">Child Elements</span></span>

|<span data-ttu-id="f87df-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="f87df-112">Element</span></span>|<span data-ttu-id="f87df-113">Description</span><span class="sxs-lookup"><span data-stu-id="f87df-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f87df-114">Elemento PropertyName per SelectionCondition per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f87df-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f87df-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="f87df-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f87df-116">Specifica una proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="f87df-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f87df-117">Elemento ScriptBlock per SelectionCondition per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f87df-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f87df-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="f87df-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f87df-119">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="f87df-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="f87df-120">Elemento SelectionSetName per SelectionCondition per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f87df-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f87df-121">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="f87df-121">Optional element.</span></span><br /><br /> <span data-ttu-id="f87df-122">Specifica il set di tipi .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="f87df-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="f87df-123">Elemento TypeName per SelectionCondition per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f87df-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f87df-124">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="f87df-124">Optional element.</span></span><br /><br /> <span data-ttu-id="f87df-125">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="f87df-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f87df-126">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f87df-126">Parent Elements</span></span>

|<span data-ttu-id="f87df-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="f87df-127">Element</span></span>|<span data-ttu-id="f87df-128">Description</span><span class="sxs-lookup"><span data-stu-id="f87df-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f87df-129">Elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f87df-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="f87df-130">Definisce i tipi .NET che usano questa voce della definizione di controllo comuni.</span><span class="sxs-lookup"><span data-stu-id="f87df-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f87df-131">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f87df-131">Remarks</span></span>

<span data-ttu-id="f87df-132">Quando si definisce una condizione di selezione, è necessario eseguire le linee guida seguenti:</span><span class="sxs-lookup"><span data-stu-id="f87df-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="f87df-133">La condizione di selezione è necessario specificare un nome di una proprietà minimi o un blocco di script, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="f87df-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="f87df-134">La condizione di selezione può includere un numero qualsiasi di tipi .NET o selezione imposta, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="f87df-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="f87df-135">Per altre informazioni sull'utilizzo di condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f87df-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f87df-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f87df-136">See Also</span></span>

[<span data-ttu-id="f87df-137">Elemento PropertyName per SelectionCondition per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f87df-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f87df-138">Elemento ScriptBlock per SelectionCondition per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f87df-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f87df-139">Elemento SelectionSetName per SelectionCondition per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f87df-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f87df-140">Elemento TypeName per SelectionCondition per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f87df-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f87df-141">Elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f87df-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="f87df-142">La scrittura di un metodo di formattazione di Windows PowerShell e i tipi di File</span><span class="sxs-lookup"><span data-stu-id="f87df-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
