---
title: Creazione di una visualizzazione più ampia | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066720"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="7aa97-102">Creazione di una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="7aa97-102">Creating a Wide View</span></span>

<span data-ttu-id="7aa97-103">Una visualizzazione più ampia Visualizza un singolo valore per ogni oggetto che viene visualizzato.</span><span class="sxs-lookup"><span data-stu-id="7aa97-103">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="7aa97-104">Il valore visualizzato può essere il valore di una proprietà dell'oggetto .NET oppure il valore di uno script.</span><span class="sxs-lookup"><span data-stu-id="7aa97-104">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="7aa97-105">Per impostazione predefinita, non l'etichetta o intestazione per questa visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="7aa97-105">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="7aa97-106">Visualizzare una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="7aa97-106">A Wide View Display</span></span>

<span data-ttu-id="7aa97-107">Nell'esempio seguente viene illustrato come Windows PowerShell consente di visualizzare il [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto restituito dalle [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet quando il relativo output viene reindirizzato al [ Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7aa97-107">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="7aa97-108">(Per impostazione predefinita, il [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet restituisce una visualizzazione tabella.) In questo esempio, le due colonne vengono usate per visualizzare il nome del processo per ogni oggetto restituito.</span><span class="sxs-lookup"><span data-stu-id="7aa97-108">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="7aa97-109">Il nome della proprietà dell'oggetto non viene visualizzato, solo il valore della proprietà.</span><span class="sxs-lookup"><span data-stu-id="7aa97-109">The name of the object's property is not displayed, only the value of the property.</span></span>

```
Get-Process | format-wide
AEADISRV                     agrsmsvc
Ati2evxx                     Ati2evxx
audiodg                      CCC
CcmExec                      communicator
Crypserv                     csrss
csrss                        DevDtct2
DM1Service                   dpupdchk
dwm                          DxStudio
EXCEL                        explorer
GoogleToolbarNotifier        GrooveMonitor
hpqwmiex                     hpservice
Idle                         InoRpc
InoRT                        InoTask
ipoint                       lsass
lsm                          MOM
MSASCui                      notepad
...                          ...

```

## <a name="defining-the-wide-view"></a><span data-ttu-id="7aa97-110">Che definisce la visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="7aa97-110">Defining the Wide View</span></span>

