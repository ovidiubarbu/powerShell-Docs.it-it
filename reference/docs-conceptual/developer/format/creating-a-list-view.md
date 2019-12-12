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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368980"
---
# <a name="creating-a-list-view"></a>Creazione di una visualizzazione elenco

In una visualizzazione elenco i dati vengono visualizzati in una singola colonna (in ordine sequenziale). I dati visualizzati nell'elenco possono corrispondere al valore di una proprietà .NET o al valore di uno script.

## <a name="a-list-view-display"></a>Visualizzazione elenco

L'output seguente mostra in che modo Windows PowerShell Visualizza le proprietà di [System. ServiceProcess. ServiceController? DisplayProperty = oggetti FullName](/dotnet/api/System.ServiceProcess.ServiceController) restituiti dal cmdlet [Get-Service](/powershell/module/microsoft.powershell.management/get-service) . In questo esempio sono stati restituiti tre oggetti, con ogni oggetto separato dall'oggetto precedente da una riga vuota.

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

## <a name="defining-the-list-view"></a>Definizione della visualizzazione elenco

Il codice XML seguente mostra lo schema di visualizzazione elenco per visualizzare diverse proprietà di [System. ServiceProcess. ServiceController? Oggetto DisplayProperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) . È necessario specificare ogni proprietà che si desidera visualizzare nella visualizzazione elenco.

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

Per definire una visualizzazione elenco vengono utilizzati gli elementi XML seguenti:

- L'elemento [View](./view-element-format.md) è l'elemento padre della visualizzazione elenco. Si tratta dello stesso elemento padre per la tabella, la larghezza e le visualizzazioni di controlli personalizzati.

- L'elemento [Name](./name-element-for-view-format.md) specifica il nome della vista. Questo elemento è obbligatorio per tutte le visualizzazioni.

- L'elemento [ViewSelectedBy](./viewselectedby-element-format.md) definisce gli oggetti che utilizzano la visualizzazione. Questo elemento è obbligatorio.

- L'elemento [GroupBy](./groupby-element-for-view-format.md) definisce quando viene visualizzato un nuovo gruppo di oggetti. Un nuovo gruppo viene avviato ogni volta che viene modificato il valore di una proprietà o di uno script specifico. Questo elemento è facoltativo.

- L'elemento [Controls](./controls-element-for-view-format.md) definisce i controlli personalizzati definiti dalla visualizzazione elenco. I controlli consentono di specificare in modo più dettagliato la modalità di visualizzazione dei dati. Questo elemento è facoltativo. Una vista può definire i propri controlli personalizzati oppure può utilizzare controlli comuni che possono essere utilizzati da qualsiasi visualizzazione nel file di formattazione. Per ulteriori informazioni sui controlli personalizzati, vedere [creazione di controlli personalizzati](./creating-custom-controls.md).

- L'elemento [ListControl](./listcontrol-element-format.md) definisce gli elementi visualizzati nella visualizzazione e la relativa formattazione. Analogamente a tutte le altre viste, una visualizzazione elenco può visualizzare i valori delle proprietà dell'oggetto o i valori generati dallo script.

Per un esempio di un file di formattazione completo che definisce una semplice visualizzazione elenco, vedere [visualizzazione elenco (di base)](./list-view-basic.md).

## <a name="providing-definitions-for-your-list-view"></a>Fornire definizioni per la visualizzazione elenco

