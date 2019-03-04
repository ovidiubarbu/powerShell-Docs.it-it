---
title: Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855577"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="8cb79-102">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="8cb79-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="8cb79-103">Specifica il blocco di script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="8cb79-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="8cb79-104">Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene usata la voce della tabella.</span><span class="sxs-lookup"><span data-stu-id="8cb79-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="8cb79-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento di configurazione per TableRowEntry (formato) Elemento SelectionCondition per EntrySelectedBy per elemento ScriptBlock TableRowEntry (formato) per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8cb79-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8cb79-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8cb79-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8cb79-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="8cb79-107">Attributes and Elements</span></span>

<span data-ttu-id="8cb79-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="8cb79-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8cb79-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="8cb79-109">Attributes</span></span>

<span data-ttu-id="8cb79-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="8cb79-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8cb79-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="8cb79-111">Child Elements</span></span>

<span data-ttu-id="8cb79-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="8cb79-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8cb79-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="8cb79-113">Parent Elements</span></span>

|<span data-ttu-id="8cb79-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="8cb79-114">Element</span></span>|<span data-ttu-id="8cb79-115">Description</span><span class="sxs-lookup"><span data-stu-id="8cb79-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8cb79-116">Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8cb79-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="8cb79-117">Definisce la condizione che deve essere presente per questa voce di tabella da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="8cb79-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8cb79-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="8cb79-118">Text Value</span></span>

<span data-ttu-id="8cb79-119">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="8cb79-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="8cb79-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="8cb79-120">Remarks</span></span>

<span data-ttu-id="8cb79-121">La condizione di selezione è necessario specificare almeno un nome di proprietà o di blocco di script, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="8cb79-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="8cb79-122">Per altre informazioni su come usare le condizioni di selezione, vedere [definizione di condizioni per quando una voce di visualizzazione o viene usato l'elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="8cb79-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="8cb79-123">Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="8cb79-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8cb79-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8cb79-124">See Also</span></span>

[<span data-ttu-id="8cb79-125">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="8cb79-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8cb79-126">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="8cb79-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="8cb79-127">Elemento PropertyName per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8cb79-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="8cb79-128">Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8cb79-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="8cb79-129">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="8cb79-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
