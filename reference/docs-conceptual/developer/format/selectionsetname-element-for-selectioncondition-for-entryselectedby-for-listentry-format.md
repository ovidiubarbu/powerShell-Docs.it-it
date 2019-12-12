---
title: Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per ListEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368400"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="5ce38-102">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="5ce38-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="5ce38-103">Specifica il set di tipi .NET che attivano la condizione.</span><span class="sxs-lookup"><span data-stu-id="5ce38-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="5ce38-104">Quando uno dei tipi in questo set è presente, la condizione viene soddisfatta e l'oggetto viene visualizzato utilizzando questa definizione della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="5ce38-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="5ce38-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento EntrySelectedBy per ListEntry (Format) SelectionCondition elemento per EntrySelectedBy per ListEntry (Format) elemento SelectionSetName per SelectionCondition per EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5ce38-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5ce38-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5ce38-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5ce38-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="5ce38-107">Attributes and Elements</span></span>

<span data-ttu-id="5ce38-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="5ce38-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5ce38-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="5ce38-109">Attributes</span></span>

<span data-ttu-id="5ce38-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="5ce38-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5ce38-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="5ce38-111">Child Elements</span></span>

<span data-ttu-id="5ce38-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="5ce38-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5ce38-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="5ce38-113">Parent Elements</span></span>

|<span data-ttu-id="5ce38-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ce38-114">Element</span></span>|<span data-ttu-id="5ce38-115">Description</span><span class="sxs-lookup"><span data-stu-id="5ce38-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ce38-116">Elemento SelectionCondition per EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5ce38-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="5ce38-117">Definisce la condizione che deve esistere per utilizzare questa definizione della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="5ce38-117">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5ce38-118">Valore testo</span><span class="sxs-lookup"><span data-stu-id="5ce38-118">Text Value</span></span>

<span data-ttu-id="5ce38-119">Consente di specificare il nome del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="5ce38-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ce38-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="5ce38-120">Remarks</span></span>

<span data-ttu-id="5ce38-121">La condizione di selezione può specificare un set di selezione o un tipo .NET, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="5ce38-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="5ce38-122">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5ce38-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="5ce38-123">I set di selezione sono gruppi comuni di oggetti .NET che possono essere utilizzati da qualsiasi visualizzazione definita dal file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="5ce38-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="5ce38-124">Per ulteriori informazioni sulla creazione e il riferimento a set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="5ce38-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="5ce38-125">Per ulteriori informazioni sugli altri componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="5ce38-125">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5ce38-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5ce38-126">See Also</span></span>

[<span data-ttu-id="5ce38-127">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="5ce38-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="5ce38-128">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="5ce38-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="5ce38-129">Elemento SelectionCondition per EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5ce38-129">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="5ce38-130">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="5ce38-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