Le visualizzazioni elenco possono fornire una o più definizioni usando gli elementi figlio dell'elemento [ListControl](./listcontrol-element-format.md) . In genere, una vista avrà una sola definizione. Nell'esempio seguente, la vista fornisce una singola definizione che visualizza diverse proprietà di [System. Diagnostics. Process? Oggetto DisplayProperty = FullName](/dotnet/api/System.Diagnostics.Process) . In una visualizzazione elenco è possibile visualizzare il valore di una proprietà o il valore di uno script (non illustrato nell'esempio).

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

È possibile utilizzare gli elementi XML seguenti per fornire definizioni per una visualizzazione elenco:

- L'elemento [ListControl](./listcontrol-element-format.md) e i relativi elementi figlio definiscono ciò che viene visualizzato nella visualizzazione.

- L'elemento [ListEntries](./listentries-element-for-listcontrol-format.md) fornisce le definizioni della vista. Nella maggior parte dei casi, una vista avrà una sola definizione. Questo elemento è obbligatorio.

- L'elemento [ListEntry](./listentry-element-for-listcontrol-format.md) fornisce una definizione della vista. È necessario almeno un [ListEntry](./listentry-element-for-listcontrol-format.md) . Tuttavia, non esiste alcun limite massimo per il numero di elementi che è possibile aggiungere. Nella maggior parte dei casi, una vista avrà una sola definizione.

- L'elemento [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) specifica gli oggetti visualizzati da una definizione specifica. Questo elemento è facoltativo ed è necessario solo quando si definiscono più elementi [ListEntry](./listentry-element-for-listcontrol-format.md) che visualizzano oggetti diversi.

- L'elemento [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) specifica le proprietà e gli script i cui valori vengono visualizzati nelle righe della visualizzazione elenco.

- L'elemento [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) specifica una proprietà o uno script il cui valore viene visualizzato in una riga della visualizzazione elenco. Una visualizzazione elenco deve specificare almeno una proprietà o uno script. Non esiste un limite massimo per il numero di righe che è possibile specificare.

- L'elemento [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) specifica la proprietà il cui valore viene visualizzato nella riga. È necessario specificare una proprietà o uno script, ma non è possibile specificarli entrambi.

- L'elemento [scriptblock](./scriptblock-element-for-listitem-for-listcontrol-format.md) specifica lo script il cui valore viene visualizzato nella riga. È necessario specificare uno script o una proprietà, ma non è possibile specificarli entrambi.

- L'elemento [Label](./label-element-for-listitem-for-listcontrol-format.md) specifica l'etichetta visualizzata a sinistra della proprietà o del valore dello script nella riga. Questo elemento è facoltativo. Se non si specifica un'etichetta, viene visualizzato il nome della proprietà o dello script. Per un esempio completo, vedere [visualizzazione elenco (etichette)](./list-view-labels.md).

- L'elemento [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) specifica una condizione che deve esistere per la visualizzazione della riga. Per ulteriori informazioni sull'aggiunta di condizioni alla visualizzazione elenco, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md). Questo elemento è facoltativo.

- L'elemento [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) specifica un modello utilizzato per visualizzare il valore della proprietà o dello script. Questo elemento è facoltativo.

Per un esempio di un file di formattazione completo che definisce una semplice visualizzazione elenco, vedere [visualizzazione elenco (di base)](./list-view-basic.md).

## <a name="defining-the-objects-that-use-the-list-view"></a>Definizione degli oggetti che utilizzano la visualizzazione elenco

Esistono due modi per definire gli oggetti .NET che utilizzano la visualizzazione elenco. È possibile utilizzare l'elemento [ViewSelectedBy](./viewselectedby-element-format.md) per definire gli oggetti che possono essere visualizzati da tutte le definizioni della vista oppure è possibile utilizzare l'elemento [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) per definire quali oggetti vengono visualizzati da una definizione specifica della vista. Nella maggior parte dei casi, una vista ha una sola definizione, quindi gli oggetti vengono in genere definiti dall'elemento [ViewSelectedBy](./viewselectedby-element-format.md) .

Nell'esempio seguente viene illustrato come definire gli oggetti visualizzati dalla visualizzazione elenco usando gli elementi [ViewSelectedBy](./viewselectedby-element-format.md) e [typeName](./typename-element-for-viewselectedby-format.md) . Non esiste alcun limite al numero di elementi [typeName](./typename-element-for-viewselectedby-format.md) che è possibile specificare e il loro ordine non è significativo.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Per specificare gli oggetti utilizzati dalla visualizzazione elenco, è possibile utilizzare gli elementi XML seguenti:

- L'elemento [ViewSelectedBy](./viewselectedby-element-format.md) definisce quali oggetti vengono visualizzati dalla visualizzazione elenco.

- L'elemento [typeName](./typename-element-for-viewselectedby-format.md) specifica l'oggetto .NET visualizzato dalla visualizzazione. Il nome completo del tipo .NET è obbligatorio. È necessario specificare almeno un tipo o un set di selezione per la vista, ma non esiste un numero massimo di elementi che è possibile specificare.

Per un esempio di un file di formattazione completo, vedere [visualizzazione elenco (di base)](./list-view-basic.md).

