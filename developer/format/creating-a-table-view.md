---
title: Creazione di una visualizzazione tabella | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 862f942facafff6cea66c4f8f1040772c6a62ec3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066839"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="a2ce0-102">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="a2ce0-102">Creating a Table View</span></span>

<span data-ttu-id="a2ce0-103">Una visualizzazione tabella visualizza i dati in una o più colonne.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-103">A table view displays data in one or more columns.</span></span> <span data-ttu-id="a2ce0-104">Ogni riga della tabella rappresenta un oggetto .NET e ogni colonna della tabella rappresenta una proprietà dell'oggetto o un valore di script.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-104">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="a2ce0-105">È possibile definire una visualizzazione tabella che visualizza tutte le proprietà di un oggetto o un subset delle proprietà di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-105">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="a2ce0-106">Una visualizzazione di tabella</span><span class="sxs-lookup"><span data-stu-id="a2ce0-106">A Table View Display</span></span>

<span data-ttu-id="a2ce0-107">Nell'esempio seguente viene illustrato come Windows PowerShell consente di visualizzare il [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) l'oggetto restituito dalle [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-107">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="a2ce0-108">Per questo oggetto, Windows PowerShell è stato definito una vista tabella contenente le `Status` proprietà, il `Name` proprietà (questa proprietà è una proprietà alias per il `ServiceName` proprietà) e il `DisplayName` proprietà.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-108">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="a2ce0-109">Ogni riga della tabella rappresenta un oggetto restituito dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-109">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="a2ce0-110">Che definisce la vista tabella</span><span class="sxs-lookup"><span data-stu-id="a2ce0-110">Defining the Table View</span></span>

<span data-ttu-id="a2ce0-111">Il codice XML seguente viene illustrato lo schema della vista tabella per la visualizzazione di [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) oggetto.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-111">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="a2ce0-112">È necessario specificare ogni proprietà che si desidera visualizzare nella visualizzazione della tabella.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-112">You must specify each property that you want displayed in the table view.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>8</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>18</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>38</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

<span data-ttu-id="a2ce0-113">Gli elementi XML seguenti vengono usati per definire una visualizzazione elenco:</span><span class="sxs-lookup"><span data-stu-id="a2ce0-113">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="a2ce0-114">Il [vista](./view-element-format.md) è l'elemento padre della visualizzazione della tabella.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-114">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="a2ce0-115">(Questo è lo stesso elemento padre per l'elenco, le viste di controllo wide e personalizzati).</span><span class="sxs-lookup"><span data-stu-id="a2ce0-115">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="a2ce0-116">Il [nome](./name-element-for-view-format.md) elemento specifica il nome della visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="a2ce0-117">Questo elemento è obbligatorio per tutte le visualizzazioni.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-117">This element is required for all views.</span></span>

- <span data-ttu-id="a2ce0-118">Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento definisce gli oggetti che utilizzano la vista.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="a2ce0-119">Questo elemento è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-119">This element is required.</span></span>

- <span data-ttu-id="a2ce0-120">Il [GroupBy](./groupby-element-for-view-format.md) elemento (non illustrato in questo esempio) consente di definire quando viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-120">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="a2ce0-121">Ogni volta che cambia il valore di una proprietà specifica o uno script, viene avviato un nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="a2ce0-122">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-122">This element is optional.</span></span>

