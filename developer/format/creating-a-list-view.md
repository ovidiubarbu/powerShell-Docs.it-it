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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861577"
---
# <a name="creating-a-list-view"></a><span data-ttu-id="88305-102">Creazione di una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="88305-102">Creating a List View</span></span>

<span data-ttu-id="88305-103">Una visualizzazione elenco Visualizza i dati in una singola colonna (in ordine sequenziale).</span><span class="sxs-lookup"><span data-stu-id="88305-103">A list view displays data in a single column (in sequential order).</span></span> <span data-ttu-id="88305-104">I dati visualizzati nell'elenco possono essere il valore della proprietà .NET o il valore di uno script.</span><span class="sxs-lookup"><span data-stu-id="88305-104">The data displayed in the list can be the value of a .NET property or the value of a script.</span></span>

## <a name="a-list-view-display"></a><span data-ttu-id="88305-105">Una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="88305-105">A List View Display</span></span>

<span data-ttu-id="88305-106">L'output seguente viene illustrato come Windows PowerShell consente di visualizzare le proprietà di [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) gli oggetti restituiti dai [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="88305-106">The following output shows how Windows PowerShell displays the properties of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects that are returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="88305-107">In questo esempio, sono stati restituiti tre oggetti, con un oggetto separato dal precedente oggetto da una riga vuota.</span><span class="sxs-lookup"><span data-stu-id="88305-107">In this example, three objects were returned, with each object separated from the preceding object by a blank line.</span></span>

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

## <a name="defining-the-list-view"></a><span data-ttu-id="88305-108">Che definisce la vista elenco</span><span class="sxs-lookup"><span data-stu-id="88305-108">Defining the List View</span></span>

<span data-ttu-id="88305-109">Il codice XML seguente viene illustrato lo schema della vista elenco per visualizzare diverse proprietà del [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) oggetto.</span><span class="sxs-lookup"><span data-stu-id="88305-109">The following XML shows the list view schema for displaying several properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="88305-110">È necessario specificare ogni proprietà che si desidera visualizzare nella visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="88305-110">You must specify each property that you want displayed in the list view.</span></span>

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

<span data-ttu-id="88305-111">Gli elementi XML seguenti vengono usati per definire una visualizzazione elenco:</span><span class="sxs-lookup"><span data-stu-id="88305-111">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="88305-112">Il [vista](./view-element-format.md) è l'elemento padre della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="88305-112">The [View](./view-element-format.md) element is the parent element of the list view.</span></span> <span data-ttu-id="88305-113">(Questo è lo stesso elemento padre per la tabella, le viste di controllo wide e personalizzati).</span><span class="sxs-lookup"><span data-stu-id="88305-113">(This is the same parent element for the table, wide, and custom control views.)</span></span>

- <span data-ttu-id="88305-114">Il [nome](./name-element-for-view-format.md) elemento specifica il nome della visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="88305-114">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="88305-115">Questo elemento è obbligatorio per tutte le visualizzazioni.</span><span class="sxs-lookup"><span data-stu-id="88305-115">This element is required for all views.</span></span>

- <span data-ttu-id="88305-116">Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento definisce gli oggetti che utilizzano la vista.</span><span class="sxs-lookup"><span data-stu-id="88305-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="88305-117">Questo elemento è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="88305-117">This element is required.</span></span>

- <span data-ttu-id="88305-118">Il [GroupBy](./groupby-element-for-view-format.md) elemento definisce quando viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="88305-118">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="88305-119">Ogni volta che cambia il valore di una proprietà specifica o uno script, viene avviato un nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="88305-119">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="88305-120">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="88305-120">This element is optional.</span></span>

