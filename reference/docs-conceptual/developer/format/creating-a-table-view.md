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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363410"
---
# <a name="creating-a-table-view"></a>Creazione di una visualizzazione tabella

Una vista tabella consente di visualizzare i dati in una o più colonne. Ogni riga della tabella rappresenta un oggetto .NET e ogni colonna della tabella rappresenta una proprietà dell'oggetto o un valore dello script. È possibile definire una vista tabella che Visualizza tutte le proprietà di un oggetto o un subset delle proprietà di un oggetto.

## <a name="a-table-view-display"></a>Visualizzazione tabella

Nell'esempio seguente viene illustrato come Windows PowerShell visualizzi l'oggetto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) restituito dal cmdlet [Get-Service](/powershell/module/microsoft.powershell.management/get-service) . Per questo oggetto, Windows PowerShell ha definito una vista tabella che visualizza la proprietà `Status`, la proprietà `Name` (questa proprietà è una proprietà alias per la proprietà `ServiceName`) e la proprietà `DisplayName`. Ogni riga della tabella rappresenta un oggetto restituito dal cmdlet.

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a>Definizione della visualizzazione tabella

Nel codice XML seguente viene illustrato lo schema di visualizzazione tabella per la visualizzazione di [System. ServiceProcess. ServiceController? Oggetto DisplayProperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) . È necessario specificare ogni proprietà che si desidera visualizzare nella visualizzazione tabella.

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

Per definire una visualizzazione elenco vengono utilizzati gli elementi XML seguenti:

- L'elemento [View](./view-element-format.md) è l'elemento padre della visualizzazione tabella. (Si tratta dello stesso elemento padre per le visualizzazioni elenco, Wide e Custom Control).

- L'elemento [Name](./name-element-for-view-format.md) specifica il nome della vista. Questo elemento è obbligatorio per tutte le visualizzazioni.

- L'elemento [ViewSelectedBy](./viewselectedby-element-format.md) definisce gli oggetti che utilizzano la visualizzazione. Questo elemento è obbligatorio.

- L'elemento [GroupBy](./groupby-element-for-view-format.md) (non illustrato in questo esempio) definisce quando viene visualizzato un nuovo gruppo di oggetti. Un nuovo gruppo viene avviato ogni volta che viene modificato il valore di una proprietà o di uno script specifico. Questo elemento è facoltativo.

- L'elemento [Controls](./controls-element-for-view-format.md) (non illustrato in questo esempio) definisce i controlli personalizzati definiti dalla visualizzazione tabella. I controlli consentono di specificare in modo più dettagliato la modalità di visualizzazione dei dati. Questo elemento è facoltativo. Una vista può definire i propri controlli personalizzati oppure può utilizzare controlli comuni che possono essere utilizzati da qualsiasi visualizzazione nel file di formattazione. Per ulteriori informazioni sui controlli personalizzati, vedere [creazione di controlli personalizzati](./creating-custom-controls.md).

- L'elemento [HideTableHeaders](./hidetableheaders-element-format.md) (non visualizzato in questo esempio) specifica che nella tabella non verrà visualizzata alcuna etichetta nella parte superiore della tabella. Questo elemento è facoltativo.

- Elemento [Table (](./tablecontrol-element-format.md) che definisce le informazioni di intestazione e riga della tabella. Analogamente a tutte le altre viste, una vista tabella può visualizzare i valori delle proprietà o dei valori degli oggetti generati dagli script.

## <a name="defining-column-headers"></a>Definizione delle intestazioni di colonna

1. L'elemento [TableHeaders](./tableheaders-element-format.md) e i relativi elementi figlio definiscono ciò che viene visualizzato nella parte superiore della tabella.

2. L'elemento [TableColumnHeader](./tablecolumnheader-element-format.md) definisce gli elementi visualizzati nella parte superiore di una colonna della tabella. Specificare questi elementi nell'ordine in cui si desidera visualizzare le intestazioni.

   Non esiste alcun limite al numero di questo elemento che è possibile utilizzare, ma il numero di elementi [TableColumnHeader](./tablecolumnheader-element-format.md) nella visualizzazione tabella deve corrispondere al numero di elementi [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) utilizzati.

3. L'elemento [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) specifica il testo visualizzato. Questo elemento è facoltativo.

4. L'elemento [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) specifica la larghezza (in caratteri) della colonna. Questo elemento è facoltativo.

5. L'elemento [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) specifica come viene visualizzata l'etichetta. L'etichetta può essere allineata a sinistra, a destra o centrata. Questo elemento è facoltativo.

## <a name="defining-the-table-rows"></a>Definizione delle righe della tabella

Le visualizzazioni di tabella possono fornire una o più definizioni che specificano quali dati vengono visualizzati nelle righe della tabella utilizzando gli elementi figlio dell'elemento [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) . Si noti che è possibile specificare più definizioni per le righe della tabella, ma le intestazioni per le righe rimangono invariate, indipendentemente dalla definizione di riga utilizzata. In genere, una tabella avrà una sola definizione.

Nell'esempio seguente, la vista fornisce una singola definizione che Visualizza i valori di diverse proprietà di [System. Diagnostics. Process? Oggetto DisplayProperty = FullName](/dotnet/api/System.Diagnostics.Process) . In una vista tabella è possibile visualizzare il valore di una proprietà o il valore di uno script (non illustrato nell'esempio) nelle relative righe.

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

