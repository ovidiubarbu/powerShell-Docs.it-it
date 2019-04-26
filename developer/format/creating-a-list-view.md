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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066856"
---
# <a name="creating-a-list-view"></a>Creazione di una visualizzazione elenco

Una visualizzazione elenco Visualizza i dati in una singola colonna (in ordine sequenziale). I dati visualizzati nell'elenco possono essere il valore della proprietà .NET o il valore di uno script.

## <a name="a-list-view-display"></a>Una visualizzazione elenco

L'output seguente viene illustrato come Windows PowerShell consente di visualizzare le proprietà di [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) gli oggetti restituiti dai [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet. In questo esempio, sono stati restituiti tre oggetti, con un oggetto separato dal precedente oggetto da una riga vuota.

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

## <a name="defining-the-list-view"></a>Che definisce la vista elenco

Il codice XML seguente viene illustrato lo schema della vista elenco per visualizzare diverse proprietà del [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) oggetto. È necessario specificare ogni proprietà che si desidera visualizzare nella visualizzazione elenco.

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

Gli elementi XML seguenti vengono usati per definire una visualizzazione elenco:

- Il [vista](./view-element-format.md) è l'elemento padre della visualizzazione elenco. (Questo è lo stesso elemento padre per la tabella, le viste di controllo wide e personalizzati).

- Il [nome](./name-element-for-view-format.md) elemento specifica il nome della visualizzazione. Questo elemento è obbligatorio per tutte le visualizzazioni.

- Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento definisce gli oggetti che utilizzano la vista. Questo elemento è obbligatorio.

- Il [GroupBy](./groupby-element-for-view-format.md) elemento definisce quando viene visualizzato un nuovo gruppo di oggetti. Ogni volta che cambia il valore di una proprietà specifica o uno script, viene avviato un nuovo gruppo. Questo elemento è facoltativo.

- Il [controlli](./controls-element-for-view-format.md) elemento definisce i controlli personalizzati che sono definiti dalla vista elenco. Controlli offrono un modo per specificare ulteriormente la modalità di visualizzazione dei dati. Questo elemento è facoltativo. Una vista può definire propri controlli personalizzati, oppure è possibile usare i controlli comuni che possono essere usati da qualsiasi visualizzazione nel file di formattazione. Per altre informazioni sui controlli personalizzati, vedere [Creating Custom Controls](./creating-custom-controls.md).

