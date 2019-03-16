---
title: Elemento TableColumnHeader (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057876"
---
# <a name="tablecolumnheader-element-format"></a>Elemento TableColumnHeader (formato)

Definisce l'etichetta, la larghezza della colonna e l'allineamento dell'etichetta per una colonna della tabella.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) TableHeaders elemento di configurazione per Table (formato) TableColumnHeader elemento TableHeaders per Table (formato)

## <a name="syntax"></a>Sintassi

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `TableColumnHeader` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento Label per TableColumnHeader per Table (formato)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Definisce l'etichetta che viene visualizzato nella parte superiore della colonna. Se viene specificata alcuna etichetta, viene utilizzato il nome della proprietà il cui valore viene visualizzato nelle righe.|
|[Elemento larghezza per TableColumnHeader per Table (formato)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|Elemento obbligatorio.<br /><br /> Specifica la larghezza (in caratteri) della colonna.|
|[Elemento Alignment per TableColumnHeader per Table (formato)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica come viene visualizzata l'etichetta della colonna. Se non viene specificato alcun allineamento, l'etichetta è allineata a sinistra.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableHeaders (formato)](./tableheaders-element-format.md)|Definisce le colonne di una visualizzazione tabella.|

## <a name="remarks"></a>Osservazioni

Specificare un'intestazione per ogni colonna della tabella. Le colonne vengono visualizzate nell'ordine in cui il `TableColumnHeader` vengono definiti gli elementi.

Una tabella deve avere lo stesso numero di `TableColumnHeader` elementi come `TableRowEntry` elementi. L'intestazione di colonna definisce come viene visualizzato il testo nella parte superiore della tabella. Le voci di riga definiscono quali dati vengono visualizzati nelle righe della tabella.

Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [vista tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente vengono illustrati due `TableColumnHeader` elementi. Il primo elemento definisce una colonna con etichetta "Column 1", ha una larghezza pari a 16 caratteri e la cui etichetta è allineata a sinistra. Il secondo elemento definisce una colonna la cui etichetta è "2 Column", ha una larghezza pari a 10 caratteri e la cui etichetta è centrato nella colonna.

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

[Elemento Alignment per TableColumnHeader per Table (formato)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Creazione di una visualizzazione tabella](./creating-a-table-view.md)

[Elemento Label per TableColumnHeader per Table (formato)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Elemento TableHeaders per Table (formato)](./tableheaders-element-format.md)

[Larghezza per TableColumnHeader per elemento Table (formato)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
