---
title: Elemento PropertyName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365000"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="3f2de-102">Elemento PropertyName per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3f2de-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="3f2de-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="3f2de-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="3f2de-104">Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene utilizzata la voce della tabella.</span><span class="sxs-lookup"><span data-stu-id="3f2de-104">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="3f2de-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) elemento EntrySelectedBy per TableRowEntry (Format) Elemento SelectionCondition per EntrySelectedBy per l'elemento TableRowEntry (Format) PropertyName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="3f2de-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3f2de-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3f2de-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3f2de-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="3f2de-107">Attributes and Elements</span></span>

<span data-ttu-id="3f2de-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="3f2de-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3f2de-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="3f2de-109">Attributes</span></span>

<span data-ttu-id="3f2de-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="3f2de-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3f2de-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="3f2de-111">Child Elements</span></span>

<span data-ttu-id="3f2de-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="3f2de-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3f2de-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="3f2de-113">Parent Elements</span></span>

|<span data-ttu-id="3f2de-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="3f2de-114">Element</span></span>|<span data-ttu-id="3f2de-115">Description</span><span class="sxs-lookup"><span data-stu-id="3f2de-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3f2de-116">Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="3f2de-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="3f2de-117">Definisce la condizione che deve esistere per la voce della tabella da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="3f2de-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3f2de-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="3f2de-118">Text Value</span></span>

<span data-ttu-id="3f2de-119">Specificare il nome della proprietà .NET.</span><span class="sxs-lookup"><span data-stu-id="3f2de-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="3f2de-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="3f2de-120">Remarks</span></span>

<span data-ttu-id="3f2de-121">La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="3f2de-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="3f2de-122">Per ulteriori informazioni sul modo in cui è possibile utilizzare le condizioni di selezione, vedere [definizione di condizioni per l'utilizzo di una voce o di un elemento della visualizzazione](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3f2de-122">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="3f2de-123">Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="3f2de-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3f2de-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3f2de-124">See Also</span></span>

[<span data-ttu-id="3f2de-125">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="3f2de-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="3f2de-126">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="3f2de-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="3f2de-127">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="3f2de-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="3f2de-128">Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="3f2de-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="3f2de-129">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f2de-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
