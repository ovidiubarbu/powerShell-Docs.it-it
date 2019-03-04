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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858497"
---
# <a name="creating-a-wide-view"></a>Creazione di una visualizzazione più ampia

Una visualizzazione più ampia Visualizza un singolo valore per ogni oggetto che viene visualizzato. Il valore visualizzato può essere il valore di una proprietà dell'oggetto .NET oppure il valore di uno script. Per impostazione predefinita, non l'etichetta o intestazione per questa visualizzazione.

## <a name="a-wide-view-display"></a>Visualizzare una visualizzazione più ampia

Nell'esempio seguente viene illustrato come Windows PowerShell consente di visualizzare il [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto restituito dalle [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet quando il relativo output viene reindirizzato al [ Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet. (Per impostazione predefinita, il [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet restituisce una visualizzazione tabella.) In questo esempio, le due colonne vengono usate per visualizzare il nome del processo per ogni oggetto restituito. Il nome della proprietà dell'oggetto non viene visualizzato, solo il valore della proprietà.

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

## <a name="defining-the-wide-view"></a>Che definisce la visualizzazione più ampia

Il codice XML seguente mostra lo schema di visualizzazione più ampia per il [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto.

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

Gli elementi XML seguenti vengono usati per definire una visualizzazione più ampia:

- Il [vista](./view-element-format.md) è l'elemento padre di visualizzazione estesa. (Questo è lo stesso elemento padre per la tabella, elenco e le viste di controllo personalizzato).

- Il [nome](./name-element-for-view-format.md) elemento specifica il nome della visualizzazione. Questo elemento è obbligatorio per tutte le visualizzazioni.

- Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento definisce gli oggetti che utilizzano la vista. Questo elemento è obbligatorio.

- Il [GroupBy](./groupby-element-for-view-format.md) elemento definisce quando viene visualizzato un nuovo gruppo di oggetti. Ogni volta che cambia il valore di una proprietà specifica o uno script, viene avviato un nuovo gruppo. Questo elemento è facoltativo.

- Il [controlli](./controls-element-for-view-format.md) elementi definisce i controlli personalizzati definiti per la visualizzazione più ampia. Controlli offrono un modo per specificare ulteriormente la modalità di visualizzazione dei dati. Questo elemento è facoltativo. Una vista può definire propri controlli personalizzati, oppure è possibile usare i controlli comuni che possono essere usati da qualsiasi visualizzazione nel file di formattazione. Per altre informazioni sui controlli personalizzati, vedere [Creating Custom Controls](./creating-custom-controls.md).

- Il [WideControl](./widecontrol-element-format.md) elemento e i relativi elementi figlio definiscono gli elementi visualizzati nella vista. Nell'esempio precedente, la vista è progettata per visualizzare il [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) proprietà.

Per un esempio di un file di formattazione completato che definisce una semplice visualizzazione più ampia, vedere [visualizzazione più ampia (Basic)](./wide-view-basic.md).

## <a name="providing-definitions-for-your-wide-view"></a>Che fornisce le definizioni per la visualizzazione più ampia

Visualizzazioni ampie possono fornire una o più definizioni con gli elementi figlio del [WideControl](./widecontrol-element-format.md) elemento. In genere, una vista avrà una sola definizione. Nell'esempio seguente, la vista fornisce una singola definizione che visualizza il valore della [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) proprietà. Una visualizzazione più ampia possibile visualizzare il valore di una proprietà o il valore di uno script (non illustrato nell'esempio).

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

Gli elementi XML seguenti possono essere utilizzati per fornire le definizioni per una visualizzazione più ampia:

- Il [WideControl](./widecontrol-element-format.md) elemento e i relativi elementi figlio definiscono gli elementi visualizzati nella vista.

- Il [AutoSize](./autosize-element-for-widecontrol-format.md) elemento consente di specificare se la dimensione della colonna e il numero di colonne vengono adattate in base alla dimensione dei dati. Questo elemento è facoltativo.

- Il [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) elemento specifica il numero di colonne nella visualizzazione wide. Questo elemento è facoltativo.

- Il [WideEntries](./wideentries-element-for-widecontrol-format.md) elemento fornisce le definizioni della vista. Nella maggior parte dei casi, una vista avrà una sola definizione. Questo elemento è obbligatorio.

