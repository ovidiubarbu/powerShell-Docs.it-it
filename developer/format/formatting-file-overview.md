---
title: Panoramica dei File di formattazione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863297"
---
# <a name="formatting-file-overview"></a>Panoramica dei file di formattazione

Il formato di visualizzazione per gli oggetti che vengono restituiti dai comandi (cmdlet, funzioni e script) sono definiti tramite file di formattazione (format.ps1xml file). Molti di questi file vengono forniti da PowerShell per definire il formato di visualizzazione per gli oggetti restituiti dai comandi di PowerShell fornito, come le [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto restituito dal `Get-Process` cmdlet. Tuttavia, è anche possibile creare i proprio file di formattazione personalizzati per sovrascrivere i formati di visualizzazione predefinito o è possibile scrivere un file di formattazione personalizzato per definire la visualizzazione degli oggetti restituiti dai propri comandi.

> [!IMPORTANT]
> File di formattazione non determinano gli elementi di un oggetto che vengono restituiti alla pipeline. Quando un oggetto viene restituito alla pipeline, tutti i membri di tale oggetto sono disponibili anche se alcuni non vengono visualizzati.

PowerShell Usa i dati in questi file di formattazione per determinare quali informazioni visualizzare e come formattare i dati visualizzati. I dati visualizzati possono includere le proprietà di un oggetto o il valore di uno script. Gli script vengono utilizzati se si desidera visualizzare un valore che non è disponibile direttamente dalle proprietà di un oggetto, ad esempio aggiungere il valore di due proprietà di un oggetto e quindi Visualizza la somma come una porzione di dati. Formattazione dei dati visualizzati viene eseguita definendo le visualizzazioni per gli oggetti che si desidera visualizzare. È possibile definire una singola visualizzazione per ogni oggetto, è possibile definire una singola visualizzazione per più oggetti o è possibile definire più visualizzazioni per lo stesso oggetto. Non sono previsti limiti al numero di visualizzazioni che è possibile definire.

## <a name="common-features-of-formatting-files"></a>Funzionalità comuni di file di formattazione

Ogni file di formattazione possa definire i componenti seguenti che possono essere condivise tra tutte le viste definite nel file:

- Impostazione di configurazione, ad esempio se i dati visualizzati nelle righe delle tabelle verranno visualizzati nella riga successiva se i dati sono più lunghi rispetto alla larghezza della colonna. Per altre informazioni su queste impostazioni, vedere [definizione delle impostazioni di configurazione comuni](./defining-common-configuration-features.md).

- Set di oggetti che possono essere visualizzati da qualsiasi visualizzazione del file di formattazione. Per altre informazioni su questi set (detta *set di selezione*), vedere [definizione imposta di oggetti](./defining-selection-sets.md).

- Controlli comuni che possono essere usati da tutte le visualizzazioni del file di formattazione. I controlli consentono un controllo più preciso su modalità di visualizzazione dati. Per altre informazioni sui controlli, vedere [definire i controlli personalizzati](./creating-custom-controls.md).

## <a name="formatting-views"></a>Le visualizzazioni di formattazione

Formattazione viste è possono visualizzare gli oggetti in un formato di tabella, formato di elenco, formato grande e formato personalizzato. Nella maggior parte, ogni definizione di formattazione è descritta da un set di tag XML che descrivono la visualizzazione. Ogni visualizzazione contiene il nome della visualizzazione, gli oggetti che utilizzano la vista e gli elementi della visualizzazione, ad esempio le informazioni di colonna e riga per una visualizzazione tabella.

Visualizza gli elenchi delle proprietà di un oggetto o un valore di blocco di script in una o più colonne di tabella. Ogni colonna rappresenta una singola proprietà dell'oggetto o un valore di script. È possibile definire una visualizzazione tabella che visualizza tutte le proprietà di un oggetto, un subset delle proprietà di un oggetto o una combinazione di proprietà e valori di script. Ogni riga della tabella rappresenta un oggetto restituito. Creazione di una visualizzazione tabella è molto simile a quando si invia tramite pipe un oggetto per il `Format-Table` cmdlet. Per altre informazioni su questa vista, vedere [vista tabella](./creating-a-table-view.md).

Elenco nella visualizzazione sono elencate le proprietà di un oggetto o un valore di uno script in una singola colonna. Ogni riga dell'elenco Visualizza un'etichetta facoltativa o il nome della proprietà seguito dal valore della proprietà o dello script. Creazione di una visualizzazione elenco è molto simile a tramite pipe un oggetto per il `Format-List` cmdlet. Per altre informazioni su questa vista, vedere [visualizzazione elenco](./creating-a-list-view.md).

Visualizzazione più ampia elenca una singola proprietà di un oggetto o un valore di uno script in una o più colonne. Non sono etichetta o intestazione per questa visualizzazione. Creazione di una visualizzazione più ampia è molto simile a tramite pipe un oggetto per il `Format-Wide` cmdlet. Per altre informazioni su questa vista, vedere [visualizzazione estesa](./creating-a-wide-view.md).

Visualizzazione personalizzata Visualizza una visualizzazione di proprietà degli oggetti o valori dello script personalizzabile che non rispettano la struttura rigida di viste delle tabelle, visualizzazioni elenco o visualizzazioni ampie. È possibile definire una visualizzazione personalizzata autonoma oppure è possibile definire una visualizzazione personalizzata che viene usata da un'altra visualizzazione, ad esempio una tabella o una vista elenco. Creare una visualizzazione personalizzata è molto simile a tramite pipe un oggetto per il `Format-Custom` cmdlet. Per altre informazioni su questa vista, vedere [vista personalizzata](./creating-custom-controls.md).

## <a name="components-of-a-view"></a>Componenti di una vista

Gli esempi XML seguenti illustrano i componenti di base XML di una vista. I singoli elementi XML variano a seconda di quale visualizzazione si vuole creare, ma i componenti di base delle viste sono tutti uguali.

Per iniziare, ogni visualizzazione dispone di un `Name` elemento che specifica un nome descrittivo usato per fare riferimento la vista. una `ViewSelectedBy` elemento che definisce quali oggetti .NET vengono visualizzati dalla visualizzazione, e una *controllo* elemento che definisce la vista.

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

All'interno dell'elemento di controllo, è possibile definire uno o più *voce* elementi. Se si usano più definizioni, è necessario specificare quali oggetti .NET usano ogni definizione. In genere solo una voce, con una sola definizione, è necessaria per ogni controllo.

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

All'interno di ogni elemento della voce di una vista, si specifica la *elemento* gli elementi che definiscono le proprietà .NET o script che vengono visualizzate per tale vista.

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

Come illustrato negli esempi precedenti, il file di formattazione può contenere più viste, una vista può contenere più definizioni e ogni definizione può contenere più elementi.

## <a name="example-of-a-table-view"></a>Esempio di una visualizzazione tabella

Nell'esempio seguente mostra i tag XML utilizzati per definire una visualizzazione tabella che contiene due colonne. Il [ViewDefinitions](./viewdefinitions-element-format.md) elemento corrisponde all'elemento contenitore per tutte le viste definite nel file di formattazione. Il [vista](./view-element-format.md) elemento definisce la tabella specifica, elenco, visualizzazione wide o personalizzato. All'interno di ciascun [vista](./view-element-format.md) elemento, il [nome](./name-element-for-view-format.md) elemento specifica il nome della visualizzazione, il [ViewSelectedBy](./viewselectedby-element-format.md) elemento definisce gli oggetti che utilizzano la vista e i diversi gli elementi del controllo (ad esempio il `TableControl` elemento mostrato nell'esempio seguente) definiscono il tipo di visualizzazione.

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

[Creazione di una visualizzazione tabella](./creating-a-table-view.md)

[Creazione di una visualizzazione più ampia](./creating-a-wide-view.md)

[Creazione di controlli personalizzati](./creating-custom-controls.md)

[La scrittura di una formattazione di PowerShell e dei tipi](./writing-a-powershell-formatting-file.md)
