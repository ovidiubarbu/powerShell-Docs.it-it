---
title: Cenni preliminari sul file di formattazione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363690"
---
# <a name="formatting-file-overview"></a>Panoramica dei file di formattazione

Il formato di visualizzazione per gli oggetti restituiti dai comandi (cmdlet, funzioni e script) viene definito usando i file di formattazione (file format. ps1xml). Molti di questi file sono forniti da PowerShell per definire il formato di visualizzazione per gli oggetti restituiti dai comandi forniti da PowerShell, ad esempio l'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) restituito dal cmdlet `Get-Process`. Tuttavia, è anche possibile creare file di formattazione personalizzati per sovrascrivere i formati di visualizzazione predefiniti oppure è possibile scrivere un file di formattazione personalizzato per definire la visualizzazione degli oggetti restituiti dai propri comandi.

> [!IMPORTANT]
> I file di formattazione non determinano gli elementi di un oggetto restituiti alla pipeline. Quando un oggetto viene restituito alla pipeline, tutti i membri di tale oggetto sono disponibili anche se alcuni non sono visualizzati.

PowerShell usa i dati nei file di formattazione per determinare gli elementi visualizzati e il modo in cui vengono formattati i dati visualizzati. I dati visualizzati possono includere le proprietà di un oggetto o il valore di uno script. Gli script vengono utilizzati se si desidera visualizzare un valore non disponibile direttamente dalle proprietà di un oggetto, ad esempio l'aggiunta del valore di due proprietà di un oggetto e la visualizzazione della somma come una porzione di dati. La formattazione dei dati visualizzati viene eseguita definendo le visualizzazioni per gli oggetti che si desidera visualizzare. È possibile definire una singola visualizzazione per ogni oggetto, è possibile definire una singola visualizzazione per più oggetti oppure è possibile definire più visualizzazioni per lo stesso oggetto. Non esiste alcun limite al numero di visualizzazioni che è possibile definire.

## <a name="common-features-of-formatting-files"></a>Funzionalità comuni dei file di formattazione

Ogni file di formattazione può definire i componenti seguenti che possono essere condivisi tra tutte le visualizzazioni definite dal file:

- Impostazione di configurazione predefinita, ad esempio se i dati visualizzati nelle righe delle tabelle verranno visualizzati nella riga successiva se i dati sono più lunghi della larghezza della colonna. Per ulteriori informazioni su queste impostazioni, vedere [definizione delle impostazioni di configurazione comuni](./defining-common-configuration-features.md).

- Set di oggetti che possono essere visualizzati da qualsiasi visualizzazione del file di formattazione. Per ulteriori informazioni su questi set (definiti set di *selezione*), vedere [definizione di set di oggetti](./defining-selection-sets.md).

- Controlli comuni che possono essere utilizzati da tutte le visualizzazioni del file di formattazione. I controlli consentono di ottenere un controllo più preciso sulla modalità di visualizzazione dei dati. Per ulteriori informazioni sui controlli, vedere [definizione di controlli personalizzati](./creating-custom-controls.md).

## <a name="formatting-views"></a>Formattazione di visualizzazioni

Le visualizzazioni di formattazione possono visualizzare oggetti in formato tabella, formato elenco, formato esteso e formato personalizzato. Nella maggior parte dei casi, ogni definizione di formattazione è descritta da un set di tag XML che descrivono la visualizzazione. Ogni vista contiene il nome della vista, gli oggetti che utilizzano la vista e gli elementi della vista, ad esempio le informazioni su colonna e riga per una visualizzazione tabella.

Visualizzazione tabella sono elencate le proprietà di un oggetto o di un valore del blocco di script in una o più colonne. Ogni colonna rappresenta una singola proprietà dell'oggetto o un valore di script. È possibile definire una vista tabella che Visualizza tutte le proprietà di un oggetto, un subset delle proprietà di un oggetto o una combinazione di proprietà e valori di script. Ogni riga della tabella rappresenta un oggetto restituito. La creazione di una vista tabella è molto simile a quando si invia un oggetto tramite pipe al cmdlet `Format-Table`. Per ulteriori informazioni su questa vista, vedere [visualizzazione tabella](./creating-a-table-view.md).

