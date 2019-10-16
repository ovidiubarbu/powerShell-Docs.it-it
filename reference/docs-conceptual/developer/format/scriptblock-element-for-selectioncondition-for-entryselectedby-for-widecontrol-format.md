---
title: Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368560"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="f2c6b-102">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f2c6b-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="f2c6b-103">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="f2c6b-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="f2c6b-104">Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene usata la definizione di voce estesa.</span><span class="sxs-lookup"><span data-stu-id="f2c6b-104">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="f2c6b-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) elemento EntrySelectedBy per WideEntry (Format) SelectionCondition elemento per EntrySelectedBy per WideEntry (Format) elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f2c6b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f2c6b-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f2c6b-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f2c6b-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="f2c6b-107">Attributes and Elements</span></span>

<span data-ttu-id="f2c6b-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="f2c6b-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f2c6b-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="f2c6b-109">Attributes</span></span>

<span data-ttu-id="f2c6b-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f2c6b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f2c6b-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f2c6b-111">Child Elements</span></span>

<span data-ttu-id="f2c6b-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f2c6b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f2c6b-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f2c6b-113">Parent Elements</span></span>

|<span data-ttu-id="f2c6b-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="f2c6b-114">Element</span></span>|<span data-ttu-id="f2c6b-115">Description</span><span class="sxs-lookup"><span data-stu-id="f2c6b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2c6b-116">Elemento SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f2c6b-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="f2c6b-117">Definisce la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="f2c6b-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f2c6b-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="f2c6b-118">Text Value</span></span>

<span data-ttu-id="f2c6b-119">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="f2c6b-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="f2c6b-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f2c6b-120">Remarks</span></span>

<span data-ttu-id="f2c6b-121">La condizione di selezione deve specificare almeno un nome di script o di proprietà da valutare, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="f2c6b-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="f2c6b-122">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f2c6b-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f2c6b-123">Per ulteriori informazioni su altri componenti di una visualizzazione estesa, vedere [visualizzazione estesa](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="f2c6b-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f2c6b-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f2c6b-124">See Also</span></span>

[<span data-ttu-id="f2c6b-125">Creazione di una visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="f2c6b-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="f2c6b-126">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="f2c6b-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f2c6b-127">Elemento PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f2c6b-127">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="f2c6b-128">Elemento SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f2c6b-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="f2c6b-129">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f2c6b-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
