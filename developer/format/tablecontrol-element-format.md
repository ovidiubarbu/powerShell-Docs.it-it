---
title: Elemento Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: dd48e82452e83f93e2e005c9db53bbc51d8b2eb4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858917"
---
# <a name="tablecontrol-element-format"></a>Elemento TableControl (formato)

Definisce un formato di tabella per una visualizzazione.

Elemento TABLE di elemento (formato) visualizzazione elemento ViewDefinitions (formato) (formato)

## <a name="syntax"></a>Sintassi

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono l'elemento padre di attributi e gli elementi figlio di `TableControl` elemento. È necessario specificare le righe della tabella. Tutti gli elementi figlio sono facoltativi.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[AutoSize (elemento) per Table (formato)](./autosize-element-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica se la dimensione della colonna e il numero di colonne vengono adattate in base alla dimensione dei dati.|
|[Elemento HideTableHeaders per Table (formato)](./hidetableheaders-element-format.md)|Elemento facoltativo.<br /><br /> Indica se l'intestazione della tabella non viene visualizzato.|
|[Elemento TableHeaders per Table (formato)](./tableheaders-element-format.md)|Elemento obbligatorio.<br /><br /> Definisce le etichette, la larghezza e l'allineamento dei dati per le colonne della visualizzazione della tabella.|
|[Elemento TableRowEntries per TableCotrol (formato)](./tablerowentries-element-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Fornisce le definizioni della visualizzazione della tabella.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento di visualizzazione (formato)](./view-element-format.md)|Definisce una vista che consente di visualizzare i membri di uno o più oggetti.|

## <a name="remarks"></a>Osservazioni

Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

Questo esempio viene illustrato un `TableControl` che consente di visualizzare le proprietà dell'elemento il [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) oggetto.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione tabella](./creating-a-table-view.md)

[Elemento di visualizzazione (formato)](./view-element-format.md)

[AutoSize (elemento) per Table (formato)](./autosize-element-for-tablecontrol-format.md)

[Elemento HideTableHeaders (formato)](./hidetableheaders-element-format.md)

[Elemento TableHeaders (formato)](./tableheaders-element-format.md)

[Elemento TableRowEntries (formato)](./tablerowentries-element-for-tablecontrol-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