Visualizzazione elenco elenca le proprietà di un oggetto o di un valore di script in un'unica colonna. Ogni riga dell'elenco Visualizza un'etichetta facoltativa o il nome della proprietà seguito dal valore della proprietà o dello script. La creazione di una visualizzazione elenco è molto simile a inviare tramite pipe un oggetto al cmdlet `Format-List`. Per ulteriori informazioni su questa visualizzazione, vedere [visualizzazione elenco](./creating-a-list-view.md).

Visualizzazione estesa elenca una singola proprietà di un oggetto o un valore di script in una o più colonne. Nessuna etichetta o intestazione per questa visualizzazione. La creazione di una visualizzazione estesa è molto simile a inviare tramite pipe un oggetto al cmdlet `Format-Wide`. Per ulteriori informazioni su questa visualizzazione, vedere [visualizzazione estesa](./creating-a-wide-view.md).

Visualizzazione personalizzata consente di visualizzare una visualizzazione personalizzabile delle proprietà degli oggetti o dei valori di script che non sono conformi alla struttura rigida delle visualizzazioni di tabella, delle visualizzazioni elenco o delle visualizzazioni estese. È possibile definire una visualizzazione personalizzata autonoma oppure è possibile definire una visualizzazione personalizzata utilizzata da un'altra visualizzazione, ad esempio una visualizzazione tabella o una visualizzazione elenco. La creazione di una vista personalizzata è molto simile a inviare tramite pipe un oggetto al cmdlet `Format-Custom`. Per ulteriori informazioni su questa visualizzazione, vedere [visualizzazione personalizzata](./creating-custom-controls.md).

## <a name="components-of-a-view"></a>Componenti di una vista

Negli esempi XML seguenti vengono illustrati i componenti XML di base di una vista. I singoli elementi XML variano a seconda della visualizzazione che si desidera creare, ma i componenti di base delle visualizzazioni sono tutti uguali.

Per iniziare, ogni visualizzazione dispone di un elemento `Name` che specifica un nome descrittivo utilizzato per fare riferimento alla vista. elemento `ViewSelectedBy` che definisce quali oggetti .NET vengono visualizzati dalla visualizzazione e un elemento *Control* che definisce la visualizzazione.

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

All'interno dell'elemento Control è possibile definire uno o più elementi *entry* . Se si usano più definizioni, è necessario specificare gli oggetti .NET che usano ogni definizione. In genere, per ogni controllo è necessaria una sola voce con una sola definizione.

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

All'interno di ogni elemento entry di una vista, si specificano gli elementi *Item* che definiscono le proprietà .NET o gli script visualizzati da tale visualizzazione.

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

Come illustrato negli esempi precedenti, il file di formattazione può contenere più visualizzazioni, una vista può contenere più definizioni e ogni definizione può contenere più elementi.

## <a name="example-of-a-table-view"></a>Esempio di una vista tabella

Nell'esempio seguente vengono illustrati i tag XML utilizzati per definire una vista tabella contenente due colonne. L'elemento [ViewDefinitions](./viewdefinitions-element-format.md) è l'elemento contenitore per tutte le visualizzazioni definite nel file di formattazione. L'elemento [View](./view-element-format.md) definisce la tabella, l'elenco, la larghezza o la visualizzazione personalizzata specifica. All'interno di ogni elemento di [visualizzazione](./view-element-format.md) , l'elemento [Name](./name-element-for-view-format.md) specifica il nome della vista, l'elemento [ViewSelectedBy](./viewselectedby-element-format.md) definisce gli oggetti che utilizzano la visualizzazione e i diversi elementi del controllo, ad esempio l'elemento `TableControl` illustrato nell'esempio seguente, definiscono il tipo della visualizzazione.

```xml
<ViewDefinitions>
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Creazione di una vista tabella](./creating-a-table-view.md)

[Creazione di una visualizzazione estesa](./creating-a-wide-view.md)

[Creazione di controlli personalizzati](./creating-custom-controls.md)

[Scrittura di un file di formattazione e di tipi di PowerShell](./writing-a-powershell-formatting-file.md)
