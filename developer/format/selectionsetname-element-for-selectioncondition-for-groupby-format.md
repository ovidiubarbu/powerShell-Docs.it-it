---
title: Elemento SelectionSetName per SelectionCondition per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063767"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="cc45a-102">Elemento SelectionSetName per SelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cc45a-102">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="cc45a-103">Specifica il set di tipi .NET che attivano la condizione.</span><span class="sxs-lookup"><span data-stu-id="cc45a-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="cc45a-104">Quando uno dei tipi in questo set è presentano, viene soddisfatta la condizione e l'oggetto viene visualizzato tramite questo controllo.</span><span class="sxs-lookup"><span data-stu-id="cc45a-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="cc45a-105">Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="cc45a-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="cc45a-106">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per elemento EntrySelectedBy GroupBy (formato) per CustomEntry per elemento SelectionCondition GroupBy (formato) per EntrySelectedBy per elemento SelectionSetName GroupBy (formato) per SelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cc45a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cc45a-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="cc45a-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cc45a-108">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="cc45a-108">Attributes and Elements</span></span>

<span data-ttu-id="cc45a-109">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="cc45a-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cc45a-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="cc45a-110">Attributes</span></span>

<span data-ttu-id="cc45a-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="cc45a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cc45a-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="cc45a-112">Child Elements</span></span>

<span data-ttu-id="cc45a-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="cc45a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cc45a-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="cc45a-114">Parent Elements</span></span>

|<span data-ttu-id="cc45a-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="cc45a-115">Element</span></span>|<span data-ttu-id="cc45a-116">Description</span><span class="sxs-lookup"><span data-stu-id="cc45a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cc45a-117">Elemento SelectionCondition per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cc45a-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="cc45a-118">Definisce una condizione che deve essere presente per la definizione di controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="cc45a-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cc45a-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="cc45a-119">Text Value</span></span>

<span data-ttu-id="cc45a-120">Specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="cc45a-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="cc45a-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="cc45a-121">Remarks</span></span>

<span data-ttu-id="cc45a-122">Set di selezione sono i gruppi di oggetti .NET che possono essere usati da qualsiasi vista che definisce il file di formattazione comuni.</span><span class="sxs-lookup"><span data-stu-id="cc45a-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="cc45a-123">Per altre informazioni sulla creazione e che fanno riferimento a set di selezione, vedere [definizione di selezione imposta](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="cc45a-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="cc45a-124">Quando questo elemento viene specificato, non è possibile specificare il [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="cc45a-124">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="cc45a-125">Per altre informazioni sulla definizione di condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="cc45a-125">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cc45a-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cc45a-126">See Also</span></span>

[<span data-ttu-id="cc45a-127">Elemento TypeName per SelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cc45a-127">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="cc45a-128">Elemento SelectionCondition per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cc45a-128">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="cc45a-129">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="cc45a-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="cc45a-130">La definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="cc45a-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="cc45a-131">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="cc45a-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
