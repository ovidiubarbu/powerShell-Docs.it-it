---
title: Elemento TypeName per SelectionCondition per EntrySelectedBy per WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083808"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="43de9-102">Elemento TypeName per SelectionCondition per EntrySelectedBy per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="43de9-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="43de9-103">Specifica un tipo .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="43de9-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="43de9-104">Quando questo tipo è presente, la definizione viene utilizzata.</span><span class="sxs-lookup"><span data-stu-id="43de9-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="43de9-105">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento di configurazione per elemento SelectionCondition WideEntry (formato) per EntrySelectedBy per elemento TypeName WideEntry (formato) per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="43de9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="43de9-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="43de9-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="43de9-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="43de9-107">Attributes and Elements</span></span>

<span data-ttu-id="43de9-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="43de9-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="43de9-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="43de9-109">Attributes</span></span>

<span data-ttu-id="43de9-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="43de9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="43de9-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="43de9-111">Child Elements</span></span>

<span data-ttu-id="43de9-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="43de9-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="43de9-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="43de9-113">Parent Elements</span></span>

|<span data-ttu-id="43de9-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="43de9-114">Element</span></span>|<span data-ttu-id="43de9-115">Description</span><span class="sxs-lookup"><span data-stu-id="43de9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="43de9-116">Elemento SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="43de9-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="43de9-117">Definisce la condizione che deve essere presente per questa voce wide da usare.</span><span class="sxs-lookup"><span data-stu-id="43de9-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="43de9-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="43de9-118">Text Value</span></span>

<span data-ttu-id="43de9-119">Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="43de9-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="43de9-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="43de9-120">Remarks</span></span>

<span data-ttu-id="43de9-121">La condizione di selezione può includere un tipo .NET o una selezione set, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="43de9-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="43de9-122">Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="43de9-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="43de9-123">Per altre informazioni sugli altri componenti di una visualizzazione più ampia, vedere [creazione di una visualizzazione più ampia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="43de9-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="43de9-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="43de9-124">See Also</span></span>

[<span data-ttu-id="43de9-125">Creazione di una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="43de9-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="43de9-126">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="43de9-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="43de9-127">Elemento SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="43de9-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="43de9-128">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="43de9-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="43de9-129">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="43de9-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
