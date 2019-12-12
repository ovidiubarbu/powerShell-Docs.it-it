---
title: File di formattazione personalizzati | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369830"
---
# <a name="custom-formatting-files"></a>File di formattazione personalizzati

Il formato di visualizzazione per gli oggetti restituiti da cmdlet, funzioni e script viene definito utilizzando i file di formattazione (file format. ps1xml). Molti di questi file sono forniti da Windows PowerShell per definire il formato di visualizzazione predefinito per gli oggetti restituiti dai cmdlet di Windows PowerShell. Tuttavia, è anche possibile creare file di formattazione personalizzati per sovrascrivere i formati di visualizzazione predefiniti o per definire la visualizzazione degli oggetti restituiti dai propri comandi.

Windows PowerShell usa i dati nei file di formattazione per determinare gli elementi visualizzati e il modo in cui vengono formattati i dati. I dati visualizzati possono includere le proprietà di un oggetto o il valore di un blocco di script.  I blocchi di script vengono utilizzati se si desidera visualizzare un valore non disponibile direttamente dalle proprietà di un oggetto. Ad esempio, è possibile aggiungere il valore di due proprietà di un oggetto e visualizzare la somma come una porzione di dati separata. Quando si scrive un file di formattazione personalizzato, sarà necessario definire le *visualizzazioni* per gli oggetti che si desidera visualizzare. È possibile definire una singola visualizzazione per ogni oggetto, è possibile definire una singola visualizzazione per più oggetti oppure è possibile definire più visualizzazioni per lo stesso oggetto. Non esiste alcun limite al numero di visualizzazioni che è possibile definire.

> [!IMPORTANT]
> I file di formattazione non determinano gli elementi di un oggetto restituiti alla pipeline. Quando un oggetto viene restituito alla pipeline, sono disponibili tutti i membri di tale oggetto.

## <a name="format-views"></a>Formatta visualizzazioni

Le visualizzazioni di formattazione possono visualizzare oggetti in formato tabella, formato elenco, formato esteso e formato personalizzato. Nella maggior parte dei casi, ogni definizione di formattazione è descritta da un set di tag XML che descrivono una visualizzazione. Ogni vista contiene il nome della vista, gli oggetti che utilizzano la vista e gli elementi della vista, ad esempio le informazioni su colonna e riga per una visualizzazione tabella.

Sono disponibili le viste seguenti.

Visualizzazione tabella sono elencate le proprietà di un oggetto o di un valore del blocco di script in una o più colonne. Ogni colonna rappresenta una proprietà dell'oggetto o un valore del blocco di script. È possibile definire una vista tabella che Visualizza tutte le proprietà di un oggetto, un subset delle proprietà di un oggetto o una combinazione di proprietà e valori di blocchi di script. Ogni riga della tabella rappresenta un oggetto restituito. Per ulteriori informazioni su questa vista, vedere [visualizzazione tabella](../format/creating-a-table-view.md).

Visualizzazione elenco elenca le proprietà di un oggetto o di un valore del blocco di script in un'unica colonna. Ogni riga dell'elenco Visualizza un'etichetta facoltativa o il nome della proprietà seguito dal valore della proprietà o del blocco di script. Per ulteriori informazioni su questa visualizzazione, vedere [visualizzazione elenco](../format/creating-a-list-view.md).

Visualizzazione estesa elenca una singola proprietà di un oggetto o un valore del blocco di script in una o più colonne. Nessuna etichetta o intestazione per questa visualizzazione. Per ulteriori informazioni su questa visualizzazione, vedere [visualizzazione estesa](../format/creating-a-wide-view.md).

Visualizzazione personalizzata consente di visualizzare una visualizzazione personalizzabile delle proprietà degli oggetti o dei valori del blocco di script che non rispettano la struttura rigida delle visualizzazioni di tabella, delle visualizzazioni elenco o delle visualizzazioni estese. È possibile definire una visualizzazione personalizzata autonoma oppure è possibile definire una visualizzazione personalizzata utilizzata da un'altra visualizzazione, ad esempio una visualizzazione tabella o una visualizzazione elenco. Per ulteriori informazioni su questa visualizzazione, vedere [visualizzazione personalizzata](../format/creating-custom-controls.md).

## <a name="view-xml-elements"></a>Visualizzazione di elementi XML

Nell'esempio seguente vengono illustrati i tag XML utilizzati per definire una vista tabella contenente due colonne. L'elemento [ViewDefinitions](../format/viewdefinitions-element-format.md) è l'elemento contenitore per tutte le visualizzazioni definite nel file di formattazione. L'elemento [View](../format/view-element-format.md) definisce la tabella, l'elenco, la larghezza o la visualizzazione personalizzata specifica. All'interno di ogni visualizzazione, l'elemento [Name](../format/name-element-for-view-format.md) specifica il nome della vista, l'elemento [ViewSelectedBy](../format/viewselectedby-element-format.md) definisce gli oggetti che utilizzano la visualizzazione e i diversi elementi del controllo, ad esempio l'elemento `TableControl`, definiscono il formato della visualizzazione.

```xml
ViewDefinitions
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

[Visualizzazione tabella](../format/creating-a-table-view.md)

[Visualizzazione elenco](../format/creating-a-list-view.md)

[Visualizzazione estesa](../format/creating-a-wide-view.md)

[Visualizzazione personalizzata](../format/creating-custom-controls.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
