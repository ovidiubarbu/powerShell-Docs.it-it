---
title: Elemento SelectionSetName per SelectionCondition per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361970"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="e4df7-102">Elemento SelectionSetName per SelectionCondition per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="e4df7-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="e4df7-103">Specifica il set di tipi .NET che attivano la condizione.</span><span class="sxs-lookup"><span data-stu-id="e4df7-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="e4df7-104">Quando uno dei tipi in questo set è presente, la condizione viene soddisfatta e l'oggetto viene visualizzato utilizzando questo controllo.</span><span class="sxs-lookup"><span data-stu-id="e4df7-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="e4df7-105">Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="e4df7-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e4df7-106">Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per i controlli per la visualizzazione (formato) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) EntrySelectedBy elemento per CustomEntry per i controlli per la visualizzazione (formato) SelectionCondition elemento per EntrySelectedBy per i controlli per la visualizzazione ( Format) elemento SelectionSetName per SelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="e4df7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e4df7-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e4df7-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e4df7-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="e4df7-108">Attributes and Elements</span></span>

<span data-ttu-id="e4df7-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="e4df7-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e4df7-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="e4df7-110">Attributes</span></span>

<span data-ttu-id="e4df7-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e4df7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e4df7-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="e4df7-112">Child Elements</span></span>

<span data-ttu-id="e4df7-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e4df7-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e4df7-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="e4df7-114">Parent Elements</span></span>

|<span data-ttu-id="e4df7-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="e4df7-115">Element</span></span>|<span data-ttu-id="e4df7-116">Description</span><span class="sxs-lookup"><span data-stu-id="e4df7-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e4df7-117">Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="e4df7-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="e4df7-118">Definisce una condizione che deve esistere per la definizione del controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="e4df7-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e4df7-119">Valore testo</span><span class="sxs-lookup"><span data-stu-id="e4df7-119">Text Value</span></span>

<span data-ttu-id="e4df7-120">Consente di specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="e4df7-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="e4df7-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e4df7-121">Remarks</span></span>

<span data-ttu-id="e4df7-122">I set di selezione sono gruppi comuni di oggetti .NET che possono essere utilizzati da qualsiasi visualizzazione definita dal file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="e4df7-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="e4df7-123">Per ulteriori informazioni sulla creazione e il riferimento a set di selezione, vedere [definizione di set di selezione](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e4df7-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="e4df7-124">La condizione di selezione può specificare un set di selezione o un tipo .NET, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="e4df7-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="e4df7-125">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e4df7-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e4df7-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e4df7-126">See Also</span></span>

[<span data-ttu-id="e4df7-127">Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="e4df7-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="e4df7-128">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="e4df7-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e4df7-129">Definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="e4df7-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="e4df7-130">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4df7-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
