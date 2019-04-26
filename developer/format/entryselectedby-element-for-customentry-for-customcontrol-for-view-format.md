---
title: Elemento EntrySelectedBy per CustomEntry per CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066278"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="46e31-102">Elemento EntrySelectedBy per CustomEntry per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="46e31-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="46e31-103">Definisce i tipi .NET che usano questa voce personalizzata o la condizione che deve essere presente per questa voce da usare.</span><span class="sxs-lookup"><span data-stu-id="46e31-103">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="46e31-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per EntrySelectedBy visualizzazione (formato) Elemento per CustomEntry per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="46e31-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="46e31-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="46e31-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="46e31-106">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="46e31-106">Attributes and Elements</span></span>

<span data-ttu-id="46e31-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="46e31-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="46e31-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="46e31-108">Attributes</span></span>

<span data-ttu-id="46e31-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="46e31-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="46e31-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="46e31-110">Child Elements</span></span>

|<span data-ttu-id="46e31-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="46e31-111">Element</span></span>|<span data-ttu-id="46e31-112">Description</span><span class="sxs-lookup"><span data-stu-id="46e31-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="46e31-113">Elemento SelectionCondition per EntrySelectedBy per CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="46e31-113">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="46e31-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="46e31-114">Optional element.</span></span><br /><br /> <span data-ttu-id="46e31-115">Definisce la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="46e31-115">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="46e31-116">Elemento SelectionSetName per EntrySelectedBy per CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="46e31-116">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="46e31-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="46e31-117">Optional element.</span></span><br /><br /> <span data-ttu-id="46e31-118">Specifica un set di tipi .NET che usano questa definizione della vista del controllo.</span><span class="sxs-lookup"><span data-stu-id="46e31-118">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="46e31-119">Elemento TypeName per EntrySelectedBy per CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="46e31-119">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="46e31-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="46e31-120">Optional element.</span></span><br /><br /> <span data-ttu-id="46e31-121">Specifica un tipo .NET che usa questa definizione della vista del controllo.</span><span class="sxs-lookup"><span data-stu-id="46e31-121">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="46e31-122">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="46e31-122">Parent Elements</span></span>

|<span data-ttu-id="46e31-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="46e31-123">Element</span></span>|<span data-ttu-id="46e31-124">Description</span><span class="sxs-lookup"><span data-stu-id="46e31-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="46e31-125">Elemento CustomEntry per CustomEntries per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="46e31-125">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="46e31-126">Definisce i controlli usati da specifici oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="46e31-126">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="46e31-127">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="46e31-127">Remarks</span></span>

<span data-ttu-id="46e31-128">È necessario specificare almeno un tipo, il set di selezione o condizione di selezione per una voce.</span><span class="sxs-lookup"><span data-stu-id="46e31-128">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="46e31-129">Non è definito alcun limite massimo al numero di elementi figlio che è possibile usare.</span><span class="sxs-lookup"><span data-stu-id="46e31-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="46e31-130">Condizioni di selezione vengono usate per definire una condizione che deve essere presente per la voce da usare, ad esempio quando un oggetto dispone di una proprietà specifica o quando un valore di proprietà specifica o lo script restituisce `true`.</span><span class="sxs-lookup"><span data-stu-id="46e31-130">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="46e31-131">Per altre informazioni sulle condizioni di selezione, vedere [definizione di condizioni per quando una voce di visualizzazione o viene usato l'elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="46e31-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="46e31-132">Per altre informazioni sui componenti di una vista di controllo personalizzato, vedere [visualizzazione di controlli personalizzati](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="46e31-132">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="46e31-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="46e31-133">See Also</span></span>

[<span data-ttu-id="46e31-134">Elemento SelectionCondition per EntrySelectedBy per CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="46e31-134">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="46e31-135">Elemento SelectionSetName per EntrySelectedBy per CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="46e31-135">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="46e31-136">Elemento TypeName per EntrySelectedBy per CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="46e31-136">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="46e31-137">Elemento CustomEntry per CustomEntries per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="46e31-137">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="46e31-138">Visualizzazione controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="46e31-138">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="46e31-139">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="46e31-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
