---
title: Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861217"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="218b7-102">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="218b7-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="218b7-103">Specifica il set di tipi .NET che attivano la condizione.</span><span class="sxs-lookup"><span data-stu-id="218b7-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="218b7-104">Quando uno dei tipi in questo set sono presente, la condizione viene soddisfatta.</span><span class="sxs-lookup"><span data-stu-id="218b7-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="218b7-105">Configurazione elemento elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) EnumerableExpansions (formato) EntrySelectedBy elemento per elemento SelectionCondition EnumerableExpansion (formato) per EntrySelectedBy per Elemento SelectionSetName EnumerableExpansion (formato) per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="218b7-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="218b7-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="218b7-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="218b7-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="218b7-107">Attributes and Elements</span></span>

<span data-ttu-id="218b7-108">Le sezioni seguenti descrivono l'elemento padre di attributi e gli elementi figlio di `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="218b7-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="218b7-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="218b7-109">Attributes</span></span>

<span data-ttu-id="218b7-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="218b7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="218b7-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="218b7-111">Child Elements</span></span>

<span data-ttu-id="218b7-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="218b7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="218b7-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="218b7-113">Parent Elements</span></span>

|<span data-ttu-id="218b7-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="218b7-114">Element</span></span>|<span data-ttu-id="218b7-115">Description</span><span class="sxs-lookup"><span data-stu-id="218b7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="218b7-116">Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="218b7-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="218b7-117">Definisce la condizione che deve essere presente per espandere gli oggetti dell'insieme di questa definizione.</span><span class="sxs-lookup"><span data-stu-id="218b7-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="218b7-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="218b7-118">Text Value</span></span>

<span data-ttu-id="218b7-119">Specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="218b7-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="218b7-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="218b7-120">Remarks</span></span>

<span data-ttu-id="218b7-121">La condizione di selezione è possibile specificare un set di selezione o un tipo .NET, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="218b7-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="218b7-122">Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="218b7-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="218b7-123">Set di selezione sono i gruppi di oggetti .NET che possono essere usati da qualsiasi vista che definisce il file di formattazione comuni.</span><span class="sxs-lookup"><span data-stu-id="218b7-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="218b7-124">Per altre informazioni sulla creazione e che fanno riferimento a set di selezione, vedere [definizione di selezione imposta](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="218b7-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="218b7-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="218b7-125">See Also</span></span>

[<span data-ttu-id="218b7-126">La definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="218b7-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="218b7-127">Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="218b7-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="218b7-128">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="218b7-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
