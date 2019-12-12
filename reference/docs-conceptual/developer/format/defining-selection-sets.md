---
title: Definizione di set di selezione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368850"
---
# <a name="defining-selection-sets"></a><span data-ttu-id="1c2be-102">Definizione di set di selezione</span><span class="sxs-lookup"><span data-stu-id="1c2be-102">Defining Selection Sets</span></span>

<span data-ttu-id="1c2be-103">Quando si creano più viste e controlli, è possibile definire set di oggetti definiti set di selezione.</span><span class="sxs-lookup"><span data-stu-id="1c2be-103">When creating multiple views and controls, you can define sets of objects that are referred to as selection sets.</span></span> <span data-ttu-id="1c2be-104">Un set di selezione consente di definire gli oggetti una volta, senza che sia necessario definirli ripetutamente per ogni visualizzazione o controllo.</span><span class="sxs-lookup"><span data-stu-id="1c2be-104">A selection set enables you to define the objects one time, without having to define them repeatedly for each view or control.</span></span> <span data-ttu-id="1c2be-105">In genere, i set di selezione vengono usati quando si dispone di un set di oggetti .NET correlati.</span><span class="sxs-lookup"><span data-stu-id="1c2be-105">Typically, selection sets are used when you have a set of related .NET objects.</span></span> <span data-ttu-id="1c2be-106">Ad esempio, il file di formattazione `FileSystem` (FileSystem. Format. ps1xml) definisce un set di selezione dei tipi di file system utilizzati da diverse visualizzazioni.</span><span class="sxs-lookup"><span data-stu-id="1c2be-106">For example, The `FileSystem` formatting file (FileSystem.format.ps1xml) defines a selection set of the file system types that several views use.</span></span>

## <a name="where-selection-sets-are-defined-and-referenced"></a><span data-ttu-id="1c2be-107">Dove sono definiti e a cui viene fatto riferimento nei set di selezione</span><span class="sxs-lookup"><span data-stu-id="1c2be-107">Where Selection Sets are Defined and Referenced</span></span>

<span data-ttu-id="1c2be-108">I set di selezione vengono definiti come parte dei dati comuni che possono essere utilizzati da tutte le visualizzazioni e i controlli definiti nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="1c2be-108">You define selection sets as part of the common data that can be used by all the views and controls defined in the formatting file.</span></span> <span data-ttu-id="1c2be-109">Nell'esempio seguente viene illustrato come definire tre set di selezione.</span><span class="sxs-lookup"><span data-stu-id="1c2be-109">The following example shows how to define three selection sets.</span></span>

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

<span data-ttu-id="1c2be-110">È possibile fare riferimento a un set di selezione nei modi seguenti:</span><span class="sxs-lookup"><span data-stu-id="1c2be-110">You can reference a selection sets in the following ways:</span></span>

- <span data-ttu-id="1c2be-111">Ogni visualizzazione dispone di un elemento `ViewSelectedBy` che definisce quali oggetti vengono visualizzati tramite la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="1c2be-111">Each view has a `ViewSelectedBy` element that defines which objects are displayed by using the view.</span></span> <span data-ttu-id="1c2be-112">L'elemento `ViewSelectedBy` dispone di un elemento `SelectionSetName` figlio che specifica il set di selezione usato da tutte le definizioni della visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="1c2be-112">The `ViewSelectedBy` element has a `SelectionSetName` child element that specifies the selection set that all the definitions of the view use.</span></span> <span data-ttu-id="1c2be-113">Non esiste alcuna restrizione al numero di set di selezione a cui è possibile fare riferimento da una vista.</span><span class="sxs-lookup"><span data-stu-id="1c2be-113">There is no restriction on the number of selection sets that you can reference from a view.</span></span>

- <span data-ttu-id="1c2be-114">In ogni definizione di una vista o di un controllo, l'elemento `EntrySelectedBy` definisce quali oggetti vengono visualizzati tramite tale definizione.</span><span class="sxs-lookup"><span data-stu-id="1c2be-114">In each definition of a view or control, the `EntrySelectedBy` element defines which objects are displayed by using that definition.</span></span> <span data-ttu-id="1c2be-115">Una vista o un controllo ha in genere una sola definizione, quindi gli oggetti vengono definiti dall'elemento `ViewSelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="1c2be-115">Typically a view or control has only one definition so the objects are defined by the `ViewSelectedBy` element.</span></span> <span data-ttu-id="1c2be-116">L'elemento `EntrySelectedBy` della definizione dispone di un elemento `SelectionSetName` figlio che specifica il set di selezione.</span><span class="sxs-lookup"><span data-stu-id="1c2be-116">The `EntrySelectedBy` element of the definition has a `SelectionSetName` child element that specifies the selection set.</span></span> <span data-ttu-id="1c2be-117">Se si specifica il set di selezione per una definizione, non è possibile specificare gli altri elementi figlio dell'elemento `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="1c2be-117">If you specify the selection set for a definition, you cannot specify any of the other child elements of the `EntrySelectedBy` element.</span></span>

