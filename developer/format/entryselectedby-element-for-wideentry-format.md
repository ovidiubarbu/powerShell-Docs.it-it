---
title: Elemento EntrySelectedBy per WideEntry (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854977"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="f4f92-102">Elemento EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f4f92-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="f4f92-103">Definisce i tipi .NET che usano questa definizione di visualizzazione estesa o la condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="f4f92-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="f4f92-104">Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento di configurazione per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f4f92-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f4f92-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f4f92-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f4f92-106">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="f4f92-106">Attributes and Elements</span></span>

<span data-ttu-id="f4f92-107">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="f4f92-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f4f92-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="f4f92-108">Attributes</span></span>

<span data-ttu-id="f4f92-109">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f4f92-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f4f92-110">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f4f92-110">Child Elements</span></span>

|<span data-ttu-id="f4f92-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="f4f92-111">Element</span></span>|<span data-ttu-id="f4f92-112">Description</span><span class="sxs-lookup"><span data-stu-id="f4f92-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f4f92-113">Elemento SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f4f92-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="f4f92-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="f4f92-114">Optional element.</span></span><br /><br /> <span data-ttu-id="f4f92-115">Definisce la condizione che deve essere presente per questa definizione di visualizzazione estesa da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="f4f92-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="f4f92-116">Elemento SelectionSetName per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f4f92-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="f4f92-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="f4f92-117">Optional element.</span></span><br /><br /> <span data-ttu-id="f4f92-118">Specifica un set di tipi .NET che usano questa definizione di visualizzazione più ampia.</span><span class="sxs-lookup"><span data-stu-id="f4f92-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="f4f92-119">Elemento TypeName per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f4f92-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="f4f92-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="f4f92-120">Optional element.</span></span><br /><br /> <span data-ttu-id="f4f92-121">Specifica un tipo .NET che usa questa definizione di visualizzazione più ampia.</span><span class="sxs-lookup"><span data-stu-id="f4f92-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f4f92-122">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f4f92-122">Parent Elements</span></span>

|<span data-ttu-id="f4f92-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="f4f92-123">Element</span></span>|<span data-ttu-id="f4f92-124">Description</span><span class="sxs-lookup"><span data-stu-id="f4f92-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f4f92-125">Elemento WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f4f92-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="f4f92-126">Fornisce una definizione della vista wide.</span><span class="sxs-lookup"><span data-stu-id="f4f92-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f4f92-127">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f4f92-127">Remarks</span></span>

<span data-ttu-id="f4f92-128">È necessario specificare almeno un tipo, il set di selezione o condizione di selezione per una definizione di visualizzazione più ampia.</span><span class="sxs-lookup"><span data-stu-id="f4f92-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="f4f92-129">Non è definito alcun limite massimo al numero di elementi figlio che è possibile usare.</span><span class="sxs-lookup"><span data-stu-id="f4f92-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="f4f92-130">Condizioni di selezione vengono usate per definire una condizione che deve essere presente per la definizione da usare, ad esempio quando un oggetto dispone di una proprietà specifica o che restituisce un valore di uno script o il valore della proprietà specifico `true`.</span><span class="sxs-lookup"><span data-stu-id="f4f92-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="f4f92-131">Per altre informazioni sulle condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f4f92-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f4f92-132">Per altre informazioni sugli altri componenti di una visualizzazione più ampia, vedere [creazione di una visualizzazione più ampia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="f4f92-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f4f92-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f4f92-133">See Also</span></span>

[<span data-ttu-id="f4f92-134">Elemento WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f4f92-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="f4f92-135">Elemento SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f4f92-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="f4f92-136">Elemento SelectionSetName per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f4f92-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="f4f92-137">Elemento TypeName per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f4f92-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="f4f92-138">Creazione di una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="f4f92-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="f4f92-139">La definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="f4f92-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f4f92-140">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f4f92-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
