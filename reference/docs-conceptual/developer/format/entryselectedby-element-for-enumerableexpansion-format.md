---
title: Elemento EntrySelectedBy per EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368800"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="7711b-102">Elemento EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="7711b-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="7711b-103">Definisce i tipi .NET che utilizzano questa definizione o la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="7711b-103">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="7711b-104">Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format) elemento EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7711b-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7711b-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7711b-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7711b-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="7711b-106">Attributes and Elements</span></span>

<span data-ttu-id="7711b-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="7711b-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7711b-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="7711b-108">Attributes</span></span>

<span data-ttu-id="7711b-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="7711b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7711b-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="7711b-110">Child Elements</span></span>

|<span data-ttu-id="7711b-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="7711b-111">Element</span></span>|<span data-ttu-id="7711b-112">Description</span><span class="sxs-lookup"><span data-stu-id="7711b-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7711b-113">Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7711b-113">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="7711b-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7711b-114">Optional element.</span></span><br /><br /> <span data-ttu-id="7711b-115">Definisce la condizione che deve esistere per espandere gli oggetti della raccolta di questa definizione.</span><span class="sxs-lookup"><span data-stu-id="7711b-115">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="7711b-116">Elemento SelectionSetName per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7711b-116">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="7711b-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7711b-117">Optional element.</span></span><br /><br /> <span data-ttu-id="7711b-118">Specifica un set di tipi .NET che utilizzano questa definizione del modo in cui gli oggetti della raccolta vengono espansi.</span><span class="sxs-lookup"><span data-stu-id="7711b-118">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="7711b-119">Elemento TypeName per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7711b-119">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="7711b-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7711b-120">Optional element.</span></span><br /><br /> <span data-ttu-id="7711b-121">Specifica un tipo .NET che usa questa definizione della modalità di espansione degli oggetti raccolta.</span><span class="sxs-lookup"><span data-stu-id="7711b-121">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7711b-122">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="7711b-122">Parent Elements</span></span>

|<span data-ttu-id="7711b-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="7711b-123">Element</span></span>|<span data-ttu-id="7711b-124">Description</span><span class="sxs-lookup"><span data-stu-id="7711b-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7711b-125">Elemento EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7711b-125">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="7711b-126">Definisce la modalità di espansione degli oggetti raccolta .NET specifici quando vengono visualizzati in una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="7711b-126">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7711b-127">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="7711b-127">Remarks</span></span>

<span data-ttu-id="7711b-128">È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per una voce di definizione.</span><span class="sxs-lookup"><span data-stu-id="7711b-128">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="7711b-129">Non esiste un limite massimo per il numero di elementi figlio che è possibile usare.</span><span class="sxs-lookup"><span data-stu-id="7711b-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="7711b-130">Le condizioni di selezione vengono usate per definire una condizione che deve esistere per la definizione da usare, ad esempio quando un oggetto ha una proprietà specifica o che un valore di proprietà o uno script specifico restituisce `true`.</span><span class="sxs-lookup"><span data-stu-id="7711b-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="7711b-131">Per ulteriori informazioni sulle condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="7711b-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7711b-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7711b-132">See Also</span></span>

[<span data-ttu-id="7711b-133">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="7711b-133">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7711b-134">Elemento EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7711b-134">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="7711b-135">Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7711b-135">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="7711b-136">Elemento SelectionSetName per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7711b-136">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="7711b-137">Elemento TypeName per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7711b-137">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="7711b-138">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="7711b-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
