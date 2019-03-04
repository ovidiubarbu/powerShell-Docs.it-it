---
title: Elemento SelectionSetName per SelectionCondition per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855117"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="4572a-102">Elemento SelectionSetName per SelectionCondition per Controls per View (formato)</span><span class="sxs-lookup"><span data-stu-id="4572a-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="4572a-103">Specifica il set di tipi .NET che attivano la condizione.</span><span class="sxs-lookup"><span data-stu-id="4572a-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="4572a-104">Quando uno dei tipi in questo set è presentano, viene soddisfatta la condizione e l'oggetto viene visualizzato l'utilizzo di questo controllo.</span><span class="sxs-lookup"><span data-stu-id="4572a-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="4572a-105">Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.</span><span class="sxs-lookup"><span data-stu-id="4572a-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="4572a-106">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl per i controlli elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) EntrySelectedBy per CustomEntry per i controlli elemento di visualizzazione (formato) SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione ( Elemento SelectionSetName Format) per SelectionCondition per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="4572a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4572a-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4572a-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4572a-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="4572a-108">Attributes and Elements</span></span>

<span data-ttu-id="4572a-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="4572a-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4572a-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="4572a-110">Attributes</span></span>

<span data-ttu-id="4572a-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="4572a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4572a-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="4572a-112">Child Elements</span></span>

<span data-ttu-id="4572a-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="4572a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4572a-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="4572a-114">Parent Elements</span></span>

|<span data-ttu-id="4572a-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="4572a-115">Element</span></span>|<span data-ttu-id="4572a-116">Description</span><span class="sxs-lookup"><span data-stu-id="4572a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4572a-117">Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="4572a-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="4572a-118">Definisce una condizione che deve essere presente per la definizione di controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="4572a-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4572a-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="4572a-119">Text Value</span></span>

<span data-ttu-id="4572a-120">Specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="4572a-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="4572a-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="4572a-121">Remarks</span></span>

<span data-ttu-id="4572a-122">Set di selezione sono i gruppi di oggetti .NET che possono essere usati da qualsiasi vista che definisce il file di formattazione comuni.</span><span class="sxs-lookup"><span data-stu-id="4572a-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="4572a-123">Per altre informazioni sulla creazione e che fanno riferimento a set di selezione, vedere [definizione di selezione imposta](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="4572a-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="4572a-124">La condizione di selezione è possibile specificare un set di selezione o un tipo .NET, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="4572a-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="4572a-125">Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="4572a-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4572a-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4572a-126">See Also</span></span>

[<span data-ttu-id="4572a-127">Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="4572a-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="4572a-128">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="4572a-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="4572a-129">La definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="4572a-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="4572a-130">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="4572a-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
