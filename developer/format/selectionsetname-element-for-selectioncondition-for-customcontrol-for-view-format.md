---
title: Elemento SelectionSetName per SelectionCondition per CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862767"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="56dc5-102">Elemento SelectionSetName per SelectionCondition per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="56dc5-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="56dc5-103">Specifica il set di tipi .NET che attivano la condizione.</span><span class="sxs-lookup"><span data-stu-id="56dc5-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="56dc5-104">Quando uno dei tipi in questo set è presentano, viene soddisfatta la condizione e l'oggetto viene visualizzato l'utilizzo di questo controllo.</span><span class="sxs-lookup"><span data-stu-id="56dc5-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="56dc5-105">Questo elemento viene usato quando si definisce una vista di controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="56dc5-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="56dc5-106">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per EntrySelectedBy visualizzazione (formato) Elemento per CustomEntry per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="56dc5-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="56dc5-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="56dc5-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="56dc5-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="56dc5-108">Attributes and Elements</span></span>

<span data-ttu-id="56dc5-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="56dc5-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="56dc5-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="56dc5-110">Attributes</span></span>

<span data-ttu-id="56dc5-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="56dc5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="56dc5-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="56dc5-112">Child Elements</span></span>

<span data-ttu-id="56dc5-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="56dc5-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="56dc5-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="56dc5-114">Parent Elements</span></span>

|<span data-ttu-id="56dc5-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="56dc5-115">Element</span></span>|<span data-ttu-id="56dc5-116">Description</span><span class="sxs-lookup"><span data-stu-id="56dc5-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="56dc5-117">Elemento SelectionCondition per EntrySelectedBy per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="56dc5-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="56dc5-118">Definisce una condizione che deve essere presente per la definizione di controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="56dc5-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="56dc5-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="56dc5-119">Text Value</span></span>

<span data-ttu-id="56dc5-120">Specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="56dc5-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="56dc5-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="56dc5-121">Remarks</span></span>

<span data-ttu-id="56dc5-122">Set di selezione sono i gruppi di oggetti .NET che possono essere usati da qualsiasi vista che definisce il file di formattazione comuni.</span><span class="sxs-lookup"><span data-stu-id="56dc5-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="56dc5-123">Per altre informazioni sulla creazione e che fanno riferimento a set di selezione, vedere [definizione imposta di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="56dc5-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="56dc5-124">La condizione di selezione è possibile specificare un set di selezione o un tipo .NET, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="56dc5-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="56dc5-125">Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="56dc5-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="56dc5-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="56dc5-126">See Also</span></span>

[<span data-ttu-id="56dc5-127">Elemento SelectionCondition per EntrySelectedBy per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="56dc5-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="56dc5-128">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="56dc5-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="56dc5-129">La definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="56dc5-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="56dc5-130">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="56dc5-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
