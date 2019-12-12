---
title: Cenni preliminari sul file di formattazione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363690"
---
# <a name="formatting-file-overview"></a><span data-ttu-id="c1f4d-102">Panoramica dei file di formattazione</span><span class="sxs-lookup"><span data-stu-id="c1f4d-102">Formatting File Overview</span></span>

<span data-ttu-id="c1f4d-103">Il formato di visualizzazione per gli oggetti restituiti dai comandi (cmdlet, funzioni e script) viene definito usando i file di formattazione (file format. ps1xml).</span><span class="sxs-lookup"><span data-stu-id="c1f4d-103">The display format for the objects that are returned by commands (cmdlets, functions, and scripts) are defined by using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="c1f4d-104">Molti di questi file sono forniti da PowerShell per definire il formato di visualizzazione per gli oggetti restituiti dai comandi forniti da PowerShell, ad esempio l'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) restituito dal cmdlet `Get-Process`.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-104">Several of these files are provided by PowerShell to define the display format for those objects returned by PowerShell-provided commands, such as the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object returned by the `Get-Process` cmdlet.</span></span> <span data-ttu-id="c1f4d-105">Tuttavia, è anche possibile creare file di formattazione personalizzati per sovrascrivere i formati di visualizzazione predefiniti oppure è possibile scrivere un file di formattazione personalizzato per definire la visualizzazione degli oggetti restituiti dai propri comandi.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-105">However, you can also create your own custom formatting files to overwrite the default display formats or you can write a custom formatting file to define the display of objects returned by your own commands.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c1f4d-106">I file di formattazione non determinano gli elementi di un oggetto restituiti alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-106">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="c1f4d-107">Quando un oggetto viene restituito alla pipeline, tutti i membri di tale oggetto sono disponibili anche se alcuni non sono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-107">When an object is returned to the pipeline, all members of that object are available even if some are not displayed.</span></span>

<span data-ttu-id="c1f4d-108">PowerShell usa i dati nei file di formattazione per determinare gli elementi visualizzati e il modo in cui vengono formattati i dati visualizzati.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-108">PowerShell uses the data in these formatting files to determine what is displayed and how the displayed data is formatted.</span></span> <span data-ttu-id="c1f4d-109">I dati visualizzati possono includere le proprietà di un oggetto o il valore di uno script.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-109">The displayed data can include the properties of an object or the value of a script.</span></span> <span data-ttu-id="c1f4d-110">Gli script vengono utilizzati se si desidera visualizzare un valore non disponibile direttamente dalle proprietà di un oggetto, ad esempio l'aggiunta del valore di due proprietà di un oggetto e la visualizzazione della somma come una porzione di dati.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-110">Scripts are used if you want to display some value that is not available directly from the properties of an object, such as adding the value of two properties of an object and then displaying the sum as a piece of data.</span></span> <span data-ttu-id="c1f4d-111">La formattazione dei dati visualizzati viene eseguita definendo le visualizzazioni per gli oggetti che si desidera visualizzare.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-111">Formatting of the displayed data is done by defining views for the objects that you want to display.</span></span> <span data-ttu-id="c1f4d-112">È possibile definire una singola visualizzazione per ogni oggetto, è possibile definire una singola visualizzazione per più oggetti oppure è possibile definire più visualizzazioni per lo stesso oggetto.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-112">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="c1f4d-113">Non esiste alcun limite al numero di visualizzazioni che è possibile definire.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-113">There is no limit to the number of views that you can define.</span></span>

## <a name="common-features-of-formatting-files"></a><span data-ttu-id="c1f4d-114">Funzionalità comuni dei file di formattazione</span><span class="sxs-lookup"><span data-stu-id="c1f4d-114">Common Features of Formatting Files</span></span>

<span data-ttu-id="c1f4d-115">Ogni file di formattazione può definire i componenti seguenti che possono essere condivisi tra tutte le visualizzazioni definite dal file:</span><span class="sxs-lookup"><span data-stu-id="c1f4d-115">Each formatting file can define the following components that can be shared across all the views defined by the file:</span></span>

- <span data-ttu-id="c1f4d-116">Impostazione di configurazione predefinita, ad esempio se i dati visualizzati nelle righe delle tabelle verranno visualizzati nella riga successiva se i dati sono più lunghi della larghezza della colonna.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-116">Default configuration setting, such as whether the data displayed in the rows of tables will be displayed on the next line if the data is longer than the width of the column.</span></span> <span data-ttu-id="c1f4d-117">Per ulteriori informazioni su queste impostazioni, vedere [definizione delle impostazioni di configurazione comuni](./defining-common-configuration-features.md).</span><span class="sxs-lookup"><span data-stu-id="c1f4d-117">For more information about these settings, see [Defining Common Configuration Settings](./defining-common-configuration-features.md).</span></span>

- <span data-ttu-id="c1f4d-118">Set di oggetti che possono essere visualizzati da qualsiasi visualizzazione del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-118">Sets of objects that can be displayed by any of the views of the formatting file.</span></span> <span data-ttu-id="c1f4d-119">Per ulteriori informazioni su questi set (definiti set di *selezione*), vedere [definizione di set di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="c1f4d-119">For more information about these sets (referred to as *selection sets*), see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

