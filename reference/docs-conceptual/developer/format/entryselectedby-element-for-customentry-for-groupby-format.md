---
title: Elemento EntrySelectedBy per CustomEntry per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363860"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="a48de-102">Elemento EntrySelectedBy per CustomEntry per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="a48de-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="a48de-103">Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="a48de-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="a48de-104">Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="a48de-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="a48de-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format) elemento EntrySelectedBy per CustomEntry per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a48de-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a48de-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a48de-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a48de-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="a48de-107">Attributes and Elements</span></span>

<span data-ttu-id="a48de-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="a48de-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="a48de-109">Per una definizione è necessario specificare almeno un tipo, un set di selezione o una condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="a48de-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="a48de-110">Non esiste un limite massimo per il numero di elementi figlio che è possibile usare.</span><span class="sxs-lookup"><span data-stu-id="a48de-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="a48de-111">Attributi</span><span class="sxs-lookup"><span data-stu-id="a48de-111">Attributes</span></span>

<span data-ttu-id="a48de-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="a48de-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a48de-113">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="a48de-113">Child Elements</span></span>

|<span data-ttu-id="a48de-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="a48de-114">Element</span></span>|<span data-ttu-id="a48de-115">Description</span><span class="sxs-lookup"><span data-stu-id="a48de-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a48de-116">Elemento SelectionCondition per EntrySelectedBy per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a48de-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="a48de-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="a48de-117">Optional element.</span></span><br /><br /> <span data-ttu-id="a48de-118">Definisce la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="a48de-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="a48de-119">Elemento SelectionSetName per EntrySelectedBy per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a48de-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="a48de-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="a48de-120">Optional element.</span></span><br /><br /> <span data-ttu-id="a48de-121">Specifica un set di tipi .NET che utilizzano questa definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="a48de-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="a48de-122">Elemento TypeName per EntrySelectedBy per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a48de-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="a48de-123">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="a48de-123">Optional element.</span></span><br /><br /> <span data-ttu-id="a48de-124">Specifica un tipo .NET che usa questa definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="a48de-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a48de-125">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="a48de-125">Parent Elements</span></span>

|<span data-ttu-id="a48de-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="a48de-126">Element</span></span>|<span data-ttu-id="a48de-127">Description</span><span class="sxs-lookup"><span data-stu-id="a48de-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a48de-128">Elemento CustomEntry per CustomControl per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a48de-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="a48de-129">Fornisce una definizione del controllo.</span><span class="sxs-lookup"><span data-stu-id="a48de-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a48de-130">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="a48de-130">Remarks</span></span>

<span data-ttu-id="a48de-131">Le condizioni di selezione vengono usate per definire una condizione che deve esistere per la definizione da usare, ad esempio quando un oggetto ha una proprietà specifica o quando uno script o un valore di proprietà specifico restituisce `true`.</span><span class="sxs-lookup"><span data-stu-id="a48de-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="a48de-132">Per ulteriori informazioni sulle condizioni di selezione, vedere [definizione di condizioni per l'utilizzo di una voce o di un elemento della visualizzazione](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a48de-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a48de-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a48de-133">See Also</span></span>

[<span data-ttu-id="a48de-134">Elemento SelectionCondition per EntrySelectedBy per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a48de-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="a48de-135">Elemento SelectionSetName per EntrySelectedBy per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a48de-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="a48de-136">Elemento TypeName per EntrySelectedBy per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a48de-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="a48de-137">Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="a48de-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="a48de-138">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="a48de-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