- <span data-ttu-id="1c2be-118">In ogni definizione di una vista o di un controllo, l'elemento `SelectionCondition` può essere utilizzato per specificare una condizione per quando viene utilizzata la definizione.</span><span class="sxs-lookup"><span data-stu-id="1c2be-118">In each definition of a view or control, the `SelectionCondition` element can be used to specify a condition for when the definition is used.</span></span> <span data-ttu-id="1c2be-119">L'elemento `SelectionCondition` dispone di un elemento `SelectionSetName` figlio che specifica il set di selezione che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="1c2be-119">The `SelectionCondition` element has a `SelectionSetName` child element that specifies the selection set that triggers the condition.</span></span> <span data-ttu-id="1c2be-120">La condizione viene attivata quando viene visualizzato uno degli oggetti definiti nel set di selezione.</span><span class="sxs-lookup"><span data-stu-id="1c2be-120">The condition is triggered when any of the objects defined in the selection set are displayed.</span></span> <span data-ttu-id="1c2be-121">Per ulteriori informazioni sull'impostazione di queste condizioni, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1c2be-121">For more information about how to set these conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="selection-set-example"></a><span data-ttu-id="1c2be-122">Esempio di set di selezione</span><span class="sxs-lookup"><span data-stu-id="1c2be-122">Selection Set Example</span></span>

<span data-ttu-id="1c2be-123">Nell'esempio seguente viene illustrato un set di selezione che viene ricavato direttamente dal file di formattazione `FileSystem` fornito da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c2be-123">The following example shows a selection set that is taken directly from the `FileSystem` formatting file provided by Windows PowerShell.</span></span> <span data-ttu-id="1c2be-124">Per altre informazioni sui file di formattazione di Windows PowerShell, vedere [file di formattazione di Windows PowerShell](./powershell-formatting-files.md).</span><span class="sxs-lookup"><span data-stu-id="1c2be-124">For more information about other Windows PowerShell formatting files, see [Windows PowerShell Formatting Files](./powershell-formatting-files.md).</span></span>

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

<span data-ttu-id="1c2be-125">Viene fatto riferimento al set di selezione precedente nell'elemento `ViewSelectedBy` di una vista tabella.</span><span class="sxs-lookup"><span data-stu-id="1c2be-125">The previous selection set is referenced in the `ViewSelectedBy` element of a table view.</span></span>

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

## <a name="xml-elements"></a><span data-ttu-id="1c2be-126">Elementi XML</span><span class="sxs-lookup"><span data-stu-id="1c2be-126">XML Elements</span></span>

 <span data-ttu-id="1c2be-127">Non esiste alcun limite al numero di set di selezione che è possibile definire.</span><span class="sxs-lookup"><span data-stu-id="1c2be-127">There is no limit to the number of selection sets that you can define.</span></span> <span data-ttu-id="1c2be-128">Per creare un set di selezione vengono utilizzati gli elementi XML seguenti.</span><span class="sxs-lookup"><span data-stu-id="1c2be-128">The following XML elements are used to create a selection set.</span></span>

- <span data-ttu-id="1c2be-129">L'elemento [SelectionSets](./selectionsets-element-format.md) definisce i set di oggetti .NET a cui fanno riferimento le viste e i controlli del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="1c2be-129">The [SelectionSets](./selectionsets-element-format.md) element defines the sets of .NET objects that are referenced by the views and controls of the formatting file.</span></span>

- <span data-ttu-id="1c2be-130">L'elemento [SelectionSet](./selectionset-element-format.md) definisce un singolo set di oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="1c2be-130">The [SelectionSet](./selectionset-element-format.md) element defines a single set of .NET objects.</span></span>

- <span data-ttu-id="1c2be-131">L'elemento [Name](./name-element-for-selectionset-format.md) specifica il nome utilizzato per fare riferimento al set di selezione.</span><span class="sxs-lookup"><span data-stu-id="1c2be-131">The [Name](./name-element-for-selectionset-format.md) element specifies the name that is used to reference the selection set.</span></span>

