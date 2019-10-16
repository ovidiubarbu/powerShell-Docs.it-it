---
title: Elemento TableRowEntry per TableRowEntries per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361800"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a>Elemento TableRowEntry per TableRowEntries per TableControl (formato)

Definisce i dati visualizzati in una riga della tabella.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries per Table ((Format) elemento TableRowEntry per TableRowEntries per Table ((Format)

## <a name="syntax"></a>Sintassi

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TableRowEntry`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per TableRowEntry per Table ((Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Elemento obbligatorio.<br /><br /> Definisce gli oggetti i cui valori di proprietà vengono visualizzati nella riga.|
|[Elemento TableColumnItems per TableRowEntry per Table ((Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Elemento obbligatorio.<br /><br /> Definisce le proprietà o gli script i cui valori sono visualizzati.|
|[Elemento wrap per TableRowEntry per Table ((Format)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica che il testo che supera la larghezza della colonna viene visualizzato nella riga successiva.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableRowEntries per Table ((Format)](./tablerowentries-element-for-tablecontrol-format.md)|Definisce le righe della tabella.|

## <a name="remarks"></a>Osservazioni

È necessario specificare un elemento `TableColumnItems` e un elemento `EntrySelectedBy`.

Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un elemento `TableRowEntry` che definisce una riga in cui vengono visualizzati i valori di due proprietà dell'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

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

[Creazione di una vista tabella](./creating-a-table-view.md)

[Elemento EntrySelectedBy per TableRowEntry per Table ((Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Elemento TableColumnItems per TableRowEntry per Table ((Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[Elemento TableRowEntries per Table ((Format)](./tablerowentries-element-for-tablecontrol-format.md)

[Elemento wrap per TableRowEntry per Table ((Format)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
