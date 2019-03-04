---
title: La definizione di set di selezione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858927"
---
# <a name="defining-selection-sets"></a><span data-ttu-id="ef94e-102">Definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="ef94e-102">Defining Selection Sets</span></span>

<span data-ttu-id="ef94e-103">Durante la creazione di più controlli e visualizzazioni, è possibile definire set di oggetti che vengono definiti come set di selezione.</span><span class="sxs-lookup"><span data-stu-id="ef94e-103">When creating multiple views and controls, you can define sets of objects that are referred to as selection sets.</span></span> <span data-ttu-id="ef94e-104">Un set di selezione consente di definire gli oggetti di una sola volta, senza la necessità di definire più volte per ogni vista o un controllo.</span><span class="sxs-lookup"><span data-stu-id="ef94e-104">A selection set enables you to define the objects one time, without having to define them repeatedly for each view or control.</span></span> <span data-ttu-id="ef94e-105">In genere, i set di selezione vengono usati quando si dispone di un set di oggetti .NET correlati.</span><span class="sxs-lookup"><span data-stu-id="ef94e-105">Typically, selection sets are used when you have a set of related .NET objects.</span></span> <span data-ttu-id="ef94e-106">Ad esempio, il `FileSystem` file di formattazione (FileSystem.format.ps1xml) definisce un set di selezione dei tipi di sistema file che usano diverse visualizzazioni.</span><span class="sxs-lookup"><span data-stu-id="ef94e-106">For example, The `FileSystem` formatting file (FileSystem.format.ps1xml) defines a selection set of the file system types that several views use.</span></span>

## <a name="where-selection-sets-are-defined-and-referenced"></a><span data-ttu-id="ef94e-107">In cui set di selezione sono definiti e riferimento</span><span class="sxs-lookup"><span data-stu-id="ef94e-107">Where Selection Sets are Defined and Referenced</span></span>

<span data-ttu-id="ef94e-108">Set di selezione vengono definite come parte dei dati comuni che possono essere utilizzati da tutte le visualizzazioni e i controlli definiti nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="ef94e-108">You define selection sets as part of the common data that can be used by all the views and controls defined in the formatting file.</span></span> <span data-ttu-id="ef94e-109">Nell'esempio seguente viene illustrato come definire tre set di selezione.</span><span class="sxs-lookup"><span data-stu-id="ef94e-109">The following example shows how to define three selection sets.</span></span>

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

<span data-ttu-id="ef94e-110">È possibile fare riferimento a una selezione imposta nei modi seguenti:</span><span class="sxs-lookup"><span data-stu-id="ef94e-110">You can reference a selection sets in the following ways:</span></span>

- <span data-ttu-id="ef94e-111">Ogni visualizzazione dispone di un `ViewSelectedBy` elemento che definisce quali oggetti vengono visualizzati tramite la vista.</span><span class="sxs-lookup"><span data-stu-id="ef94e-111">Each view has a `ViewSelectedBy` element that defines which objects are displayed by using the view.</span></span> <span data-ttu-id="ef94e-112">Il `ViewSelectedBy` elemento ha un `SelectionSetName` elemento figlio che specifica la selezione del set che tutte le definizioni dell'utilizzo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="ef94e-112">The `ViewSelectedBy` element has a `SelectionSetName` child element that specifies the selection set that all the definitions of the view use.</span></span> <span data-ttu-id="ef94e-113">Non vi è alcuna restrizione al numero di set di selezione che è possibile fare riferimento da una vista.</span><span class="sxs-lookup"><span data-stu-id="ef94e-113">There is no restriction on the number of selection sets that you can reference from a view.</span></span>

- <span data-ttu-id="ef94e-114">In ogni definizione di una vista o di un controllo, il `EntrySelectedBy` elemento definisce gli oggetti che vengono visualizzati tramite tale definizione.</span><span class="sxs-lookup"><span data-stu-id="ef94e-114">In each definition of a view or control, the `EntrySelectedBy` element defines which objects are displayed by using that definition.</span></span> <span data-ttu-id="ef94e-115">In genere una vista o un controllo dispone di una sola definizione in modo che gli oggetti vengono definiti dal `ViewSelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="ef94e-115">Typically a view or control has only one definition so the objects are defined by the `ViewSelectedBy` element.</span></span> <span data-ttu-id="ef94e-116">Il `EntrySelectedBy` della definizione dell'elemento ha un `SelectionSetName` elemento figlio che specifica il set di selezione.</span><span class="sxs-lookup"><span data-stu-id="ef94e-116">The `EntrySelectedBy` element of the definition has a `SelectionSetName` child element that specifies the selection set.</span></span> <span data-ttu-id="ef94e-117">Se si specifica l'insieme per una definizione di selezione, è possibile specificare uno degli altri elementi figlio del `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="ef94e-117">If you specify the selection set for a definition, you cannot specify any of the other child elements of the `EntrySelectedBy` element.</span></span>

