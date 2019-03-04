---
title: Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a13a429c-a31b-4e29-828c-c0c0917b5415
caps.latest.revision: 11
ms.openlocfilehash: baea89e4b259611dfa45b6bcf94fa0bf2df6b9de
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854127"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="58127-102">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="58127-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="58127-103">Specifica il set di tipi .NET che attivano la condizione.</span><span class="sxs-lookup"><span data-stu-id="58127-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="58127-104">Quando uno dei tipi in questo set è presentano, viene soddisfatta la condizione e l'oggetto viene visualizzato utilizzando questa definizione della vista wide.</span><span class="sxs-lookup"><span data-stu-id="58127-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="58127-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento di configurazione per elemento SelectionCondition WideEntry (formato) per EntrySelectedBy per elemento SelectionSetName WideEntry (formato) per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="58127-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="58127-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="58127-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="58127-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="58127-107">Attributes and Elements</span></span>

<span data-ttu-id="58127-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="58127-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="58127-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="58127-109">Attributes</span></span>

<span data-ttu-id="58127-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="58127-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="58127-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="58127-111">Child Elements</span></span>

<span data-ttu-id="58127-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="58127-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="58127-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="58127-113">Parent Elements</span></span>

|<span data-ttu-id="58127-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="58127-114">Element</span></span>|<span data-ttu-id="58127-115">Description</span><span class="sxs-lookup"><span data-stu-id="58127-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="58127-116">Elemento SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="58127-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="58127-117">Definisce la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="58127-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="58127-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="58127-118">Text Value</span></span>

<span data-ttu-id="58127-119">Specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="58127-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="58127-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="58127-120">Remarks</span></span>

<span data-ttu-id="58127-121">La condizione di selezione è possibile specificare un set di selezione o un tipo .NET, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="58127-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="58127-122">Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="58127-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="58127-123">Set di selezione sono i gruppi di oggetti .NET che possono essere usati da qualsiasi vista che definisce il file di formattazione comuni.</span><span class="sxs-lookup"><span data-stu-id="58127-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="58127-124">Per altre informazioni sulla creazione e che fanno riferimento a set di selezione, vedere [definizione imposta di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="58127-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="58127-125">Per altre informazioni sugli altri componenti di una visualizzazione più ampia, vedere [creazione di una visualizzazione più ampia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="58127-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="58127-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="58127-126">See Also</span></span>

[<span data-ttu-id="58127-127">Creazione di una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="58127-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="58127-128">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="58127-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="58127-129">La definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="58127-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="58127-130">Elemento SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="58127-130">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="58127-131">Elemento TypeName per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="58127-131">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="58127-132">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="58127-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
