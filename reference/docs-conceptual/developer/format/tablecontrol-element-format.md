---
title: Elemento Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368200"
---
# <a name="tablecontrol-element-format"></a>Elemento TableControl (formato)

Definisce un formato di tabella per una visualizzazione.

Elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format)

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

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TableControl`. È necessario specificare le righe della tabella. Tutti gli altri elementi figlio sono facoltativi.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento AutoSize per Table ((Format)](./autosize-element-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica se le dimensioni della colonna e il numero di colonne vengono regolate in base alle dimensioni dei dati.|
|[Elemento HideTableHeaders per Table ((Format)](./hidetableheaders-element-format.md)|Elemento facoltativo.<br /><br /> Indica se l'intestazione della tabella non viene visualizzata.|
|[Elemento TableHeaders per Table ((Format)](./tableheaders-element-format.md)|Elemento obbligatorio.<br /><br /> Definisce le etichette, le larghezze e l'allineamento dei dati per le colonne della visualizzazione tabella.|
|[Elemento TableRowEntries per Table ((Format)](./tablerowentries-element-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Fornisce le definizioni della visualizzazione tabella.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento View (Format)](./view-element-format.md)|Definisce una vista utilizzata per visualizzare i membri di uno o più oggetti.|

## <a name="remarks"></a>Osservazioni

Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

Questo esempio illustra un elemento `TableControl` usato per visualizzare le proprietà dell'oggetto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .

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

[Creazione di una vista tabella](./creating-a-table-view.md)

[Elemento View (Format)](./view-element-format.md)

[Elemento AutoSize per Table ((Format)](./autosize-element-for-tablecontrol-format.md)

[Elemento HideTableHeaders (Format)](./hidetableheaders-element-format.md)

[Elemento TableHeaders (Format)](./tableheaders-element-format.md)

[Elemento TableRowEntries (Format)](./tablerowentries-element-for-tablecontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
