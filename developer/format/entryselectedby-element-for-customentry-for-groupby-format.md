---
title: Elemento EntrySelectedBy per CustomEntry per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862817"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="80ca2-102">Elemento EntrySelectedBy per CustomEntry per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="80ca2-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="80ca2-103">Definisce i tipi .NET che usano questa definizione di controllo o la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="80ca2-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="80ca2-104">Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="80ca2-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="80ca2-105">Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per elemento EntrySelectedBy GroupBy (formato) per CustomEntry per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="80ca2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="80ca2-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="80ca2-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="80ca2-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="80ca2-107">Attributes and Elements</span></span>

<span data-ttu-id="80ca2-108">Le sezioni seguenti descrivono l'elemento padre di attributi e gli elementi figlio di `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="80ca2-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="80ca2-109">È necessario specificare almeno un tipo, set di selezione o condizione di selezione per una definizione.</span><span class="sxs-lookup"><span data-stu-id="80ca2-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="80ca2-110">Non è definito alcun limite massimo al numero di elementi figlio che è possibile usare.</span><span class="sxs-lookup"><span data-stu-id="80ca2-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="80ca2-111">Attributes</span><span class="sxs-lookup"><span data-stu-id="80ca2-111">Attributes</span></span>

<span data-ttu-id="80ca2-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="80ca2-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="80ca2-113">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="80ca2-113">Child Elements</span></span>

|<span data-ttu-id="80ca2-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="80ca2-114">Element</span></span>|<span data-ttu-id="80ca2-115">Description</span><span class="sxs-lookup"><span data-stu-id="80ca2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80ca2-116">Elemento SelectionCondition per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="80ca2-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="80ca2-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="80ca2-117">Optional element.</span></span><br /><br /> <span data-ttu-id="80ca2-118">Definisce la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="80ca2-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="80ca2-119">Elemento SelectionSetName per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="80ca2-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="80ca2-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="80ca2-120">Optional element.</span></span><br /><br /> <span data-ttu-id="80ca2-121">Specifica un set di tipi .NET che usano questa definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="80ca2-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="80ca2-122">Elemento TypeName per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="80ca2-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="80ca2-123">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="80ca2-123">Optional element.</span></span><br /><br /> <span data-ttu-id="80ca2-124">Specifica un tipo .NET che usa questa definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="80ca2-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="80ca2-125">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="80ca2-125">Parent Elements</span></span>

|<span data-ttu-id="80ca2-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="80ca2-126">Element</span></span>|<span data-ttu-id="80ca2-127">Description</span><span class="sxs-lookup"><span data-stu-id="80ca2-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80ca2-128">Elemento CustomEntry per CustomControl per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="80ca2-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="80ca2-129">Fornisce una definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="80ca2-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="80ca2-130">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="80ca2-130">Remarks</span></span>

<span data-ttu-id="80ca2-131">Condizioni di selezione vengono usate per definire una condizione che deve essere presente per la definizione da usare, ad esempio quando un oggetto dispone di una proprietà specifica o quando un valore di proprietà specifica o lo script restituisce `true`.</span><span class="sxs-lookup"><span data-stu-id="80ca2-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="80ca2-132">Per altre informazioni sulle condizioni di selezione, vedere [definizione di condizioni per quando una voce di visualizzazione o viene usato l'elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="80ca2-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="80ca2-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="80ca2-133">See Also</span></span>

[<span data-ttu-id="80ca2-134">Elemento SelectionCondition per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="80ca2-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="80ca2-135">Elemento SelectionSetName per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="80ca2-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="80ca2-136">Elemento TypeName per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="80ca2-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="80ca2-137">Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="80ca2-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="80ca2-138">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="80ca2-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
