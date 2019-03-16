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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057366"
---
# <a name="creating-a-table-view"></a>Creazione di una visualizzazione tabella

Una visualizzazione tabella visualizza i dati in una o più colonne. Ogni riga della tabella rappresenta un oggetto .NET e ogni colonna della tabella rappresenta una proprietà dell'oggetto o un valore di script. È possibile definire una visualizzazione tabella che visualizza tutte le proprietà di un oggetto o un subset delle proprietà di un oggetto.

## <a name="a-table-view-display"></a>Una visualizzazione di tabella

Nell'esempio seguente viene illustrato come Windows PowerShell consente di visualizzare il [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) l'oggetto restituito dalle [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet. Per questo oggetto, Windows PowerShell è stato definito una vista tabella contenente le `Status` proprietà, il `Name` proprietà (questa proprietà è una proprietà alias per il `ServiceName` proprietà) e il `DisplayName` proprietà. Ogni riga della tabella rappresenta un oggetto restituito dal cmdlet.

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a>Che definisce la vista tabella

Il codice XML seguente viene illustrato lo schema della vista tabella per la visualizzazione di [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) oggetto. È necessario specificare ogni proprietà che si desidera visualizzare nella visualizzazione della tabella.

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

Gli elementi XML seguenti vengono usati per definire una visualizzazione elenco:

- Il [vista](./view-element-format.md) è l'elemento padre della visualizzazione della tabella. (Questo è lo stesso elemento padre per l'elenco, le viste di controllo wide e personalizzati).

- Il [nome](./name-element-for-view-format.md) elemento specifica il nome della visualizzazione. Questo elemento è obbligatorio per tutte le visualizzazioni.

- Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento definisce gli oggetti che utilizzano la vista. Questo elemento è obbligatorio.

- Il [GroupBy](./groupby-element-for-view-format.md) elemento (non illustrato in questo esempio) consente di definire quando viene visualizzato un nuovo gruppo di oggetti. Ogni volta che cambia il valore di una proprietà specifica o uno script, viene avviato un nuovo gruppo. Questo elemento è facoltativo.

- Il [controlli](./controls-element-for-view-format.md) elemento (non illustrato in questo esempio) consente di definire i controlli personalizzati che sono definiti dalla visualizzazione della tabella. Controlli offrono un modo per specificare ulteriormente la modalità di visualizzazione dei dati. Questo elemento è facoltativo. Una vista può definire propri controlli personalizzati, oppure è possibile usare i controlli comuni che possono essere usati da qualsiasi visualizzazione nel file di formattazione. Per altre informazioni sui controlli personalizzati, vedere [Creating Custom Controls](./creating-custom-controls.md).

- Il [HideTableHeaders](./hidetableheaders-element-format.md) elemento (non riportato in questo esempio) consente di specificare che la tabella non visualizzerà le etichette nella parte superiore della tabella. Questo elemento è facoltativo.

- Il [Table](./tablecontrol-element-format.md) elemento che definisce le informazioni di intestazione e di riga della tabella. Analogamente a tutte le altre visualizzazioni, una visualizzazione tabella può visualizzare i valori delle proprietà degli oggetti o valori generati da script.

## <a name="defining-column-headers"></a>La definizione di intestazioni di colonna

1. Il [TableHeaders](./tableheaders-element-format.md) elemento e i relativi elementi figlio definiscono che cosa viene visualizzata nella parte superiore della tabella.