- Il [dell'oggetto ListControl](./listcontrol-element-format.md) elemento definisce gli elementi visualizzati nella visualizzazione e come viene formattato. Analogamente a tutte le altre visualizzazioni, una visualizzazione elenco può visualizzare i valori delle proprietà degli oggetti o valori generati dallo script.

Per un esempio di un file di formattazione completato che definisce una visualizzazione elenco semplice, vedere [visualizzazione elenco (Basic)](./list-view-basic.md).

## <a name="providing-definitions-for-your-list-view"></a>Che fornisce le definizioni per la visualizzazione elenco

Visualizzazioni elenco possono fornire una o più definizioni con gli elementi figlio del [dell'oggetto ListControl](./listcontrol-element-format.md) elemento. In genere, una vista avrà una sola definizione. Nell'esempio seguente, la vista fornisce una singola definizione che consente di visualizzare diverse proprietà del [Diagnostics? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) oggetto. Una visualizzazione elenco è possibile visualizzare il valore di una proprietà o il valore di uno script (non illustrato nell'esempio).

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

Gli elementi XML seguenti sono utilizzabile per fornire le definizioni per una visualizzazione elenco:

- Il [dell'oggetto ListControl](./listcontrol-element-format.md) elemento e i relativi elementi figlio definiscono gli elementi visualizzati nella vista.

- Il [ListEntries](./listentries-element-for-listcontrol-format.md) elemento fornisce le definizioni della vista. Nella maggior parte dei casi, una vista avrà una sola definizione. Questo elemento è obbligatorio.

- Il [ListEntry](./listentry-element-for-listcontrol-format.md) elemento fornisce una definizione della vista. Almeno un [ListEntry](./listentry-element-for-listcontrol-format.md) è obbligatorio; tuttavia, non è definito alcun limite massimo al numero di elementi che è possibile aggiungere. Nella maggior parte dei casi, una vista avrà una sola definizione.

- Il [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento specifica gli oggetti visualizzati da una definizione specifica. Questo elemento è facoltativo ed è necessario solo quando si definiscono più [ListEntry](./listentry-element-for-listcontrol-format.md) gli elementi che consentono di visualizzare diversi oggetti.

- Il [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) elemento specifica le proprietà e gli script i cui valori vengono visualizzati nelle righe della visualizzazione elenco.

- Il [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) elemento specifica una proprietà o script il cui valore viene visualizzato in una riga della visualizzazione elenco. Una visualizzazione elenco è necessario specificare almeno una proprietà o dello script. Non è definito alcun limite massimo al numero di righe che possono essere specificati.

- Il [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento specifica la proprietà il cui valore viene visualizzato nella riga. È necessario specificare una proprietà o uno script, ma è possibile specificare entrambi.

- Il [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento specifica lo script il cui valore viene visualizzato nella riga. È necessario specificare uno script o una proprietà, ma è possibile specificare entrambi.

- Il [etichetta](./label-element-for-listitem-for-listcontrol-format.md) elemento specifica l'etichetta che viene visualizzato a sinistra del valore della proprietà o script della riga. Questo elemento è facoltativo. Se non viene specificata un'etichetta, viene visualizzato il nome della proprietà o lo script. Per un esempio completo, vedere [visualizzazione elenco (etichette punteggio)](./list-view-labels.md).

- Il [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) elemento specifica una condizione che deve essere presente per la riga da visualizzare. Per altre informazioni sull'aggiunta di condizioni per la visualizzazione elenco, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md). Questo elemento è facoltativo.

- Il [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) elemento specifica un criterio che consente di visualizzare il valore della proprietà o dello script. Questo elemento è facoltativo.

Per un esempio di un file di formattazione completato che definisce una visualizzazione elenco semplice, vedere [visualizzazione elenco (Basic)](./list-view-basic.md).

## <a name="defining-the-objects-that-use-the-list-view"></a>Definire gli oggetti che utilizzano la vista elenco

Esistono due modi per definire quali oggetti .NET usano la visualizzazione elenco. È possibile usare la [ViewSelectedBy](./viewselectedby-element-format.md) elemento per definire gli oggetti che possono essere visualizzati da tutte le definizioni di visualizzazione, oppure è possibile utilizzare il [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento per definire quali oggetti vengono visualizzati da un definizione della vista specifica. Nella maggior parte dei casi, una vista ha una sola definizione, in modo che gli oggetti vengono in genere definiti per il [ViewSelectedBy](./viewselectedby-element-format.md) elemento.

Nell'esempio seguente viene illustrato come definire gli oggetti che vengono visualizzati per la visualizzazione elenco utilizzando il [ViewSelectedBy](./viewselectedby-element-format.md) e [nomeTipo](./typename-element-for-viewselectedby-format.md) elementi. Non sono previsti limiti al numero di [TypeName](./typename-element-for-viewselectedby-format.md) gli elementi che è possibile specificare l'ordine non è significativo.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Gli elementi XML seguenti sono utilizzabile per specificare gli oggetti utilizzati dalla visualizzazione elenco:

- Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento definisce gli oggetti che vengono visualizzati nella visualizzazione elenco.

- Il [TypeName](./typename-element-for-viewselectedby-format.md) elemento specifica l'oggetto .NET che viene visualizzato nella visualizzazione. Il nome del tipo .NET completo è obbligatorio. È necessario specificare almeno un tipo o la selezione impostato per la visualizzazione, ma nessun numero massimo di elementi che possono essere specificati.

Per un esempio di un file di formattazione completato, vedere [visualizzazione elenco (Basic)](./list-view-basic.md).

L'esempio seguente usa il [ViewSelectedBy](./viewselectedby-element-format.md) e [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementi. Usare i set di selezione in cui è presente un set correlato di oggetti che vengono visualizzati utilizzando più viste, ad esempio quando si definisce una visualizzazione elenco e visualizzazione di una tabella per gli oggetti stessi. Per altre informazioni su come creare un set di selezione, vedere [definizione di set di selezione](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Gli elementi XML seguenti sono utilizzabile per specificare gli oggetti utilizzati dalla visualizzazione elenco:

- Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento definisce gli oggetti che vengono visualizzati nella visualizzazione elenco.

- Il [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento specifica un set di oggetti che possono essere visualizzati da parte della vista. È necessario specificare almeno un set di selezione o tipo per la visualizzazione, ma nessun numero massimo di elementi che possono essere specificati.

Nell'esempio seguente viene illustrato come definire gli oggetti visualizzati da una definizione di specifica della visualizzazione elenco mediante il [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento. Utilizzo di questo elemento, è possibile specificare il nome del tipo .NET dell'oggetto, un set di selezione di oggetti o una condizione di selezione che consente di specificare quando viene utilizzata la definizione. Per altre informazioni su come creare una selezione condizioni, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

Gli elementi XML seguenti possono essere utilizzati per specificare gli oggetti usati da una definizione di specifica della visualizzazione elenco:

- Il [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento definisce gli oggetti che vengono visualizzati per la definizione.

- Il [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) elemento specifica l'oggetto .NET che viene visualizzato per la definizione. Quando si usa questo elemento, è necessario il nome del tipo .NET completo. È necessario specificare almeno un tipo, set di selezione o condizione di selezione per la definizione, ma nessun numero massimo di elementi che possono essere specificati.

- Il [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) elemento (non mostrato) specifica un set di oggetti che possono essere visualizzati da questa definizione. È necessario specificare almeno un tipo, set di selezione o condizione di selezione per la definizione, ma nessun numero massimo di elementi che possono essere specificati.

- Il [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) elemento (non mostrato) specifica una condizione che deve essere presente per questa definizione da usare. È necessario specificare almeno un tipo, set di selezione o condizione di selezione per la definizione, ma nessun numero massimo di elementi che possono essere specificati. Per altre informazioni sulla definizione di condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-list-view"></a>Visualizzazione di gruppi di oggetti in una visualizzazione elenco

È possibile separare gli oggetti che vengono visualizzati nella visualizzazione elenco in gruppi. Ciò non significa che si definisce un gruppo, solo che Windows PowerShell avvia un nuovo gruppo ogni volta che cambia il valore di una proprietà specifica o uno script. Nell'esempio seguente viene avviato un nuovo gruppo ogni volta che il valore della [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) le modifiche alle proprietà.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Gli elementi XML seguenti vengono usati per definire quando viene avviato un gruppo:

- Il [GroupBy](./groupby-element-for-view-format.md) elemento definisce le proprietà o uno script che avvia il nuovo gruppo e definisce come viene visualizzato il gruppo.

- Il [PropertyName](./propertyname-element-for-groupby-format.md) elemento specifica la proprietà che inizia un nuovo gruppo ogni volta che cambia il relativo valore. È necessario specificare una proprietà o script per avviare il gruppo, ma è possibile specificare entrambi.

- Il [ScriptBlock](./scriptblock-element-for-groupby-format.md) elemento specifica lo script che avvia un nuovo gruppo ogni volta che cambia il relativo valore. È necessario specificare uno script o una proprietà per avviare il gruppo, ma è possibile specificare entrambi.

- Il [etichetta](./label-element-for-groupby-format.md) elemento definisce un'etichetta che viene visualizzata all'inizio di ogni gruppo. Oltre al testo specificato da questo elemento, Windows PowerShell Visualizza il valore che ha attivato il nuovo gruppo e aggiunge una riga vuota prima e dopo l'etichetta. Questo elemento è facoltativo.

- Il [CustomControl](./customcontrol-element-for-groupby-format.md) elemento definisce un controllo che consente di visualizzare i dati. Questo elemento è facoltativo.

- Il [CustomControlName](./customcontrolname-element-for-groupby-format.md) elemento specifica un comune o controllo che consente di visualizzare i dati di visualizzazione. Questo elemento è facoltativo.

Per un esempio di un file di formattazione completato che definisce i gruppi, vedere [visualizzazione elenco (GroupBy)](./list-view-groupby.md).

## <a name="using-format-strings"></a>Stringhe di formato

Stringhe di formattazione possono essere aggiunti a una visualizzazione per definire ulteriormente la modalità di visualizzazione dei dati. Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della `StartTime` proprietà.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

Gli elementi XML seguenti possono essere utilizzati per specificare uno schema di formattazione:

- Il [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento specifica i dati che viene visualizzati nella visualizzazione.

- Il [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento specifica la proprietà il cui valore viene visualizzato nella visualizzazione. È necessario specificare una proprietà o uno script, ma è possibile specificare entrambi.

- Il [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) elemento specifica un modello di formato che definisce come viene visualizzato il valore di proprietà o lo script nella visualizzazione.

- Il [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento (non mostrato) consente di specificare lo script il cui valore viene visualizzato nella visualizzazione. È necessario specificare uno script o una proprietà, ma è possibile specificare entrambi.

Nell'esempio seguente, il `ToString` metodo viene chiamato per formattare il valore dello script. Gli script possono chiamare qualsiasi metodo di un oggetto. Pertanto, se un oggetto dispone di un metodo, ad esempio `ToString`, che può avere parametri di formattazione, lo script può chiamare tale metodo per formattare il valore di output dello script.

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

L'elemento XML seguente è utilizzabile per chiamare il `ToString` metodo:

- Il [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento specifica i dati che viene visualizzati nella visualizzazione.

- Il [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento (non mostrato) consente di specificare lo script il cui valore viene visualizzato nella visualizzazione. È necessario specificare uno script o una proprietà, ma è possibile specificare entrambi.

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md)
