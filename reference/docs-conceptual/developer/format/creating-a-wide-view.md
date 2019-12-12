---
title: Creazione di una visualizzazione estesa | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368950"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="98346-102">Creazione di una visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="98346-102">Creating a Wide View</span></span>

<span data-ttu-id="98346-103">In una visualizzazione estesa viene visualizzato un singolo valore per ogni oggetto visualizzato.</span><span class="sxs-lookup"><span data-stu-id="98346-103">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="98346-104">Il valore visualizzato può corrispondere al valore di una proprietà dell'oggetto .NET o al valore di uno script.</span><span class="sxs-lookup"><span data-stu-id="98346-104">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="98346-105">Per impostazione predefinita, non è presente alcuna etichetta o intestazione per questa visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="98346-105">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="98346-106">Visualizzazione dell'ampia visualizzazione</span><span class="sxs-lookup"><span data-stu-id="98346-106">A Wide View Display</span></span>

<span data-ttu-id="98346-107">Nell'esempio seguente viene illustrato come Windows PowerShell visualizzi l'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) restituito dal cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) quando l'output viene reindirizzato al cmdlet [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) .</span><span class="sxs-lookup"><span data-stu-id="98346-107">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="98346-108">Per impostazione predefinita, il cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) restituisce una visualizzazione tabella. In questo esempio le due colonne vengono usate per visualizzare il nome del processo per ogni oggetto restituito.</span><span class="sxs-lookup"><span data-stu-id="98346-108">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="98346-109">Il nome della proprietà dell'oggetto non viene visualizzato, ma solo il valore della proprietà.</span><span class="sxs-lookup"><span data-stu-id="98346-109">The name of the object's property is not displayed, only the value of the property.</span></span>

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

## <a name="defining-the-wide-view"></a><span data-ttu-id="98346-110">Definizione della visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="98346-110">Defining the Wide View</span></span>

<span data-ttu-id="98346-111">Il codice XML seguente mostra lo schema di visualizzazione estesa per l'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="98346-111">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="98346-112">Gli elementi XML seguenti vengono utilizzati per definire una visualizzazione estesa:</span><span class="sxs-lookup"><span data-stu-id="98346-112">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="98346-113">L'elemento [View](./view-element-format.md) è l'elemento padre della visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="98346-113">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="98346-114">Si tratta dello stesso elemento padre per le visualizzazioni tabella, elenco e controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="98346-114">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="98346-115">L'elemento [Name](./name-element-for-view-format.md) specifica il nome della vista.</span><span class="sxs-lookup"><span data-stu-id="98346-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="98346-116">Questo elemento è obbligatorio per tutte le visualizzazioni.</span><span class="sxs-lookup"><span data-stu-id="98346-116">This element is required for all views.</span></span>

- <span data-ttu-id="98346-117">L'elemento [ViewSelectedBy](./viewselectedby-element-format.md) definisce gli oggetti che utilizzano la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="98346-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="98346-118">Questo elemento è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="98346-118">This element is required.</span></span>

- <span data-ttu-id="98346-119">L'elemento [GroupBy](./groupby-element-for-view-format.md) definisce quando viene visualizzato un nuovo gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="98346-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="98346-120">Un nuovo gruppo viene avviato ogni volta che viene modificato il valore di una proprietà o di uno script specifico.</span><span class="sxs-lookup"><span data-stu-id="98346-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="98346-121">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="98346-121">This element is optional.</span></span>

