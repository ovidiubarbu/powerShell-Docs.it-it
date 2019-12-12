---
title: Elemento EntrySelectedBy per WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363330"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="1f7b9-102">Elemento EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="1f7b9-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="1f7b9-103">Definisce i tipi .NET che utilizzano questa definizione della visualizzazione estesa o la condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="1f7b9-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="1f7b9-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) elemento EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1f7b9-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1f7b9-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1f7b9-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1f7b9-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="1f7b9-106">Attributes and Elements</span></span>

<span data-ttu-id="1f7b9-107">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="1f7b9-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f7b9-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="1f7b9-108">Attributes</span></span>

<span data-ttu-id="1f7b9-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="1f7b9-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1f7b9-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="1f7b9-110">Child Elements</span></span>

|<span data-ttu-id="1f7b9-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="1f7b9-111">Element</span></span>|<span data-ttu-id="1f7b9-112">Description</span><span class="sxs-lookup"><span data-stu-id="1f7b9-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f7b9-113">Elemento SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1f7b9-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="1f7b9-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="1f7b9-114">Optional element.</span></span><br /><br /> <span data-ttu-id="1f7b9-115">Definisce la condizione che deve esistere per la definizione della vista estesa da usare.</span><span class="sxs-lookup"><span data-stu-id="1f7b9-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="1f7b9-116">Elemento SelectionSetName per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1f7b9-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="1f7b9-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="1f7b9-117">Optional element.</span></span><br /><br /> <span data-ttu-id="1f7b9-118">Specifica un set di tipi .NET che utilizzano questa definizione di visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="1f7b9-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="1f7b9-119">Elemento TypeName per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1f7b9-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="1f7b9-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="1f7b9-120">Optional element.</span></span><br /><br /> <span data-ttu-id="1f7b9-121">Specifica un tipo .NET che usa questa definizione di visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="1f7b9-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1f7b9-122">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="1f7b9-122">Parent Elements</span></span>

|<span data-ttu-id="1f7b9-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="1f7b9-123">Element</span></span>|<span data-ttu-id="1f7b9-124">Description</span><span class="sxs-lookup"><span data-stu-id="1f7b9-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f7b9-125">Elemento WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1f7b9-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="1f7b9-126">Fornisce una definizione dell'ampia visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="1f7b9-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1f7b9-127">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="1f7b9-127">Remarks</span></span>

<span data-ttu-id="1f7b9-128">Per una definizione di visualizzazione estesa, è necessario specificare almeno un tipo, un set di selezione o una condizione di selezione.</span><span class="sxs-lookup"><span data-stu-id="1f7b9-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="1f7b9-129">Non esiste un limite massimo per il numero di elementi figlio che è possibile usare.</span><span class="sxs-lookup"><span data-stu-id="1f7b9-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="1f7b9-130">Le condizioni di selezione vengono usate per definire una condizione che deve esistere per la definizione da usare, ad esempio quando un oggetto ha una proprietà specifica o che un valore di proprietà o un valore di script specifico restituisce `true`.</span><span class="sxs-lookup"><span data-stu-id="1f7b9-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="1f7b9-131">Per ulteriori informazioni sulle condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1f7b9-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1f7b9-132">Per ulteriori informazioni su altri componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="1f7b9-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1f7b9-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1f7b9-133">See Also</span></span>

[<span data-ttu-id="1f7b9-134">Elemento WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1f7b9-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="1f7b9-135">Elemento SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1f7b9-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="1f7b9-136">Elemento SelectionSetName per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1f7b9-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="1f7b9-137">Elemento TypeName per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1f7b9-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="1f7b9-138">Creazione di una visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="1f7b9-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="1f7b9-139">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="1f7b9-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1f7b9-140">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f7b9-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
