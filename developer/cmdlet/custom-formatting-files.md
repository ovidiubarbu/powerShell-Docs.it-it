---
title: I file di formattazione personalizzata | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860607"
---
# <a name="custom-formatting-files"></a>File di formattazione personalizzati

Il formato di visualizzazione per gli oggetti restituiti dal cmdlet, funzioni e gli script vengono definiti utilizzando il file di formattazione (format.ps1xml file). Molti di questi file vengono forniti tramite Windows PowerShell per definire il formato di visualizzazione predefinito per gli oggetti restituiti dai cmdlet di Windows PowerShell. Tuttavia, è anche possibile creare i proprio file di formattazione personalizzati per sovrascrivere i formati di visualizzazione predefinito o per definire la visualizzazione degli oggetti restituiti da comandi personalizzati.

Windows PowerShell Usa i dati in questi file di formattazione per determinare ciò che viene visualizzato e il modo in cui sono formattati i dati. I dati visualizzati possono includere le proprietà di un oggetto o il valore di un blocco di script.  Se si desidera visualizzare un valore che non è disponibile direttamente dalle proprietà di un oggetto, vengono utilizzati i blocchi di script. Ad esempio, è possibile aggiungere il valore di due proprietà di un oggetto e visualizzare la somma come una parte separata dei dati. Quando si scrive un file di formattazione personalizzato, è necessario definire *viste* per gli oggetti che si desidera visualizzare. È possibile definire una singola visualizzazione per ogni oggetto, è possibile definire una singola visualizzazione per più oggetti o è possibile definire più visualizzazioni per lo stesso oggetto. Non sono previsti limiti al numero di visualizzazioni che è possibile definire.

> [!IMPORTANT]
> File di formattazione non determinano gli elementi di un oggetto che vengono restituiti alla pipeline. Quando un oggetto viene restituito alla pipeline, sono disponibili tutti i membri di tale oggetto.

## <a name="format-views"></a>Viste di formato

Formattazione viste è possono visualizzare gli oggetti in un formato di tabella, un formato di elenco, un formato esteso e un formato personalizzato. Nella maggior parte, ogni definizione di formattazione è descritta da un set di tag XML che descrivono una vista. Ogni visualizzazione contiene il nome della visualizzazione, gli oggetti che utilizzano la vista e gli elementi della visualizzazione, ad esempio le informazioni di colonna e riga per una visualizzazione tabella.

Le viste seguenti sono disponibili.

Visualizzazione tabella sono elencate le proprietà di un oggetto o un valore di blocco di script in una o più colonne. Ogni colonna rappresenta una proprietà dell'oggetto o un valore di blocco di script. È possibile definire una visualizzazione tabella che visualizza tutte le proprietà di un oggetto, un subset delle proprietà di un oggetto o una combinazione di proprietà e i valori di blocco di script. Ogni riga della tabella rappresenta un oggetto restituito. Per altre informazioni su questa vista, vedere [vista tabella](../format/creating-a-table-view.md).

Visualizzazione elenco sono elencate le proprietà di un oggetto o un valore di blocco di script in una singola colonna. Ogni riga dell'elenco Visualizza un'etichetta facoltativa o il nome della proprietà seguito dal valore del blocco di proprietà o dello script. Per altre informazioni su questa vista, vedere [visualizzazione elenco](../format/creating-a-list-view.md).

Visualizzazione più ampia elenca una singola proprietà di un oggetto o un valore di blocco di script in una o più colonne. Non sono etichetta o intestazione per questa visualizzazione. Per altre informazioni su questa vista, vedere [visualizzazione estesa](../format/creating-a-wide-view.md).

Visualizzazione personalizzata consente di visualizzare una visualizzazione di proprietà degli oggetti o valori di blocco di script personalizzabile che non rispettano la struttura rigida di viste delle tabelle, visualizzazioni elenco o visualizzazioni ampie. È possibile definire una visualizzazione personalizzata autonoma oppure è possibile definire una visualizzazione personalizzata che viene usata da un'altra visualizzazione, ad esempio una tabella o una vista elenco. Per altre informazioni su questa vista, vedere [vista personalizzata](../format/creating-custom-controls.md).

## <a name="view-xml-elements"></a>Visualizzare gli elementi XML

Nell'esempio seguente mostra i tag XML utilizzati per definire una visualizzazione tabella che contiene due colonne. Il [ViewDefinitions](../format/viewdefinitions-element-format.md) elemento corrisponde all'elemento contenitore per tutte le viste definite nel file di formattazione. Il [vista](../format/view-element-format.md) elemento definisce la tabella specifica, elenco, visualizzazione wide o personalizzato. All'interno di ogni visualizzazione, il [nome](../format/name-element-for-view-format.md) elemento specifica il nome della visualizzazione, il [ViewSelectedBy](../format/viewselectedby-element-format.md) elemento definisce gli oggetti che utilizzano la vista e gli elementi di controllo diverso (come il `TableControl` elemento) definisce il formato di visualizzazione.

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

[Visualizzazione più ampia](../format/creating-a-wide-view.md)

[Visualizzazione personalizzata](../format/creating-custom-controls.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
