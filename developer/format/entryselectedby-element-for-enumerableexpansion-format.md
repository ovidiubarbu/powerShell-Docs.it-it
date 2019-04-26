---
title: Elemento EntrySelectedBy per EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066210"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="637ff-102">Elemento EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="637ff-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="637ff-103">Definisce i tipi .NET che usano questa definizione o la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="637ff-103">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="637ff-104">Configurazione (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) elemento EnumerableExpansion (formato) EntrySelectedBy elemento dell'elemento EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="637ff-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="637ff-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="637ff-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="637ff-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="637ff-106">Attributes and Elements</span></span>

<span data-ttu-id="637ff-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="637ff-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="637ff-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="637ff-108">Attributes</span></span>

<span data-ttu-id="637ff-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="637ff-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="637ff-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="637ff-110">Child Elements</span></span>

|<span data-ttu-id="637ff-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="637ff-111">Element</span></span>|<span data-ttu-id="637ff-112">Description</span><span class="sxs-lookup"><span data-stu-id="637ff-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="637ff-113">Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="637ff-113">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="637ff-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="637ff-114">Optional element.</span></span><br /><br /> <span data-ttu-id="637ff-115">Definisce la condizione che deve essere presente per espandere gli oggetti dell'insieme di questa definizione.</span><span class="sxs-lookup"><span data-stu-id="637ff-115">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="637ff-116">Elemento SelectionSetName per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="637ff-116">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="637ff-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="637ff-117">Optional element.</span></span><br /><br /> <span data-ttu-id="637ff-118">Specifica un set di tipi .NET che usano questa definizione del modo in cui gli oggetti di raccolta vengono espansi.</span><span class="sxs-lookup"><span data-stu-id="637ff-118">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="637ff-119">Elemento TypeName per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="637ff-119">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="637ff-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="637ff-120">Optional element.</span></span><br /><br /> <span data-ttu-id="637ff-121">Specifica un tipo .NET che usa questa definizione del modo in cui gli oggetti di raccolta vengono espansi.</span><span class="sxs-lookup"><span data-stu-id="637ff-121">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="637ff-122">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="637ff-122">Parent Elements</span></span>

|<span data-ttu-id="637ff-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="637ff-123">Element</span></span>|<span data-ttu-id="637ff-124">Description</span><span class="sxs-lookup"><span data-stu-id="637ff-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="637ff-125">Elemento EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="637ff-125">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="637ff-126">Definisce una raccolta .NET come specifica gli oggetti vengono espansi quando vengono visualizzati in una vista.</span><span class="sxs-lookup"><span data-stu-id="637ff-126">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="637ff-127">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="637ff-127">Remarks</span></span>

<span data-ttu-id="637ff-128">È necessario specificare almeno un tipo, il set di selezione o condizione di selezione per una voce di definizione.</span><span class="sxs-lookup"><span data-stu-id="637ff-128">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="637ff-129">Non è definito alcun limite massimo al numero di elementi figlio che è possibile usare.</span><span class="sxs-lookup"><span data-stu-id="637ff-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="637ff-130">Condizioni di selezione vengono usate per definire una condizione che deve essere presente per la definizione da usare, ad esempio quando un oggetto dispone di una proprietà specifica o che restituisce un valore della proprietà specifica o uno script `true`.</span><span class="sxs-lookup"><span data-stu-id="637ff-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="637ff-131">Per altre informazioni sulle condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="637ff-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="637ff-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="637ff-132">See Also</span></span>

[<span data-ttu-id="637ff-133">La definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="637ff-133">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="637ff-134">Elemento EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="637ff-134">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="637ff-135">Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="637ff-135">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="637ff-136">Elemento SelectionSetName per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="637ff-136">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="637ff-137">Elemento TypeName per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="637ff-137">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="637ff-138">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="637ff-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
