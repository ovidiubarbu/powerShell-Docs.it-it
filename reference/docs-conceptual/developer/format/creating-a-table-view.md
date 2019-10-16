---
title: Creazione di una vista tabella | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 862f942facafff6cea66c4f8f1040772c6a62ec3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363410"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="ad44f-102">Creazione di una visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="ad44f-102">Creating a Table View</span></span>

<span data-ttu-id="ad44f-103">Una vista tabella consente di visualizzare i dati in una o più colonne.</span><span class="sxs-lookup"><span data-stu-id="ad44f-103">A table view displays data in one or more columns.</span></span> <span data-ttu-id="ad44f-104">Ogni riga della tabella rappresenta un oggetto .NET e ogni colonna della tabella rappresenta una proprietà dell'oggetto o un valore dello script.</span><span class="sxs-lookup"><span data-stu-id="ad44f-104">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="ad44f-105">È possibile definire una vista tabella che Visualizza tutte le proprietà di un oggetto o un subset delle proprietà di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="ad44f-105">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="ad44f-106">Visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="ad44f-106">A Table View Display</span></span>

<span data-ttu-id="ad44f-107">Nell'esempio seguente viene illustrato come Windows PowerShell visualizzi l'oggetto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) restituito dal cmdlet [Get-Service](/powershell/module/microsoft.powershell.management/get-service) .</span><span class="sxs-lookup"><span data-stu-id="ad44f-107">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="ad44f-108">Per questo oggetto, Windows PowerShell ha definito una vista tabella che visualizza la proprietà `Status`, la proprietà `Name` (questa proprietà è una proprietà alias per la proprietà `ServiceName`) e la proprietà `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="ad44f-108">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="ad44f-109">Ogni riga della tabella rappresenta un oggetto restituito dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ad44f-109">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="ad44f-110">Definizione della visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="ad44f-110">Defining the Table View</span></span>

<span data-ttu-id="ad44f-111">Nel codice XML seguente viene illustrato lo schema di visualizzazione tabella per la visualizzazione di [System. ServiceProcess. ServiceController? Oggetto DisplayProperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="ad44f-111">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="ad44f-112">È necessario specificare ogni proprietà che si desidera visualizzare nella visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="ad44f-112">You must specify each property that you want displayed in the table view.</span></span>

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

<span data-ttu-id="ad44f-113">Per definire una visualizzazione elenco vengono utilizzati gli elementi XML seguenti:</span><span class="sxs-lookup"><span data-stu-id="ad44f-113">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="ad44f-114">L'elemento [View](./view-element-format.md) è l'elemento padre della visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="ad44f-114">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="ad44f-115">(Si tratta dello stesso elemento padre per le visualizzazioni elenco, Wide e Custom Control).</span><span class="sxs-lookup"><span data-stu-id="ad44f-115">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="ad44f-116">L'elemento [Name](./name-element-for-view-format.md) specifica il nome della vista.</span><span class="sxs-lookup"><span data-stu-id="ad44f-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="ad44f-117">Questo elemento è obbligatorio per tutte le visualizzazioni.</span><span class="sxs-lookup"><span data-stu-id="ad44f-117">This element is required for all views.</span></span>

- <span data-ttu-id="ad44f-118">L'elemento [ViewSelectedBy](./viewselectedby-element-format.md) definisce gli oggetti che utilizzano la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="ad44f-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="ad44f-119">Questo elemento è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="ad44f-119">This element is required.</span></span>

- <span data-ttu-id="ad44f-120">L'elemento [GroupBy](./groupby-element-for-view-format.md) (non illustrato in questo esempio) definisce quando viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="ad44f-120">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="ad44f-121">Un nuovo gruppo viene avviato ogni volta che viene modificato il valore di una proprietà o di uno script specifico.</span><span class="sxs-lookup"><span data-stu-id="ad44f-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="ad44f-122">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="ad44f-122">This element is optional.</span></span>

- <span data-ttu-id="ad44f-123">L'elemento [Controls](./controls-element-for-view-format.md) (non illustrato in questo esempio) definisce i controlli personalizzati definiti dalla visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="ad44f-123">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="ad44f-124">I controlli consentono di specificare in modo più dettagliato la modalità di visualizzazione dei dati.</span><span class="sxs-lookup"><span data-stu-id="ad44f-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="ad44f-125">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="ad44f-125">This element is optional.</span></span> <span data-ttu-id="ad44f-126">Una vista può definire i propri controlli personalizzati oppure può utilizzare controlli comuni che possono essere utilizzati da qualsiasi visualizzazione nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="ad44f-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="ad44f-127">Per ulteriori informazioni sui controlli personalizzati, vedere [creazione di controlli personalizzati](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="ad44f-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="ad44f-128">L'elemento [HideTableHeaders](./hidetableheaders-element-format.md) (non visualizzato in questo esempio) specifica che nella tabella non verrà visualizzata alcuna etichetta nella parte superiore della tabella.</span><span class="sxs-lookup"><span data-stu-id="ad44f-128">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="ad44f-129">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="ad44f-129">This element is optional.</span></span>

- <span data-ttu-id="ad44f-130">Elemento [Table (](./tablecontrol-element-format.md) che definisce le informazioni di intestazione e riga della tabella.</span><span class="sxs-lookup"><span data-stu-id="ad44f-130">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="ad44f-131">Analogamente a tutte le altre viste, una vista tabella può visualizzare i valori delle proprietà o dei valori degli oggetti generati dagli script.</span><span class="sxs-lookup"><span data-stu-id="ad44f-131">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="ad44f-132">Definizione delle intestazioni di colonna</span><span class="sxs-lookup"><span data-stu-id="ad44f-132">Defining Column Headers</span></span>

1. <span data-ttu-id="ad44f-133">L'elemento [TableHeaders](./tableheaders-element-format.md) e i relativi elementi figlio definiscono ciò che viene visualizzato nella parte superiore della tabella.</span><span class="sxs-lookup"><span data-stu-id="ad44f-133">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="ad44f-134">L'elemento [TableColumnHeader](./tablecolumnheader-element-format.md) definisce gli elementi visualizzati nella parte superiore di una colonna della tabella.</span><span class="sxs-lookup"><span data-stu-id="ad44f-134">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="ad44f-135">Specificare questi elementi nell'ordine in cui si desidera visualizzare le intestazioni.</span><span class="sxs-lookup"><span data-stu-id="ad44f-135">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="ad44f-136">Non esiste alcun limite al numero di questo elemento che è possibile utilizzare, ma il numero di elementi [TableColumnHeader](./tablecolumnheader-element-format.md) nella visualizzazione tabella deve corrispondere al numero di elementi [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) utilizzati.</span><span class="sxs-lookup"><span data-stu-id="ad44f-136">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="ad44f-137">L'elemento [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) specifica il testo visualizzato.</span><span class="sxs-lookup"><span data-stu-id="ad44f-137">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="ad44f-138">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="ad44f-138">This element is optional.</span></span>

4. <span data-ttu-id="ad44f-139">L'elemento [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) specifica la larghezza (in caratteri) della colonna.</span><span class="sxs-lookup"><span data-stu-id="ad44f-139">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="ad44f-140">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="ad44f-140">This element is optional.</span></span>

5. <span data-ttu-id="ad44f-141">L'elemento [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) specifica come viene visualizzata l'etichetta.</span><span class="sxs-lookup"><span data-stu-id="ad44f-141">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="ad44f-142">L'etichetta può essere allineata a sinistra, a destra o centrata.</span><span class="sxs-lookup"><span data-stu-id="ad44f-142">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="ad44f-143">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="ad44f-143">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="ad44f-144">Definizione delle righe della tabella</span><span class="sxs-lookup"><span data-stu-id="ad44f-144">Defining the Table Rows</span></span>

<span data-ttu-id="ad44f-145">Le visualizzazioni di tabella possono fornire una o più definizioni che specificano quali dati vengono visualizzati nelle righe della tabella utilizzando gli elementi figlio dell'elemento [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) .</span><span class="sxs-lookup"><span data-stu-id="ad44f-145">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="ad44f-146">Si noti che è possibile specificare più definizioni per le righe della tabella, ma le intestazioni per le righe rimangono invariate, indipendentemente dalla definizione di riga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="ad44f-146">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="ad44f-147">In genere, una tabella avrà una sola definizione.</span><span class="sxs-lookup"><span data-stu-id="ad44f-147">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="ad44f-148">Nell'esempio seguente, la vista fornisce una singola definizione che Visualizza i valori di diverse proprietà di [System. Diagnostics. Process? Oggetto DisplayProperty = FullName](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="ad44f-148">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="ad44f-149">In una vista tabella è possibile visualizzare il valore di una proprietà o il valore di uno script (non illustrato nell'esempio) nelle relative righe.</span><span class="sxs-lookup"><span data-stu-id="ad44f-149">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

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

<span data-ttu-id="ad44f-150">Per fornire definizioni per una riga, è possibile utilizzare gli elementi XML seguenti:</span><span class="sxs-lookup"><span data-stu-id="ad44f-150">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="ad44f-151">L'elemento [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) e i relativi elementi figlio definiscono ciò che viene visualizzato nelle righe della tabella.</span><span class="sxs-lookup"><span data-stu-id="ad44f-151">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="ad44f-152">L'elemento [TableRowEntry](./listentry-element-for-listcontrol-format.md) fornisce una definizione della riga.</span><span class="sxs-lookup"><span data-stu-id="ad44f-152">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="ad44f-153">È necessario almeno un [TableRowEntry](./listentry-element-for-listcontrol-format.md) . Tuttavia, non esiste alcun limite massimo per il numero di elementi che è possibile aggiungere.</span><span class="sxs-lookup"><span data-stu-id="ad44f-153">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="ad44f-154">Nella maggior parte dei casi, una vista avrà una sola definizione.</span><span class="sxs-lookup"><span data-stu-id="ad44f-154">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="ad44f-155">L'elemento [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) specifica gli oggetti visualizzati da una definizione specifica.</span><span class="sxs-lookup"><span data-stu-id="ad44f-155">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="ad44f-156">Questo elemento è facoltativo ed è necessario solo quando si definiscono più elementi [TableRowEntry](./listentry-element-for-listcontrol-format.md) che visualizzano oggetti diversi.</span><span class="sxs-lookup"><span data-stu-id="ad44f-156">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="ad44f-157">L'elemento [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) specifica che il testo che supera la larghezza della colonna viene visualizzato nella riga successiva.</span><span class="sxs-lookup"><span data-stu-id="ad44f-157">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="ad44f-158">Per impostazione predefinita, il testo di dimensioni superiori alla larghezza della colonna viene troncato.</span><span class="sxs-lookup"><span data-stu-id="ad44f-158">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="ad44f-159">L'elemento [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) definisce le proprietà o gli script i cui valori vengono visualizzati nella riga.</span><span class="sxs-lookup"><span data-stu-id="ad44f-159">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="ad44f-160">L'elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) definisce la proprietà o lo script il cui valore viene visualizzato nella colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="ad44f-160">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="ad44f-161">Un elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) è obbligatorio per ogni colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="ad44f-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="ad44f-162">La prima voce viene visualizzata nella prima colonna, nella seconda voce della seconda colonna e così via.</span><span class="sxs-lookup"><span data-stu-id="ad44f-162">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="ad44f-163">L'elemento [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) specifica la proprietà il cui valore viene visualizzato nella riga.</span><span class="sxs-lookup"><span data-stu-id="ad44f-163">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="ad44f-164">È necessario specificare una proprietà o uno script, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="ad44f-164">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="ad44f-165">L'elemento [scriptblock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) specifica lo script il cui valore viene visualizzato nella riga.</span><span class="sxs-lookup"><span data-stu-id="ad44f-165">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="ad44f-166">È necessario specificare uno script o una proprietà, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="ad44f-166">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="ad44f-167">L'elemento [FormatString](./label-element-for-listitem-for-listcontrol-format.md) specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script.</span><span class="sxs-lookup"><span data-stu-id="ad44f-167">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="ad44f-168">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="ad44f-168">This element is optional.</span></span>

- <span data-ttu-id="ad44f-169">L'elemento [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) specifica il modo in cui viene visualizzato il valore della proprietà o dello script.</span><span class="sxs-lookup"><span data-stu-id="ad44f-169">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="ad44f-170">Il valore può essere allineato a sinistra, a destra o centrato.</span><span class="sxs-lookup"><span data-stu-id="ad44f-170">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="ad44f-171">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="ad44f-171">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="ad44f-172">Definizione degli oggetti che utilizzano la visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="ad44f-172">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="ad44f-173">Esistono due modi per definire gli oggetti .NET che utilizzano la visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="ad44f-173">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="ad44f-174">È possibile utilizzare l'elemento [ViewSelectedBy](./viewselectedby-element-format.md) per definire gli oggetti che possono essere visualizzati da tutte le definizioni della vista oppure è possibile utilizzare l'elemento [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) per definire quali oggetti vengono visualizzati da una definizione specifica della vista.</span><span class="sxs-lookup"><span data-stu-id="ad44f-174">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="ad44f-175">Nella maggior parte dei casi, una vista ha una sola definizione, quindi gli oggetti vengono in genere definiti dall'elemento [ViewSelectedBy](./viewselectedby-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="ad44f-175">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="ad44f-176">Nell'esempio seguente viene illustrato come definire gli oggetti visualizzati dalla visualizzazione tabella utilizzando gli elementi [ViewSelectedBy](./viewselectedby-element-format.md) e [typeName](./typename-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="ad44f-176">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="ad44f-177">Non esiste alcun limite al numero di elementi [typeName](./typename-element-for-viewselectedby-format.md) che è possibile specificare e il loro ordine non è significativo.</span><span class="sxs-lookup"><span data-stu-id="ad44f-177">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="ad44f-178">Per specificare gli oggetti utilizzati dalla vista tabella, è possibile utilizzare gli elementi XML seguenti:</span><span class="sxs-lookup"><span data-stu-id="ad44f-178">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="ad44f-179">L'elemento [ViewSelectedBy](./viewselectedby-element-format.md) definisce quali oggetti vengono visualizzati dalla visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="ad44f-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="ad44f-180">L'elemento [typeName](./typename-element-for-viewselectedby-format.md) specifica l'oggetto .NET visualizzato dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="ad44f-180">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="ad44f-181">Il nome completo del tipo .NET è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="ad44f-181">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="ad44f-182">È necessario specificare almeno un tipo o un set di selezione per la vista, ma non esiste un numero massimo di elementi che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="ad44f-182">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="ad44f-183">Nell'esempio seguente vengono usati gli elementi [ViewSelectedBy](./viewselectedby-element-format.md) e [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="ad44f-183">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="ad44f-184">Utilizzare i set di selezione in cui è presente un set correlato di oggetti visualizzati utilizzando più visualizzazioni, ad esempio quando si definiscono una visualizzazione elenco e una vista tabella per gli stessi oggetti.</span><span class="sxs-lookup"><span data-stu-id="ad44f-184">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="ad44f-185">Per ulteriori informazioni su come creare un set di selezione, vedere [definizione](./defining-selection-sets.md)di set di selezione.</span><span class="sxs-lookup"><span data-stu-id="ad44f-185">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="ad44f-186">Per specificare gli oggetti utilizzati dalla visualizzazione elenco, è possibile utilizzare gli elementi XML seguenti:</span><span class="sxs-lookup"><span data-stu-id="ad44f-186">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="ad44f-187">L'elemento [ViewSelectedBy](./viewselectedby-element-format.md) definisce quali oggetti vengono visualizzati dalla visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="ad44f-187">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="ad44f-188">L'elemento [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) specifica un set di oggetti che possono essere visualizzati dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="ad44f-188">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="ad44f-189">È necessario specificare almeno un set di selezione o un tipo per la vista, ma non esiste un numero massimo di elementi che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="ad44f-189">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="ad44f-190">Nell'esempio seguente viene illustrato come definire gli oggetti visualizzati da una definizione specifica della visualizzazione tabella utilizzando l'elemento [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) .</span><span class="sxs-lookup"><span data-stu-id="ad44f-190">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="ad44f-191">Utilizzando questo elemento, è possibile specificare il nome del tipo .NET dell'oggetto, un set di selezione di oggetti o una condizione di selezione che specifica quando viene utilizzata la definizione.</span><span class="sxs-lookup"><span data-stu-id="ad44f-191">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="ad44f-192">Per ulteriori informazioni sulla creazione di condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ad44f-192">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ad44f-193">Quando si creano più definizioni della vista tabella, non è possibile specificare intestazioni di colonna diverse.</span><span class="sxs-lookup"><span data-stu-id="ad44f-193">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="ad44f-194">È possibile specificare solo ciò che viene visualizzato nelle righe della tabella, ad esempio quali oggetti vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="ad44f-194">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="ad44f-195">Gli elementi XML seguenti possono essere utilizzati per specificare gli oggetti utilizzati da una definizione specifica della visualizzazione elenco:</span><span class="sxs-lookup"><span data-stu-id="ad44f-195">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="ad44f-196">L'elemento [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) definisce quali oggetti vengono visualizzati dalla definizione.</span><span class="sxs-lookup"><span data-stu-id="ad44f-196">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="ad44f-197">L'elemento [typeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) specifica l'oggetto .NET visualizzato dalla definizione.</span><span class="sxs-lookup"><span data-stu-id="ad44f-197">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="ad44f-198">Quando si usa questo elemento, il nome completo del tipo .NET è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="ad44f-198">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="ad44f-199">È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per la definizione, ma non esiste un numero massimo di elementi che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="ad44f-199">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="ad44f-200">L'elemento [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) (non mostrato) specifica un set di oggetti che possono essere visualizzati da questa definizione.</span><span class="sxs-lookup"><span data-stu-id="ad44f-200">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="ad44f-201">È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per la definizione, ma non esiste un numero massimo di elementi che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="ad44f-201">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="ad44f-202">L'elemento [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (non mostrato) specifica una condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="ad44f-202">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="ad44f-203">È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per la definizione, ma non esiste un numero massimo di elementi che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="ad44f-203">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="ad44f-204">Per ulteriori informazioni sulla definizione delle condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ad44f-204">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="ad44f-205">Uso di stringhe di formato</span><span class="sxs-lookup"><span data-stu-id="ad44f-205">Using Format Strings</span></span>

<span data-ttu-id="ad44f-206">È possibile aggiungere stringhe di formattazione a una visualizzazione per definire ulteriormente la modalità di visualizzazione dei dati.</span><span class="sxs-lookup"><span data-stu-id="ad44f-206">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="ad44f-207">Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della proprietà `StartTime`.</span><span class="sxs-lookup"><span data-stu-id="ad44f-207">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="ad44f-208">Per specificare un modello di formato, è possibile utilizzare gli elementi XML seguenti:</span><span class="sxs-lookup"><span data-stu-id="ad44f-208">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="ad44f-209">L'elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) definisce la proprietà o lo script il cui valore viene visualizzato nella colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="ad44f-209">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="ad44f-210">Un elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) è obbligatorio per ogni colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="ad44f-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="ad44f-211">La prima voce viene visualizzata nella prima colonna, nella seconda voce della seconda colonna e così via.</span><span class="sxs-lookup"><span data-stu-id="ad44f-211">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="ad44f-212">L'elemento [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) specifica la proprietà il cui valore viene visualizzato nella riga.</span><span class="sxs-lookup"><span data-stu-id="ad44f-212">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="ad44f-213">È necessario specificare una proprietà o uno script, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="ad44f-213">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="ad44f-214">L'elemento [FormatString](./label-element-for-listitem-for-listcontrol-format.md) specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script.</span><span class="sxs-lookup"><span data-stu-id="ad44f-214">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="ad44f-215">Nell'esempio seguente viene chiamato il metodo `ToString` per formattare il valore dello script.</span><span class="sxs-lookup"><span data-stu-id="ad44f-215">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="ad44f-216">Gli script possono chiamare qualsiasi metodo di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="ad44f-216">Scripts can call any method of an object.</span></span> <span data-ttu-id="ad44f-217">Pertanto, se un oggetto dispone di un metodo, ad esempio `ToString`, con parametri di formattazione, lo script può chiamare tale metodo per formattare il valore di output dello script.</span><span class="sxs-lookup"><span data-stu-id="ad44f-217">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="ad44f-218">È possibile utilizzare l'elemento XML seguente per chiamare il metodo `ToString`:</span><span class="sxs-lookup"><span data-stu-id="ad44f-218">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="ad44f-219">L'elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) definisce la proprietà o lo script il cui valore viene visualizzato nella colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="ad44f-219">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="ad44f-220">Un elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) è obbligatorio per ogni colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="ad44f-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="ad44f-221">La prima voce viene visualizzata nella prima colonna, nella seconda voce della seconda colonna e così via.</span><span class="sxs-lookup"><span data-stu-id="ad44f-221">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="ad44f-222">L'elemento [scriptblock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) specifica lo script il cui valore viene visualizzato nella riga.</span><span class="sxs-lookup"><span data-stu-id="ad44f-222">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="ad44f-223">È necessario specificare uno script o una proprietà, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="ad44f-223">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad44f-224">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ad44f-224">See Also</span></span>

[<span data-ttu-id="ad44f-225">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad44f-225">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
