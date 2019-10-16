---
title: Elemento TypeName per SelectionCondition per EntrySelectedBy per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368060"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="df385-102">Elemento TypeName per SelectionCondition per EntrySelectedBy per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="df385-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="df385-103">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="df385-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="df385-104">Quando questo tipo è presente, viene usata la definizione.</span><span class="sxs-lookup"><span data-stu-id="df385-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="df385-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) elemento EntrySelectedBy per WideEntry (Format) SelectionCondition elemento per EntrySelectedBy per WideEntry (Format) TypeName elemento per SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="df385-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="df385-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="df385-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="df385-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="df385-107">Attributes and Elements</span></span>

<span data-ttu-id="df385-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="df385-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="df385-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="df385-109">Attributes</span></span>

<span data-ttu-id="df385-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="df385-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="df385-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="df385-111">Child Elements</span></span>

<span data-ttu-id="df385-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="df385-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="df385-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="df385-113">Parent Elements</span></span>

|<span data-ttu-id="df385-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="df385-114">Element</span></span>|<span data-ttu-id="df385-115">Description</span><span class="sxs-lookup"><span data-stu-id="df385-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="df385-116">Elemento SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="df385-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="df385-117">Definisce la condizione che deve esistere affinché questa voce di tipo Wide venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="df385-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="df385-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="df385-118">Text Value</span></span>

<span data-ttu-id="df385-119">Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="df385-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="df385-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="df385-120">Remarks</span></span>

<span data-ttu-id="df385-121">La condizione di selezione può specificare un tipo .NET o un set di selezione, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="df385-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="df385-122">Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="df385-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="df385-123">Per ulteriori informazioni su altri componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="df385-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="df385-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="df385-124">See Also</span></span>

[<span data-ttu-id="df385-125">Creazione di una visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="df385-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="df385-126">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="df385-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="df385-127">Elemento SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="df385-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="df385-128">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="df385-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="df385-129">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="df385-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
