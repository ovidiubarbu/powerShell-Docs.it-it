---
title: Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: fd708473d04a76bcf6cf3a8f8278e1d15fb9addf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858657"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="2f9bb-102">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="2f9bb-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="2f9bb-103">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="2f9bb-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="2f9bb-104">Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene usata la voce dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="2f9bb-104">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="2f9bb-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) elemento ListEntries (formato) elemento ListEntry (formato) EntrySelectedBy elemento di configurazione per elemento SelectionCondition ListEntry (formato) EntrySelectedBy per elemento ScriptBlock ListEntry (formato) per SelectionCondition per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="2f9bb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2f9bb-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2f9bb-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2f9bb-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="2f9bb-107">Attributes and Elements</span></span>

<span data-ttu-id="2f9bb-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="2f9bb-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2f9bb-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="2f9bb-109">Attributes</span></span>

<span data-ttu-id="2f9bb-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2f9bb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2f9bb-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="2f9bb-111">Child Elements</span></span>

<span data-ttu-id="2f9bb-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="2f9bb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2f9bb-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="2f9bb-113">Parent Elements</span></span>

|<span data-ttu-id="2f9bb-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="2f9bb-114">Element</span></span>|<span data-ttu-id="2f9bb-115">Description</span><span class="sxs-lookup"><span data-stu-id="2f9bb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2f9bb-116">Elemento SelectionCondition per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="2f9bb-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="2f9bb-117">Definisce la condizione che deve essere presente per questa voce di elenco da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="2f9bb-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2f9bb-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="2f9bb-118">Text Value</span></span>

<span data-ttu-id="2f9bb-119">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="2f9bb-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="2f9bb-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="2f9bb-120">Remarks</span></span>

<span data-ttu-id="2f9bb-121">La condizione di selezione è necessario specificare un nome di script o proprietà uno minimi per valutare, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="2f9bb-121">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="2f9bb-122">(Per altre informazioni sull'utilizzo di condizioni di selezione, vedere [definizione di condizioni per quando una voce di visualizzazione o viene usato l'elemento](./defining-conditions-for-displaying-data.md).)</span><span class="sxs-lookup"><span data-stu-id="2f9bb-122">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="2f9bb-123">Per altre informazioni su altri componenti di una visualizzazione elenco, vedere [visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="2f9bb-123">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2f9bb-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2f9bb-124">See Also</span></span>

[<span data-ttu-id="2f9bb-125">Elemento ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="2f9bb-125">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="2f9bb-126">Elemento PropertyName per SelectionCondition per EmtrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="2f9bb-126">PropertyName Element for SelectionCondition for EmtrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="2f9bb-127">Elemento SelectionCondition per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="2f9bb-127">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="2f9bb-128">Visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="2f9bb-128">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="2f9bb-129">La definizione delle condizioni per quando viene utilizzata una voce di visualizzazione o un elemento</span><span class="sxs-lookup"><span data-stu-id="2f9bb-129">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2f9bb-130">La scrittura di un metodo di formattazione di Windows PowerShell e i tipi di File</span><span class="sxs-lookup"><span data-stu-id="2f9bb-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
