---
title: Elemento PropertyName per SelectionCondition per EntrySelectedBy per TableRowEntry (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860987"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="005e6-102">Elemento PropertyName per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="005e6-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="005e6-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="005e6-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="005e6-104">Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene usata la voce della tabella.</span><span class="sxs-lookup"><span data-stu-id="005e6-104">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="005e6-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento di configurazione per TableRowEntry (formato) Elemento SelectionCondition per EntrySelectedBy per elemento PropertyName TableRowEntry (formato) per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="005e6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="005e6-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="005e6-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="005e6-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="005e6-107">Attributes and Elements</span></span>

<span data-ttu-id="005e6-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="005e6-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="005e6-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="005e6-109">Attributes</span></span>

<span data-ttu-id="005e6-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="005e6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="005e6-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="005e6-111">Child Elements</span></span>

<span data-ttu-id="005e6-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="005e6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="005e6-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="005e6-113">Parent Elements</span></span>

|<span data-ttu-id="005e6-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="005e6-114">Element</span></span>|<span data-ttu-id="005e6-115">Description</span><span class="sxs-lookup"><span data-stu-id="005e6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="005e6-116">Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="005e6-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="005e6-117">Definisce la condizione che deve essere presente per questa voce di tabella da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="005e6-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="005e6-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="005e6-118">Text Value</span></span>

<span data-ttu-id="005e6-119">Specificare il nome della proprietà .NET.</span><span class="sxs-lookup"><span data-stu-id="005e6-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="005e6-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="005e6-120">Remarks</span></span>

<span data-ttu-id="005e6-121">La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="005e6-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="005e6-122">Per altre informazioni sull'utilizzo di condizioni di selezione, vedere [definizione di condizioni per quando una voce di visualizzazione o viene usato l'elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="005e6-122">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="005e6-123">Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="005e6-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="005e6-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="005e6-124">See Also</span></span>

[<span data-ttu-id="005e6-125">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="005e6-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="005e6-126">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="005e6-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="005e6-127">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="005e6-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="005e6-128">Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="005e6-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="005e6-129">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="005e6-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