2. Il [TableColumnHeader](./tablecolumnheader-element-format.md) elemento definisce gli elementi visualizzati nella parte superiore di una colonna della tabella. Questi elementi vengono specificati nell'ordine in cui le intestazioni visualizzate.

   Non sono previsti limiti per il numero di questi elemento che è possibile usare, ma il numero di [TableColumnHeader](./tablecolumnheader-element-format.md) devono essere uguale il numero di elementi nella visualizzazione tabella [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elementi usati.

3. Il [etichetta](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento specifica il testo visualizzato. Questo elemento è facoltativo.

4. Il [larghezza](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento specifica la larghezza (in caratteri) della colonna. Questo elemento è facoltativo.

5. Il [allineamento](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento specifica come viene visualizzata l'etichetta. L'etichetta può essere allineato a sinistra, a destra, o al centro. Questo elemento è facoltativo.

## <a name="defining-the-table-rows"></a>Definire le righe della tabella

Le visualizzazioni di tabelle possono fornire una o più definizioni che specificano quali dati vengono visualizzati nelle righe della tabella usando gli elementi figlio del [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) elemento. Si noti che è possibile specificare più definizioni per le righe della tabella, ma le intestazioni per le righe rimane lo stesso, indipendentemente da quale definizione di riga viene usata. In genere, una tabella avrà una sola definizione.

Nell'esempio seguente, la vista fornisce una singola definizione che consente di visualizzare i valori delle diverse proprietà del [Diagnostics? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) oggetto. Visualizzazione di una tabella è possibile visualizzare il valore di una proprietà o il valore di uno script (non illustrato nell'esempio) nelle righe Dell.

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

Gli elementi XML seguenti sono utilizzabile per fornire le definizioni per una riga:

- Il [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) elemento e i relativi elementi figlio definiscono che cosa viene visualizzata nelle righe della tabella.

- Il [TableRowEntry](./listentry-element-for-listcontrol-format.md) elemento fornisce una definizione della riga. Almeno un [TableRowEntry](./listentry-element-for-listcontrol-format.md) è obbligatorio; tuttavia, non è definito alcun limite massimo al numero di elementi che è possibile aggiungere. Nella maggior parte dei casi, una vista avrà una sola definizione.

- Il [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento specifica gli oggetti visualizzati da una definizione specifica. Questo elemento è facoltativo ed è necessario solo quando si definiscono più [TableRowEntry](./listentry-element-for-listcontrol-format.md) gli elementi che consentono di visualizzare diversi oggetti.

- Il [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) elemento specifica che il testo che supera la larghezza della colonna viene visualizzato nella riga successiva. Per impostazione predefinita, il testo di dimensioni superiori alla larghezza della colonna viene troncato.

- Il [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) elemento definisce le proprietà o gli script i cui valori vengono visualizzati nella riga.

- Il [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento definisce le proprietà il cui valore viene visualizzato nella colonna della riga di script. Oggetto [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento è obbligatorio per ogni colonna della riga. La prima voce viene visualizzata nella prima colonna, la seconda voce nella seconda colonna e così via.

- Il [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento specifica la proprietà il cui valore viene visualizzato nella riga. È necessario specificare una proprietà o uno script, ma è possibile specificare entrambi.

- Il [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento specifica lo script il cui valore viene visualizzato nella riga. È necessario specificare uno script o una proprietà, ma è possibile specificare entrambi.

- Il [FormatString](./label-element-for-listitem-for-listcontrol-format.md) elemento specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script. Questo elemento è facoltativo.

- Il [allineamento](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento specifica come viene visualizzato il valore della proprietà o dello script. Il valore può essere allineato a sinistra, a destra, o al centro. Questo elemento è facoltativo.

## <a name="defining-the-objects-that-use-the-table-view"></a>Definire gli oggetti che utilizzano la vista tabella

Esistono due modi per definire quali oggetti .NET usano la visualizzazione di tabella. È possibile usare la [ViewSelectedBy](./viewselectedby-element-format.md) elemento per definire gli oggetti che possono essere visualizzati da tutte le definizioni di visualizzazione, oppure è possibile utilizzare il [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento per definire quali oggetti vengono visualizzati da un definizione della vista specifica. Nella maggior parte dei casi, una vista ha una sola definizione, in modo che gli oggetti vengono in genere definiti per il [ViewSelectedBy](./viewselectedby-element-format.md) elemento.

Nell'esempio seguente viene illustrato come definire gli oggetti che vengono visualizzati per la visualizzazione di tabella usando il [ViewSelectedBy](./viewselectedby-element-format.md) e [nomeTipo](./typename-element-for-viewselectedby-format.md) elementi. Non sono previsti limiti al numero di [TypeName](./typename-element-for-viewselectedby-format.md) gli elementi che è possibile specificare l'ordine non è significativo.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Gli elementi XML seguenti sono utilizzabile per specificare gli oggetti utilizzati per la visualizzazione di tabella:

- Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento definisce gli oggetti che vengono visualizzati nella visualizzazione elenco.

- Il [TypeName](./typename-element-for-viewselectedby-format.md) elemento specifica l'oggetto .NET che viene visualizzato nella visualizzazione. Il nome del tipo .NET completo è obbligatorio. È necessario specificare almeno un tipo o la selezione impostato per la visualizzazione, ma nessun numero massimo di elementi che possono essere specificati.

L'esempio seguente usa il [ViewSelectedBy](./viewselectedby-element-format.md) e [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementi. Usare i set di selezione in cui è presente un set correlato di oggetti che vengono visualizzati utilizzando più viste, ad esempio quando si definisce una visualizzazione elenco e visualizzazione di una tabella per gli oggetti stessi. Per altre informazioni su come creare un set di selezione, vedere [definizione di set di selezione](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Gli elementi XML seguenti sono utilizzabile per specificare gli oggetti utilizzati dalla visualizzazione elenco:

- Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento definisce gli oggetti che vengono visualizzati nella visualizzazione elenco.

- Il [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento specifica un set di oggetti che possono essere visualizzati da parte della vista. È necessario specificare almeno un set di selezione o tipo per la visualizzazione, ma nessun numero massimo di elementi che possono essere specificati.

Nell'esempio seguente viene illustrato come definire gli oggetti visualizzati da una definizione di specifica della visualizzazione tabella mediante la [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento. Utilizzo di questo elemento, è possibile specificare il nome del tipo .NET dell'oggetto, un set di selezione di oggetti o una condizione di selezione che consente di specificare quando viene utilizzata la definizione. Per altre informazioni su come creare una selezione condizioni, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

> [!NOTE]
> Quando si creano più definizioni della visualizzazione della tabella che non è possibile specificare le intestazioni di colonna diverso. È possibile specificare solo gli elementi visualizzati nelle righe della tabella, ad esempio gli oggetti che vengono visualizzati.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

Gli elementi XML seguenti possono essere utilizzati per specificare gli oggetti usati da una definizione di specifica della visualizzazione elenco:

- Il [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento definisce gli oggetti che vengono visualizzati per la definizione.

- Il [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) elemento specifica l'oggetto .NET che viene visualizzato per la definizione. Quando si usa questo elemento, è necessario il nome del tipo .NET completo. È necessario specificare almeno un tipo, set di selezione o condizione di selezione per la definizione, ma nessun numero massimo di elementi che possono essere specificati.

- Il [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) elemento (non mostrato) specifica un set di oggetti che possono essere visualizzati da questa definizione. È necessario specificare almeno un tipo, set di selezione o condizione di selezione per la definizione, ma nessun numero massimo di elementi che possono essere specificati.

- Il [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) elemento (non mostrato) specifica una condizione che deve essere presente per questa definizione da usare. È necessario specificare almeno un tipo, set di selezione o condizione di selezione per la definizione, ma nessun numero massimo di elementi che possono essere specificati. Per altre informazioni sulla definizione di condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="using-format-strings"></a>Stringhe di formato

Stringhe di formattazione possono essere aggiunti a una visualizzazione per definire ulteriormente la modalità di visualizzazione dei dati. Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della `StartTime` proprietà.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

Gli elementi XML seguenti possono essere utilizzati per specificare uno schema di formattazione:

- Il [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento definisce le proprietà il cui valore viene visualizzato nella colonna della riga di script. Oggetto [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento è obbligatorio per ogni colonna della riga. La prima voce viene visualizzata nella prima colonna, la seconda voce nella seconda colonna e così via.

- Il [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento specifica la proprietà il cui valore viene visualizzato nella riga. È necessario specificare una proprietà o uno script, ma è possibile specificare entrambi.

- Il [FormatString](./label-element-for-listitem-for-listcontrol-format.md) elemento specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script.

Nell'esempio seguente, il `ToString` metodo viene chiamato per formattare il valore dello script. Gli script possono chiamare qualsiasi metodo di un oggetto. Pertanto, se un oggetto dispone di un metodo, ad esempio `ToString`, che può avere parametri di formattazione, lo script può chiamare tale metodo per formattare il valore di output dello script.

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

L'elemento XML seguente è utilizzabile per chiamare il `ToString` metodo:

- Il [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento definisce le proprietà il cui valore viene visualizzato nella colonna della riga di script. Oggetto [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento è obbligatorio per ogni colonna della riga. La prima voce viene visualizzata nella prima colonna, la seconda voce nella seconda colonna e così via.

- Il [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento specifica lo script il cui valore viene visualizzato nella riga. È necessario specificare uno script o una proprietà, ma è possibile specificare entrambi.

## <a name="see-also"></a>Vedere anche

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
