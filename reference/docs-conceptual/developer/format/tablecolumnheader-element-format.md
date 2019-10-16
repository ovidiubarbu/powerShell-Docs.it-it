---
title: Elemento TableColumnHeader (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361850"
---
# <a name="tablecolumnheader-element-format"></a>Elemento TableColumnHeader (formato)

Definisce l'etichetta, la larghezza della colonna e l'allineamento dell'etichetta per una colonna della tabella.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableHeaders per Table ((Format) elemento TableColumnHeader per TableHeaders per Table ((Format)

## <a name="syntax"></a>Sintassi

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TableColumnHeader`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento label per TableColumnHeader per Table ((Format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Definisce l'etichetta visualizzata nella parte superiore della colonna. Se non viene specificata alcuna etichetta, viene usato il nome della proprietà il cui valore viene visualizzato nelle righe.|
|[Elemento Width per TableColumnHeader per Table ((Format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|Elemento obbligatorio.<br /><br /> Specifica la larghezza (in caratteri) della colonna.|
|[Elemento Alignment per TableColumnHeader per Table ((Format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica la modalità di visualizzazione dell'etichetta della colonna. Se non viene specificato alcun allineamento, l'etichetta viene allineata a sinistra.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableHeaders (Format)](./tableheaders-element-format.md)|Definisce le colonne di una visualizzazione tabella.|

## <a name="remarks"></a>Osservazioni

Specificare un'intestazione per ogni colonna della tabella. Le colonne vengono visualizzate nell'ordine in cui sono definiti gli elementi `TableColumnHeader`.

Una tabella deve avere lo stesso numero di elementi `TableColumnHeader` come elementi `TableRowEntry`. L'intestazione di colonna definisce il modo in cui viene visualizzato il testo nella parte superiore della tabella. Le voci di riga definiscono quali dati vengono visualizzati nelle righe della tabella.

Per ulteriori informazioni sui componenti di una vista tabella, vedere [visualizzazione tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente vengono illustrati due elementi `TableColumnHeader`. Il primo elemento definisce una colonna la cui etichetta è "Column 1", ha una larghezza di 16 caratteri e la cui etichetta è allineata a sinistra. Il secondo elemento definisce una colonna la cui etichetta è "Column 2", ha una larghezza di 10 caratteri e la cui etichetta è centrata nella colonna.

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
    <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a>Vedere anche

[Elemento Alignment per TableColumnHeader per Table ((Format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Creazione di una vista tabella](./creating-a-table-view.md)

[Elemento label per TableColumnHeader per Table ((Format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Elemento TableHeaders per Table ((Format)](./tableheaders-element-format.md)

[Width per TableColumnHeader per l'elemento Table ((Format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
