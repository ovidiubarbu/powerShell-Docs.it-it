---
title: Creazione di una visualizzazione elenco | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368980"
---
# <a name="creating-a-list-view"></a><span data-ttu-id="03aea-102">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="03aea-102">Creating a List View</span></span>

<span data-ttu-id="03aea-103">In una visualizzazione elenco i dati vengono visualizzati in una singola colonna (in ordine sequenziale).</span><span class="sxs-lookup"><span data-stu-id="03aea-103">A list view displays data in a single column (in sequential order).</span></span> <span data-ttu-id="03aea-104">I dati visualizzati nell'elenco possono corrispondere al valore di una proprietà .NET o al valore di uno script.</span><span class="sxs-lookup"><span data-stu-id="03aea-104">The data displayed in the list can be the value of a .NET property or the value of a script.</span></span>

## <a name="a-list-view-display"></a><span data-ttu-id="03aea-105">Visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="03aea-105">A List View Display</span></span>

<span data-ttu-id="03aea-106">L'output seguente mostra in che modo Windows PowerShell Visualizza le proprietà di [System. ServiceProcess. ServiceController? DisplayProperty = oggetti FullName](/dotnet/api/System.ServiceProcess.ServiceController) restituiti dal cmdlet [Get-Service](/powershell/module/microsoft.powershell.management/get-service) .</span><span class="sxs-lookup"><span data-stu-id="03aea-106">The following output shows how Windows PowerShell displays the properties of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects that are returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="03aea-107">In questo esempio sono stati restituiti tre oggetti, con ogni oggetto separato dall'oggetto precedente da una riga vuota.</span><span class="sxs-lookup"><span data-stu-id="03aea-107">In this example, three objects were returned, with each object separated from the preceding object by a blank line.</span></span>

```powershell
Get-Service | format-list
```

```output
Name                : AEADIFilters
DisplayName         : Andrea ADI Filters Service
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess

Name                : AeLookupSvc
DisplayName         : Application Experience
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32ShareProcess

Name                : AgereModemAudio
DisplayName         : Agere Modem Call Progress Audio
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess
...
```

## <a name="defining-the-list-view"></a><span data-ttu-id="03aea-108">Definizione della visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="03aea-108">Defining the List View</span></span>