- <span data-ttu-id="98346-122">Gli elementi [Controls](./controls-element-for-view-format.md) definiscono i controlli personalizzati definiti dall'ampia visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="98346-122">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="98346-123">I controlli consentono di specificare in modo più dettagliato la modalità di visualizzazione dei dati.</span><span class="sxs-lookup"><span data-stu-id="98346-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="98346-124">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="98346-124">This element is optional.</span></span> <span data-ttu-id="98346-125">Una vista può definire i propri controlli personalizzati oppure può utilizzare controlli comuni che possono essere utilizzati da qualsiasi visualizzazione nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="98346-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="98346-126">Per ulteriori informazioni sui controlli personalizzati, vedere [creazione di controlli personalizzati](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="98346-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="98346-127">L'elemento [WideControl](./widecontrol-element-format.md) e i relativi elementi figlio definiscono ciò che viene visualizzato nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="98346-127">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="98346-128">Nell'esempio precedente, la vista è progettata per visualizzare la proprietà [System. Diagnostics. Process. ProcessName](/dotnet/api/System.Diagnostics.Process.ProcessName) .</span><span class="sxs-lookup"><span data-stu-id="98346-128">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="98346-129">Per un esempio di un file di formattazione completo che definisce una visualizzazione estesa semplice, vedere [Wide View (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="98346-129">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="98346-130">Fornire definizioni per la visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="98346-130">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="98346-131">Le visualizzazioni Wide possono fornire una o più definizioni usando gli elementi figlio dell'elemento [WideControl](./widecontrol-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="98346-131">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="98346-132">In genere, una vista avrà una sola definizione.</span><span class="sxs-lookup"><span data-stu-id="98346-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="98346-133">Nell'esempio seguente, la vista fornisce una singola definizione che Visualizza il valore della proprietà [System. Diagnostics. Process. ProcessName](/dotnet/api/System.Diagnostics.Process.ProcessName) .</span><span class="sxs-lookup"><span data-stu-id="98346-133">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="98346-134">Una visualizzazione estesa può visualizzare il valore di una proprietà o il valore di uno script (non illustrato nell'esempio).</span><span class="sxs-lookup"><span data-stu-id="98346-134">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="98346-135">È possibile utilizzare gli elementi XML seguenti per fornire definizioni per una visualizzazione estesa:</span><span class="sxs-lookup"><span data-stu-id="98346-135">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="98346-136">L'elemento [WideControl](./widecontrol-element-format.md) e i relativi elementi figlio definiscono ciò che viene visualizzato nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="98346-136">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="98346-137">L'elemento [AutoSize](./autosize-element-for-widecontrol-format.md) specifica se le dimensioni della colonna e il numero di colonne vengono regolate in base alle dimensioni dei dati.</span><span class="sxs-lookup"><span data-stu-id="98346-137">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="98346-138">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="98346-138">This element is optional.</span></span>

- <span data-ttu-id="98346-139">L'elemento [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) specifica il numero di colonne visualizzate nella visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="98346-139">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="98346-140">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="98346-140">This element is optional.</span></span>

- <span data-ttu-id="98346-141">L'elemento [WideEntries](./wideentries-element-for-widecontrol-format.md) fornisce le definizioni della vista.</span><span class="sxs-lookup"><span data-stu-id="98346-141">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="98346-142">Nella maggior parte dei casi, una vista avrà una sola definizione.</span><span class="sxs-lookup"><span data-stu-id="98346-142">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="98346-143">Questo elemento è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="98346-143">This element is required.</span></span>

- <span data-ttu-id="98346-144">L'elemento [WideEntry](./wideentry-element-for-widecontrol-format.md) fornisce una definizione della vista.</span><span class="sxs-lookup"><span data-stu-id="98346-144">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="98346-145">È necessario almeno un [WideEntry](./wideentry-element-for-widecontrol-format.md) . Tuttavia, non esiste alcun limite massimo per il numero di elementi che è possibile aggiungere.</span><span class="sxs-lookup"><span data-stu-id="98346-145">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="98346-146">Nella maggior parte dei casi, una vista avrà una sola definizione.</span><span class="sxs-lookup"><span data-stu-id="98346-146">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="98346-147">L'elemento [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) specifica gli oggetti visualizzati da una definizione specifica.</span><span class="sxs-lookup"><span data-stu-id="98346-147">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="98346-148">Questo elemento è facoltativo ed è necessario solo quando si definiscono più elementi [WideEntry](./wideentry-element-for-widecontrol-format.md) che visualizzano oggetti diversi.</span><span class="sxs-lookup"><span data-stu-id="98346-148">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="98346-149">L'elemento [WideItem](./wideitem-element-for-widecontrol-format.md) specifica i dati visualizzati dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="98346-149">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="98346-150">Diversamente da altri tipi di viste, un controllo Wide può visualizzare solo un elemento.</span><span class="sxs-lookup"><span data-stu-id="98346-150">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="98346-151">L'elemento [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) specifica la proprietà il cui valore viene visualizzato dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="98346-151">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="98346-152">È necessario specificare una proprietà o uno script, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="98346-152">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="98346-153">L'elemento [scriptblock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) specifica lo script il cui valore viene visualizzato dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="98346-153">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="98346-154">È necessario specificare uno script o una proprietà, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="98346-154">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="98346-155">L'elemento [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) specifica un modello usato per visualizzare i dati.</span><span class="sxs-lookup"><span data-stu-id="98346-155">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="98346-156">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="98346-156">This element is optional.</span></span>

<span data-ttu-id="98346-157">Per un esempio di un file di formattazione completo che definisce una definizione di visualizzazione estesa, vedere [Wide View (base)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="98346-157">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="98346-158">Definizione degli oggetti che utilizzano la visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="98346-158">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="98346-159">Esistono due modi per definire gli oggetti .NET che utilizzano l'ampia visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="98346-159">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="98346-160">È possibile utilizzare l'elemento [ViewSelectedBy](./viewselectedby-element-format.md) per definire gli oggetti che possono essere visualizzati da tutte le definizioni della vista oppure è possibile utilizzare l'elemento [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) per definire quali oggetti vengono visualizzati da una definizione specifica della vista.</span><span class="sxs-lookup"><span data-stu-id="98346-160">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="98346-161">Nella maggior parte dei casi, una vista ha una sola definizione, quindi gli oggetti vengono in genere definiti dall'elemento [ViewSelectedBy](./viewselectedby-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="98346-161">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="98346-162">Nell'esempio seguente viene illustrato come definire gli oggetti visualizzati dalla visualizzazione estesa utilizzando gli elementi [ViewSelectedBy](./viewselectedby-element-format.md) e [typeName](./typename-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="98346-162">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="98346-163">Non esiste alcun limite al numero di elementi [typeName](./typename-element-for-viewselectedby-format.md) che è possibile specificare e il loro ordine non è significativo.</span><span class="sxs-lookup"><span data-stu-id="98346-163">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="98346-164">Gli elementi XML seguenti possono essere utilizzati per specificare gli oggetti utilizzati dalla visualizzazione estesa:</span><span class="sxs-lookup"><span data-stu-id="98346-164">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="98346-165">L'elemento [ViewSelectedBy](./viewselectedby-element-format.md) definisce quali oggetti vengono visualizzati dall'ampia visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="98346-165">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="98346-166">L'elemento [typeName](./typename-element-for-viewselectedby-format.md) specifica il .NET visualizzato dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="98346-166">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="98346-167">Il nome completo del tipo .NET è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="98346-167">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="98346-168">È necessario specificare almeno un tipo o un set di selezione per la vista, ma non esiste un numero massimo di elementi che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="98346-168">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="98346-169">Per un esempio di un file di formattazione completo, vedere [visualizzazione estesa (di base)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="98346-169">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="98346-170">Nell'esempio seguente vengono usati gli elementi [ViewSelectedBy](./viewselectedby-element-format.md) e [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="98346-170">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="98346-171">Utilizzare i set di selezione in cui è presente un set correlato di oggetti visualizzati utilizzando più visualizzazioni, ad esempio quando si definiscono una visualizzazione estesa e una vista tabella per gli stessi oggetti.</span><span class="sxs-lookup"><span data-stu-id="98346-171">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="98346-172">Per ulteriori informazioni su come creare un set di selezione, vedere [definizione](./defining-selection-sets.md)di set di selezione.</span><span class="sxs-lookup"><span data-stu-id="98346-172">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="98346-173">Gli elementi XML seguenti possono essere utilizzati per specificare gli oggetti utilizzati dalla visualizzazione estesa:</span><span class="sxs-lookup"><span data-stu-id="98346-173">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="98346-174">L'elemento [ViewSelectedBy](./viewselectedby-element-format.md) definisce quali oggetti vengono visualizzati dall'ampia visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="98346-174">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="98346-175">L'elemento [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) specifica un set di oggetti che possono essere visualizzati dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="98346-175">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="98346-176">È necessario specificare almeno un set di selezione o un tipo per la vista, ma non esiste un numero massimo di elementi che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="98346-176">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="98346-177">Nell'esempio seguente viene illustrato come definire gli oggetti visualizzati da una definizione specifica della visualizzazione estesa utilizzando l'elemento [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) .</span><span class="sxs-lookup"><span data-stu-id="98346-177">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="98346-178">Utilizzando questo elemento, è possibile specificare il nome del tipo .NET dell'oggetto, un set di selezione di oggetti o una condizione di selezione che specifica quando viene utilizzata la definizione.</span><span class="sxs-lookup"><span data-stu-id="98346-178">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="98346-179">Per ulteriori informazioni sulla creazione di condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="98346-179">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="98346-180">Gli elementi XML seguenti possono essere utilizzati per specificare gli oggetti utilizzati da una definizione specifica dell'ampia visualizzazione:</span><span class="sxs-lookup"><span data-stu-id="98346-180">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="98346-181">L'elemento [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) definisce quali oggetti vengono visualizzati dalla definizione.</span><span class="sxs-lookup"><span data-stu-id="98346-181">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="98346-182">L'elemento [typeName](./typename-element-for-viewselectedby-format.md) specifica il .NET visualizzato dalla definizione.</span><span class="sxs-lookup"><span data-stu-id="98346-182">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="98346-183">Quando si usa questo elemento, è necessario il nome completo del tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="98346-183">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="98346-184">È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per la definizione, ma non esiste un numero massimo di elementi che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="98346-184">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="98346-185">L'elemento [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) (non mostrato) specifica un set di oggetti che possono essere visualizzati da questa definizione.</span><span class="sxs-lookup"><span data-stu-id="98346-185">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="98346-186">È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per la definizione, ma non esiste un numero massimo di elementi che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="98346-186">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="98346-187">L'elemento [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) (non mostrato) specifica una condizione che deve esistere affinché questa definizione venga utilizzata.</span><span class="sxs-lookup"><span data-stu-id="98346-187">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="98346-188">È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per la definizione, ma non esiste un numero massimo di elementi che è possibile specificare.</span><span class="sxs-lookup"><span data-stu-id="98346-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="98346-189">Per ulteriori informazioni sulla definizione delle condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="98346-189">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="98346-190">Visualizzazione di gruppi di oggetti in una visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="98346-190">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="98346-191">È possibile separare gli oggetti visualizzati dall'ampia visualizzazione in gruppi.</span><span class="sxs-lookup"><span data-stu-id="98346-191">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="98346-192">Ciò non significa che si definisce un gruppo, solo che Windows PowerShell avvia un nuovo gruppo ogni volta che viene modificato il valore di una proprietà o di uno script specifico.</span><span class="sxs-lookup"><span data-stu-id="98346-192">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="98346-193">Nell'esempio seguente viene avviato un nuovo gruppo ogni volta che viene modificato il valore della proprietà [System. ServiceProcess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) .</span><span class="sxs-lookup"><span data-stu-id="98346-193">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="98346-194">Per definire quando viene avviato un gruppo, vengono utilizzati gli elementi XML seguenti:</span><span class="sxs-lookup"><span data-stu-id="98346-194">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="98346-195">L'elemento [GroupBy](./groupby-element-for-view-format.md) definisce la proprietà o lo script che avvia il nuovo gruppo e definisce la modalità di visualizzazione del gruppo.</span><span class="sxs-lookup"><span data-stu-id="98346-195">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="98346-196">L'elemento [PropertyName](./propertyname-element-for-groupby-format.md) specifica la proprietà che avvia un nuovo gruppo ogni volta che viene modificato il valore.</span><span class="sxs-lookup"><span data-stu-id="98346-196">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="98346-197">È necessario specificare una proprietà o uno script per avviare il gruppo, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="98346-197">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="98346-198">L'elemento [scriptblock](./scriptblock-element-for-groupby-format.md) specifica lo script che avvia un nuovo gruppo ogni volta che viene modificato il valore.</span><span class="sxs-lookup"><span data-stu-id="98346-198">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="98346-199">Per avviare il gruppo, è necessario specificare uno script o una proprietà, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="98346-199">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="98346-200">L'elemento [Label](./label-element-for-groupby-format.md) definisce un'etichetta che viene visualizzata all'inizio di ogni gruppo.</span><span class="sxs-lookup"><span data-stu-id="98346-200">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="98346-201">Oltre al testo specificato da questo elemento, Windows PowerShell Visualizza il valore che ha attivato il nuovo gruppo e aggiunge una riga vuota prima e dopo l'etichetta.</span><span class="sxs-lookup"><span data-stu-id="98346-201">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="98346-202">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="98346-202">This element is optional.</span></span>

- <span data-ttu-id="98346-203">L'elemento [CustomControl](./customcontrol-element-for-groupby-format.md) definisce un controllo usato per visualizzare i dati.</span><span class="sxs-lookup"><span data-stu-id="98346-203">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="98346-204">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="98346-204">This element is optional.</span></span>

- <span data-ttu-id="98346-205">L'elemento [CustomControlName](./customcontrolname-element-for-groupby-format.md) specifica un controllo comune o di visualizzazione usato per visualizzare i dati.</span><span class="sxs-lookup"><span data-stu-id="98346-205">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="98346-206">Questo elemento è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="98346-206">This element is optional.</span></span>

<span data-ttu-id="98346-207">Per un esempio di un file di formattazione completo che definisce i gruppi, vedere [visualizzazione estesa (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="98346-207">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="98346-208">Uso di stringhe di formato</span><span class="sxs-lookup"><span data-stu-id="98346-208">Using Format Strings</span></span>

<span data-ttu-id="98346-209">È possibile aggiungere stringhe di formattazione a una visualizzazione estesa per definire ulteriormente la modalità di visualizzazione dei dati.</span><span class="sxs-lookup"><span data-stu-id="98346-209">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="98346-210">Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della proprietà `StartTime`.</span><span class="sxs-lookup"><span data-stu-id="98346-210">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="98346-211">Per specificare un modello di formato, è possibile utilizzare gli elementi XML seguenti:</span><span class="sxs-lookup"><span data-stu-id="98346-211">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="98346-212">L'elemento [WideItem](./wideitem-element-for-widecontrol-format.md) specifica i dati visualizzati dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="98346-212">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="98346-213">L'elemento [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) specifica la proprietà il cui valore viene visualizzato dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="98346-213">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="98346-214">È necessario specificare una proprietà o uno script, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="98346-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="98346-215">L'elemento [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) specifica un modello di formato che definisce la modalità di visualizzazione della proprietà o del valore dello script nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="98346-215">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="98346-216">L'elemento [scriptblock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (non mostrato) specifica lo script il cui valore viene visualizzato dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="98346-216">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="98346-217">È necessario specificare uno script o una proprietà, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="98346-217">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="98346-218">Nell'esempio seguente viene chiamato il metodo `ToString` per formattare il valore dello script.</span><span class="sxs-lookup"><span data-stu-id="98346-218">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="98346-219">Gli script possono chiamare qualsiasi metodo di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="98346-219">Scripts can call any method of an object.</span></span> <span data-ttu-id="98346-220">Pertanto, se un oggetto dispone di un metodo, ad esempio `ToString`, che dispone di parametri di formattazione, lo script può chiamare tale metodo per formattare il valore di output dello script.</span><span class="sxs-lookup"><span data-stu-id="98346-220">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="98346-221">Per chiamare il metodo `ToString` è possibile utilizzare l'elemento XML seguente:</span><span class="sxs-lookup"><span data-stu-id="98346-221">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="98346-222">L'elemento [WideItem](./wideitem-element-for-widecontrol-format.md) specifica i dati visualizzati dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="98346-222">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="98346-223">L'elemento [scriptblock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (non mostrato) specifica lo script il cui valore viene visualizzato dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="98346-223">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="98346-224">È necessario specificare uno script o una proprietà, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="98346-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="98346-225">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="98346-225">See Also</span></span>

[<span data-ttu-id="98346-226">Visualizzazione estesa (di base)</span><span class="sxs-lookup"><span data-stu-id="98346-226">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="98346-227">Visualizzazione estesa (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="98346-227">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="98346-228">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="98346-228">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
