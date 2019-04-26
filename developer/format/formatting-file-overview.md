---
title: Panoramica dei File di formattazione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065734"
---
# <a name="formatting-file-overview"></a><span data-ttu-id="f7de4-102">Panoramica dei file di formattazione</span><span class="sxs-lookup"><span data-stu-id="f7de4-102">Formatting File Overview</span></span>

<span data-ttu-id="f7de4-103">Il formato di visualizzazione per gli oggetti che vengono restituiti dai comandi (cmdlet, funzioni e script) sono definiti tramite file di formattazione (format.ps1xml file).</span><span class="sxs-lookup"><span data-stu-id="f7de4-103">The display format for the objects that are returned by commands (cmdlets, functions, and scripts) are defined by using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="f7de4-104">Molti di questi file vengono forniti da PowerShell per definire il formato di visualizzazione per gli oggetti restituiti dai comandi di PowerShell fornito, come le [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto restituito dal `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f7de4-104">Several of these files are provided by PowerShell to define the display format for those objects returned by PowerShell-provided commands, such as the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object returned by the `Get-Process` cmdlet.</span></span> <span data-ttu-id="f7de4-105">Tuttavia, è anche possibile creare i proprio file di formattazione personalizzati per sovrascrivere i formati di visualizzazione predefinito o è possibile scrivere un file di formattazione personalizzato per definire la visualizzazione degli oggetti restituiti dai propri comandi.</span><span class="sxs-lookup"><span data-stu-id="f7de4-105">However, you can also create your own custom formatting files to overwrite the default display formats or you can write a custom formatting file to define the display of objects returned by your own commands.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f7de4-106">File di formattazione non determinano gli elementi di un oggetto che vengono restituiti alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="f7de4-106">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="f7de4-107">Quando un oggetto viene restituito alla pipeline, tutti i membri di tale oggetto sono disponibili anche se alcuni non vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="f7de4-107">When an object is returned to the pipeline, all members of that object are available even if some are not displayed.</span></span>

<span data-ttu-id="f7de4-108">PowerShell Usa i dati in questi file di formattazione per determinare quali informazioni visualizzare e come formattare i dati visualizzati.</span><span class="sxs-lookup"><span data-stu-id="f7de4-108">PowerShell uses the data in these formatting files to determine what is displayed and how the displayed data is formatted.</span></span> <span data-ttu-id="f7de4-109">I dati visualizzati possono includere le proprietà di un oggetto o il valore di uno script.</span><span class="sxs-lookup"><span data-stu-id="f7de4-109">The displayed data can include the properties of an object or the value of a script.</span></span> <span data-ttu-id="f7de4-110">Gli script vengono utilizzati se si desidera visualizzare un valore che non è disponibile direttamente dalle proprietà di un oggetto, ad esempio aggiungere il valore di due proprietà di un oggetto e quindi Visualizza la somma come una porzione di dati.</span><span class="sxs-lookup"><span data-stu-id="f7de4-110">Scripts are used if you want to display some value that is not available directly from the properties of an object, such as adding the value of two properties of an object and then displaying the sum as a piece of data.</span></span> <span data-ttu-id="f7de4-111">Formattazione dei dati visualizzati viene eseguita definendo le visualizzazioni per gli oggetti che si desidera visualizzare.</span><span class="sxs-lookup"><span data-stu-id="f7de4-111">Formatting of the displayed data is done by defining views for the objects that you want to display.</span></span> <span data-ttu-id="f7de4-112">È possibile definire una singola visualizzazione per ogni oggetto, è possibile definire una singola visualizzazione per più oggetti o è possibile definire più visualizzazioni per lo stesso oggetto.</span><span class="sxs-lookup"><span data-stu-id="f7de4-112">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="f7de4-113">Non sono previsti limiti al numero di visualizzazioni che è possibile definire.</span><span class="sxs-lookup"><span data-stu-id="f7de4-113">There is no limit to the number of views that you can define.</span></span>

## <a name="common-features-of-formatting-files"></a><span data-ttu-id="f7de4-114">Funzionalità comuni di file di formattazione</span><span class="sxs-lookup"><span data-stu-id="f7de4-114">Common Features of Formatting Files</span></span>

<span data-ttu-id="f7de4-115">Ogni file di formattazione possa definire i componenti seguenti che possono essere condivise tra tutte le viste definite nel file:</span><span class="sxs-lookup"><span data-stu-id="f7de4-115">Each formatting file can define the following components that can be shared across all the views defined by the file:</span></span>

- <span data-ttu-id="f7de4-116">Impostazione di configurazione, ad esempio se i dati visualizzati nelle righe delle tabelle verranno visualizzati nella riga successiva se i dati sono più lunghi rispetto alla larghezza della colonna.</span><span class="sxs-lookup"><span data-stu-id="f7de4-116">Default configuration setting, such as whether the data displayed in the rows of tables will be displayed on the next line if the data is longer than the width of the column.</span></span> <span data-ttu-id="f7de4-117">Per altre informazioni su queste impostazioni, vedere [definizione delle impostazioni di configurazione comuni](./defining-common-configuration-features.md).</span><span class="sxs-lookup"><span data-stu-id="f7de4-117">For more information about these settings, see [Defining Common Configuration Settings](./defining-common-configuration-features.md).</span></span>

- <span data-ttu-id="f7de4-118">Set di oggetti che possono essere visualizzati da qualsiasi visualizzazione del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="f7de4-118">Sets of objects that can be displayed by any of the views of the formatting file.</span></span> <span data-ttu-id="f7de4-119">Per altre informazioni su questi set (detta *set di selezione*), vedere [definizione imposta di oggetti](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="f7de4-119">For more information about these sets (referred to as *selection sets*), see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

- <span data-ttu-id="f7de4-120">Controlli comuni che possono essere usati da tutte le visualizzazioni del file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="f7de4-120">Common controls that can be used by all the views of the formatting file.</span></span> <span data-ttu-id="f7de4-121">I controlli consentono un controllo più preciso su modalità di visualizzazione dati.</span><span class="sxs-lookup"><span data-stu-id="f7de4-121">Controls give you finer control on how data is displayed.</span></span> <span data-ttu-id="f7de4-122">Per altre informazioni sui controlli, vedere [definire i controlli personalizzati](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="f7de4-122">For more information about controls, see [Defining Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="formatting-views"></a><span data-ttu-id="f7de4-123">Le visualizzazioni di formattazione</span><span class="sxs-lookup"><span data-stu-id="f7de4-123">Formatting Views</span></span>

<span data-ttu-id="f7de4-124">Formattazione viste è possono visualizzare gli oggetti in un formato di tabella, formato di elenco, formato grande e formato personalizzato.</span><span class="sxs-lookup"><span data-stu-id="f7de4-124">Formatting views can display objects in a table format, list format, wide format, and custom format.</span></span> <span data-ttu-id="f7de4-125">Nella maggior parte, ogni definizione di formattazione è descritta da un set di tag XML che descrivono la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="f7de4-125">For the most part, each formatting definition is described by a set of XML tags that describe the view.</span></span> <span data-ttu-id="f7de4-126">Ogni visualizzazione contiene il nome della visualizzazione, gli oggetti che utilizzano la vista e gli elementi della visualizzazione, ad esempio le informazioni di colonna e riga per una visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="f7de4-126">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="f7de4-127">Visualizza gli elenchi delle proprietà di un oggetto o un valore di blocco di script in una o più colonne di tabella.</span><span class="sxs-lookup"><span data-stu-id="f7de4-127">Table View Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="f7de4-128">Ogni colonna rappresenta una singola proprietà dell'oggetto o un valore di script.</span><span class="sxs-lookup"><span data-stu-id="f7de4-128">Each column represents a single property of the object or a script value.</span></span> <span data-ttu-id="f7de4-129">È possibile definire una visualizzazione tabella che visualizza tutte le proprietà di un oggetto, un subset delle proprietà di un oggetto o una combinazione di proprietà e valori di script.</span><span class="sxs-lookup"><span data-stu-id="f7de4-129">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script values.</span></span> <span data-ttu-id="f7de4-130">Ogni riga della tabella rappresenta un oggetto restituito.</span><span class="sxs-lookup"><span data-stu-id="f7de4-130">Each row of the table represents a returned object.</span></span> <span data-ttu-id="f7de4-131">Creazione di una visualizzazione tabella è molto simile a quando si invia tramite pipe un oggetto per il `Format-Table` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f7de4-131">Creating a table view is very similar to when you pipe an object to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="f7de4-132">Per altre informazioni su questa vista, vedere [vista tabella](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f7de4-132">For more information about this view, see [Table View](./creating-a-table-view.md).</span></span>

<span data-ttu-id="f7de4-133">Elenco nella visualizzazione sono elencate le proprietà di un oggetto o un valore di uno script in una singola colonna.</span><span class="sxs-lookup"><span data-stu-id="f7de4-133">List View Lists the properties of an object or a script value in a single column.</span></span> <span data-ttu-id="f7de4-134">Ogni riga dell'elenco Visualizza un'etichetta facoltativa o il nome della proprietà seguito dal valore della proprietà o dello script.</span><span class="sxs-lookup"><span data-stu-id="f7de4-134">Each row of the list displays an optional label or the property name followed by the value of the property or script.</span></span> <span data-ttu-id="f7de4-135">Creazione di una visualizzazione elenco è molto simile a tramite pipe un oggetto per il `Format-List` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f7de4-135">Creating a list view is very similar to piping an object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="f7de4-136">Per altre informazioni su questa vista, vedere [visualizzazione elenco](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="f7de4-136">For more information about this view, see [List View](./creating-a-list-view.md).</span></span>

<span data-ttu-id="f7de4-137">Visualizzazione più ampia elenca una singola proprietà di un oggetto o un valore di uno script in una o più colonne.</span><span class="sxs-lookup"><span data-stu-id="f7de4-137">Wide View Lists a single property of an object or a script value in one or more columns.</span></span> <span data-ttu-id="f7de4-138">Non sono etichetta o intestazione per questa visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="f7de4-138">There is no label or header for this view.</span></span> <span data-ttu-id="f7de4-139">Creazione di una visualizzazione più ampia è molto simile a tramite pipe un oggetto per il `Format-Wide` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f7de4-139">Creating a wide view is very similar to piping an object to the `Format-Wide` cmdlet.</span></span> <span data-ttu-id="f7de4-140">Per altre informazioni su questa vista, vedere [visualizzazione estesa](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="f7de4-140">For more information about this view, see [Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="f7de4-141">Visualizzazione personalizzata Visualizza una visualizzazione di proprietà degli oggetti o valori dello script personalizzabile che non rispettano la struttura rigida di viste delle tabelle, visualizzazioni elenco o visualizzazioni ampie.</span><span class="sxs-lookup"><span data-stu-id="f7de4-141">Custom View Displays a customizable view of object properties or script values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="f7de4-142">È possibile definire una visualizzazione personalizzata autonoma oppure è possibile definire una visualizzazione personalizzata che viene usata da un'altra visualizzazione, ad esempio una tabella o una vista elenco.</span><span class="sxs-lookup"><span data-stu-id="f7de4-142">You can define a stand-alone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="f7de4-143">Creare una visualizzazione personalizzata è molto simile a tramite pipe un oggetto per il `Format-Custom` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f7de4-143">Creating a custom view is very similar to piping an object to the `Format-Custom` cmdlet.</span></span> <span data-ttu-id="f7de4-144">Per altre informazioni su questa vista, vedere [vista personalizzata](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="f7de4-144">For more information about this view, see [Custom View](./creating-custom-controls.md).</span></span>

## <a name="components-of-a-view"></a><span data-ttu-id="f7de4-145">Componenti di una vista</span><span class="sxs-lookup"><span data-stu-id="f7de4-145">Components of a View</span></span>

<span data-ttu-id="f7de4-146">Gli esempi XML seguenti illustrano i componenti di base XML di una vista.</span><span class="sxs-lookup"><span data-stu-id="f7de4-146">The following XML examples show the basic XML components of a view.</span></span> <span data-ttu-id="f7de4-147">I singoli elementi XML variano a seconda di quale visualizzazione si vuole creare, ma i componenti di base delle viste sono tutti uguali.</span><span class="sxs-lookup"><span data-stu-id="f7de4-147">The individual XML elements vary depending on which view you want to create, but the basic components of the views are all the same.</span></span>

<span data-ttu-id="f7de4-148">Per iniziare, ogni visualizzazione dispone di un `Name` elemento che specifica un nome descrittivo usato per fare riferimento la vista.</span><span class="sxs-lookup"><span data-stu-id="f7de4-148">To start with, each view has a `Name` element that specifies a user friendly name that is used to reference the view.</span></span> <span data-ttu-id="f7de4-149">una `ViewSelectedBy` elemento che definisce quali oggetti .NET vengono visualizzati dalla visualizzazione, e una *controllo* elemento che definisce la vista.</span><span class="sxs-lookup"><span data-stu-id="f7de4-149">a `ViewSelectedBy` element that defines which .NET objects are displayed by the view, and a *control* element that defines the view.</span></span>

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

<span data-ttu-id="f7de4-150">All'interno dell'elemento di controllo, è possibile definire uno o più *voce* elementi.</span><span class="sxs-lookup"><span data-stu-id="f7de4-150">Within the control element, you can define one or more *entry* elements.</span></span> <span data-ttu-id="f7de4-151">Se si usano più definizioni, è necessario specificare quali oggetti .NET usano ogni definizione.</span><span class="sxs-lookup"><span data-stu-id="f7de4-151">If you use multiple definitions, you must specify which .NET objects use each definition.</span></span> <span data-ttu-id="f7de4-152">In genere solo una voce, con una sola definizione, è necessaria per ogni controllo.</span><span class="sxs-lookup"><span data-stu-id="f7de4-152">Typically only one entry, with only one definition, is needed for each control.</span></span>

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

<span data-ttu-id="f7de4-153">All'interno di ogni elemento della voce di una vista, si specifica la *elemento* gli elementi che definiscono le proprietà .NET o script che vengono visualizzate per tale vista.</span><span class="sxs-lookup"><span data-stu-id="f7de4-153">Within each entry element of a view, you specify the *item* elements that define the .NET properties or scripts that are displayed by that view.</span></span>

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

<span data-ttu-id="f7de4-154">Come illustrato negli esempi precedenti, il file di formattazione può contenere più viste, una vista può contenere più definizioni e ogni definizione può contenere più elementi.</span><span class="sxs-lookup"><span data-stu-id="f7de4-154">As shown in the preceding examples, the formatting file can contain multiple views, a view can contain multiple definitions, and each definition can contain multiple items.</span></span>

## <a name="example-of-a-table-view"></a><span data-ttu-id="f7de4-155">Esempio di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="f7de4-155">Example of a Table View</span></span>

<span data-ttu-id="f7de4-156">Nell'esempio seguente mostra i tag XML utilizzati per definire una visualizzazione tabella che contiene due colonne.</span><span class="sxs-lookup"><span data-stu-id="f7de4-156">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="f7de4-157">Il [ViewDefinitions](./viewdefinitions-element-format.md) elemento corrisponde all'elemento contenitore per tutte le viste definite nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="f7de4-157">The [ViewDefinitions](./viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="f7de4-158">Il [vista](./view-element-format.md) elemento definisce la tabella specifica, elenco, visualizzazione wide o personalizzato.</span><span class="sxs-lookup"><span data-stu-id="f7de4-158">The [View](./view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="f7de4-159">All'interno di ciascun [vista](./view-element-format.md) elemento, il [nome](./name-element-for-view-format.md) elemento specifica il nome della visualizzazione, il [ViewSelectedBy](./viewselectedby-element-format.md) elemento definisce gli oggetti che utilizzano la vista e i diversi gli elementi del controllo (ad esempio il `TableControl` elemento mostrato nell'esempio seguente) definiscono il tipo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="f7de4-159">Within each [View](./view-element-format.md) element, the [Name](./name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element shown in the following example) define the type of the view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f7de4-160">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f7de4-160">See Also</span></span>

[<span data-ttu-id="f7de4-161">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="f7de4-161">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f7de4-162">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="f7de4-162">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f7de4-163">Creazione di una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="f7de4-163">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="f7de4-164">Creazione di controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="f7de4-164">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="f7de4-165">La scrittura di una formattazione di PowerShell e dei tipi</span><span class="sxs-lookup"><span data-stu-id="f7de4-165">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