- <span data-ttu-id="ef94e-118">In ogni definizione di una vista o di un controllo, il `SelectionCondition` elemento può essere usato per specificare una condizione per quando viene utilizzata la definizione.</span><span class="sxs-lookup"><span data-stu-id="ef94e-118">In each definition of a view or control, the `SelectionCondition` element can be used to specify a condition for when the definition is used.</span></span> <span data-ttu-id="ef94e-119">Il `SelectionCondition` elemento ha un `SelectionSetName` elemento figlio che specifica set di selezione attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="ef94e-119">The `SelectionCondition` element has a `SelectionSetName` child element that specifies the selection set that triggers the condition.</span></span> <span data-ttu-id="ef94e-120">La condizione viene attivata quando viene visualizzato uno degli oggetti definiti nel set di selezione.</span><span class="sxs-lookup"><span data-stu-id="ef94e-120">The condition is triggered when any of the objects defined in the selection set are displayed.</span></span> <span data-ttu-id="ef94e-121">Per altre informazioni su come impostare queste condizioni, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ef94e-121">For more information about how to set these conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="selection-set-example"></a><span data-ttu-id="ef94e-122">Esempio di Set di selezione</span><span class="sxs-lookup"><span data-stu-id="ef94e-122">Selection Set Example</span></span>

<span data-ttu-id="ef94e-123">L'esempio seguente mostra un set di selezione che viene recuperato direttamente dal `FileSystem` formattazione file fornito da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef94e-123">The following example shows a selection set that is taken directly from the `FileSystem` formatting file provided by Windows PowerShell.</span></span> <span data-ttu-id="ef94e-124">Per altre informazioni su altri PowerShell di Windows, file di formattazione, vedere [file di formattazione di Windows PowerShell](./powershell-formatting-files.md).</span><span class="sxs-lookup"><span data-stu-id="ef94e-124">For more information about other Windows PowerShell formatting files, see [Windows PowerShell Formatting Files](./powershell-formatting-files.md).</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

<span data-ttu-id="ef94e-125">Il set di selezione precedente fa riferimento il `ViewSelectedBy` elemento della visualizzazione di una tabella.</span><span class="sxs-lookup"><span data-stu-id="ef94e-125">The previous selection set is referenced in the `ViewSelectedBy` element of a table view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>Files</Name>
    <ViewSelectedBy>
      <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="xml-elements"></a><span data-ttu-id="ef94e-126">Elementi XML</span><span class="sxs-lookup"><span data-stu-id="ef94e-126">XML Elements</span></span>

 <span data-ttu-id="ef94e-127">Non sono previsti limiti al numero di set di selezione che è possibile definire.</span><span class="sxs-lookup"><span data-stu-id="ef94e-127">There is no limit to the number of selection sets that you can define.</span></span> <span data-ttu-id="ef94e-128">Gli elementi XML seguenti vengono utilizzati per creare un set di selezione.</span><span class="sxs-lookup"><span data-stu-id="ef94e-128">The following XML elements are used to create a selection set.</span></span>

- <span data-ttu-id="ef94e-129">Il [SelectionSets](./selectionsets-element-format.md) elemento definisce i set di oggetti .NET che fanno riferimento le viste e i controlli del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="ef94e-129">The [SelectionSets](./selectionsets-element-format.md) element defines the sets of .NET objects that are referenced by the views and controls of the formatting file.</span></span>

- <span data-ttu-id="ef94e-130">Il [SelectionSet](./selectionset-element-format.md) elemento definisce un singolo set di oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="ef94e-130">The [SelectionSet](./selectionset-element-format.md) element defines a single set of .NET objects.</span></span>

- <span data-ttu-id="ef94e-131">Il [nome](./name-element-for-selectionset-format.md) elemento specifica il nome utilizzato per fare riferimento a set di selezione.</span><span class="sxs-lookup"><span data-stu-id="ef94e-131">The [Name](./name-element-for-selectionset-format.md) element specifies the name that is used to reference the selection set.</span></span>

