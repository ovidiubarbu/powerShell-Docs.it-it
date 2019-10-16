---
title: Elemento SelectionSetName per SelectionCondition per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368270"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="821b8-102">Elemento SelectionSetName per SelectionCondition per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="821b8-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="821b8-103">Specifica il set di tipi .NET che attivano la condizione.</span><span class="sxs-lookup"><span data-stu-id="821b8-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="821b8-104">Quando uno dei tipi in questo set è presente, la condizione viene soddisfatta e l'oggetto viene visualizzato utilizzando questo controllo.</span><span class="sxs-lookup"><span data-stu-id="821b8-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="821b8-105">Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.</span><span class="sxs-lookup"><span data-stu-id="821b8-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="821b8-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per l'elemento View (Format) CustomEntry per CustomEntries per View (Format) EntrySelectedBy Elemento per CustomEntry per View (Format)</span><span class="sxs-lookup"><span data-stu-id="821b8-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="821b8-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="821b8-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="821b8-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="821b8-108">Attributes and Elements</span></span>

<span data-ttu-id="821b8-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="821b8-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="821b8-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="821b8-110">Attributes</span></span>

<span data-ttu-id="821b8-111">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="821b8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="821b8-112">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="821b8-112">Child Elements</span></span>

<span data-ttu-id="821b8-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="821b8-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="821b8-114">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="821b8-114">Parent Elements</span></span>

|<span data-ttu-id="821b8-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="821b8-115">Element</span></span>|<span data-ttu-id="821b8-116">Description</span><span class="sxs-lookup"><span data-stu-id="821b8-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="821b8-117">Elemento SelectionCondition per EntrySelectedBy per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="821b8-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="821b8-118">Definisce una condizione che deve esistere per la definizione del controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="821b8-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="821b8-119">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="821b8-119">Text Value</span></span>

<span data-ttu-id="821b8-120">Consente di specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="821b8-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="821b8-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="821b8-121">Remarks</span></span>

<span data-ttu-id="821b8-122">I set di selezione sono gruppi comuni di oggetti .NET che possono essere utilizzati da qualsiasi visualizzazione definita dal file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="821b8-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="821b8-123">Per ulteriori informazioni sulla creazione e il riferimento a set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="821b8-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="821b8-124">La condizione di selezione può specificare un set di selezione o un tipo .NET, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="821b8-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="821b8-125">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="821b8-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="821b8-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="821b8-126">See Also</span></span>

[<span data-ttu-id="821b8-127">Elemento SelectionCondition per EntrySelectedBy per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="821b8-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="821b8-128">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="821b8-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="821b8-129">Definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="821b8-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="821b8-130">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="821b8-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
