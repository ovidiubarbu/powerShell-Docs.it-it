---
title: Elemento PropertyName per SelectionCondition per EntrySelectedBy per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362290"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="8c544-102">Elemento PropertyName per SelectionCondition per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="8c544-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="8c544-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="8c544-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="8c544-104">Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene usata la voce dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="8c544-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="8c544-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento EntrySelectedBy per ListEntry (Format) SelectionCondition elemento per EntrySelectedBy per l'elemento ListEntry (Format) PropertyName per SelectionCondition per EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="8c544-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8c544-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8c544-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8c544-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="8c544-107">Attributes and Elements</span></span>

<span data-ttu-id="8c544-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="8c544-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8c544-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="8c544-109">Attributes</span></span>

<span data-ttu-id="8c544-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="8c544-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8c544-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="8c544-111">Child Elements</span></span>

<span data-ttu-id="8c544-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="8c544-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8c544-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="8c544-113">Parent Elements</span></span>

|<span data-ttu-id="8c544-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="8c544-114">Element</span></span>|<span data-ttu-id="8c544-115">Description</span><span class="sxs-lookup"><span data-stu-id="8c544-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8c544-116">Elemento SelectionCondition per EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="8c544-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="8c544-117">Definisce la condizione che deve esistere affinché questa voce di elenco venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="8c544-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8c544-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="8c544-118">Text Value</span></span>

<span data-ttu-id="8c544-119">Specificare il nome della proprietà .NET.</span><span class="sxs-lookup"><span data-stu-id="8c544-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="8c544-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="8c544-120">Remarks</span></span>

<span data-ttu-id="8c544-121">La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="8c544-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="8c544-122">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per l'utilizzo di una voce o di un elemento della visualizzazione](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="8c544-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="8c544-123">Per ulteriori informazioni sugli altri componenti di una visualizzazione elenco, vedere [creazione](./creating-a-list-view.md)di una visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="8c544-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8c544-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8c544-124">See Also</span></span>

[<span data-ttu-id="8c544-125">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="8c544-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="8c544-126">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="8c544-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="8c544-127">Elemento ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="8c544-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="8c544-128">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="8c544-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="8c544-129">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c544-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