<span data-ttu-id="7aa97-111">Il codice XML seguente mostra lo schema di visualizzazione più ampia per il [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto.</span><span class="sxs-lookup"><span data-stu-id="7aa97-111">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <GroupBy>...</GroupBy>
  <Controls>...</Controls>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

<span data-ttu-id="7aa97-112">Gli elementi XML seguenti vengono usati per definire una visualizzazione più ampia:</span><span class="sxs-lookup"><span data-stu-id="7aa97-112">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="7aa97-113">Il [vista](./view-element-format.md) è l'elemento padre di visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="7aa97-113">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="7aa97-114">(Questo è lo stesso elemento padre per la tabella, elenco e le viste di controllo personalizzato).</span><span class="sxs-lookup"><span data-stu-id="7aa97-114">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="7aa97-115">Il [nome](./name-element-for-view-format.md) elemento specifica il nome della visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="7aa97-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="7aa97-116">Questo elemento è obbligatorio per tutte le visualizzazioni.</span><span class="sxs-lookup"><span data-stu-id="7aa97-116">This element is required for all views.</span></span>

- <span data-ttu-id="7aa97-117">Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento definisce gli oggetti che utilizzano la vista.</span><span class="sxs-lookup"><span data-stu-id="7aa97-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="7aa97-118">Questo elemento è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="7aa97-118">This element is required.</span></span>

- <span data-ttu-id="7aa97-119">Il [GroupBy](./groupby-element-for-view-format.md) elemento definisce quando viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="7aa97-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="7aa97-120">Ogni volta che cambia il valore di una proprietà specifica o uno script, viene avviato un nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="7aa97-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="7aa97-121">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7aa97-121">This element is optional.</span></span>

- <span data-ttu-id="7aa97-122">Il [controlli](./controls-element-for-view-format.md) elementi definisce i controlli personalizzati definiti per la visualizzazione più ampia.</span><span class="sxs-lookup"><span data-stu-id="7aa97-122">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="7aa97-123">Controlli offrono un modo per specificare ulteriormente la modalità di visualizzazione dei dati.</span><span class="sxs-lookup"><span data-stu-id="7aa97-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="7aa97-124">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7aa97-124">This element is optional.</span></span> <span data-ttu-id="7aa97-125">Una vista può definire propri controlli personalizzati, oppure è possibile usare i controlli comuni che possono essere usati da qualsiasi visualizzazione nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="7aa97-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="7aa97-126">Per altre informazioni sui controlli personalizzati, vedere [Creating Custom Controls](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="7aa97-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="7aa97-127">Il [WideControl](./widecontrol-element-format.md) elemento e i relativi elementi figlio definiscono gli elementi visualizzati nella vista.</span><span class="sxs-lookup"><span data-stu-id="7aa97-127">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="7aa97-128">Nell'esempio precedente, la vista è progettata per visualizzare il [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) proprietà.</span><span class="sxs-lookup"><span data-stu-id="7aa97-128">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="7aa97-129">Per un esempio di un file di formattazione completato che definisce una semplice visualizzazione più ampia, vedere [visualizzazione più ampia (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="7aa97-129">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="7aa97-130">Che fornisce le definizioni per la visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="7aa97-130">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="7aa97-131">Visualizzazioni ampie possono fornire una o più definizioni con gli elementi figlio del [WideControl](./widecontrol-element-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="7aa97-131">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="7aa97-132">In genere, una vista avrà una sola definizione.</span><span class="sxs-lookup"><span data-stu-id="7aa97-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="7aa97-133">Nell'esempio seguente, la vista fornisce una singola definizione che visualizza il valore della [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) proprietà.</span><span class="sxs-lookup"><span data-stu-id="7aa97-133">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="7aa97-134">Una visualizzazione più ampia possibile visualizzare il valore di una proprietà o il valore di uno script (non illustrato nell'esempio).</span><span class="sxs-lookup"><span data-stu-id="7aa97-134">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber></ColumnNumber>
  <WideEntries>
    <WideEntry>
      <WideItem>
        <PropertyName>ProcessName</PropertyName>
      </WideItem>
    </WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="7aa97-135">Gli elementi XML seguenti possono essere utilizzati per fornire le definizioni per una visualizzazione più ampia:</span><span class="sxs-lookup"><span data-stu-id="7aa97-135">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="7aa97-136">Il [WideControl](./widecontrol-element-format.md) elemento e i relativi elementi figlio definiscono gli elementi visualizzati nella vista.</span><span class="sxs-lookup"><span data-stu-id="7aa97-136">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="7aa97-137">Il [AutoSize](./autosize-element-for-widecontrol-format.md) elemento consente di specificare se la dimensione della colonna e il numero di colonne vengono adattate in base alla dimensione dei dati.</span><span class="sxs-lookup"><span data-stu-id="7aa97-137">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="7aa97-138">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7aa97-138">This element is optional.</span></span>

- <span data-ttu-id="7aa97-139">Il [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) elemento specifica il numero di colonne nella visualizzazione wide.</span><span class="sxs-lookup"><span data-stu-id="7aa97-139">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="7aa97-140">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7aa97-140">This element is optional.</span></span>

- <span data-ttu-id="7aa97-141">Il [WideEntries](./wideentries-element-for-widecontrol-format.md) elemento fornisce le definizioni della vista.</span><span class="sxs-lookup"><span data-stu-id="7aa97-141">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="7aa97-142">Nella maggior parte dei casi, una vista avrà una sola definizione.</span><span class="sxs-lookup"><span data-stu-id="7aa97-142">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="7aa97-143">Questo elemento è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="7aa97-143">This element is required.</span></span>

- <span data-ttu-id="7aa97-144">Il [WideEntry](./wideentry-element-for-widecontrol-format.md) elemento fornisce una definizione della vista.</span><span class="sxs-lookup"><span data-stu-id="7aa97-144">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="7aa97-145">Almeno un [WideEntry](./wideentry-element-for-widecontrol-format.md) è obbligatorio; tuttavia, non è definito alcun limite massimo al numero di elementi che è possibile aggiungere.</span><span class="sxs-lookup"><span data-stu-id="7aa97-145">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="7aa97-146">Nella maggior parte dei casi, una vista avrà una sola definizione.</span><span class="sxs-lookup"><span data-stu-id="7aa97-146">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="7aa97-147">Il [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento specifica gli oggetti visualizzati da una definizione specifica.</span><span class="sxs-lookup"><span data-stu-id="7aa97-147">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="7aa97-148">Questo elemento è facoltativo ed è necessario solo quando si definiscono più [WideEntry](./wideentry-element-for-widecontrol-format.md) gli elementi che consentono di visualizzare diversi oggetti.</span><span class="sxs-lookup"><span data-stu-id="7aa97-148">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="7aa97-149">Il [WideItem](./wideitem-element-for-widecontrol-format.md) elemento specifica i dati che viene visualizzati nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="7aa97-149">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="7aa97-150">A differenza di altri tipi di visualizzazioni, è possibile visualizzare un controllo wide un solo elemento.</span><span class="sxs-lookup"><span data-stu-id="7aa97-150">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="7aa97-151">Il [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) elemento specifica la proprietà il cui valore viene visualizzato nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="7aa97-151">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="7aa97-152">È necessario specificare una proprietà o uno script, ma è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="7aa97-152">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="7aa97-153">Il [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elemento specifica lo script il cui valore viene visualizzato nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="7aa97-153">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="7aa97-154">È necessario specificare uno script o una proprietà, ma è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="7aa97-154">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="7aa97-155">Il [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) elemento specifica un criterio che consente di visualizzare i dati.</span><span class="sxs-lookup"><span data-stu-id="7aa97-155">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="7aa97-156">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7aa97-156">This element is optional.</span></span>

<span data-ttu-id="7aa97-157">Per un esempio di un file di formattazione completato che definisce una definizione di visualizzazione estesa, vedere [visualizzazione più ampia (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="7aa97-157">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="7aa97-158">Definire gli oggetti che usano la visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="7aa97-158">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="7aa97-159">Esistono due modi per definire quali oggetti .NET usano la visualizzazione più ampia.</span><span class="sxs-lookup"><span data-stu-id="7aa97-159">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="7aa97-160">È possibile usare la [ViewSelectedBy](./viewselectedby-element-format.md) elemento per definire gli oggetti che possono essere visualizzati da tutte le definizioni di visualizzazione, oppure è possibile utilizzare il [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento per definire quali oggetti vengono visualizzati da un definizione della vista specifica.</span><span class="sxs-lookup"><span data-stu-id="7aa97-160">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="7aa97-161">Nella maggior parte dei casi, una vista ha una sola definizione, in modo che gli oggetti vengono in genere definiti per il [ViewSelectedBy](./viewselectedby-element-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="7aa97-161">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="7aa97-162">Nell'esempio seguente viene illustrato come definire gli oggetti che vengono visualizzati tramite la visualizzazione più ampia di [ViewSelectedBy](./viewselectedby-element-format.md) e [nomeTipo](./typename-element-for-viewselectedby-format.md) elementi.</span><span class="sxs-lookup"><span data-stu-id="7aa97-162">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="7aa97-163">Non sono previsti limiti al numero di [TypeName](./typename-element-for-viewselectedby-format.md) gli elementi che è possibile specificare l'ordine non è significativo.</span><span class="sxs-lookup"><span data-stu-id="7aa97-163">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="7aa97-164">Gli elementi XML seguenti sono utilizzabile per specificare gli oggetti utilizzati per la visualizzazione più ampia:</span><span class="sxs-lookup"><span data-stu-id="7aa97-164">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="7aa97-165">Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento definisce gli oggetti che vengono visualizzati per la visualizzazione più ampia.</span><span class="sxs-lookup"><span data-stu-id="7aa97-165">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="7aa97-166">Il [TypeName](./typename-element-for-viewselectedby-format.md) elemento specifica di .NET che viene visualizzato nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="7aa97-166">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="7aa97-167">Il nome del tipo .NET completo è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="7aa97-167">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="7aa97-168">È necessario specificare almeno un tipo o la selezione impostato per la visualizzazione, ma nessun numero massimo di elementi che possono essere specificati.</span><span class="sxs-lookup"><span data-stu-id="7aa97-168">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="7aa97-169">Per un esempio di un file di formattazione completato, vedere [visualizzazione più ampia (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="7aa97-169">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="7aa97-170">L'esempio seguente usa il [ViewSelectedBy](./viewselectedby-element-format.md) e [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementi.</span><span class="sxs-lookup"><span data-stu-id="7aa97-170">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="7aa97-171">Usare i set di selezione in cui è presente un set correlato di oggetti che vengono visualizzati utilizzando più viste, ad esempio quando si definisce una visualizzazione più ampia e visualizzazione di una tabella per gli oggetti stessi.</span><span class="sxs-lookup"><span data-stu-id="7aa97-171">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="7aa97-172">Per altre informazioni su come creare un set di selezione, vedere [definizione di set di selezione](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="7aa97-172">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="7aa97-173">Gli elementi XML seguenti sono utilizzabile per specificare gli oggetti utilizzati per la visualizzazione più ampia:</span><span class="sxs-lookup"><span data-stu-id="7aa97-173">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="7aa97-174">Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento definisce gli oggetti che vengono visualizzati per la visualizzazione più ampia.</span><span class="sxs-lookup"><span data-stu-id="7aa97-174">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="7aa97-175">Il [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento specifica un set di oggetti che possono essere visualizzati da parte della vista.</span><span class="sxs-lookup"><span data-stu-id="7aa97-175">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="7aa97-176">È necessario specificare almeno un set di selezione o tipo per la visualizzazione, ma nessun numero massimo di elementi che possono essere specificati.</span><span class="sxs-lookup"><span data-stu-id="7aa97-176">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="7aa97-177">Nell'esempio seguente viene illustrato come definire gli oggetti visualizzati da una definizione di specifica della visualizzazione estesa utilizzando la [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="7aa97-177">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="7aa97-178">Utilizzo di questo elemento, è possibile specificare il nome del tipo .NET dell'oggetto, un set di selezione di oggetti o una condizione di selezione che consente di specificare quando viene utilizzata la definizione.</span><span class="sxs-lookup"><span data-stu-id="7aa97-178">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="7aa97-179">Per altre informazioni su come creare una selezione condizioni, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="7aa97-179">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="7aa97-180">Gli elementi XML seguenti sono utilizzabile per specificare gli oggetti usati da una definizione di specifica di visualizzazione estesa:</span><span class="sxs-lookup"><span data-stu-id="7aa97-180">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="7aa97-181">Il [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento definisce gli oggetti che vengono visualizzati per la definizione.</span><span class="sxs-lookup"><span data-stu-id="7aa97-181">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="7aa97-182">Il [TypeName](./typename-element-for-viewselectedby-format.md) elemento specifica di .NET che viene visualizzato per la definizione.</span><span class="sxs-lookup"><span data-stu-id="7aa97-182">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="7aa97-183">Quando si usa questo elemento è necessario il nome del tipo .NET completo.</span><span class="sxs-lookup"><span data-stu-id="7aa97-183">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="7aa97-184">È necessario specificare almeno un tipo, set di selezione o condizione di selezione per la definizione, ma nessun numero massimo di elementi che possono essere specificati.</span><span class="sxs-lookup"><span data-stu-id="7aa97-184">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="7aa97-185">Il [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento (non mostrato) specifica un set di oggetti che possono essere visualizzati da questa definizione.</span><span class="sxs-lookup"><span data-stu-id="7aa97-185">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="7aa97-186">È necessario specificare almeno un tipo, set di selezione o condizione di selezione per la definizione, ma nessun numero massimo di elementi che possono essere specificati.</span><span class="sxs-lookup"><span data-stu-id="7aa97-186">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="7aa97-187">Il [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) elemento (non mostrato) specifica una condizione che deve essere presente per questa definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="7aa97-187">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="7aa97-188">È necessario specificare almeno un tipo, set di selezione o condizione di selezione per la definizione, ma nessun numero massimo di elementi che possono essere specificati.</span><span class="sxs-lookup"><span data-stu-id="7aa97-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="7aa97-189">Per altre informazioni sulla definizione di condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="7aa97-189">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="7aa97-190">Visualizzazione di gruppi di oggetti in una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="7aa97-190">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="7aa97-191">È possibile separare gli oggetti che vengono visualizzati per la visualizzazione più ampia in gruppi.</span><span class="sxs-lookup"><span data-stu-id="7aa97-191">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="7aa97-192">Ciò non significa che si definisce un gruppo, solo che Windows PowerShell avvia un nuovo gruppo ogni volta che cambia il valore di una proprietà specifica o uno script.</span><span class="sxs-lookup"><span data-stu-id="7aa97-192">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="7aa97-193">Nell'esempio seguente viene avviato un nuovo gruppo ogni volta che il valore della [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) le modifiche alle proprietà.</span><span class="sxs-lookup"><span data-stu-id="7aa97-193">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="7aa97-194">Gli elementi XML seguenti vengono usati per definire quando viene avviato un gruppo:</span><span class="sxs-lookup"><span data-stu-id="7aa97-194">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="7aa97-195">Il [GroupBy](./groupby-element-for-view-format.md) elemento definisce le proprietà o uno script che avvia il nuovo gruppo e definisce come viene visualizzato il gruppo.</span><span class="sxs-lookup"><span data-stu-id="7aa97-195">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="7aa97-196">Il [PropertyName](./propertyname-element-for-groupby-format.md) elemento specifica la proprietà che inizia un nuovo gruppo ogni volta che cambia il relativo valore.</span><span class="sxs-lookup"><span data-stu-id="7aa97-196">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="7aa97-197">È necessario specificare una proprietà o script per avviare il gruppo, ma è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="7aa97-197">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="7aa97-198">Il [ScriptBlock](./scriptblock-element-for-groupby-format.md) elemento specifica lo script che avvia un nuovo gruppo ogni volta che cambia il relativo valore.</span><span class="sxs-lookup"><span data-stu-id="7aa97-198">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="7aa97-199">È necessario specificare uno script o una proprietà per avviare il gruppo, ma è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="7aa97-199">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="7aa97-200">Il [etichetta](./label-element-for-groupby-format.md) elemento definisce un'etichetta che viene visualizzata all'inizio di ogni gruppo.</span><span class="sxs-lookup"><span data-stu-id="7aa97-200">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="7aa97-201">Oltre al testo specificato da questo elemento, Windows PowerShell Visualizza il valore che ha attivato il nuovo gruppo e aggiunge una riga vuota prima e dopo l'etichetta.</span><span class="sxs-lookup"><span data-stu-id="7aa97-201">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="7aa97-202">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7aa97-202">This element is optional.</span></span>

- <span data-ttu-id="7aa97-203">Il [CustomControl](./customcontrol-element-for-groupby-format.md) elemento definisce un controllo che consente di visualizzare i dati.</span><span class="sxs-lookup"><span data-stu-id="7aa97-203">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="7aa97-204">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7aa97-204">This element is optional.</span></span>

- <span data-ttu-id="7aa97-205">Il [CustomControlName](./customcontrolname-element-for-groupby-format.md) elemento specifica un comune o controllo che consente di visualizzare i dati di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="7aa97-205">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="7aa97-206">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7aa97-206">This element is optional.</span></span>

<span data-ttu-id="7aa97-207">Per un esempio di un file di formattazione completato che definisce i gruppi, vedere [visualizzazione più ampia (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="7aa97-207">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="7aa97-208">Stringhe di formato</span><span class="sxs-lookup"><span data-stu-id="7aa97-208">Using Format Strings</span></span>

<span data-ttu-id="7aa97-209">Stringhe di formattazione possono essere aggiunti a una visualizzazione più ampia per definire ulteriormente la modalità di visualizzazione dei dati.</span><span class="sxs-lookup"><span data-stu-id="7aa97-209">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="7aa97-210">Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della `StartTime` proprietà.</span><span class="sxs-lookup"><span data-stu-id="7aa97-210">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="7aa97-211">Gli elementi XML seguenti possono essere utilizzati per specificare uno schema di formattazione:</span><span class="sxs-lookup"><span data-stu-id="7aa97-211">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="7aa97-212">Il [WideItem](./wideitem-element-for-widecontrol-format.md) elemento specifica i dati che viene visualizzati nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="7aa97-212">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="7aa97-213">Il [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) elemento specifica la proprietà il cui valore viene visualizzato nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="7aa97-213">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="7aa97-214">È necessario specificare una proprietà o uno script, ma è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="7aa97-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="7aa97-215">Il [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) elemento specifica un modello di formato che definisce come viene visualizzato il valore di proprietà o lo script nella visualizzazione</span><span class="sxs-lookup"><span data-stu-id="7aa97-215">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="7aa97-216">Il [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elemento (non mostrato) consente di specificare lo script il cui valore viene visualizzato nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="7aa97-216">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="7aa97-217">È necessario specificare uno script o una proprietà, ma è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="7aa97-217">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="7aa97-218">Nell'esempio seguente, il `ToString` metodo viene chiamato per formattare il valore dello script.</span><span class="sxs-lookup"><span data-stu-id="7aa97-218">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="7aa97-219">Gli script possono chiamare qualsiasi metodo di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="7aa97-219">Scripts can call any method of an object.</span></span> <span data-ttu-id="7aa97-220">Pertanto, se un oggetto dispone di un metodo, ad esempio `ToString`, che può avere parametri di formattazione, lo script può chiamare tale metodo per formattare il valore di output dello script.</span><span class="sxs-lookup"><span data-stu-id="7aa97-220">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="7aa97-221">L'elemento XML seguente è utilizzabile per chiamare il `ToString` metodo:</span><span class="sxs-lookup"><span data-stu-id="7aa97-221">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="7aa97-222">Il [WideItem](./wideitem-element-for-widecontrol-format.md) elemento specifica i dati che viene visualizzati nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="7aa97-222">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="7aa97-223">Il [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elemento (non mostrato) consente di specificare lo script il cui valore viene visualizzato nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="7aa97-223">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="7aa97-224">È necessario specificare uno script o una proprietà, ma è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="7aa97-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="7aa97-225">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7aa97-225">See Also</span></span>

[<span data-ttu-id="7aa97-226">Visualizzazione più ampia (Basic)</span><span class="sxs-lookup"><span data-stu-id="7aa97-226">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="7aa97-227">Visualizzazione più ampia (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="7aa97-227">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="7aa97-228">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="7aa97-228">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
