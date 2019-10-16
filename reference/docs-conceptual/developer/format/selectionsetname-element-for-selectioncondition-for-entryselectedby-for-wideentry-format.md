---
title: Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a13a429c-a31b-4e29-828c-c0c0917b5415
caps.latest.revision: 11
ms.openlocfilehash: baea89e4b259611dfa45b6bcf94fa0bf2df6b9de
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368410"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="2e903-102">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="2e903-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="2e903-103">Specifica il set di tipi .NET che attivano la condizione.</span><span class="sxs-lookup"><span data-stu-id="2e903-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="2e903-104">Quando uno dei tipi in questo set è presente, la condizione viene soddisfatta e l'oggetto viene visualizzato utilizzando questa definizione della visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="2e903-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="2e903-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) elemento EntrySelectedBy per WideEntry (Format) SelectionCondition elemento per EntrySelectedBy per WideEntry (Format) elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2e903-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2e903-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2e903-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2e903-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="2e903-107">Attributes and Elements</span></span>

<span data-ttu-id="2e903-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="2e903-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2e903-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="2e903-109">Attributes</span></span>

<span data-ttu-id="2e903-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2e903-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2e903-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="2e903-111">Child Elements</span></span>

<span data-ttu-id="2e903-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2e903-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2e903-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="2e903-113">Parent Elements</span></span>

|<span data-ttu-id="2e903-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="2e903-114">Element</span></span>|<span data-ttu-id="2e903-115">Description</span><span class="sxs-lookup"><span data-stu-id="2e903-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e903-116">Elemento SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2e903-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="2e903-117">Definisce la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="2e903-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2e903-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="2e903-118">Text Value</span></span>

<span data-ttu-id="2e903-119">Consente di specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="2e903-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="2e903-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="2e903-120">Remarks</span></span>

<span data-ttu-id="2e903-121">La condizione di selezione può specificare un set di selezione o un tipo .NET, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="2e903-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="2e903-122">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2e903-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="2e903-123">I set di selezione sono gruppi comuni di oggetti .NET che possono essere utilizzati da qualsiasi visualizzazione definita dal file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="2e903-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="2e903-124">Per ulteriori informazioni sulla creazione e il riferimento a set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="2e903-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="2e903-125">Per ulteriori informazioni su altri componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="2e903-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2e903-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2e903-126">See Also</span></span>

[<span data-ttu-id="2e903-127">Creazione di una visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="2e903-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="2e903-128">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="2e903-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2e903-129">Definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="2e903-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="2e903-130">Elemento SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2e903-130">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="2e903-131">Elemento TypeName per SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2e903-131">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="2e903-132">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="2e903-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
