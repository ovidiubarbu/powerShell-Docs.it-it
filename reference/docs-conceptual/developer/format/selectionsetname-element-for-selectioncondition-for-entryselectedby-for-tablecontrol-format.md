---
title: Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361920"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="26f3a-102">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="26f3a-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="26f3a-103">Specifica il set di tipi .NET che attivano la condizione.</span><span class="sxs-lookup"><span data-stu-id="26f3a-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="26f3a-104">Quando uno dei tipi in questo set è presente, la condizione viene soddisfatta e l'oggetto viene visualizzato utilizzando questa definizione della vista tabella.</span><span class="sxs-lookup"><span data-stu-id="26f3a-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="26f3a-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) elemento EntrySelectedBy per TableRowEntry (Format) Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format) SelectionSetName elemento per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="26f3a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="26f3a-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="26f3a-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="26f3a-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="26f3a-107">Attributes and Elements</span></span>

<span data-ttu-id="26f3a-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="26f3a-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="26f3a-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="26f3a-109">Attributes</span></span>

<span data-ttu-id="26f3a-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="26f3a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="26f3a-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="26f3a-111">Child Elements</span></span>

<span data-ttu-id="26f3a-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="26f3a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="26f3a-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="26f3a-113">Parent Elements</span></span>

|<span data-ttu-id="26f3a-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="26f3a-114">Element</span></span>|<span data-ttu-id="26f3a-115">Description</span><span class="sxs-lookup"><span data-stu-id="26f3a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="26f3a-116">Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="26f3a-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="26f3a-117">Definisce la condizione che deve esistere per utilizzare per questa definizione della visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="26f3a-117">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="26f3a-118">Valore testo</span><span class="sxs-lookup"><span data-stu-id="26f3a-118">Text Value</span></span>

<span data-ttu-id="26f3a-119">Consente di specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="26f3a-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="26f3a-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="26f3a-120">Remarks</span></span>

<span data-ttu-id="26f3a-121">La condizione di selezione può specificare un set di selezione o un tipo .NET, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="26f3a-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="26f3a-122">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="26f3a-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="26f3a-123">I set di selezione sono gruppi comuni di oggetti .NET che possono essere utilizzati da qualsiasi visualizzazione definita dal file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="26f3a-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="26f3a-124">Per ulteriori informazioni sulla creazione e il riferimento a set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="26f3a-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="26f3a-125">Per ulteriori informazioni su altri componenti di una visualizzazione estesa, vedere [creazione di una vista tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="26f3a-125">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="26f3a-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="26f3a-126">See Also</span></span>

[<span data-ttu-id="26f3a-127">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="26f3a-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="26f3a-128">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="26f3a-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="26f3a-129">Elemento TypeName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="26f3a-129">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="26f3a-130">Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="26f3a-130">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="26f3a-131">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="26f3a-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