Per fornire definizioni per una riga, è possibile utilizzare gli elementi XML seguenti:

- L'elemento [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) e i relativi elementi figlio definiscono ciò che viene visualizzato nelle righe della tabella.

- L'elemento [TableRowEntry](./listentry-element-for-listcontrol-format.md) fornisce una definizione della riga. È necessario almeno un [TableRowEntry](./listentry-element-for-listcontrol-format.md) . Tuttavia, non esiste alcun limite massimo per il numero di elementi che è possibile aggiungere. Nella maggior parte dei casi, una vista avrà una sola definizione.

- L'elemento [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) specifica gli oggetti visualizzati da una definizione specifica. Questo elemento è facoltativo ed è necessario solo quando si definiscono più elementi [TableRowEntry](./listentry-element-for-listcontrol-format.md) che visualizzano oggetti diversi.

- L'elemento [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) specifica che il testo che supera la larghezza della colonna viene visualizzato nella riga successiva. Per impostazione predefinita, il testo di dimensioni superiori alla larghezza della colonna viene troncato.

- L'elemento [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) definisce le proprietà o gli script i cui valori vengono visualizzati nella riga.

- L'elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) definisce la proprietà o lo script il cui valore viene visualizzato nella colonna della riga. Un elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) è obbligatorio per ogni colonna della riga. La prima voce viene visualizzata nella prima colonna, nella seconda voce della seconda colonna e così via.

- L'elemento [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) specifica la proprietà il cui valore viene visualizzato nella riga. È necessario specificare una proprietà o uno script, ma non è possibile specificarli entrambi.

- L'elemento [scriptblock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) specifica lo script il cui valore viene visualizzato nella riga. È necessario specificare uno script o una proprietà, ma non è possibile specificarli entrambi.

- L'elemento [FormatString](./label-element-for-listitem-for-listcontrol-format.md) specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script. Questo elemento è facoltativo.

- L'elemento [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) specifica il modo in cui viene visualizzato il valore della proprietà o dello script. Il valore può essere allineato a sinistra, a destra o centrato. Questo elemento è facoltativo.

## <a name="defining-the-objects-that-use-the-table-view"></a>Definizione degli oggetti che utilizzano la visualizzazione tabella

Esistono due modi per definire gli oggetti .NET che utilizzano la visualizzazione tabella. È possibile utilizzare l'elemento [ViewSelectedBy](./viewselectedby-element-format.md) per definire gli oggetti che possono essere visualizzati da tutte le definizioni della vista oppure è possibile utilizzare l'elemento [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) per definire quali oggetti vengono visualizzati da una definizione specifica della vista. Nella maggior parte dei casi, una vista ha una sola definizione, quindi gli oggetti vengono in genere definiti dall'elemento [ViewSelectedBy](./viewselectedby-element-format.md) .

Nell'esempio seguente viene illustrato come definire gli oggetti visualizzati dalla visualizzazione tabella utilizzando gli elementi [ViewSelectedBy](./viewselectedby-element-format.md) e [typeName](./typename-element-for-viewselectedby-format.md) . Non esiste alcun limite al numero di elementi [typeName](./typename-element-for-viewselectedby-format.md) che è possibile specificare e il loro ordine non è significativo.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Per specificare gli oggetti utilizzati dalla vista tabella, è possibile utilizzare gli elementi XML seguenti:

- L'elemento [ViewSelectedBy](./viewselectedby-element-format.md) definisce quali oggetti vengono visualizzati dalla visualizzazione elenco.

