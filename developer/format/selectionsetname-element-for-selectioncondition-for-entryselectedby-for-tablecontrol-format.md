---
title: Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863277"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="9c8e3-102">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="9c8e3-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="9c8e3-103">Specifica il set di tipi .NET che attivano la condizione.</span><span class="sxs-lookup"><span data-stu-id="9c8e3-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="9c8e3-104">Quando uno dei tipi in questo set è presentano, viene soddisfatta la condizione e l'oggetto viene visualizzato utilizzando questa definizione della visualizzazione della tabella.</span><span class="sxs-lookup"><span data-stu-id="9c8e3-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="9c8e3-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento di configurazione per TableRowEntry (formato) Elemento SelectionCondition per EntrySelectedBy per elemento SelectionSetName TableRowEntry (formato) per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="9c8e3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9c8e3-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9c8e3-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9c8e3-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="9c8e3-107">Attributes and Elements</span></span>

<span data-ttu-id="9c8e3-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="9c8e3-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9c8e3-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="9c8e3-109">Attributes</span></span>

<span data-ttu-id="9c8e3-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="9c8e3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9c8e3-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="9c8e3-111">Child Elements</span></span>

<span data-ttu-id="9c8e3-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="9c8e3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9c8e3-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="9c8e3-113">Parent Elements</span></span>

|<span data-ttu-id="9c8e3-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="9c8e3-114">Element</span></span>|<span data-ttu-id="9c8e3-115">Description</span><span class="sxs-lookup"><span data-stu-id="9c8e3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9c8e3-116">Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="9c8e3-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="9c8e3-117">Definisce la condizione che deve essere presente per l'utilizzo per questa definizione della visualizzazione della tabella.</span><span class="sxs-lookup"><span data-stu-id="9c8e3-117">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9c8e3-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="9c8e3-118">Text Value</span></span>

<span data-ttu-id="9c8e3-119">Specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="9c8e3-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="9c8e3-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="9c8e3-120">Remarks</span></span>

<span data-ttu-id="9c8e3-121">La condizione di selezione è possibile specificare un set di selezione o un tipo .NET, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="9c8e3-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="9c8e3-122">Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="9c8e3-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="9c8e3-123">Set di selezione sono i gruppi di oggetti .NET che possono essere usati da qualsiasi vista che definisce il file di formattazione comuni.</span><span class="sxs-lookup"><span data-stu-id="9c8e3-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="9c8e3-124">Per altre informazioni sulla creazione e che fanno riferimento a set di selezione, vedere [definizione imposta di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="9c8e3-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="9c8e3-125">Per altre informazioni sugli altri componenti di una visualizzazione più ampia, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="9c8e3-125">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9c8e3-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9c8e3-126">See Also</span></span>

[<span data-ttu-id="9c8e3-127">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="9c8e3-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="9c8e3-128">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="9c8e3-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9c8e3-129">Elemento TypeName per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="9c8e3-129">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="9c8e3-130">Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="9c8e3-130">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="9c8e3-131">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="9c8e3-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
