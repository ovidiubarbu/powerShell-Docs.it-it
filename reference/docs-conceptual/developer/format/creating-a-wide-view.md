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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368950"
---
# <a name="creating-a-wide-view"></a>Creazione di una visualizzazione più ampia

In una visualizzazione estesa viene visualizzato un singolo valore per ogni oggetto visualizzato. Il valore visualizzato può corrispondere al valore di una proprietà dell'oggetto .NET o al valore di uno script. Per impostazione predefinita, non è presente alcuna etichetta o intestazione per questa visualizzazione.

## <a name="a-wide-view-display"></a>Visualizzazione dell'ampia visualizzazione

Nell'esempio seguente viene illustrato come Windows PowerShell visualizzi l'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) restituito dal cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) quando l'output viene reindirizzato al cmdlet [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) . Per impostazione predefinita, il cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) restituisce una visualizzazione tabella. In questo esempio le due colonne vengono usate per visualizzare il nome del processo per ogni oggetto restituito. Il nome della proprietà dell'oggetto non viene visualizzato, ma solo il valore della proprietà.

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

## <a name="defining-the-wide-view"></a>Definizione della visualizzazione estesa

Il codice XML seguente mostra lo schema di visualizzazione estesa per l'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

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

Gli elementi XML seguenti vengono utilizzati per definire una visualizzazione estesa:

- L'elemento [View](./view-element-format.md) è l'elemento padre della visualizzazione estesa. Si tratta dello stesso elemento padre per le visualizzazioni tabella, elenco e controllo personalizzato.

- L'elemento [Name](./name-element-for-view-format.md) specifica il nome della vista. Questo elemento è obbligatorio per tutte le visualizzazioni.

- L'elemento [ViewSelectedBy](./viewselectedby-element-format.md) definisce gli oggetti che utilizzano la visualizzazione. Questo elemento è obbligatorio.

- L'elemento [GroupBy](./groupby-element-for-view-format.md) definisce quando viene visualizzato un nuovo gruppo di oggetti. Un nuovo gruppo viene avviato ogni volta che viene modificato il valore di una proprietà o di uno script specifico. Questo elemento è facoltativo.

- Gli elementi [Controls](./controls-element-for-view-format.md) definiscono i controlli personalizzati definiti dall'ampia visualizzazione. I controlli consentono di specificare in modo più dettagliato la modalità di visualizzazione dei dati. Questo elemento è facoltativo. Una vista può definire i propri controlli personalizzati oppure può utilizzare controlli comuni che possono essere utilizzati da qualsiasi visualizzazione nel file di formattazione. Per ulteriori informazioni sui controlli personalizzati, vedere [creazione di controlli personalizzati](./creating-custom-controls.md).

- L'elemento [WideControl](./widecontrol-element-format.md) e i relativi elementi figlio definiscono ciò che viene visualizzato nella visualizzazione. Nell'esempio precedente, la vista è progettata per visualizzare la proprietà [System. Diagnostics. Process. ProcessName](/dotnet/api/System.Diagnostics.Process.ProcessName) .

Per un esempio di un file di formattazione completo che definisce una visualizzazione estesa semplice, vedere [Wide View (Basic)](./wide-view-basic.md).

## <a name="providing-definitions-for-your-wide-view"></a>Fornire definizioni per la visualizzazione estesa

