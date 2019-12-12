---
title: Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: b65d953169f6daf15fb617ce4d0303cf4cb584ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368590"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="54cd0-102">Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="54cd0-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="54cd0-103">Specifica lo script che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="54cd0-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="54cd0-104">Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzata la voce dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="54cd0-104">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="54cd0-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento EntrySelectedBy per ListEntry (Format) SelectionCondition elemento per EntrySelectedBy per ListEntry (Format) elemento ScriptBlock per SelectionCondition per EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="54cd0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="54cd0-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="54cd0-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="54cd0-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="54cd0-107">Attributes and Elements</span></span>

<span data-ttu-id="54cd0-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="54cd0-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="54cd0-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="54cd0-109">Attributes</span></span>

<span data-ttu-id="54cd0-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="54cd0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="54cd0-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="54cd0-111">Child Elements</span></span>

<span data-ttu-id="54cd0-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="54cd0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="54cd0-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="54cd0-113">Parent Elements</span></span>

|<span data-ttu-id="54cd0-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="54cd0-114">Element</span></span>|<span data-ttu-id="54cd0-115">Description</span><span class="sxs-lookup"><span data-stu-id="54cd0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="54cd0-116">Elemento SelectionCondition per EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="54cd0-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="54cd0-117">Definisce la condizione che deve esistere affinché questa voce di elenco venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="54cd0-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="54cd0-118">Valore testo</span><span class="sxs-lookup"><span data-stu-id="54cd0-118">Text Value</span></span>

<span data-ttu-id="54cd0-119">Specificare lo script che viene valutato.</span><span class="sxs-lookup"><span data-stu-id="54cd0-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="54cd0-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="54cd0-120">Remarks</span></span>

<span data-ttu-id="54cd0-121">Per valutare la condizione di selezione, è necessario specificare almeno uno script o un nome di proprietà, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="54cd0-121">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="54cd0-122">Per ulteriori informazioni sul modo in cui è possibile utilizzare le condizioni di selezione, vedere [definizione di condizioni per l'utilizzo di una voce di visualizzazione o di un elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="54cd0-122">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="54cd0-123">Per ulteriori informazioni sugli altri componenti di una visualizzazione elenco, vedere [visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="54cd0-123">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="54cd0-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="54cd0-124">See Also</span></span>

[<span data-ttu-id="54cd0-125">Elemento ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="54cd0-125">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="54cd0-126">Elemento PropertyName per SelectionCondition per EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="54cd0-126">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="54cd0-127">Elemento SelectionCondition per EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="54cd0-127">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="54cd0-128">Visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="54cd0-128">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="54cd0-129">Definizione delle condizioni per l'utilizzo di una voce o un elemento della visualizzazione</span><span class="sxs-lookup"><span data-stu-id="54cd0-129">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="54cd0-130">Scrittura di un file di formattazione e di tipi di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="54cd0-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