- <span data-ttu-id="c1f4d-120">Controlli comuni che possono essere utilizzati da tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-120">Common controls that can be used by all the views of the formatting file.</span></span> <span data-ttu-id="c1f4d-121">I controlli consentono di ottenere un controllo più preciso sulla modalità di visualizzazione dei dati.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-121">Controls give you finer control on how data is displayed.</span></span> <span data-ttu-id="c1f4d-122">Per ulteriori informazioni sui controlli, vedere [definizione di controlli personalizzati](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="c1f4d-122">For more information about controls, see [Defining Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="formatting-views"></a><span data-ttu-id="c1f4d-123">Formattazione di visualizzazioni</span><span class="sxs-lookup"><span data-stu-id="c1f4d-123">Formatting Views</span></span>

<span data-ttu-id="c1f4d-124">Le visualizzazioni di formattazione possono visualizzare oggetti in formato tabella, formato elenco, formato esteso e formato personalizzato.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-124">Formatting views can display objects in a table format, list format, wide format, and custom format.</span></span> <span data-ttu-id="c1f4d-125">Nella maggior parte dei casi, ogni definizione di formattazione è descritta da un set di tag XML che descrivono la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-125">For the most part, each formatting definition is described by a set of XML tags that describe the view.</span></span> <span data-ttu-id="c1f4d-126">Ogni vista contiene il nome della vista, gli oggetti che utilizzano la vista e gli elementi della vista, ad esempio le informazioni su colonna e riga per una visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-126">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="c1f4d-127">Visualizzazione tabella sono elencate le proprietà di un oggetto o di un valore del blocco di script in una o più colonne.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-127">Table View Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="c1f4d-128">Ogni colonna rappresenta una singola proprietà dell'oggetto o un valore di script.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-128">Each column represents a single property of the object or a script value.</span></span> <span data-ttu-id="c1f4d-129">È possibile definire una vista tabella che Visualizza tutte le proprietà di un oggetto, un subset delle proprietà di un oggetto o una combinazione di proprietà e valori di script.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-129">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script values.</span></span> <span data-ttu-id="c1f4d-130">Ogni riga della tabella rappresenta un oggetto restituito.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-130">Each row of the table represents a returned object.</span></span> <span data-ttu-id="c1f4d-131">La creazione di una vista tabella è molto simile a quando si invia un oggetto tramite pipe al cmdlet `Format-Table`.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-131">Creating a table view is very similar to when you pipe an object to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="c1f4d-132">Per ulteriori informazioni su questa vista, vedere [visualizzazione tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="c1f4d-132">For more information about this view, see [Table View](./creating-a-table-view.md).</span></span>

<span data-ttu-id="c1f4d-133">Visualizzazione elenco elenca le proprietà di un oggetto o di un valore di script in un'unica colonna.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-133">List View Lists the properties of an object or a script value in a single column.</span></span> <span data-ttu-id="c1f4d-134">Ogni riga dell'elenco Visualizza un'etichetta facoltativa o il nome della proprietà seguito dal valore della proprietà o dello script.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-134">Each row of the list displays an optional label or the property name followed by the value of the property or script.</span></span> <span data-ttu-id="c1f4d-135">La creazione di una visualizzazione elenco è molto simile a inviare tramite pipe un oggetto al cmdlet `Format-List`.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-135">Creating a list view is very similar to piping an object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="c1f4d-136">Per ulteriori informazioni su questa visualizzazione, vedere [visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="c1f4d-136">For more information about this view, see [List View](./creating-a-list-view.md).</span></span>

<span data-ttu-id="c1f4d-137">Visualizzazione estesa elenca una singola proprietà di un oggetto o un valore di script in una o più colonne.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-137">Wide View Lists a single property of an object or a script value in one or more columns.</span></span> <span data-ttu-id="c1f4d-138">Nessuna etichetta o intestazione per questa visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-138">There is no label or header for this view.</span></span> <span data-ttu-id="c1f4d-139">La creazione di una visualizzazione estesa è molto simile a inviare tramite pipe un oggetto al cmdlet `Format-Wide`.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-139">Creating a wide view is very similar to piping an object to the `Format-Wide` cmdlet.</span></span> <span data-ttu-id="c1f4d-140">Per ulteriori informazioni su questa visualizzazione, vedere [visualizzazione estesa](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="c1f4d-140">For more information about this view, see [Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="c1f4d-141">Visualizzazione personalizzata consente di visualizzare una visualizzazione personalizzabile delle proprietà degli oggetti o dei valori di script che non sono conformi alla struttura rigida delle visualizzazioni di tabella, delle visualizzazioni elenco o delle visualizzazioni estese.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-141">Custom View Displays a customizable view of object properties or script values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="c1f4d-142">È possibile definire una visualizzazione personalizzata autonoma oppure è possibile definire una visualizzazione personalizzata utilizzata da un'altra visualizzazione, ad esempio una visualizzazione tabella o una visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-142">You can define a stand-alone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="c1f4d-143">La creazione di una vista personalizzata è molto simile a inviare tramite pipe un oggetto al cmdlet `Format-Custom`.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-143">Creating a custom view is very similar to piping an object to the `Format-Custom` cmdlet.</span></span> <span data-ttu-id="c1f4d-144">Per ulteriori informazioni su questa visualizzazione, vedere [visualizzazione personalizzata](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="c1f4d-144">For more information about this view, see [Custom View](./creating-custom-controls.md).</span></span>

## <a name="components-of-a-view"></a><span data-ttu-id="c1f4d-145">Componenti di una vista</span><span class="sxs-lookup"><span data-stu-id="c1f4d-145">Components of a View</span></span>

<span data-ttu-id="c1f4d-146">Negli esempi XML seguenti vengono illustrati i componenti XML di base di una vista.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-146">The following XML examples show the basic XML components of a view.</span></span> <span data-ttu-id="c1f4d-147">I singoli elementi XML variano a seconda della visualizzazione che si desidera creare, ma i componenti di base delle visualizzazioni sono tutti uguali.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-147">The individual XML elements vary depending on which view you want to create, but the basic components of the views are all the same.</span></span>

<span data-ttu-id="c1f4d-148">Per iniziare, ogni visualizzazione dispone di un elemento `Name` che specifica un nome descrittivo utilizzato per fare riferimento alla vista.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-148">To start with, each view has a `Name` element that specifies a user friendly name that is used to reference the view.</span></span> <span data-ttu-id="c1f4d-149">elemento `ViewSelectedBy` che definisce quali oggetti .NET vengono visualizzati dalla visualizzazione e un elemento *Control* che definisce la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-149">a `ViewSelectedBy` element that defines which .NET objects are displayed by the view, and a *control* element that defines the view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

<span data-ttu-id="c1f4d-150">All'interno dell'elemento Control è possibile definire uno o più elementi *entry* .</span><span class="sxs-lookup"><span data-stu-id="c1f4d-150">Within the control element, you can define one or more *entry* elements.</span></span> <span data-ttu-id="c1f4d-151">Se si usano più definizioni, è necessario specificare gli oggetti .NET che usano ogni definizione.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-151">If you use multiple definitions, you must specify which .NET objects use each definition.</span></span> <span data-ttu-id="c1f4d-152">In genere, per ogni controllo è necessaria una sola voce con una sola definizione.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-152">Typically only one entry, with only one definition, is needed for each control.</span></span>

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

<span data-ttu-id="c1f4d-153">All'interno di ogni elemento entry di una vista, si specificano gli elementi *Item* che definiscono le proprietà .NET o gli script visualizzati da tale visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-153">Within each entry element of a view, you specify the *item* elements that define the .NET properties or scripts that are displayed by that view.</span></span>

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

<span data-ttu-id="c1f4d-154">Come illustrato negli esempi precedenti, il file di formattazione può contenere più visualizzazioni, una vista può contenere più definizioni e ogni definizione può contenere più elementi.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-154">As shown in the preceding examples, the formatting file can contain multiple views, a view can contain multiple definitions, and each definition can contain multiple items.</span></span>

## <a name="example-of-a-table-view"></a><span data-ttu-id="c1f4d-155">Esempio di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="c1f4d-155">Example of a Table View</span></span>

<span data-ttu-id="c1f4d-156">Nell'esempio seguente vengono illustrati i tag XML utilizzati per definire una vista tabella contenente due colonne.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-156">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="c1f4d-157">L'elemento [ViewDefinitions](./viewdefinitions-element-format.md) è l'elemento contenitore per tutte le visualizzazioni definite nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-157">The [ViewDefinitions](./viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="c1f4d-158">L'elemento [View](./view-element-format.md) definisce la tabella, l'elenco, la larghezza o la visualizzazione personalizzata specifica.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-158">The [View](./view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="c1f4d-159">All'interno di ogni elemento di [visualizzazione](./view-element-format.md) , l'elemento [Name](./name-element-for-view-format.md) specifica il nome della vista, l'elemento [ViewSelectedBy](./viewselectedby-element-format.md) definisce gli oggetti che utilizzano la visualizzazione e i diversi elementi del controllo, ad esempio l'elemento `TableControl` illustrato nell'esempio seguente, definiscono il tipo della visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="c1f4d-159">Within each [View](./view-element-format.md) element, the [Name](./name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element shown in the following example) define the type of the view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="c1f4d-160">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c1f4d-160">See Also</span></span>

[<span data-ttu-id="c1f4d-161">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="c1f4d-161">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c1f4d-162">Creazione di una vista tabella</span><span class="sxs-lookup"><span data-stu-id="c1f4d-162">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c1f4d-163">Creazione di una visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="c1f4d-163">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="c1f4d-164">Creazione di controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="c1f4d-164">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="c1f4d-165">Scrittura di un file di formattazione e di tipi di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c1f4d-165">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