Le visualizzazioni Wide possono fornire una o più definizioni usando gli elementi figlio dell'elemento [WideControl](./widecontrol-element-format.md) . In genere, una vista avrà una sola definizione. Nell'esempio seguente, la vista fornisce una singola definizione che Visualizza il valore della proprietà [System. Diagnostics. Process. ProcessName](/dotnet/api/System.Diagnostics.Process.ProcessName) . Una visualizzazione estesa può visualizzare il valore di una proprietà o il valore di uno script (non illustrato nell'esempio).

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

È possibile utilizzare gli elementi XML seguenti per fornire definizioni per una visualizzazione estesa:

- L'elemento [WideControl](./widecontrol-element-format.md) e i relativi elementi figlio definiscono ciò che viene visualizzato nella visualizzazione.

- L'elemento [AutoSize](./autosize-element-for-widecontrol-format.md) specifica se le dimensioni della colonna e il numero di colonne vengono regolate in base alle dimensioni dei dati. Questo elemento è facoltativo.

- L'elemento [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) specifica il numero di colonne visualizzate nella visualizzazione estesa. Questo elemento è facoltativo.

- L'elemento [WideEntries](./wideentries-element-for-widecontrol-format.md) fornisce le definizioni della vista. Nella maggior parte dei casi, una vista avrà una sola definizione. Questo elemento è obbligatorio.

- L'elemento [WideEntry](./wideentry-element-for-widecontrol-format.md) fornisce una definizione della vista. È necessario almeno un [WideEntry](./wideentry-element-for-widecontrol-format.md) . Tuttavia, non esiste alcun limite massimo per il numero di elementi che è possibile aggiungere. Nella maggior parte dei casi, una vista avrà una sola definizione.

- L'elemento [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) specifica gli oggetti visualizzati da una definizione specifica. Questo elemento è facoltativo ed è necessario solo quando si definiscono più elementi [WideEntry](./wideentry-element-for-widecontrol-format.md) che visualizzano oggetti diversi.

- L'elemento [WideItem](./wideitem-element-for-widecontrol-format.md) specifica i dati visualizzati dalla visualizzazione. Diversamente da altri tipi di viste, un controllo Wide può visualizzare solo un elemento.

- L'elemento [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) specifica la proprietà il cui valore viene visualizzato dalla visualizzazione. È necessario specificare una proprietà o uno script, ma non è possibile specificarli entrambi.

- L'elemento [scriptblock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) specifica lo script il cui valore viene visualizzato dalla visualizzazione. È necessario specificare uno script o una proprietà, ma non è possibile specificarli entrambi.

- L'elemento [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) specifica un modello usato per visualizzare i dati. Questo elemento è facoltativo.

Per un esempio di un file di formattazione completo che definisce una definizione di visualizzazione estesa, vedere [Wide View (base)](./wide-view-basic.md).

## <a name="defining-the-objects-that-use-the-wide-view"></a>Definizione degli oggetti che utilizzano la visualizzazione estesa

Esistono due modi per definire gli oggetti .NET che utilizzano l'ampia visualizzazione. È possibile utilizzare l'elemento [ViewSelectedBy](./viewselectedby-element-format.md) per definire gli oggetti che possono essere visualizzati da tutte le definizioni della vista oppure è possibile utilizzare l'elemento [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) per definire quali oggetti vengono visualizzati da una definizione specifica della vista. Nella maggior parte dei casi, una vista ha una sola definizione, quindi gli oggetti vengono in genere definiti dall'elemento [ViewSelectedBy](./viewselectedby-element-format.md) .

Nell'esempio seguente viene illustrato come definire gli oggetti visualizzati dalla visualizzazione estesa utilizzando gli elementi [ViewSelectedBy](./viewselectedby-element-format.md) e [typeName](./typename-element-for-viewselectedby-format.md) . Non esiste alcun limite al numero di elementi [typeName](./typename-element-for-viewselectedby-format.md) che è possibile specificare e il loro ordine non è significativo.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Gli elementi XML seguenti possono essere utilizzati per specificare gli oggetti utilizzati dalla visualizzazione estesa:

- L'elemento [ViewSelectedBy](./viewselectedby-element-format.md) definisce quali oggetti vengono visualizzati dall'ampia visualizzazione.

- L'elemento [typeName](./typename-element-for-viewselectedby-format.md) specifica il .NET visualizzato dalla visualizzazione. Il nome completo del tipo .NET è obbligatorio. È necessario specificare almeno un tipo o un set di selezione per la vista, ma non esiste un numero massimo di elementi che è possibile specificare.

Per un esempio di un file di formattazione completo, vedere [visualizzazione estesa (di base)](./wide-view-basic.md).

Nell'esempio seguente vengono usati gli elementi [ViewSelectedBy](./viewselectedby-element-format.md) e [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) . Utilizzare i set di selezione in cui è presente un set correlato di oggetti visualizzati utilizzando più visualizzazioni, ad esempio quando si definiscono una visualizzazione estesa e una vista tabella per gli stessi oggetti. Per ulteriori informazioni su come creare un set di selezione, vedere [definizione](./defining-selection-sets.md)di set di selezione.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Gli elementi XML seguenti possono essere utilizzati per specificare gli oggetti utilizzati dalla visualizzazione estesa:

- L'elemento [ViewSelectedBy](./viewselectedby-element-format.md) definisce quali oggetti vengono visualizzati dall'ampia visualizzazione.

- L'elemento [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) specifica un set di oggetti che possono essere visualizzati dalla visualizzazione. È necessario specificare almeno un set di selezione o un tipo per la vista, ma non esiste un numero massimo di elementi che è possibile specificare.

Nell'esempio seguente viene illustrato come definire gli oggetti visualizzati da una definizione specifica della visualizzazione estesa utilizzando l'elemento [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) . Utilizzando questo elemento, è possibile specificare il nome del tipo .NET dell'oggetto, un set di selezione di oggetti o una condizione di selezione che specifica quando viene utilizzata la definizione. Per ulteriori informazioni sulla creazione di condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

Gli elementi XML seguenti possono essere utilizzati per specificare gli oggetti utilizzati da una definizione specifica dell'ampia visualizzazione:

- L'elemento [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) definisce quali oggetti vengono visualizzati dalla definizione.

- L'elemento [typeName](./typename-element-for-viewselectedby-format.md) specifica il .NET visualizzato dalla definizione. Quando si usa questo elemento, è necessario il nome completo del tipo .NET. È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per la definizione, ma non esiste un numero massimo di elementi che è possibile specificare.

- L'elemento [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) (non mostrato) specifica un set di oggetti che possono essere visualizzati da questa definizione. È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per la definizione, ma non esiste un numero massimo di elementi che è possibile specificare.

- L'elemento [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) (non mostrato) specifica una condizione che deve esistere affinché questa definizione venga utilizzata. È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per la definizione, ma non esiste un numero massimo di elementi che è possibile specificare. Per ulteriori informazioni sulla definizione delle condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>Visualizzazione di gruppi di oggetti in una visualizzazione estesa

È possibile separare gli oggetti visualizzati dall'ampia visualizzazione in gruppi. Ciò non significa che si definisce un gruppo, solo che Windows PowerShell avvia un nuovo gruppo ogni volta che viene modificato il valore di una proprietà o di uno script specifico. Nell'esempio seguente viene avviato un nuovo gruppo ogni volta che viene modificato il valore della proprietà [System. ServiceProcess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) .

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Per definire quando viene avviato un gruppo, vengono utilizzati gli elementi XML seguenti:

- L'elemento [GroupBy](./groupby-element-for-view-format.md) definisce la proprietà o lo script che avvia il nuovo gruppo e definisce la modalità di visualizzazione del gruppo.

- L'elemento [PropertyName](./propertyname-element-for-groupby-format.md) specifica la proprietà che avvia un nuovo gruppo ogni volta che viene modificato il valore. È necessario specificare una proprietà o uno script per avviare il gruppo, ma non è possibile specificarli entrambi.

- L'elemento [scriptblock](./scriptblock-element-for-groupby-format.md) specifica lo script che avvia un nuovo gruppo ogni volta che viene modificato il valore. Per avviare il gruppo, è necessario specificare uno script o una proprietà, ma non è possibile specificarli entrambi.

- L'elemento [Label](./label-element-for-groupby-format.md) definisce un'etichetta che viene visualizzata all'inizio di ogni gruppo. Oltre al testo specificato da questo elemento, Windows PowerShell Visualizza il valore che ha attivato il nuovo gruppo e aggiunge una riga vuota prima e dopo l'etichetta. Questo elemento è facoltativo.

- L'elemento [CustomControl](./customcontrol-element-for-groupby-format.md) definisce un controllo usato per visualizzare i dati. Questo elemento è facoltativo.

- L'elemento [CustomControlName](./customcontrolname-element-for-groupby-format.md) specifica un controllo comune o di visualizzazione usato per visualizzare i dati. Questo elemento è facoltativo.

Per un esempio di un file di formattazione completo che definisce i gruppi, vedere [visualizzazione estesa (GroupBy)](./wide-view-groupby.md).

## <a name="using-format-strings"></a>Uso di stringhe di formato

È possibile aggiungere stringhe di formattazione a una visualizzazione estesa per definire ulteriormente la modalità di visualizzazione dei dati. Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della proprietà `StartTime`.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

Per specificare un modello di formato, è possibile utilizzare gli elementi XML seguenti:

- L'elemento [WideItem](./wideitem-element-for-widecontrol-format.md) specifica i dati visualizzati dalla visualizzazione.

- L'elemento [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) specifica la proprietà il cui valore viene visualizzato dalla visualizzazione. È necessario specificare una proprietà o uno script, ma non è possibile specificarli entrambi.

- L'elemento [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) specifica un modello di formato che definisce la modalità di visualizzazione della proprietà o del valore dello script nella visualizzazione.

- L'elemento [scriptblock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (non mostrato) specifica lo script il cui valore viene visualizzato dalla visualizzazione. È necessario specificare uno script o una proprietà, ma non è possibile specificarli entrambi.

Nell'esempio seguente viene chiamato il metodo `ToString` per formattare il valore dello script. Gli script possono chiamare qualsiasi metodo di un oggetto. Pertanto, se un oggetto dispone di un metodo, ad esempio `ToString`, con parametri di formattazione, lo script può chiamare tale metodo per formattare il valore di output dello script.

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

È possibile utilizzare l'elemento XML seguente per chiamare il metodo `ToString`:

- L'elemento [WideItem](./wideitem-element-for-widecontrol-format.md) specifica i dati visualizzati dalla visualizzazione.

- L'elemento [scriptblock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (non mostrato) specifica lo script il cui valore viene visualizzato dalla visualizzazione. È necessario specificare uno script o una proprietà, ma non è possibile specificarli entrambi.

## <a name="see-also"></a>Vedere anche

[Visualizzazione estesa (di base)](./wide-view-basic.md)

[Visualizzazione estesa (GroupBy)](./wide-view-groupby.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
