---
title: Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per ListEntry (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075512"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="c1c21-102">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="c1c21-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="c1c21-103">Specifica il set di tipi .NET che attivano la condizione.</span><span class="sxs-lookup"><span data-stu-id="c1c21-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="c1c21-104">Quando uno dei tipi in questo set è presentano, viene soddisfatta la condizione e l'oggetto viene visualizzato utilizzando questa definizione della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="c1c21-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="c1c21-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) elemento ListEntries (formato) elemento ListEntry (formato) EntrySelectedBy elemento di configurazione per elemento SelectionCondition ListEntry (formato) EntrySelectedBy per elemento SelectionSetName ListEntry (formato) per SelectionCondition per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="c1c21-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c1c21-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c1c21-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c1c21-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="c1c21-107">Attributes and Elements</span></span>

<span data-ttu-id="c1c21-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="c1c21-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c1c21-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="c1c21-109">Attributes</span></span>

<span data-ttu-id="c1c21-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c1c21-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c1c21-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="c1c21-111">Child Elements</span></span>

<span data-ttu-id="c1c21-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c1c21-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c1c21-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="c1c21-113">Parent Elements</span></span>

|<span data-ttu-id="c1c21-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="c1c21-114">Element</span></span>|<span data-ttu-id="c1c21-115">Description</span><span class="sxs-lookup"><span data-stu-id="c1c21-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1c21-116">Elemento SelectionCondition per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="c1c21-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="c1c21-117">Definisce la condizione che deve essere presente per usare questa definizione della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="c1c21-117">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c1c21-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="c1c21-118">Text Value</span></span>

<span data-ttu-id="c1c21-119">Specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="c1c21-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="c1c21-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c1c21-120">Remarks</span></span>

<span data-ttu-id="c1c21-121">La condizione di selezione è possibile specificare un set di selezione o un tipo .NET, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="c1c21-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="c1c21-122">Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c1c21-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="c1c21-123">Set di selezione sono i gruppi di oggetti .NET che possono essere usati da qualsiasi vista che definisce il file di formattazione comuni.</span><span class="sxs-lookup"><span data-stu-id="c1c21-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="c1c21-124">Per altre informazioni sulla creazione e che fanno riferimento a set di selezione, vedere [definizione imposta di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="c1c21-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="c1c21-125">Per altre informazioni sugli altri componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="c1c21-125">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c1c21-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c1c21-126">See Also</span></span>

[<span data-ttu-id="c1c21-127">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="c1c21-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c1c21-128">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="c1c21-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c1c21-129">Elemento SelectionCondition per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="c1c21-129">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="c1c21-130">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c1c21-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