- <span data-ttu-id="a2ce0-123">Il [controlli](./controls-element-for-view-format.md) elemento (non illustrato in questo esempio) consente di definire i controlli personalizzati che sono definiti dalla visualizzazione della tabella.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-123">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="a2ce0-124">Controlli offrono un modo per specificare ulteriormente la modalità di visualizzazione dei dati.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="a2ce0-125">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-125">This element is optional.</span></span> <span data-ttu-id="a2ce0-126">Una vista può definire propri controlli personalizzati, oppure è possibile usare i controlli comuni che possono essere usati da qualsiasi visualizzazione nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="a2ce0-127">Per altre informazioni sui controlli personalizzati, vedere [Creating Custom Controls](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="a2ce0-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="a2ce0-128">Il [HideTableHeaders](./hidetableheaders-element-format.md) elemento (non riportato in questo esempio) consente di specificare che la tabella non visualizzerà le etichette nella parte superiore della tabella.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-128">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="a2ce0-129">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-129">This element is optional.</span></span>

- <span data-ttu-id="a2ce0-130">Il [Table](./tablecontrol-element-format.md) elemento che definisce le informazioni di intestazione e di riga della tabella.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-130">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="a2ce0-131">Analogamente a tutte le altre visualizzazioni, una visualizzazione tabella può visualizzare i valori delle proprietà degli oggetti o valori generati da script.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-131">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="a2ce0-132">La definizione di intestazioni di colonna</span><span class="sxs-lookup"><span data-stu-id="a2ce0-132">Defining Column Headers</span></span>

1. <span data-ttu-id="a2ce0-133">Il [TableHeaders](./tableheaders-element-format.md) elemento e i relativi elementi figlio definiscono che cosa viene visualizzata nella parte superiore della tabella.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-133">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="a2ce0-134">Il [TableColumnHeader](./tablecolumnheader-element-format.md) elemento definisce gli elementi visualizzati nella parte superiore di una colonna della tabella.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-134">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="a2ce0-135">Questi elementi vengono specificati nell'ordine in cui le intestazioni visualizzate.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-135">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="a2ce0-136">Non sono previsti limiti per il numero di questi elemento che è possibile usare, ma il numero di [TableColumnHeader](./tablecolumnheader-element-format.md) devono essere uguale il numero di elementi nella visualizzazione tabella [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elementi usati.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-136">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="a2ce0-137">Il [etichetta](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento specifica il testo visualizzato.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-137">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="a2ce0-138">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-138">This element is optional.</span></span>

4. <span data-ttu-id="a2ce0-139">Il [larghezza](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento specifica la larghezza (in caratteri) della colonna.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-139">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="a2ce0-140">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-140">This element is optional.</span></span>

5. <span data-ttu-id="a2ce0-141">Il [allineamento](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento specifica come viene visualizzata l'etichetta.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-141">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="a2ce0-142">L'etichetta può essere allineato a sinistra, a destra, o al centro.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-142">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="a2ce0-143">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-143">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="a2ce0-144">Definire le righe della tabella</span><span class="sxs-lookup"><span data-stu-id="a2ce0-144">Defining the Table Rows</span></span>

<span data-ttu-id="a2ce0-145">Le visualizzazioni di tabelle possono fornire una o più definizioni che specificano quali dati vengono visualizzati nelle righe della tabella usando gli elementi figlio del [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-145">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="a2ce0-146">Si noti che è possibile specificare più definizioni per le righe della tabella, ma le intestazioni per le righe rimane lo stesso, indipendentemente da quale definizione di riga viene usata.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-146">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="a2ce0-147">In genere, una tabella avrà una sola definizione.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-147">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="a2ce0-148">Nell'esempio seguente, la vista fornisce una singola definizione che consente di visualizzare i valori delle diverse proprietà del [Diagnostics? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) oggetto.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-148">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="a2ce0-149">Visualizzazione di una tabella è possibile visualizzare il valore di una proprietà o il valore di uno script (non illustrato nell'esempio) nelle righe Dell.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-149">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

```xml
<TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>

```

<span data-ttu-id="a2ce0-150">Gli elementi XML seguenti sono utilizzabile per fornire le definizioni per una riga:</span><span class="sxs-lookup"><span data-stu-id="a2ce0-150">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="a2ce0-151">Il [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) elemento e i relativi elementi figlio definiscono che cosa viene visualizzata nelle righe della tabella.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-151">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="a2ce0-152">Il [TableRowEntry](./listentry-element-for-listcontrol-format.md) elemento fornisce una definizione della riga.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-152">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="a2ce0-153">Almeno un [TableRowEntry](./listentry-element-for-listcontrol-format.md) è obbligatorio; tuttavia, non è definito alcun limite massimo al numero di elementi che è possibile aggiungere.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-153">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="a2ce0-154">Nella maggior parte dei casi, una vista avrà una sola definizione.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-154">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="a2ce0-155">Il [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento specifica gli oggetti visualizzati da una definizione specifica.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-155">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="a2ce0-156">Questo elemento è facoltativo ed è necessario solo quando si definiscono più [TableRowEntry](./listentry-element-for-listcontrol-format.md) gli elementi che consentono di visualizzare diversi oggetti.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-156">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="a2ce0-157">Il [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) elemento specifica che il testo che supera la larghezza della colonna viene visualizzato nella riga successiva.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-157">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="a2ce0-158">Per impostazione predefinita, il testo di dimensioni superiori alla larghezza della colonna viene troncato.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-158">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="a2ce0-159">Il [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) elemento definisce le proprietà o gli script i cui valori vengono visualizzati nella riga.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-159">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="a2ce0-160">Il [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento definisce le proprietà il cui valore viene visualizzato nella colonna della riga di script.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-160">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="a2ce0-161">Oggetto [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento è obbligatorio per ogni colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="a2ce0-162">La prima voce viene visualizzata nella prima colonna, la seconda voce nella seconda colonna e così via.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-162">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="a2ce0-163">Il [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento specifica la proprietà il cui valore viene visualizzato nella riga.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-163">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="a2ce0-164">È necessario specificare una proprietà o uno script, ma è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-164">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="a2ce0-165">Il [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento specifica lo script il cui valore viene visualizzato nella riga.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-165">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="a2ce0-166">È necessario specificare uno script o una proprietà, ma è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-166">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="a2ce0-167">Il [FormatString](./label-element-for-listitem-for-listcontrol-format.md) elemento specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-167">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="a2ce0-168">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-168">This element is optional.</span></span>

- <span data-ttu-id="a2ce0-169">Il [allineamento](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento specifica come viene visualizzato il valore della proprietà o dello script.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-169">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="a2ce0-170">Il valore può essere allineato a sinistra, a destra, o al centro.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-170">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="a2ce0-171">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-171">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="a2ce0-172">Definire gli oggetti che utilizzano la vista tabella</span><span class="sxs-lookup"><span data-stu-id="a2ce0-172">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="a2ce0-173">Esistono due modi per definire quali oggetti .NET usano la visualizzazione di tabella.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-173">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="a2ce0-174">È possibile usare la [ViewSelectedBy](./viewselectedby-element-format.md) elemento per definire gli oggetti che possono essere visualizzati da tutte le definizioni di visualizzazione, oppure è possibile utilizzare il [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento per definire quali oggetti vengono visualizzati da un definizione della vista specifica.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-174">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="a2ce0-175">Nella maggior parte dei casi, una vista ha una sola definizione, in modo che gli oggetti vengono in genere definiti per il [ViewSelectedBy](./viewselectedby-element-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-175">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="a2ce0-176">Nell'esempio seguente viene illustrato come definire gli oggetti che vengono visualizzati per la visualizzazione di tabella usando il [ViewSelectedBy](./viewselectedby-element-format.md) e [nomeTipo](./typename-element-for-viewselectedby-format.md) elementi.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-176">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="a2ce0-177">Non sono previsti limiti al numero di [TypeName](./typename-element-for-viewselectedby-format.md) gli elementi che è possibile specificare l'ordine non è significativo.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-177">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="a2ce0-178">Gli elementi XML seguenti sono utilizzabile per specificare gli oggetti utilizzati per la visualizzazione di tabella:</span><span class="sxs-lookup"><span data-stu-id="a2ce0-178">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="a2ce0-179">Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento definisce gli oggetti che vengono visualizzati nella visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="a2ce0-180">Il [TypeName](./typename-element-for-viewselectedby-format.md) elemento specifica l'oggetto .NET che viene visualizzato nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-180">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="a2ce0-181">Il nome del tipo .NET completo è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-181">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="a2ce0-182">È necessario specificare almeno un tipo o la selezione impostato per la visualizzazione, ma nessun numero massimo di elementi che possono essere specificati.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-182">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="a2ce0-183">L'esempio seguente usa il [ViewSelectedBy](./viewselectedby-element-format.md) e [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementi.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-183">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="a2ce0-184">Usare i set di selezione in cui è presente un set correlato di oggetti che vengono visualizzati utilizzando più viste, ad esempio quando si definisce una visualizzazione elenco e visualizzazione di una tabella per gli oggetti stessi.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-184">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="a2ce0-185">Per altre informazioni su come creare un set di selezione, vedere [definizione di set di selezione](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="a2ce0-185">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="a2ce0-186">Gli elementi XML seguenti sono utilizzabile per specificare gli oggetti utilizzati dalla visualizzazione elenco:</span><span class="sxs-lookup"><span data-stu-id="a2ce0-186">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="a2ce0-187">Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento definisce gli oggetti che vengono visualizzati nella visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-187">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="a2ce0-188">Il [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento specifica un set di oggetti che possono essere visualizzati da parte della vista.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-188">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="a2ce0-189">È necessario specificare almeno un set di selezione o tipo per la visualizzazione, ma nessun numero massimo di elementi che possono essere specificati.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-189">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="a2ce0-190">Nell'esempio seguente viene illustrato come definire gli oggetti visualizzati da una definizione di specifica della visualizzazione tabella mediante la [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-190">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="a2ce0-191">Utilizzo di questo elemento, è possibile specificare il nome del tipo .NET dell'oggetto, un set di selezione di oggetti o una condizione di selezione che consente di specificare quando viene utilizzata la definizione.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-191">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="a2ce0-192">Per altre informazioni su come creare una selezione condizioni, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a2ce0-192">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a2ce0-193">Quando si creano più definizioni della visualizzazione della tabella che non è possibile specificare le intestazioni di colonna diverso.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-193">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="a2ce0-194">È possibile specificare solo gli elementi visualizzati nelle righe della tabella, ad esempio gli oggetti che vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-194">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="a2ce0-195">Gli elementi XML seguenti possono essere utilizzati per specificare gli oggetti usati da una definizione di specifica della visualizzazione elenco:</span><span class="sxs-lookup"><span data-stu-id="a2ce0-195">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="a2ce0-196">Il [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento definisce gli oggetti che vengono visualizzati per la definizione.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-196">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="a2ce0-197">Il [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) elemento specifica l'oggetto .NET che viene visualizzato per la definizione.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-197">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="a2ce0-198">Quando si usa questo elemento, è necessario il nome del tipo .NET completo.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-198">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="a2ce0-199">È necessario specificare almeno un tipo, set di selezione o condizione di selezione per la definizione, ma nessun numero massimo di elementi che possono essere specificati.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-199">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="a2ce0-200">Il [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) elemento (non mostrato) specifica un set di oggetti che possono essere visualizzati da questa definizione.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-200">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="a2ce0-201">È necessario specificare almeno un tipo, set di selezione o condizione di selezione per la definizione, ma nessun numero massimo di elementi che possono essere specificati.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-201">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="a2ce0-202">Il [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) elemento (non mostrato) specifica una condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-202">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="a2ce0-203">È necessario specificare almeno un tipo, set di selezione o condizione di selezione per la definizione, ma nessun numero massimo di elementi che possono essere specificati.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-203">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="a2ce0-204">Per altre informazioni sulla definizione di condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a2ce0-204">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="a2ce0-205">Stringhe di formato</span><span class="sxs-lookup"><span data-stu-id="a2ce0-205">Using Format Strings</span></span>

<span data-ttu-id="a2ce0-206">Stringhe di formattazione possono essere aggiunti a una visualizzazione per definire ulteriormente la modalità di visualizzazione dei dati.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-206">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="a2ce0-207">Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della `StartTime` proprietà.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-207">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="a2ce0-208">Gli elementi XML seguenti possono essere utilizzati per specificare uno schema di formattazione:</span><span class="sxs-lookup"><span data-stu-id="a2ce0-208">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="a2ce0-209">Il [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento definisce le proprietà il cui valore viene visualizzato nella colonna della riga di script.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-209">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="a2ce0-210">Oggetto [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento è obbligatorio per ogni colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="a2ce0-211">La prima voce viene visualizzata nella prima colonna, la seconda voce nella seconda colonna e così via.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-211">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="a2ce0-212">Il [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento specifica la proprietà il cui valore viene visualizzato nella riga.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-212">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="a2ce0-213">È necessario specificare una proprietà o uno script, ma è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-213">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="a2ce0-214">Il [FormatString](./label-element-for-listitem-for-listcontrol-format.md) elemento specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-214">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="a2ce0-215">Nell'esempio seguente, il `ToString` metodo viene chiamato per formattare il valore dello script.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-215">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="a2ce0-216">Gli script possono chiamare qualsiasi metodo di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-216">Scripts can call any method of an object.</span></span> <span data-ttu-id="a2ce0-217">Pertanto, se un oggetto dispone di un metodo, ad esempio `ToString`, che può avere parametri di formattazione, lo script può chiamare tale metodo per formattare il valore di output dello script.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-217">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="a2ce0-218">L'elemento XML seguente è utilizzabile per chiamare il `ToString` metodo:</span><span class="sxs-lookup"><span data-stu-id="a2ce0-218">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="a2ce0-219">Il [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento definisce le proprietà il cui valore viene visualizzato nella colonna della riga di script.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-219">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="a2ce0-220">Oggetto [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento è obbligatorio per ogni colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="a2ce0-221">La prima voce viene visualizzata nella prima colonna, la seconda voce nella seconda colonna e così via.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-221">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="a2ce0-222">Il [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento specifica lo script il cui valore viene visualizzato nella riga.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-222">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="a2ce0-223">È necessario specificare uno script o una proprietà, ma è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="a2ce0-223">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2ce0-224">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a2ce0-224">See Also</span></span>

[<span data-ttu-id="a2ce0-225">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="a2ce0-225">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
