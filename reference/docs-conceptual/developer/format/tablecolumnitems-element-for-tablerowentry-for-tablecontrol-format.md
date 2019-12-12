---
title: Elemento TableColumnItems per TableRowEntry per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361810"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a>Elemento TableColumnItems per TableRowEntry per TableControl (formato)

Definisce le proprietà o gli script i cui valori sono visualizzati in una riga.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries per Table ((Format) elemento TableRowEntry per TableRowEntries per Table ((Format) Elemento TableColumnItems per TableControlEntry per Table ((Format)

## <a name="syntax"></a>Sintassi

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TableColumnItems`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableColumnItem per TableColumnItems per Table ((Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Elemento obbligatorio.<br /><br /> Definisce la proprietà o lo script il cui valore viene visualizzato in una colonna della riga.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableRowEntry per TableRowEntries per Table ((Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Definisce i dati visualizzati in una riga della tabella.|

## <a name="remarks"></a>Osservazioni

È necessario un elemento `TableColumnItem` per ogni colonna della riga. La prima voce viene visualizzata nella prima colonna, nella seconda voce della seconda colonna e così via.

Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un elemento `TableColumnItems` che definisce tre proprietà dell'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

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

[Creazione di una vista tabella](./creating-a-table-view.md)

[Elemento TableColumnItem (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Elemento TableRowEntry (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
