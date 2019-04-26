---
title: Elemento TableRowEntries per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075495"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a>Elemento TableRowEntries per TableControl (formato)

Definire le righe della tabella.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) TableRowEntries elemento di configurazione per Table (formato)

## <a name="syntax"></a>Sintassi

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `TableRowEntries` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableRowEntry per TableRowEntries per Table (formato)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Elemento obbligatorio.<br /><br /> Definisce i dati che viene visualizzati in una riga della tabella.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento Table (formato)](./tablecontrol-element-format.md)|Definisce un formato di tabella per una visualizzazione.|

## <a name="remarks"></a>Osservazioni

È necessario specificare uno o più `TableRowEntry` elementi per la visualizzazione di tabella. Non sono previsti limiti al numero di massimo `TableRowEntry` gli elementi che è possibile aggiungere né il relativo ordine significativo.

Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

L'esempio seguente mostra una `TableRowEntries` elemento che definisce una riga che visualizza i valori delle due proprietà del [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto.

```xml
<TableRowEntries>
  <TableRowEntry>
    <EntrySelectedBy>
      <TypeName>System.Diagnostics.Process</TypeName>
    </EntrySelectedBy>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName> Property for first column</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName> Property for second column</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>

```

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione tabella](./creating-a-table-view.md)

[Elemento Table (formato)](./tablecontrol-element-format.md)

[Elemento TableRowEntry (formato)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
