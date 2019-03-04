---
title: Elemento SelectionSetName per SelectionCondition per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858137"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="1cf84-102">Elemento SelectionSetName per SelectionCondition per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="1cf84-102">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="1cf84-103">Specifica il set di tipi .NET che attivano la condizione.</span><span class="sxs-lookup"><span data-stu-id="1cf84-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="1cf84-104">Quando uno dei tipi in questo set è presentano, viene soddisfatta la condizione e l'oggetto viene visualizzato tramite questo controllo.</span><span class="sxs-lookup"><span data-stu-id="1cf84-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="1cf84-105">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="1cf84-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="1cf84-106">Configurazione (formato) i controlli elemento dell'elemento di controllo di configurazione (formato) per i controlli per Configuration (formato) CustomControl elemento per elemento Configuration (formato) CustomEntries CustomControl dei controlli per il controllo Elemento CustomEntry di configurazione (formato) per CustomControl per i controlli per Configuration (formato) EntrySelectedBy elemento CustomEntry per i controlli per Configuration (formato) SelectionCondition elemento EntrySelectedBy per i controlli per Elemento SelectionSetName di configurazione (formato) per SelectionCondition per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="1cf84-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1cf84-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1cf84-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1cf84-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="1cf84-108">Attributes and Elements</span></span>

<span data-ttu-id="1cf84-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="1cf84-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1cf84-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="1cf84-110">Attributes</span></span>

<span data-ttu-id="1cf84-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="1cf84-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1cf84-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="1cf84-112">Child Elements</span></span>

<span data-ttu-id="1cf84-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="1cf84-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1cf84-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="1cf84-114">Parent Elements</span></span>

|<span data-ttu-id="1cf84-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="1cf84-115">Element</span></span>|<span data-ttu-id="1cf84-116">Description</span><span class="sxs-lookup"><span data-stu-id="1cf84-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1cf84-117">Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="1cf84-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="1cf84-118">Definisce una condizione che deve essere presente per la definizione di controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="1cf84-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1cf84-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="1cf84-119">Text Value</span></span>

<span data-ttu-id="1cf84-120">Specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="1cf84-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="1cf84-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="1cf84-121">Remarks</span></span>

<span data-ttu-id="1cf84-122">Set di selezione sono i gruppi di oggetti .NET che possono essere usati da qualsiasi vista che definisce il file di formattazione comuni.</span><span class="sxs-lookup"><span data-stu-id="1cf84-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="1cf84-123">Per altre informazioni sulla creazione e che fanno riferimento a set di selezione, vedere [definizione imposta di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="1cf84-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="1cf84-124">La condizione di selezione è possibile specificare un set di selezione o un tipo .NET, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="1cf84-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="1cf84-125">Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1cf84-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1cf84-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1cf84-126">See Also</span></span>

[<span data-ttu-id="1cf84-127">Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="1cf84-127">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="1cf84-128">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="1cf84-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1cf84-129">La definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="1cf84-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="1cf84-130">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="1cf84-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
