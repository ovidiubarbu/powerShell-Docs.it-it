---
title: Elemento EntrySelectedBy per CustomEntry per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368780"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="00e3f-102">Elemento EntrySelectedBy per CustomEntry per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="00e3f-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="00e3f-103">Definisce i tipi .NET che utilizzano questa voce personalizzata o la condizione che deve esistere affinché questa voce venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="00e3f-103">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="00e3f-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per l'elemento View (Format) CustomEntry per CustomEntries per View (Format) EntrySelectedBy Elemento per CustomEntry per View (Format)</span><span class="sxs-lookup"><span data-stu-id="00e3f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="00e3f-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="00e3f-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="00e3f-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="00e3f-106">Attributes and Elements</span></span>

<span data-ttu-id="00e3f-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="00e3f-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="00e3f-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="00e3f-108">Attributes</span></span>

<span data-ttu-id="00e3f-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="00e3f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="00e3f-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="00e3f-110">Child Elements</span></span>

|<span data-ttu-id="00e3f-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="00e3f-111">Element</span></span>|<span data-ttu-id="00e3f-112">Description</span><span class="sxs-lookup"><span data-stu-id="00e3f-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="00e3f-113">Elemento SelectionCondition per EntrySelectedBy per CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="00e3f-113">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="00e3f-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="00e3f-114">Optional element.</span></span><br /><br /> <span data-ttu-id="00e3f-115">Definisce la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="00e3f-115">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="00e3f-116">Elemento SelectionSetName per EntrySelectedBy per CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="00e3f-116">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="00e3f-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="00e3f-117">Optional element.</span></span><br /><br /> <span data-ttu-id="00e3f-118">Specifica un set di tipi .NET che utilizzano questa definizione della visualizzazione controlli.</span><span class="sxs-lookup"><span data-stu-id="00e3f-118">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="00e3f-119">Elemento TypeName per EntrySelectedBy per CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="00e3f-119">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="00e3f-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="00e3f-120">Optional element.</span></span><br /><br /> <span data-ttu-id="00e3f-121">Specifica un tipo .NET che usa questa definizione della visualizzazione controlli.</span><span class="sxs-lookup"><span data-stu-id="00e3f-121">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="00e3f-122">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="00e3f-122">Parent Elements</span></span>

|<span data-ttu-id="00e3f-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="00e3f-123">Element</span></span>|<span data-ttu-id="00e3f-124">Description</span><span class="sxs-lookup"><span data-stu-id="00e3f-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="00e3f-125">Elemento CustomEntry per CustomEntries per View (Format)</span><span class="sxs-lookup"><span data-stu-id="00e3f-125">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="00e3f-126">Definisce i controlli utilizzati da oggetti .NET specifici.</span><span class="sxs-lookup"><span data-stu-id="00e3f-126">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="00e3f-127">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="00e3f-127">Remarks</span></span>

<span data-ttu-id="00e3f-128">È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per una voce.</span><span class="sxs-lookup"><span data-stu-id="00e3f-128">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="00e3f-129">Non esiste un limite massimo per il numero di elementi figlio che è possibile usare.</span><span class="sxs-lookup"><span data-stu-id="00e3f-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="00e3f-130">Le condizioni di selezione vengono usate per definire una condizione che deve esistere per la voce da usare, ad esempio quando un oggetto ha una proprietà specifica o quando uno script o un valore di proprietà specifico restituisce `true`.</span><span class="sxs-lookup"><span data-stu-id="00e3f-130">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="00e3f-131">Per ulteriori informazioni sulle condizioni di selezione, vedere [definizione di condizioni per l'utilizzo di una voce o di un elemento della visualizzazione](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="00e3f-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="00e3f-132">Per ulteriori informazioni sui componenti di una visualizzazione controlli personalizzata, vedere [visualizzazione controlli personalizzati](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="00e3f-132">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="00e3f-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="00e3f-133">See Also</span></span>

[<span data-ttu-id="00e3f-134">Elemento SelectionCondition per EntrySelectedBy per CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="00e3f-134">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="00e3f-135">Elemento SelectionSetName per EntrySelectedBy per CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="00e3f-135">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="00e3f-136">Elemento TypeName per EntrySelectedBy per CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="00e3f-136">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="00e3f-137">Elemento CustomEntry per CustomEntries per View (Format)</span><span class="sxs-lookup"><span data-stu-id="00e3f-137">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="00e3f-138">Visualizzazione controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="00e3f-138">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="00e3f-139">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="00e3f-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