- Il [WideEntry](./wideentry-element-for-widecontrol-format.md) elemento fornisce una definizione della vista. Almeno un [WideEntry](./wideentry-element-for-widecontrol-format.md) è obbligatorio; tuttavia, non è definito alcun limite massimo al numero di elementi che è possibile aggiungere. Nella maggior parte dei casi, una vista avrà una sola definizione.

- Il [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento specifica gli oggetti visualizzati da una definizione specifica. Questo elemento è facoltativo ed è necessario solo quando si definiscono più [WideEntry](./wideentry-element-for-widecontrol-format.md) gli elementi che consentono di visualizzare diversi oggetti.

- Il [WideItem](./wideitem-element-for-widecontrol-format.md) elemento specifica i dati che viene visualizzati nella visualizzazione. A differenza di altri tipi di visualizzazioni, è possibile visualizzare un controllo wide un solo elemento.

- Il [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) elemento specifica la proprietà il cui valore viene visualizzato nella visualizzazione. È necessario specificare una proprietà o uno script, ma è possibile specificare entrambi.

- Il [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elemento specifica lo script il cui valore viene visualizzato nella visualizzazione. È necessario specificare uno script o una proprietà, ma è possibile specificare entrambi.

- Il [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) elemento specifica un criterio che consente di visualizzare i dati. Questo elemento è facoltativo.

Per un esempio di un file di formattazione completato che definisce una definizione di visualizzazione estesa, vedere [visualizzazione più ampia (Basic)](./wide-view-basic.md).

## <a name="defining-the-objects-that-use-the-wide-view"></a>Definire gli oggetti che usano la visualizzazione più ampia

Esistono due modi per definire quali oggetti .NET usano la visualizzazione più ampia. È possibile usare la [ViewSelectedBy](./viewselectedby-element-format.md) elemento per definire gli oggetti che possono essere visualizzati da tutte le definizioni di visualizzazione, oppure è possibile utilizzare il [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento per definire quali oggetti vengono visualizzati da un definizione della vista specifica. Nella maggior parte dei casi, una vista ha una sola definizione, in modo che gli oggetti vengono in genere definiti per il [ViewSelectedBy](./viewselectedby-element-format.md) elemento.

Nell'esempio seguente viene illustrato come definire gli oggetti che vengono visualizzati tramite la visualizzazione più ampia di [ViewSelectedBy](./viewselectedby-element-format.md) e [nomeTipo](./typename-element-for-viewselectedby-format.md) elementi. Non sono previsti limiti al numero di [TypeName](./typename-element-for-viewselectedby-format.md) gli elementi che è possibile specificare l'ordine non è significativo.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Gli elementi XML seguenti sono utilizzabile per specificare gli oggetti utilizzati per la visualizzazione più ampia:

- Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento definisce gli oggetti che vengono visualizzati per la visualizzazione più ampia.

- Il [TypeName](./typename-element-for-viewselectedby-format.md) elemento specifica di .NET che viene visualizzato nella visualizzazione. Il nome del tipo .NET completo è obbligatorio. È necessario specificare almeno un tipo o la selezione impostato per la visualizzazione, ma nessun numero massimo di elementi che possono essere specificati.

Per un esempio di un file di formattazione completato, vedere [visualizzazione più ampia (Basic)](./wide-view-basic.md).

L'esempio seguente usa il [ViewSelectedBy](./viewselectedby-element-format.md) e [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementi. Usare i set di selezione in cui è presente un set correlato di oggetti che vengono visualizzati utilizzando più viste, ad esempio quando si definisce una visualizzazione più ampia e visualizzazione di una tabella per gli oggetti stessi. Per altre informazioni su come creare un set di selezione, vedere [definizione di set di selezione](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Gli elementi XML seguenti sono utilizzabile per specificare gli oggetti utilizzati per la visualizzazione più ampia:

- Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento definisce gli oggetti che vengono visualizzati per la visualizzazione più ampia.

- Il [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento specifica un set di oggetti che possono essere visualizzati da parte della vista. È necessario specificare almeno un set di selezione o tipo per la visualizzazione, ma nessun numero massimo di elementi che possono essere specificati.

Nell'esempio seguente viene illustrato come definire gli oggetti visualizzati da una definizione di specifica della visualizzazione estesa utilizzando la [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento. Utilizzo di questo elemento, è possibile specificare il nome del tipo .NET dell'oggetto, un set di selezione di oggetti o una condizione di selezione che consente di specificare quando viene utilizzata la definizione. Per altre informazioni su come creare una selezione condizioni, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

Gli elementi XML seguenti sono utilizzabile per specificare gli oggetti usati da una definizione di specifica di visualizzazione estesa:

- Il [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento definisce gli oggetti che vengono visualizzati per la definizione.

- Il [TypeName](./typename-element-for-viewselectedby-format.md) elemento specifica di .NET che viene visualizzato per la definizione. Quando si usa questo elemento è necessario il nome del tipo .NET completo. È necessario specificare almeno un tipo, set di selezione o condizione di selezione per la definizione, ma nessun numero massimo di elementi che possono essere specificati.

- Il [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento (non mostrato) specifica un set di oggetti che possono essere visualizzati da questa definizione. È necessario specificare almeno un tipo, set di selezione o condizione di selezione per la definizione, ma nessun numero massimo di elementi che possono essere specificati.

- Il [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) elemento (non mostrato) specifica una condizione che deve essere presente per questa definizione da usare. È necessario specificare almeno un tipo, set di selezione o condizione di selezione per la definizione, ma nessun numero massimo di elementi che possono essere specificati. Per altre informazioni sulla definizione di condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>Visualizzazione di gruppi di oggetti in una visualizzazione più ampia

È possibile separare gli oggetti che vengono visualizzati per la visualizzazione più ampia in gruppi. Ciò non significa che si definisce un gruppo, solo che Windows PowerShell avvia un nuovo gruppo ogni volta che cambia il valore di una proprietà specifica o uno script. Nell'esempio seguente viene avviato un nuovo gruppo ogni volta che il valore della [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) le modifiche alle proprietà.

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

Per un esempio di un file di formattazione completato che definisce i gruppi, vedere [visualizzazione più ampia (GroupBy)](./wide-view-groupby.md).

## <a name="using-format-strings"></a>Stringhe di formato

Stringhe di formattazione possono essere aggiunti a una visualizzazione più ampia per definire ulteriormente la modalità di visualizzazione dei dati. Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della `StartTime` proprietà.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

Gli elementi XML seguenti possono essere utilizzati per specificare uno schema di formattazione:

- Il [WideItem](./wideitem-element-for-widecontrol-format.md) elemento specifica i dati che viene visualizzati nella visualizzazione.

- Il [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) elemento specifica la proprietà il cui valore viene visualizzato nella visualizzazione. È necessario specificare una proprietà o uno script, ma è possibile specificare entrambi.

- Il [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) elemento specifica un modello di formato che definisce come viene visualizzato il valore di proprietà o lo script nella visualizzazione

- Il [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elemento (non mostrato) consente di specificare lo script il cui valore viene visualizzato nella visualizzazione. È necessario specificare uno script o una proprietà, ma è possibile specificare entrambi.

Nell'esempio seguente, il `ToString` metodo viene chiamato per formattare il valore dello script. Gli script possono chiamare qualsiasi metodo di un oggetto. Pertanto, se un oggetto dispone di un metodo, ad esempio `ToString`, che può avere parametri di formattazione, lo script può chiamare tale metodo per formattare il valore di output dello script.

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

L'elemento XML seguente è utilizzabile per chiamare il `ToString` metodo:

- Il [WideItem](./wideitem-element-for-widecontrol-format.md) elemento specifica i dati che viene visualizzati nella visualizzazione.

- Il [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elemento (non mostrato) consente di specificare lo script il cui valore viene visualizzato nella visualizzazione. È necessario specificare uno script o una proprietà, ma è possibile specificare entrambi.

## <a name="see-also"></a>Vedere anche

[Visualizzazione più ampia (Basic)](./wide-view-basic.md)

[Visualizzazione più ampia (GroupBy)](./wide-view-groupby.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
