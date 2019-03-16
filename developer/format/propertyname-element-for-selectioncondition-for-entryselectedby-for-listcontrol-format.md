---
title: Elemento PropertyName per SelectionCondition per EntrySelectedBy per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059015"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="aa7ff-102">Elemento PropertyName per SelectionCondition per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="aa7ff-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="aa7ff-103">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="aa7ff-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="aa7ff-104">Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene usata la voce dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="aa7ff-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="aa7ff-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) elemento ListEntries (formato) elemento ListEntry (formato) EntrySelectedBy elemento di configurazione per elemento SelectionCondition ListEntry (formato) EntrySelectedBy per elemento PropertyName ListEntry (formato) per SelectionCondition per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="aa7ff-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aa7ff-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="aa7ff-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aa7ff-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="aa7ff-107">Attributes and Elements</span></span>

<span data-ttu-id="aa7ff-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="aa7ff-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aa7ff-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="aa7ff-109">Attributes</span></span>

<span data-ttu-id="aa7ff-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="aa7ff-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aa7ff-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="aa7ff-111">Child Elements</span></span>

<span data-ttu-id="aa7ff-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="aa7ff-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="aa7ff-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="aa7ff-113">Parent Elements</span></span>

|<span data-ttu-id="aa7ff-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="aa7ff-114">Element</span></span>|<span data-ttu-id="aa7ff-115">Description</span><span class="sxs-lookup"><span data-stu-id="aa7ff-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aa7ff-116">Elemento SelectionCondition per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="aa7ff-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="aa7ff-117">Definisce la condizione che deve essere presente per questa voce di elenco da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="aa7ff-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="aa7ff-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="aa7ff-118">Text Value</span></span>

<span data-ttu-id="aa7ff-119">Specificare il nome della proprietà .NET.</span><span class="sxs-lookup"><span data-stu-id="aa7ff-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="aa7ff-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="aa7ff-120">Remarks</span></span>

<span data-ttu-id="aa7ff-121">La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="aa7ff-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="aa7ff-122">Per altre informazioni su come usare le condizioni di selezione, vedere [definizione di condizioni per quando una voce di visualizzazione o viene usato l'elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="aa7ff-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="aa7ff-123">Per altre informazioni sugli altri componenti di una visualizzazione elenco, vedere [creazione di visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="aa7ff-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aa7ff-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="aa7ff-124">See Also</span></span>

[<span data-ttu-id="aa7ff-125">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="aa7ff-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="aa7ff-126">La definizione delle condizioni per i dati quando viene visualizzata</span><span class="sxs-lookup"><span data-stu-id="aa7ff-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="aa7ff-127">Elemento ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="aa7ff-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="aa7ff-128">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="aa7ff-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="aa7ff-129">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa7ff-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