<span data-ttu-id="03aea-109">Il codice XML seguente mostra lo schema di visualizzazione elenco per visualizzare diverse proprietà di [System. ServiceProcess. ServiceController? Oggetto DisplayProperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="03aea-109">The following XML shows the list view schema for displaying several properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="03aea-110">È necessario specificare ogni proprietà che si desidera visualizzare nella visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="03aea-110">You must specify each property that you want displayed in the list view.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

<span data-ttu-id="03aea-111">Per definire una visualizzazione elenco vengono utilizzati gli elementi XML seguenti:</span><span class="sxs-lookup"><span data-stu-id="03aea-111">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="03aea-112">L'elemento [View](./view-element-format.md) è l'elemento padre della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="03aea-112">The [View](./view-element-format.md) element is the parent element of the list view.</span></span> <span data-ttu-id="03aea-113">Si tratta dello stesso elemento padre per la tabella, la larghezza e le visualizzazioni di controlli personalizzati.</span><span class="sxs-lookup"><span data-stu-id="03aea-113">(This is the same parent element for the table, wide, and custom control views.)</span></span>

- <span data-ttu-id="03aea-114">L'elemento [Name](./name-element-for-view-format.md) specifica il nome della vista.</span><span class="sxs-lookup"><span data-stu-id="03aea-114">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="03aea-115">Questo elemento è obbligatorio per tutte le visualizzazioni.</span><span class="sxs-lookup"><span data-stu-id="03aea-115">This element is required for all views.</span></span>

- <span data-ttu-id="03aea-116">L'elemento [ViewSelectedBy](./viewselectedby-element-format.md) definisce gli oggetti che utilizzano la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="03aea-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="03aea-117">Questo elemento è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="03aea-117">This element is required.</span></span>

- <span data-ttu-id="03aea-118">L'elemento [GroupBy](./groupby-element-for-view-format.md) definisce quando viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="03aea-118">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="03aea-119">Un nuovo gruppo viene avviato ogni volta che viene modificato il valore di una proprietà o di uno script specifico.</span><span class="sxs-lookup"><span data-stu-id="03aea-119">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="03aea-120">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="03aea-120">This element is optional.</span></span>

- <span data-ttu-id="03aea-121">L'elemento [Controls](./controls-element-for-view-format.md) definisce i controlli personalizzati definiti dalla visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="03aea-121">The [Controls](./controls-element-for-view-format.md) element defines the custom controls that are defined by the list view.</span></span> <span data-ttu-id="03aea-122">I controlli consentono di specificare in modo più dettagliato la modalità di visualizzazione dei dati.</span><span class="sxs-lookup"><span data-stu-id="03aea-122">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="03aea-123">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="03aea-123">This element is optional.</span></span> <span data-ttu-id="03aea-124">Una vista può definire i propri controlli personalizzati oppure può utilizzare controlli comuni che possono essere utilizzati da qualsiasi visualizzazione nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="03aea-124">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="03aea-125">Per ulteriori informazioni sui controlli personalizzati, vedere [creazione di controlli personalizzati](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="03aea-125">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="03aea-126">L'elemento [ListControl](./listcontrol-element-format.md) definisce gli elementi visualizzati nella visualizzazione e la relativa formattazione.</span><span class="sxs-lookup"><span data-stu-id="03aea-126">The [ListControl](./listcontrol-element-format.md) element defines what is displayed in the view and how it is formatted.</span></span> <span data-ttu-id="03aea-127">Analogamente a tutte le altre viste, una visualizzazione elenco può visualizzare i valori delle proprietà dell'oggetto o i valori generati dallo script.</span><span class="sxs-lookup"><span data-stu-id="03aea-127">Similar to all other views, a list view can display the values of object properties or values generated by script.</span></span>

<span data-ttu-id="03aea-128">Per un esempio di un file di formattazione completo che definisce una semplice visualizzazione elenco, vedere [visualizzazione elenco (di base)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="03aea-128">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-list-view"></a><span data-ttu-id="03aea-129">Fornire definizioni per la visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="03aea-129">Providing Definitions for Your List View</span></span>

<span data-ttu-id="03aea-130">Le visualizzazioni elenco possono fornire una o più definizioni usando gli elementi figlio dell'elemento [ListControl](./listcontrol-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="03aea-130">List views can provide one or more definitions by using the child elements of the [ListControl](./listcontrol-element-format.md) element.</span></span> <span data-ttu-id="03aea-131">In genere, una vista avrà una sola definizione.</span><span class="sxs-lookup"><span data-stu-id="03aea-131">Typically, a view will have only one definition.</span></span> <span data-ttu-id="03aea-132">Nell'esempio seguente, la vista fornisce una singola definizione che visualizza diverse proprietà di [System. Diagnostics. Process? Oggetto DisplayProperty = FullName](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="03aea-132">In the following example, the view provides a single definition that displays several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="03aea-133">In una visualizzazione elenco è possibile visualizzare il valore di una proprietà o il valore di uno script (non illustrato nell'esempio).</span><span class="sxs-lookup"><span data-stu-id="03aea-133">A list view can display the value of a property or the value of a script (not shown in the example).</span></span>

```xml
<ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>

```

<span data-ttu-id="03aea-134">È possibile utilizzare gli elementi XML seguenti per fornire definizioni per una visualizzazione elenco:</span><span class="sxs-lookup"><span data-stu-id="03aea-134">The following XML elements can be used to provide definitions for a list view:</span></span>

- <span data-ttu-id="03aea-135">L'elemento [ListControl](./listcontrol-element-format.md) e i relativi elementi figlio definiscono ciò che viene visualizzato nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="03aea-135">The [ListControl](./listcontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="03aea-136">L'elemento [ListEntries](./listentries-element-for-listcontrol-format.md) fornisce le definizioni della vista.</span><span class="sxs-lookup"><span data-stu-id="03aea-136">The [ListEntries](./listentries-element-for-listcontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="03aea-137">Nella maggior parte dei casi, una vista avrà una sola definizione.</span><span class="sxs-lookup"><span data-stu-id="03aea-137">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="03aea-138">Questo elemento è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="03aea-138">This element is required.</span></span>

- <span data-ttu-id="03aea-139">L'elemento [ListEntry](./listentry-element-for-listcontrol-format.md) fornisce una definizione della vista.</span><span class="sxs-lookup"><span data-stu-id="03aea-139">The [ListEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="03aea-140">È necessario almeno un [ListEntry](./listentry-element-for-listcontrol-format.md) . Tuttavia, non esiste alcun limite massimo per il numero di elementi che è possibile aggiungere.</span><span class="sxs-lookup"><span data-stu-id="03aea-140">At least one [ListEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="03aea-141">Nella maggior parte dei casi, una vista avrà una sola definizione.</span><span class="sxs-lookup"><span data-stu-id="03aea-141">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="03aea-142">L'elemento [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) specifica gli oggetti visualizzati da una definizione specifica.</span><span class="sxs-lookup"><span data-stu-id="03aea-142">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="03aea-143">Questo elemento è facoltativo ed è necessario solo quando si definiscono più elementi [ListEntry](./listentry-element-for-listcontrol-format.md) che visualizzano oggetti diversi.</span><span class="sxs-lookup"><span data-stu-id="03aea-143">This element is optional and is needed only when you define multiple [ListEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="03aea-144">L'elemento [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) specifica le proprietà e gli script i cui valori vengono visualizzati nelle righe della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="03aea-144">The [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies the properties and scripts whose values are displayed in the rows of the list view.</span></span>

- <span data-ttu-id="03aea-145">L'elemento [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) specifica una proprietà o uno script il cui valore viene visualizzato in una riga della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="03aea-145">The [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies a property or script whose value is displayed in a row of the list view.</span></span> <span data-ttu-id="03aea-146">Una visualizzazione elenco deve specificare almeno una proprietà o uno script.</span><span class="sxs-lookup"><span data-stu-id="03aea-146">A list view must specify at least one property or script.</span></span> <span data-ttu-id="03aea-147">Non esiste un limite massimo per il numero di righe che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="03aea-147">There is no maximum limit to the number of rows that can be specified.</span></span>

- <span data-ttu-id="03aea-148">L'elemento [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) specifica la proprietà il cui valore viene visualizzato nella riga.</span><span class="sxs-lookup"><span data-stu-id="03aea-148">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="03aea-149">È necessario specificare una proprietà o uno script, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="03aea-149">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="03aea-150">L'elemento [scriptblock](./scriptblock-element-for-listitem-for-listcontrol-format.md) specifica lo script il cui valore viene visualizzato nella riga.</span><span class="sxs-lookup"><span data-stu-id="03aea-150">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="03aea-151">È necessario specificare uno script o una proprietà, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="03aea-151">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="03aea-152">L'elemento [Label](./label-element-for-listitem-for-listcontrol-format.md) specifica l'etichetta visualizzata a sinistra della proprietà o del valore dello script nella riga.</span><span class="sxs-lookup"><span data-stu-id="03aea-152">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element specifies the label that is displayed to the left of the property or script value in the row.</span></span> <span data-ttu-id="03aea-153">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="03aea-153">This element is optional.</span></span> <span data-ttu-id="03aea-154">Se non si specifica un'etichetta, viene visualizzato il nome della proprietà o dello script.</span><span class="sxs-lookup"><span data-stu-id="03aea-154">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="03aea-155">Per un esempio completo, vedere [visualizzazione elenco (etichette)](./list-view-labels.md).</span><span class="sxs-lookup"><span data-stu-id="03aea-155">For a complete example, see [List View (Labels)](./list-view-labels.md).</span></span>

- <span data-ttu-id="03aea-156">L'elemento [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) specifica una condizione che deve esistere per la visualizzazione della riga.</span><span class="sxs-lookup"><span data-stu-id="03aea-156">The [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element specifies a condition that must exist for the row to be displayed.</span></span> <span data-ttu-id="03aea-157">Per ulteriori informazioni sull'aggiunta di condizioni alla visualizzazione elenco, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="03aea-157">For more information about adding conditions to the list view, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span> <span data-ttu-id="03aea-158">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="03aea-158">This element is optional.</span></span>

- <span data-ttu-id="03aea-159">L'elemento [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) specifica un modello utilizzato per visualizzare il valore della proprietà o dello script.</span><span class="sxs-lookup"><span data-stu-id="03aea-159">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a pattern that is used to display the value of the property or script.</span></span> <span data-ttu-id="03aea-160">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="03aea-160">This element is optional.</span></span>

<span data-ttu-id="03aea-161">Per un esempio di un file di formattazione completo che definisce una semplice visualizzazione elenco, vedere [visualizzazione elenco (di base)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="03aea-161">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-list-view"></a><span data-ttu-id="03aea-162">Definizione degli oggetti che utilizzano la visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="03aea-162">Defining the Objects That Use the List View</span></span>

<span data-ttu-id="03aea-163">Esistono due modi per definire gli oggetti .NET che utilizzano la visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="03aea-163">There are two ways to define which .NET objects use the list view.</span></span> <span data-ttu-id="03aea-164">È possibile utilizzare l'elemento [ViewSelectedBy](./viewselectedby-element-format.md) per definire gli oggetti che possono essere visualizzati da tutte le definizioni della vista oppure è possibile utilizzare l'elemento [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) per definire quali oggetti vengono visualizzati da una definizione specifica della vista.</span><span class="sxs-lookup"><span data-stu-id="03aea-164">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="03aea-165">Nella maggior parte dei casi, una vista ha una sola definizione, quindi gli oggetti vengono in genere definiti dall'elemento [ViewSelectedBy](./viewselectedby-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="03aea-165">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="03aea-166">Nell'esempio seguente viene illustrato come definire gli oggetti visualizzati dalla visualizzazione elenco usando gli elementi [ViewSelectedBy](./viewselectedby-element-format.md) e [typeName](./typename-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="03aea-166">The following example shows how to define the objects that are displayed by the list view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="03aea-167">Non esiste alcun limite al numero di elementi [typeName](./typename-element-for-viewselectedby-format.md) che è possibile specificare e il loro ordine non è significativo.</span><span class="sxs-lookup"><span data-stu-id="03aea-167">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="03aea-168">Per specificare gli oggetti utilizzati dalla visualizzazione elenco, è possibile utilizzare gli elementi XML seguenti:</span><span class="sxs-lookup"><span data-stu-id="03aea-168">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="03aea-169">L'elemento [ViewSelectedBy](./viewselectedby-element-format.md) definisce quali oggetti vengono visualizzati dalla visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="03aea-169">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="03aea-170">L'elemento [typeName](./typename-element-for-viewselectedby-format.md) specifica l'oggetto .NET visualizzato dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="03aea-170">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="03aea-171">Il nome completo del tipo .NET è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="03aea-171">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="03aea-172">È necessario specificare almeno un tipo o un set di selezione per la vista, ma non esiste un numero massimo di elementi che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="03aea-172">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="03aea-173">Per un esempio di un file di formattazione completo, vedere [visualizzazione elenco (di base)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="03aea-173">For an example of a complete formatting file, see [List View (Basic)](./list-view-basic.md).</span></span>

<span data-ttu-id="03aea-174">Nell'esempio seguente vengono usati gli elementi [ViewSelectedBy](./viewselectedby-element-format.md) e [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="03aea-174">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="03aea-175">Utilizzare i set di selezione in cui è presente un set correlato di oggetti visualizzati utilizzando più visualizzazioni, ad esempio quando si definiscono una visualizzazione elenco e una vista tabella per gli stessi oggetti.</span><span class="sxs-lookup"><span data-stu-id="03aea-175">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="03aea-176">Per ulteriori informazioni su come creare un set di selezione, vedere [definizione](./defining-selection-sets.md)di set di selezione.</span><span class="sxs-lookup"><span data-stu-id="03aea-176">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="03aea-177">Per specificare gli oggetti utilizzati dalla visualizzazione elenco, è possibile utilizzare gli elementi XML seguenti:</span><span class="sxs-lookup"><span data-stu-id="03aea-177">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="03aea-178">L'elemento [ViewSelectedBy](./viewselectedby-element-format.md) definisce quali oggetti vengono visualizzati dalla visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="03aea-178">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="03aea-179">L'elemento [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) specifica un set di oggetti che possono essere visualizzati dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="03aea-179">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="03aea-180">È necessario specificare almeno un set di selezione o un tipo per la vista, ma non esiste un numero massimo di elementi che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="03aea-180">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="03aea-181">Nell'esempio seguente viene illustrato come definire gli oggetti visualizzati da una definizione specifica della visualizzazione elenco utilizzando l'elemento [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) .</span><span class="sxs-lookup"><span data-stu-id="03aea-181">The following example shows how to define the objects displayed by a specific definition of the list view using the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span></span> <span data-ttu-id="03aea-182">Utilizzando questo elemento, è possibile specificare il nome del tipo .NET dell'oggetto, un set di selezione di oggetti o una condizione di selezione che specifica quando viene utilizzata la definizione.</span><span class="sxs-lookup"><span data-stu-id="03aea-182">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="03aea-183">Per ulteriori informazioni sulla creazione di condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="03aea-183">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

<span data-ttu-id="03aea-184">Gli elementi XML seguenti possono essere utilizzati per specificare gli oggetti utilizzati da una definizione specifica della visualizzazione elenco:</span><span class="sxs-lookup"><span data-stu-id="03aea-184">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="03aea-185">L'elemento [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) definisce quali oggetti vengono visualizzati dalla definizione.</span><span class="sxs-lookup"><span data-stu-id="03aea-185">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="03aea-186">L'elemento [typeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) specifica l'oggetto .NET visualizzato dalla definizione.</span><span class="sxs-lookup"><span data-stu-id="03aea-186">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="03aea-187">Quando si usa questo elemento, il nome completo del tipo .NET è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="03aea-187">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="03aea-188">È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per la definizione, ma non esiste un numero massimo di elementi che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="03aea-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="03aea-189">L'elemento [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) (non mostrato) specifica un set di oggetti che possono essere visualizzati da questa definizione.</span><span class="sxs-lookup"><span data-stu-id="03aea-189">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="03aea-190">È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per la definizione, ma non esiste un numero massimo di elementi che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="03aea-190">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="03aea-191">L'elemento [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (non mostrato) specifica una condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="03aea-191">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="03aea-192">È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per la definizione, ma non esiste un numero massimo di elementi che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="03aea-192">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="03aea-193">Per ulteriori informazioni sulla definizione delle condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="03aea-193">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-list-view"></a><span data-ttu-id="03aea-194">Visualizzazione di gruppi di oggetti in una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="03aea-194">Displaying Groups of Objects in a List View</span></span>

<span data-ttu-id="03aea-195">È possibile separare gli oggetti visualizzati dalla visualizzazione elenco in gruppi.</span><span class="sxs-lookup"><span data-stu-id="03aea-195">You can separate the objects that are displayed by the list view into groups.</span></span> <span data-ttu-id="03aea-196">Ciò non significa che si definisce un gruppo, solo che Windows PowerShell avvia un nuovo gruppo ogni volta che viene modificato il valore di una proprietà o di uno script specifico.</span><span class="sxs-lookup"><span data-stu-id="03aea-196">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="03aea-197">Nell'esempio seguente viene avviato un nuovo gruppo ogni volta che viene modificato il valore della proprietà [System. ServiceProcess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) .</span><span class="sxs-lookup"><span data-stu-id="03aea-197">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="03aea-198">Per definire quando viene avviato un gruppo, vengono utilizzati gli elementi XML seguenti:</span><span class="sxs-lookup"><span data-stu-id="03aea-198">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="03aea-199">L'elemento [GroupBy](./groupby-element-for-view-format.md) definisce la proprietà o lo script che avvia il nuovo gruppo e definisce la modalità di visualizzazione del gruppo.</span><span class="sxs-lookup"><span data-stu-id="03aea-199">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="03aea-200">L'elemento [PropertyName](./propertyname-element-for-groupby-format.md) specifica la proprietà che avvia un nuovo gruppo ogni volta che viene modificato il valore.</span><span class="sxs-lookup"><span data-stu-id="03aea-200">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="03aea-201">È necessario specificare una proprietà o uno script per avviare il gruppo, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="03aea-201">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="03aea-202">L'elemento [scriptblock](./scriptblock-element-for-groupby-format.md) specifica lo script che avvia un nuovo gruppo ogni volta che viene modificato il valore.</span><span class="sxs-lookup"><span data-stu-id="03aea-202">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="03aea-203">Per avviare il gruppo, è necessario specificare uno script o una proprietà, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="03aea-203">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="03aea-204">L'elemento [Label](./label-element-for-groupby-format.md) definisce un'etichetta che viene visualizzata all'inizio di ogni gruppo.</span><span class="sxs-lookup"><span data-stu-id="03aea-204">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="03aea-205">Oltre al testo specificato da questo elemento, Windows PowerShell Visualizza il valore che ha attivato il nuovo gruppo e aggiunge una riga vuota prima e dopo l'etichetta.</span><span class="sxs-lookup"><span data-stu-id="03aea-205">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="03aea-206">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="03aea-206">This element is optional.</span></span>

- <span data-ttu-id="03aea-207">L'elemento [CustomControl](./customcontrol-element-for-groupby-format.md) definisce un controllo usato per visualizzare i dati.</span><span class="sxs-lookup"><span data-stu-id="03aea-207">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="03aea-208">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="03aea-208">This element is optional.</span></span>

- <span data-ttu-id="03aea-209">L'elemento [CustomControlName](./customcontrolname-element-for-groupby-format.md) specifica un controllo comune o di visualizzazione usato per visualizzare i dati.</span><span class="sxs-lookup"><span data-stu-id="03aea-209">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="03aea-210">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="03aea-210">This element is optional.</span></span>

<span data-ttu-id="03aea-211">Per un esempio di un file di formattazione completo che definisce i gruppi, vedere [visualizzazione elenco (GroupBy)](./list-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="03aea-211">For an example of a complete formatting file that defines groups, see [List View (GroupBy)](./list-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="03aea-212">Uso di stringhe di formato</span><span class="sxs-lookup"><span data-stu-id="03aea-212">Using Format Strings</span></span>

<span data-ttu-id="03aea-213">È possibile aggiungere stringhe di formattazione a una visualizzazione per definire ulteriormente la modalità di visualizzazione dei dati.</span><span class="sxs-lookup"><span data-stu-id="03aea-213">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="03aea-214">Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della proprietà `StartTime`.</span><span class="sxs-lookup"><span data-stu-id="03aea-214">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

<span data-ttu-id="03aea-215">Per specificare un modello di formato, è possibile utilizzare gli elementi XML seguenti:</span><span class="sxs-lookup"><span data-stu-id="03aea-215">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="03aea-216">L'elemento [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) specifica i dati visualizzati dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="03aea-216">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="03aea-217">L'elemento [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) specifica la proprietà il cui valore viene visualizzato dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="03aea-217">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="03aea-218">È necessario specificare una proprietà o uno script, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="03aea-218">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="03aea-219">L'elemento [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="03aea-219">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

- <span data-ttu-id="03aea-220">L'elemento [scriptblock](./scriptblock-element-for-listitem-for-listcontrol-format.md) (non mostrato) specifica lo script il cui valore viene visualizzato dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="03aea-220">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="03aea-221">È necessario specificare uno script o una proprietà, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="03aea-221">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="03aea-222">Nell'esempio seguente viene chiamato il metodo `ToString` per formattare il valore dello script.</span><span class="sxs-lookup"><span data-stu-id="03aea-222">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="03aea-223">Gli script possono chiamare qualsiasi metodo di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="03aea-223">Scripts can call any method of an object.</span></span> <span data-ttu-id="03aea-224">Pertanto, se un oggetto dispone di un metodo, ad esempio `ToString`, con parametri di formattazione, lo script può chiamare tale metodo per formattare il valore di output dello script.</span><span class="sxs-lookup"><span data-stu-id="03aea-224">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="03aea-225">È possibile utilizzare l'elemento XML seguente per chiamare il metodo `ToString`:</span><span class="sxs-lookup"><span data-stu-id="03aea-225">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="03aea-226">L'elemento [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) specifica i dati visualizzati dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="03aea-226">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="03aea-227">L'elemento [scriptblock](./scriptblock-element-for-listitem-for-listcontrol-format.md) (non mostrato) specifica lo script il cui valore viene visualizzato dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="03aea-227">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="03aea-228">È necessario specificare uno script o una proprietà, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="03aea-228">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="03aea-229">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="03aea-229">See Also</span></span>

[<span data-ttu-id="03aea-230">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="03aea-230">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/writing-a-windows-powershell-cmdlet.md)
