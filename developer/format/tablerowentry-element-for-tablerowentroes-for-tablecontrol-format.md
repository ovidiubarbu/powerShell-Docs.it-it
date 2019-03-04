---
title: Elemento TableRowEntry per TableRowEntroes per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 001d46debde61f928c338b2f68112fb201f96216
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853587"
---
# <a name="tablerowentry-element-for-tablerowentroes-for-tablecontrol-format"></a>Elemento TableRowEntry per TableRowEntries per TableControl (formato)

Definisce i dati che viene visualizzati in una riga della tabella.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) TableRowEntries elemento di configurazione per Table (formato) TableRowEntry elemento TableRowEntries per Table (formato)

## <a name="syntax"></a>Sintassi

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono l'elemento padre di attributi e gli elementi figlio di `TableRowEntry` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per TableRowEntry per Table (formato)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Elemento obbligatorio.<br /><br /> Definisce gli oggetti i cui valori di proprietà vengono visualizzati nella riga.|
|[Elemento TableColumnItems per TableRowEntry per Table (formato)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Elemento obbligatorio.<br /><br /> Definisce le proprietà o gli script i cui valori vengono visualizzati.|
|[Eseguire il wrapping di elemento per TableRowEntry per TableCntrol (formato)](./wrap-element-for-tablerowentry-for-tablecontrl-format.md)|Elemento facoltativo.<br /><br /> Specifica che il testo che supera la larghezza della colonna viene visualizzato nella riga successiva.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableRowEntries per Table (formato)](./tablerowentries-element-for-tablecontrol-format.md)|Definire le righe della tabella.|

## <a name="remarks"></a>Osservazioni

Uno `TableColumnItems` elemento e l'altra `EntrySelectedBy` elemento deve essere specificato.

Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

L'esempio seguente mostra una `TableRowEntry` elemento che definisce una riga che visualizza i valori delle due proprietà del [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto.

```xml
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
```

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione tabella](./creating-a-table-view.md)

[Elemento EntrySelectedBy per TableRowEntry per Table (formato)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Elemento TableColumnItems per TableRowEntry per Table (formato)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[Elemento TableRowEntries per Table (formato)](./tablerowentries-element-for-tablecontrol-format.md)

[Elemento TableRowEntry per TableRowEntries per Table (formato)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[Eseguire il wrapping di elemento per TableRowEntry per TableCntrol (formato)](./wrap-element-for-tablerowentry-for-tablecontrl-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