- <span data-ttu-id="88305-121">Il [controlli](./controls-element-for-view-format.md) elemento definisce i controlli personalizzati che sono definiti dalla vista elenco.</span><span class="sxs-lookup"><span data-stu-id="88305-121">The [Controls](./controls-element-for-view-format.md) element defines the custom controls that are defined by the list view.</span></span> <span data-ttu-id="88305-122">Controlli offrono un modo per specificare ulteriormente la modalità di visualizzazione dei dati.</span><span class="sxs-lookup"><span data-stu-id="88305-122">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="88305-123">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="88305-123">This element is optional.</span></span> <span data-ttu-id="88305-124">Una vista può definire propri controlli personalizzati, oppure è possibile usare i controlli comuni che possono essere usati da qualsiasi visualizzazione nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="88305-124">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="88305-125">Per altre informazioni sui controlli personalizzati, vedere [Creating Custom Controls](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="88305-125">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="88305-126">Il [dell'oggetto ListControl](./listcontrol-element-format.md) elemento definisce gli elementi visualizzati nella visualizzazione e come viene formattato.</span><span class="sxs-lookup"><span data-stu-id="88305-126">The [ListControl](./listcontrol-element-format.md) element defines what is displayed in the view and how it is formatted.</span></span> <span data-ttu-id="88305-127">Analogamente a tutte le altre visualizzazioni, una visualizzazione elenco può visualizzare i valori delle proprietà degli oggetti o valori generati dallo script.</span><span class="sxs-lookup"><span data-stu-id="88305-127">Similar to all other views, a list view can display the values of object properties or values generated by script.</span></span>

<span data-ttu-id="88305-128">Per un esempio di un file di formattazione completato che definisce una visualizzazione elenco semplice, vedere [visualizzazione elenco (Basic)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="88305-128">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-list-view"></a><span data-ttu-id="88305-129">Che fornisce le definizioni per la visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="88305-129">Providing Definitions for Your List View</span></span>

<span data-ttu-id="88305-130">Visualizzazioni elenco possono fornire una o più definizioni con gli elementi figlio del [dell'oggetto ListControl](./listcontrol-element-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="88305-130">List views can provide one or more definitions by using the child elements of the [ListControl](./listcontrol-element-format.md) element.</span></span> <span data-ttu-id="88305-131">In genere, una vista avrà una sola definizione.</span><span class="sxs-lookup"><span data-stu-id="88305-131">Typically, a view will have only one definition.</span></span> <span data-ttu-id="88305-132">Nell'esempio seguente, la vista fornisce una singola definizione che consente di visualizzare diverse proprietà del [Diagnostics? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) oggetto.</span><span class="sxs-lookup"><span data-stu-id="88305-132">In the following example, the view provides a single definition that displays several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="88305-133">Una visualizzazione elenco è possibile visualizzare il valore di una proprietà o il valore di uno script (non illustrato nell'esempio).</span><span class="sxs-lookup"><span data-stu-id="88305-133">A list view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="88305-134">Gli elementi XML seguenti sono utilizzabile per fornire le definizioni per una visualizzazione elenco:</span><span class="sxs-lookup"><span data-stu-id="88305-134">The following XML elements can be used to provide definitions for a list view:</span></span>

- <span data-ttu-id="88305-135">Il [dell'oggetto ListControl](./listcontrol-element-format.md) elemento e i relativi elementi figlio definiscono gli elementi visualizzati nella vista.</span><span class="sxs-lookup"><span data-stu-id="88305-135">The [ListControl](./listcontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="88305-136">Il [ListEntries](./listentries-element-for-listcontrol-format.md) elemento fornisce le definizioni della vista.</span><span class="sxs-lookup"><span data-stu-id="88305-136">The [ListEntries](./listentries-element-for-listcontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="88305-137">Nella maggior parte dei casi, una vista avrà una sola definizione.</span><span class="sxs-lookup"><span data-stu-id="88305-137">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="88305-138">Questo elemento è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="88305-138">This element is required.</span></span>

- <span data-ttu-id="88305-139">Il [ListEntry](./listentry-element-for-listcontrol-format.md) elemento fornisce una definizione della vista.</span><span class="sxs-lookup"><span data-stu-id="88305-139">The [ListEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="88305-140">Almeno un [ListEntry](./listentry-element-for-listcontrol-format.md) è obbligatorio; tuttavia, non è definito alcun limite massimo al numero di elementi che è possibile aggiungere.</span><span class="sxs-lookup"><span data-stu-id="88305-140">At least one [ListEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="88305-141">Nella maggior parte dei casi, una vista avrà una sola definizione.</span><span class="sxs-lookup"><span data-stu-id="88305-141">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="88305-142">Il [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento specifica gli oggetti visualizzati da una definizione specifica.</span><span class="sxs-lookup"><span data-stu-id="88305-142">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="88305-143">Questo elemento è facoltativo ed è necessario solo quando si definiscono più [ListEntry](./listentry-element-for-listcontrol-format.md) gli elementi che consentono di visualizzare diversi oggetti.</span><span class="sxs-lookup"><span data-stu-id="88305-143">This element is optional and is needed only when you define multiple [ListEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="88305-144">Il [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) elemento specifica le proprietà e gli script i cui valori vengono visualizzati nelle righe della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="88305-144">The [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies the properties and scripts whose values are displayed in the rows of the list view.</span></span>

- <span data-ttu-id="88305-145">Il [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) elemento specifica una proprietà o script il cui valore viene visualizzato in una riga della visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="88305-145">The [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies a property or script whose value is displayed in a row of the list view.</span></span> <span data-ttu-id="88305-146">Una visualizzazione elenco è necessario specificare almeno una proprietà o dello script.</span><span class="sxs-lookup"><span data-stu-id="88305-146">A list view must specify at least one property or script.</span></span> <span data-ttu-id="88305-147">Non è definito alcun limite massimo al numero di righe che possono essere specificati.</span><span class="sxs-lookup"><span data-stu-id="88305-147">There is no maximum limit to the number of rows that can be specified.</span></span>

- <span data-ttu-id="88305-148">Il [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento specifica la proprietà il cui valore viene visualizzato nella riga.</span><span class="sxs-lookup"><span data-stu-id="88305-148">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="88305-149">È necessario specificare una proprietà o uno script, ma è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="88305-149">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="88305-150">Il [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento specifica lo script il cui valore viene visualizzato nella riga.</span><span class="sxs-lookup"><span data-stu-id="88305-150">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="88305-151">È necessario specificare uno script o una proprietà, ma è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="88305-151">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="88305-152">Il [etichetta](./label-element-for-listitem-for-listcontrol-format.md) elemento specifica l'etichetta che viene visualizzato a sinistra del valore della proprietà o script della riga.</span><span class="sxs-lookup"><span data-stu-id="88305-152">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element specifies the label that is displayed to the left of the property or script value in the row.</span></span> <span data-ttu-id="88305-153">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="88305-153">This element is optional.</span></span> <span data-ttu-id="88305-154">Se non viene specificata un'etichetta, viene visualizzato il nome della proprietà o lo script.</span><span class="sxs-lookup"><span data-stu-id="88305-154">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="88305-155">Per un esempio completo, vedere [visualizzazione elenco (etichette punteggio)](./list-view-labels.md).</span><span class="sxs-lookup"><span data-stu-id="88305-155">For a complete example, see [List View (Labels)](./list-view-labels.md).</span></span>

- <span data-ttu-id="88305-156">Il [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) elemento specifica una condizione che deve essere presente per la riga da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="88305-156">The [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element specifies a condition that must exist for the row to be displayed.</span></span> <span data-ttu-id="88305-157">Per altre informazioni sull'aggiunta di condizioni per la visualizzazione elenco, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="88305-157">For more information about adding conditions to the list view, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span> <span data-ttu-id="88305-158">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="88305-158">This element is optional.</span></span>

- <span data-ttu-id="88305-159">Il [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) elemento specifica un criterio che consente di visualizzare il valore della proprietà o dello script.</span><span class="sxs-lookup"><span data-stu-id="88305-159">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a pattern that is used to display the value of the property or script.</span></span> <span data-ttu-id="88305-160">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="88305-160">This element is optional.</span></span>

<span data-ttu-id="88305-161">Per un esempio di un file di formattazione completato che definisce una visualizzazione elenco semplice, vedere [visualizzazione elenco (Basic)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="88305-161">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-list-view"></a><span data-ttu-id="88305-162">Definire gli oggetti che utilizzano la vista elenco</span><span class="sxs-lookup"><span data-stu-id="88305-162">Defining the Objects That Use the List View</span></span>

<span data-ttu-id="88305-163">Esistono due modi per definire quali oggetti .NET usano la visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="88305-163">There are two ways to define which .NET objects use the list view.</span></span> <span data-ttu-id="88305-164">È possibile usare la [ViewSelectedBy](./viewselectedby-element-format.md) elemento per definire gli oggetti che possono essere visualizzati da tutte le definizioni di visualizzazione, oppure è possibile utilizzare il [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento per definire quali oggetti vengono visualizzati da un definizione della vista specifica.</span><span class="sxs-lookup"><span data-stu-id="88305-164">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="88305-165">Nella maggior parte dei casi, una vista ha una sola definizione, in modo che gli oggetti vengono in genere definiti per il [ViewSelectedBy](./viewselectedby-element-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="88305-165">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="88305-166">Nell'esempio seguente viene illustrato come definire gli oggetti che vengono visualizzati per la visualizzazione elenco utilizzando il [ViewSelectedBy](./viewselectedby-element-format.md) e [nomeTipo](./typename-element-for-viewselectedby-format.md) elementi.</span><span class="sxs-lookup"><span data-stu-id="88305-166">The following example shows how to define the objects that are displayed by the list view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="88305-167">Non sono previsti limiti al numero di [TypeName](./typename-element-for-viewselectedby-format.md) gli elementi che è possibile specificare l'ordine non è significativo.</span><span class="sxs-lookup"><span data-stu-id="88305-167">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="88305-168">Gli elementi XML seguenti sono utilizzabile per specificare gli oggetti utilizzati dalla visualizzazione elenco:</span><span class="sxs-lookup"><span data-stu-id="88305-168">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="88305-169">Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento definisce gli oggetti che vengono visualizzati nella visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="88305-169">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="88305-170">Il [TypeName](./typename-element-for-viewselectedby-format.md) elemento specifica l'oggetto .NET che viene visualizzato nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="88305-170">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="88305-171">Il nome del tipo .NET completo è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="88305-171">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="88305-172">È necessario specificare almeno un tipo o la selezione impostato per la visualizzazione, ma nessun numero massimo di elementi che possono essere specificati.</span><span class="sxs-lookup"><span data-stu-id="88305-172">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="88305-173">Per un esempio di un file di formattazione completato, vedere [visualizzazione elenco (Basic)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="88305-173">For an example of a complete formatting file, see [List View (Basic)](./list-view-basic.md).</span></span>

<span data-ttu-id="88305-174">L'esempio seguente usa il [ViewSelectedBy](./viewselectedby-element-format.md) e [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementi.</span><span class="sxs-lookup"><span data-stu-id="88305-174">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="88305-175">Usare i set di selezione in cui è presente un set correlato di oggetti che vengono visualizzati utilizzando più viste, ad esempio quando si definisce una visualizzazione elenco e visualizzazione di una tabella per gli oggetti stessi.</span><span class="sxs-lookup"><span data-stu-id="88305-175">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="88305-176">Per altre informazioni su come creare un set di selezione, vedere [definizione di set di selezione](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="88305-176">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="88305-177">Gli elementi XML seguenti sono utilizzabile per specificare gli oggetti utilizzati dalla visualizzazione elenco:</span><span class="sxs-lookup"><span data-stu-id="88305-177">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="88305-178">Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento definisce gli oggetti che vengono visualizzati nella visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="88305-178">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="88305-179">Il [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento specifica un set di oggetti che possono essere visualizzati da parte della vista.</span><span class="sxs-lookup"><span data-stu-id="88305-179">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="88305-180">È necessario specificare almeno un set di selezione o tipo per la visualizzazione, ma nessun numero massimo di elementi che possono essere specificati.</span><span class="sxs-lookup"><span data-stu-id="88305-180">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="88305-181">Nell'esempio seguente viene illustrato come definire gli oggetti visualizzati da una definizione di specifica della visualizzazione elenco mediante il [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="88305-181">The following example shows how to define the objects displayed by a specific definition of the list view using the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span></span> <span data-ttu-id="88305-182">Utilizzo di questo elemento, è possibile specificare il nome del tipo .NET dell'oggetto, un set di selezione di oggetti o una condizione di selezione che consente di specificare quando viene utilizzata la definizione.</span><span class="sxs-lookup"><span data-stu-id="88305-182">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="88305-183">Per altre informazioni su come creare una selezione condizioni, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="88305-183">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

<span data-ttu-id="88305-184">Gli elementi XML seguenti possono essere utilizzati per specificare gli oggetti usati da una definizione di specifica della visualizzazione elenco:</span><span class="sxs-lookup"><span data-stu-id="88305-184">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="88305-185">Il [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento definisce gli oggetti che vengono visualizzati per la definizione.</span><span class="sxs-lookup"><span data-stu-id="88305-185">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="88305-186">Il [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) elemento specifica l'oggetto .NET che viene visualizzato per la definizione.</span><span class="sxs-lookup"><span data-stu-id="88305-186">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="88305-187">Quando si usa questo elemento, è necessario il nome del tipo .NET completo.</span><span class="sxs-lookup"><span data-stu-id="88305-187">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="88305-188">È necessario specificare almeno un tipo, set di selezione o condizione di selezione per la definizione, ma nessun numero massimo di elementi che possono essere specificati.</span><span class="sxs-lookup"><span data-stu-id="88305-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="88305-189">Il [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) elemento (non mostrato) specifica un set di oggetti che possono essere visualizzati da questa definizione.</span><span class="sxs-lookup"><span data-stu-id="88305-189">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="88305-190">È necessario specificare almeno un tipo, set di selezione o condizione di selezione per la definizione, ma nessun numero massimo di elementi che possono essere specificati.</span><span class="sxs-lookup"><span data-stu-id="88305-190">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="88305-191">Il [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) elemento (non mostrato) specifica una condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="88305-191">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="88305-192">È necessario specificare almeno un tipo, set di selezione o condizione di selezione per la definizione, ma nessun numero massimo di elementi che possono essere specificati.</span><span class="sxs-lookup"><span data-stu-id="88305-192">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="88305-193">Per altre informazioni sulla definizione di condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="88305-193">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-list-view"></a><span data-ttu-id="88305-194">Visualizzazione di gruppi di oggetti in una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="88305-194">Displaying Groups of Objects in a List View</span></span>

<span data-ttu-id="88305-195">È possibile separare gli oggetti che vengono visualizzati nella visualizzazione elenco in gruppi.</span><span class="sxs-lookup"><span data-stu-id="88305-195">You can separate the objects that are displayed by the list view into groups.</span></span> <span data-ttu-id="88305-196">Ciò non significa che si definisce un gruppo, solo che Windows PowerShell avvia un nuovo gruppo ogni volta che cambia il valore di una proprietà specifica o uno script.</span><span class="sxs-lookup"><span data-stu-id="88305-196">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="88305-197">Nell'esempio seguente viene avviato un nuovo gruppo ogni volta che il valore della [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) le modifiche alle proprietà.</span><span class="sxs-lookup"><span data-stu-id="88305-197">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="88305-198">Gli elementi XML seguenti vengono usati per definire quando viene avviato un gruppo:</span><span class="sxs-lookup"><span data-stu-id="88305-198">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="88305-199">Il [GroupBy](./groupby-element-for-view-format.md) elemento definisce le proprietà o uno script che avvia il nuovo gruppo e definisce come viene visualizzato il gruppo.</span><span class="sxs-lookup"><span data-stu-id="88305-199">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="88305-200">Il [PropertyName](./propertyname-element-for-groupby-format.md) elemento specifica la proprietà che inizia un nuovo gruppo ogni volta che cambia il relativo valore.</span><span class="sxs-lookup"><span data-stu-id="88305-200">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="88305-201">È necessario specificare una proprietà o script per avviare il gruppo, ma è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="88305-201">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="88305-202">Il [ScriptBlock](./scriptblock-element-for-groupby-format.md) elemento specifica lo script che avvia un nuovo gruppo ogni volta che cambia il relativo valore.</span><span class="sxs-lookup"><span data-stu-id="88305-202">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="88305-203">È necessario specificare uno script o una proprietà per avviare il gruppo, ma è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="88305-203">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="88305-204">Il [etichetta](./label-element-for-groupby-format.md) elemento definisce un'etichetta che viene visualizzata all'inizio di ogni gruppo.</span><span class="sxs-lookup"><span data-stu-id="88305-204">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="88305-205">Oltre al testo specificato da questo elemento, Windows PowerShell Visualizza il valore che ha attivato il nuovo gruppo e aggiunge una riga vuota prima e dopo l'etichetta.</span><span class="sxs-lookup"><span data-stu-id="88305-205">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="88305-206">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="88305-206">This element is optional.</span></span>

- <span data-ttu-id="88305-207">Il [CustomControl](./customcontrol-element-for-groupby-format.md) elemento definisce un controllo che consente di visualizzare i dati.</span><span class="sxs-lookup"><span data-stu-id="88305-207">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="88305-208">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="88305-208">This element is optional.</span></span>

- <span data-ttu-id="88305-209">Il [CustomControlName](./customcontrolname-element-for-groupby-format.md) elemento specifica un comune o controllo che consente di visualizzare i dati di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="88305-209">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="88305-210">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="88305-210">This element is optional.</span></span>

<span data-ttu-id="88305-211">Per un esempio di un file di formattazione completato che definisce i gruppi, vedere [visualizzazione elenco (GroupBy)](./list-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="88305-211">For an example of a complete formatting file that defines groups, see [List View (GroupBy)](./list-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="88305-212">Stringhe di formato</span><span class="sxs-lookup"><span data-stu-id="88305-212">Using Format Strings</span></span>

<span data-ttu-id="88305-213">Stringhe di formattazione possono essere aggiunti a una visualizzazione per definire ulteriormente la modalità di visualizzazione dei dati.</span><span class="sxs-lookup"><span data-stu-id="88305-213">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="88305-214">Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della `StartTime` proprietà.</span><span class="sxs-lookup"><span data-stu-id="88305-214">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

<span data-ttu-id="88305-215">Gli elementi XML seguenti possono essere utilizzati per specificare uno schema di formattazione:</span><span class="sxs-lookup"><span data-stu-id="88305-215">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="88305-216">Il [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento specifica i dati che viene visualizzati nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="88305-216">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="88305-217">Il [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento specifica la proprietà il cui valore viene visualizzato nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="88305-217">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="88305-218">È necessario specificare una proprietà o uno script, ma è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="88305-218">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="88305-219">Il [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) elemento specifica un modello di formato che definisce come viene visualizzato il valore di proprietà o lo script nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="88305-219">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

- <span data-ttu-id="88305-220">Il [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento (non mostrato) consente di specificare lo script il cui valore viene visualizzato nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="88305-220">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="88305-221">È necessario specificare uno script o una proprietà, ma è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="88305-221">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="88305-222">Nell'esempio seguente, il `ToString` metodo viene chiamato per formattare il valore dello script.</span><span class="sxs-lookup"><span data-stu-id="88305-222">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="88305-223">Gli script possono chiamare qualsiasi metodo di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="88305-223">Scripts can call any method of an object.</span></span> <span data-ttu-id="88305-224">Pertanto, se un oggetto dispone di un metodo, ad esempio `ToString`, che può avere parametri di formattazione, lo script può chiamare tale metodo per formattare il valore di output dello script.</span><span class="sxs-lookup"><span data-stu-id="88305-224">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="88305-225">L'elemento XML seguente è utilizzabile per chiamare il `ToString` metodo:</span><span class="sxs-lookup"><span data-stu-id="88305-225">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="88305-226">Il [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento specifica i dati che viene visualizzati nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="88305-226">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="88305-227">Il [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento (non mostrato) consente di specificare lo script il cui valore viene visualizzato nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="88305-227">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="88305-228">È necessario specificare uno script o una proprietà, ma è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="88305-228">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="88305-229">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="88305-229">See Also</span></span>

[<span data-ttu-id="88305-230">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="88305-230">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/writing-a-windows-powershell-cmdlet.md)