- L'elemento [typeName](./typename-element-for-viewselectedby-format.md) specifica l'oggetto .NET visualizzato dalla visualizzazione. Il nome completo del tipo .NET è obbligatorio. È necessario specificare almeno un tipo o un set di selezione per la vista, ma non esiste un numero massimo di elementi che è possibile specificare.

Nell'esempio seguente vengono usati gli elementi [ViewSelectedBy](./viewselectedby-element-format.md) e [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) . Utilizzare i set di selezione in cui è presente un set correlato di oggetti visualizzati utilizzando più visualizzazioni, ad esempio quando si definiscono una visualizzazione elenco e una vista tabella per gli stessi oggetti. Per ulteriori informazioni su come creare un set di selezione, vedere [definizione](./defining-selection-sets.md)di set di selezione.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Per specificare gli oggetti utilizzati dalla visualizzazione elenco, è possibile utilizzare gli elementi XML seguenti:

- L'elemento [ViewSelectedBy](./viewselectedby-element-format.md) definisce quali oggetti vengono visualizzati dalla visualizzazione elenco.

- L'elemento [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) specifica un set di oggetti che possono essere visualizzati dalla visualizzazione. È necessario specificare almeno un set di selezione o un tipo per la vista, ma non esiste un numero massimo di elementi che è possibile specificare.

Nell'esempio seguente viene illustrato come definire gli oggetti visualizzati da una definizione specifica della visualizzazione tabella utilizzando l'elemento [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) . Utilizzando questo elemento, è possibile specificare il nome del tipo .NET dell'oggetto, un set di selezione di oggetti o una condizione di selezione che specifica quando viene utilizzata la definizione. Per ulteriori informazioni sulla creazione di condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

> [!NOTE]
> Quando si creano più definizioni della vista tabella, non è possibile specificare intestazioni di colonna diverse. È possibile specificare solo ciò che viene visualizzato nelle righe della tabella, ad esempio quali oggetti vengono visualizzati.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

Gli elementi XML seguenti possono essere utilizzati per specificare gli oggetti utilizzati da una definizione specifica della visualizzazione elenco:

- L'elemento [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) definisce quali oggetti vengono visualizzati dalla definizione.

- L'elemento [typeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) specifica l'oggetto .NET visualizzato dalla definizione. Quando si usa questo elemento, il nome completo del tipo .NET è obbligatorio. È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per la definizione, ma non esiste un numero massimo di elementi che è possibile specificare.

- L'elemento [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) (non mostrato) specifica un set di oggetti che possono essere visualizzati da questa definizione. È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per la definizione, ma non esiste un numero massimo di elementi che è possibile specificare.

- L'elemento [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (non mostrato) specifica una condizione che deve esistere affinché questa definizione venga utilizzata. È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per la definizione, ma non esiste un numero massimo di elementi che è possibile specificare. Per ulteriori informazioni sulla definizione delle condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="using-format-strings"></a>Uso di stringhe di formato

È possibile aggiungere stringhe di formattazione a una visualizzazione per definire ulteriormente la modalità di visualizzazione dei dati. Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della proprietà `StartTime`.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

Per specificare un modello di formato, è possibile utilizzare gli elementi XML seguenti:

- L'elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) definisce la proprietà o lo script il cui valore viene visualizzato nella colonna della riga. Un elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) è obbligatorio per ogni colonna della riga. La prima voce viene visualizzata nella prima colonna, nella seconda voce della seconda colonna e così via.

- L'elemento [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) specifica la proprietà il cui valore viene visualizzato nella riga. È necessario specificare una proprietà o uno script, ma non è possibile specificarli entrambi.

- L'elemento [FormatString](./label-element-for-listitem-for-listcontrol-format.md) specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script.

Nell'esempio seguente viene chiamato il metodo `ToString` per formattare il valore dello script. Gli script possono chiamare qualsiasi metodo di un oggetto. Pertanto, se un oggetto dispone di un metodo, ad esempio `ToString`, che dispone di parametri di formattazione, lo script può chiamare tale metodo per formattare il valore di output dello script.

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

Per chiamare il metodo `ToString` è possibile utilizzare l'elemento XML seguente:

- L'elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) definisce la proprietà o lo script il cui valore viene visualizzato nella colonna della riga. Un elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) è obbligatorio per ogni colonna della riga. La prima voce viene visualizzata nella prima colonna, nella seconda voce della seconda colonna e così via.

- L'elemento [scriptblock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) specifica lo script il cui valore viene visualizzato nella riga. È necessario specificare uno script o una proprietà, ma non è possibile specificarli entrambi.

## <a name="see-also"></a>Vedere anche

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
