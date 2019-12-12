---
title: Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368580"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="f8118-102">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f8118-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="f8118-103">Specifica il blocco di script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="f8118-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="f8118-104">Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzata la voce della tabella.</span><span class="sxs-lookup"><span data-stu-id="f8118-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="f8118-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) elemento EntrySelectedBy per TableRowEntry (Format) Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format) ScriptBlock elemento per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f8118-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f8118-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f8118-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f8118-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="f8118-107">Attributes and Elements</span></span>

<span data-ttu-id="f8118-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="f8118-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f8118-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="f8118-109">Attributes</span></span>

<span data-ttu-id="f8118-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f8118-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f8118-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f8118-111">Child Elements</span></span>

<span data-ttu-id="f8118-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f8118-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f8118-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f8118-113">Parent Elements</span></span>

|<span data-ttu-id="f8118-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="f8118-114">Element</span></span>|<span data-ttu-id="f8118-115">Description</span><span class="sxs-lookup"><span data-stu-id="f8118-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f8118-116">Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f8118-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="f8118-117">Definisce la condizione che deve esistere per la voce della tabella da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="f8118-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f8118-118">Valore testo</span><span class="sxs-lookup"><span data-stu-id="f8118-118">Text Value</span></span>

<span data-ttu-id="f8118-119">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="f8118-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="f8118-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f8118-120">Remarks</span></span>

<span data-ttu-id="f8118-121">La condizione di selezione deve specificare almeno un blocco di script o un nome di proprietà, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="f8118-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="f8118-122">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per l'utilizzo di una voce o di un elemento della visualizzazione](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f8118-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f8118-123">Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f8118-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f8118-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f8118-124">See Also</span></span>

[<span data-ttu-id="f8118-125">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="f8118-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f8118-126">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="f8118-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f8118-127">Elemento PropertyName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f8118-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="f8118-128">Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f8118-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="f8118-129">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8118-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