Nell'esempio seguente vengono usati gli elementi [ViewSelectedBy](./viewselectedby-element-format.md) e [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) . Utilizzare i set di selezione in cui è presente un set correlato di oggetti visualizzati utilizzando più visualizzazioni, ad esempio quando si definiscono una visualizzazione elenco e una vista tabella per gli stessi oggetti. Per ulteriori informazioni su come creare un set di selezione, vedere [definizione](./defining-selection-sets.md)di set di selezione.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Per specificare gli oggetti utilizzati dalla visualizzazione elenco, è possibile utilizzare gli elementi XML seguenti:

- L'elemento [ViewSelectedBy](./viewselectedby-element-format.md) definisce quali oggetti vengono visualizzati dalla visualizzazione elenco.

- L'elemento [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) specifica un set di oggetti che possono essere visualizzati dalla visualizzazione. È necessario specificare almeno un set di selezione o un tipo per la vista, ma non esiste un numero massimo di elementi che è possibile specificare.

Nell'esempio seguente viene illustrato come definire gli oggetti visualizzati da una definizione specifica della visualizzazione elenco utilizzando l'elemento [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) . Utilizzando questo elemento, è possibile specificare il nome del tipo .NET dell'oggetto, un set di selezione di oggetti o una condizione di selezione che specifica quando viene utilizzata la definizione. Per ulteriori informazioni sulla creazione di condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

Gli elementi XML seguenti possono essere utilizzati per specificare gli oggetti utilizzati da una definizione specifica della visualizzazione elenco:

- L'elemento [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) definisce quali oggetti vengono visualizzati dalla definizione.

- L'elemento [typeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) specifica l'oggetto .NET visualizzato dalla definizione. Quando si usa questo elemento, il nome completo del tipo .NET è obbligatorio. È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per la definizione, ma non esiste un numero massimo di elementi che è possibile specificare.

- L'elemento [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) (non mostrato) specifica un set di oggetti che possono essere visualizzati da questa definizione. È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per la definizione, ma non esiste un numero massimo di elementi che è possibile specificare.

- L'elemento [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (non mostrato) specifica una condizione che deve esistere affinché questa definizione venga utilizzata. È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per la definizione, ma non esiste un numero massimo di elementi che è possibile specificare. Per ulteriori informazioni sulla definizione delle condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-list-view"></a>Visualizzazione di gruppi di oggetti in una visualizzazione elenco

È possibile separare gli oggetti visualizzati dalla visualizzazione elenco in gruppi. Ciò non significa che si definisce un gruppo, solo che Windows PowerShell avvia un nuovo gruppo ogni volta che viene modificato il valore di una proprietà o di uno script specifico. Nell'esempio seguente viene avviato un nuovo gruppo ogni volta che viene modificato il valore della proprietà [System. ServiceProcess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) .

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

Per un esempio di un file di formattazione completo che definisce i gruppi, vedere [visualizzazione elenco (GroupBy)](./list-view-groupby.md).

## <a name="using-format-strings"></a>Uso di stringhe di formato

È possibile aggiungere stringhe di formattazione a una visualizzazione per definire ulteriormente la modalità di visualizzazione dei dati. Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della proprietà `StartTime`.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

Per specificare un modello di formato, è possibile utilizzare gli elementi XML seguenti:

- L'elemento [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) specifica i dati visualizzati dalla visualizzazione.

- L'elemento [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) specifica la proprietà il cui valore viene visualizzato dalla visualizzazione. È necessario specificare una proprietà o uno script, ma non è possibile specificarli entrambi.

- L'elemento [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script nella visualizzazione.

- L'elemento [scriptblock](./scriptblock-element-for-listitem-for-listcontrol-format.md) (non mostrato) specifica lo script il cui valore viene visualizzato dalla visualizzazione. È necessario specificare uno script o una proprietà, ma non è possibile specificarli entrambi.

Nell'esempio seguente viene chiamato il metodo `ToString` per formattare il valore dello script. Gli script possono chiamare qualsiasi metodo di un oggetto. Pertanto, se un oggetto dispone di un metodo, ad esempio `ToString`, che dispone di parametri di formattazione, lo script può chiamare tale metodo per formattare il valore di output dello script.

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

Per chiamare il metodo `ToString` è possibile utilizzare l'elemento XML seguente:

- L'elemento [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) specifica i dati visualizzati dalla visualizzazione.

- L'elemento [scriptblock](./scriptblock-element-for-listitem-for-listcontrol-format.md) (non mostrato) specifica lo script il cui valore viene visualizzato dalla visualizzazione. È necessario specificare uno script o una proprietà, ma non è possibile specificarli entrambi.

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md)
