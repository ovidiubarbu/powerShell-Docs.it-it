---
title: Elemento TableHeaders (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361820"
---
# <a name="tableheaders-element-format"></a>Elemento TableHeaders (formato)

Definisce le intestazioni per le colonne di una tabella.

Elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableHeaders per Table ((Format)

## <a name="syntax"></a>Sintassi

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre dell'elemento `TableHeaders`. Deve essere presente un elemento figlio per ogni proprietà dell'oggetto che deve essere visualizzato. Le informazioni sull'intestazione di colonna vengono visualizzate nell'ordine in cui sono specificati gli elementi figlio.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableColumnHeader (Format)](./tablecolumnheader-element-format.md)|Elemento facoltativo.<br /><br /> Definisce l'etichetta, la larghezza e l'allineamento dei dati per una colonna di una vista tabella.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento Table ((Format)](./tablecontrol-element-format.md)|Definisce un formato di tabella per una visualizzazione.|

## <a name="remarks"></a>Osservazioni

Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

Questo esempio mostra un elemento `TableHeaders` che definisce due intestazioni di colonna.

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

[Creazione di una vista tabella](./creating-a-table-view.md)

[Elemento TableColumnHeader (Format)](./tablecolumnheader-element-format.md)

[Elemento Table ((Format)](./tablecontrol-element-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
