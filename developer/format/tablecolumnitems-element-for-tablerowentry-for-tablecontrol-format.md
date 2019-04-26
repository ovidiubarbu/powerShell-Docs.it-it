---
title: Elemento TableColumnItems per TableRowEntry per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075393"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a>Elemento TableColumnItems per TableRowEntry per TableControl (formato)

Definisce le proprietà o gli script i cui valori vengono visualizzati in una riga.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) TableRowEntries elemento di configurazione per Table (formato) TableRowEntry elemento TableRowEntries per Table (formato) Elemento TableColumnItems per TableControlEntry per Table (formato)

## <a name="syntax"></a>Sintassi

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `TableColumnItems` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableColumnItem per TableColumnItems per Table (formato)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Elemento obbligatorio.<br /><br /> Definisce le proprietà il cui valore viene visualizzato in una colonna della riga di script.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableRowEntry per TableRowEntries per Table (formato)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Definisce i dati che viene visualizzati in una riga della tabella.|

## <a name="remarks"></a>Osservazioni

Oggetto `TableColumnItem` elemento è obbligatorio per ogni colonna della riga. La prima voce viene visualizzata nella prima colonna, la seconda voce nella seconda colonna e così via.

Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

L'esempio seguente mostra un `TableColumnItems` che definisce tre proprietà dell'elemento di [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto.

```xml
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

```

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione tabella](./creating-a-table-view.md)

[Elemento TableColumnItem (formato)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Elemento TableRowEntry (formato)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