- <span data-ttu-id="1c2be-132">L'elemento [types](./types-element-for-selectionset-format.md) specifica i tipi .NET degli oggetti del set di selezione.</span><span class="sxs-lookup"><span data-stu-id="1c2be-132">The [Types](./types-element-for-selectionset-format.md) element specifies the .NET types of the objects of the selection set.</span></span> <span data-ttu-id="1c2be-133">(All'interno dei file di formattazione, gli oggetti vengono specificati dal tipo .NET.)</span><span class="sxs-lookup"><span data-stu-id="1c2be-133">(Within formatting files, objects are specified by their .NET type.)</span></span>

 <span data-ttu-id="1c2be-134">Gli elementi XML seguenti vengono utilizzati per specificare un set di selezione.</span><span class="sxs-lookup"><span data-stu-id="1c2be-134">The following XML elements are used to specify a selection set.</span></span>

- <span data-ttu-id="1c2be-135">L'elemento seguente specifica il set di selezione da usare in tutte le definizioni della vista:</span><span class="sxs-lookup"><span data-stu-id="1c2be-135">The following element specifies the selection set to use in all the definitions of the view:</span></span>

    - [<span data-ttu-id="1c2be-136">Elemento SelectionSetName per ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1c2be-136">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

    - [<span data-ttu-id="1c2be-137">Elemento SelectionSetName per EntrySelectedBy per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1c2be-137">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="1c2be-138">Gli elementi seguenti specificano il set di selezione usato da una singola definizione di visualizzazione:</span><span class="sxs-lookup"><span data-stu-id="1c2be-138">The following elements specify the selection set used by a single view definition:</span></span>

    - [<span data-ttu-id="1c2be-139">Elemento SelectionSetName per EntrySelectedBy per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1c2be-139">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="1c2be-140">Elemento SelectionSetName per EntrySelectedBy per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="1c2be-140">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="1c2be-141">Elemento SelectionSetName per EntrySelectedBy per WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1c2be-141">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="1c2be-142">Elemento SelectionSetName per EntrySelectedBy per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="1c2be-142">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- <span data-ttu-id="1c2be-143">Gli elementi seguenti specificano il set di selezione usato dalle definizioni di controllo comuni e di visualizzazione:</span><span class="sxs-lookup"><span data-stu-id="1c2be-143">The following elements specify the selection set used by common and view control definitions:</span></span>

    - [<span data-ttu-id="1c2be-144">Elemento SelectionSetName per EntrySelectedBy per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="1c2be-144">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [<span data-ttu-id="1c2be-145">Elemento SelectionSetName per EntrySelectedBy per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="1c2be-145">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- <span data-ttu-id="1c2be-146">Gli elementi seguenti specificano il set di selezione usato quando si definisce l'oggetto da espandere:</span><span class="sxs-lookup"><span data-stu-id="1c2be-146">The following elements specify the selection set used when you define which object to expand:</span></span>

    - [<span data-ttu-id="1c2be-147">Elemento SelectionSetName per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="1c2be-147">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="1c2be-148">Gli elementi seguenti specificano il set di selezione usato dalle condizioni di selezione.</span><span class="sxs-lookup"><span data-stu-id="1c2be-148">The following elements specify the selection set used by selection conditions.</span></span>

    - [<span data-ttu-id="1c2be-149">Elemento SelectionSetName per SelectionCondition per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="1c2be-149">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="1c2be-150">Elemento SelectionSetName per SelectionCondition per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="1c2be-150">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [<span data-ttu-id="1c2be-151">Elemento SelectionSetName per SelectionCondition per CustomControl per View (Format)</span><span class="sxs-lookup"><span data-stu-id="1c2be-151">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [<span data-ttu-id="1c2be-152">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="1c2be-152">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [<span data-ttu-id="1c2be-153">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1c2be-153">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [<span data-ttu-id="1c2be-154">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="1c2be-154">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="1c2be-155">Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1c2be-155">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [<span data-ttu-id="1c2be-156">Elemento SelectionSetName per SelectionCondition per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1c2be-156">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="1c2be-157">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1c2be-157">See Also</span></span>

[<span data-ttu-id="1c2be-158">SelectionSets</span><span class="sxs-lookup"><span data-stu-id="1c2be-158">SelectionSets</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="1c2be-159">SelectionSet</span><span class="sxs-lookup"><span data-stu-id="1c2be-159">SelectionSet</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="1c2be-160">Nome</span><span class="sxs-lookup"><span data-stu-id="1c2be-160">Name</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="1c2be-161">Tipi</span><span class="sxs-lookup"><span data-stu-id="1c2be-161">Types</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="1c2be-162">File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c2be-162">PowerShell Formatting Files</span></span>](./powershell-formatting-files.md)

[<span data-ttu-id="1c2be-163">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="1c2be-163">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1c2be-164">Scrittura di un file di formattazione e di tipi di PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c2be-164">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
