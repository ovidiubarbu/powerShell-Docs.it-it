---
title: Elemento SelectionSetName per SelectionCondition per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368280"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="f3328-102">Elemento SelectionSetName per SelectionCondition per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="f3328-102">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="f3328-103">Specifica il set di tipi .NET che attivano la condizione.</span><span class="sxs-lookup"><span data-stu-id="f3328-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="f3328-104">Quando uno dei tipi in questo set è presente, la condizione viene soddisfatta e l'oggetto viene visualizzato tramite questo controllo.</span><span class="sxs-lookup"><span data-stu-id="f3328-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="f3328-105">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="f3328-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="f3328-106">Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per i controlli per Configuration (Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (Format) SelectionCondition elemento per EntrySelectedBy per i controlli per Configuration (Format) elemento SelectionSetName per SelectionCondition per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="f3328-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f3328-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f3328-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f3328-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="f3328-108">Attributes and Elements</span></span>

<span data-ttu-id="f3328-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="f3328-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f3328-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="f3328-110">Attributes</span></span>

<span data-ttu-id="f3328-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f3328-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f3328-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f3328-112">Child Elements</span></span>

<span data-ttu-id="f3328-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f3328-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f3328-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f3328-114">Parent Elements</span></span>

|<span data-ttu-id="f3328-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="f3328-115">Element</span></span>|<span data-ttu-id="f3328-116">Description</span><span class="sxs-lookup"><span data-stu-id="f3328-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f3328-117">Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="f3328-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="f3328-118">Definisce una condizione che deve esistere per la definizione del controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="f3328-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f3328-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="f3328-119">Text Value</span></span>

<span data-ttu-id="f3328-120">Consente di specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="f3328-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="f3328-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f3328-121">Remarks</span></span>

<span data-ttu-id="f3328-122">I set di selezione sono gruppi comuni di oggetti .NET che possono essere utilizzati da qualsiasi visualizzazione definita dal file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="f3328-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="f3328-123">Per ulteriori informazioni sulla creazione e il riferimento a set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="f3328-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="f3328-124">La condizione di selezione può specificare un set di selezione o un tipo .NET, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="f3328-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="f3328-125">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f3328-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f3328-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f3328-126">See Also</span></span>

[<span data-ttu-id="f3328-127">Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="f3328-127">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="f3328-128">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="f3328-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f3328-129">Definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="f3328-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="f3328-130">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f3328-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