- <span data-ttu-id="ef94e-132">Il [tipi](./types-element-for-selectionset-format.md) elemento specifica i tipi .NET degli oggetti del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="ef94e-132">The [Types](./types-element-for-selectionset-format.md) element specifies the .NET types of the objects of the selection set.</span></span> <span data-ttu-id="ef94e-133">(All'interno di file di formattazione, gli oggetti vengono specificati in base al tipo .NET).</span><span class="sxs-lookup"><span data-stu-id="ef94e-133">(Within formatting files, objects are specified by their .NET type.)</span></span>

 <span data-ttu-id="ef94e-134">Gli elementi XML seguenti consentono di specificare un set di selezione.</span><span class="sxs-lookup"><span data-stu-id="ef94e-134">The following XML elements are used to specify a selection set.</span></span>

- <span data-ttu-id="ef94e-135">L'elemento seguente specifica la selezione di set da utilizzare in tutte le definizioni della vista:</span><span class="sxs-lookup"><span data-stu-id="ef94e-135">The following element specifies the selection set to use in all the definitions of the view:</span></span>

    - [<span data-ttu-id="ef94e-136">Elemento SelectionSetName per ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="ef94e-136">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

    - [<span data-ttu-id="ef94e-137">Elemento SelectionSetName per EntrySelectedBy per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="ef94e-137">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="ef94e-138">Gli elementi seguenti specificano il set di selezione utilizzato dalla definizione di una singola vista:</span><span class="sxs-lookup"><span data-stu-id="ef94e-138">The following elements specify the selection set used by a single view definition:</span></span>

    - [<span data-ttu-id="ef94e-139">Elemento SelectionSetName per EntrySelectedBy per ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="ef94e-139">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="ef94e-140">Elemento SelectionSetName per EntrySelectedBy per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="ef94e-140">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="ef94e-141">Elemento SelectionSetName per EntrySelectedBy per WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="ef94e-141">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="ef94e-142">Elemento SelectionSetName per EntrySelectedBy per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ef94e-142">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- <span data-ttu-id="ef94e-143">Gli elementi seguenti specificano il set di selezione utilizzato da più comuni e visualizzare le definizioni di controllo:</span><span class="sxs-lookup"><span data-stu-id="ef94e-143">The following elements specify the selection set used by common and view control definitions:</span></span>

    - [<span data-ttu-id="ef94e-144">Elemento SelectionSetName per EntrySelectedBy per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ef94e-144">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [<span data-ttu-id="ef94e-145">Elemento SelectionSetName per EntrySelectedBy per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ef94e-145">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- <span data-ttu-id="ef94e-146">Gli elementi seguenti specificano il set di selezione utilizzato quando si definisce l'oggetto da espandere:</span><span class="sxs-lookup"><span data-stu-id="ef94e-146">The following elements specify the selection set used when you define which object to expand:</span></span>

    - [<span data-ttu-id="ef94e-147">Elemento SelectionSetName per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="ef94e-147">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="ef94e-148">Gli elementi seguenti specificano il set di selezione utilizzato da condizioni di selezione.</span><span class="sxs-lookup"><span data-stu-id="ef94e-148">The following elements specify the selection set used by selection conditions.</span></span>

    - [<span data-ttu-id="ef94e-149">Elemento SelectionSetName per SelectionCondition per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ef94e-149">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="ef94e-150">Elemento SelectionSetName per SelectionCondition per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ef94e-150">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [<span data-ttu-id="ef94e-151">Elemento SelectionSetName per SelectionCondition per CustomControl per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="ef94e-151">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [<span data-ttu-id="ef94e-152">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="ef94e-152">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [<span data-ttu-id="ef94e-153">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ef94e-153">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [<span data-ttu-id="ef94e-154">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per Table (formato)</span><span class="sxs-lookup"><span data-stu-id="ef94e-154">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="ef94e-155">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ef94e-155">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [<span data-ttu-id="ef94e-156">Elemento SelectionSetName per SelectionCondition per GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="ef94e-156">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="ef94e-157">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ef94e-157">See Also</span></span>

[<span data-ttu-id="ef94e-158">SelectionSets</span><span class="sxs-lookup"><span data-stu-id="ef94e-158">SelectionSets</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="ef94e-159">SelectionSet</span><span class="sxs-lookup"><span data-stu-id="ef94e-159">SelectionSet</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="ef94e-160">Name</span><span class="sxs-lookup"><span data-stu-id="ef94e-160">Name</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="ef94e-161">Tipi</span><span class="sxs-lookup"><span data-stu-id="ef94e-161">Types</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="ef94e-162">File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="ef94e-162">PowerShell Formatting Files</span></span>](./powershell-formatting-files.md)

[<span data-ttu-id="ef94e-163">La definizione delle condizioni per quando i dati vengono visualizzati</span><span class="sxs-lookup"><span data-stu-id="ef94e-163">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ef94e-164">La scrittura di una formattazione di PowerShell e dei tipi</span><span class="sxs-lookup"><span data-stu-id="ef94e-164">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
