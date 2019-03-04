---
title: Elemento TableHeaders (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856877"
---
# <a name="tableheaders-element-format"></a>Elemento TableHeaders (formato)

Definisce le intestazioni per le colonne di una tabella.

Elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) TableHeaders elemento per Table (formato)

## <a name="syntax"></a>Sintassi

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi, elementi figlio e gli elementi padre del `TableHeaders` elemento. Deve esistere un elemento figlio per ogni proprietà dell'oggetto che deve essere visualizzato. Le informazioni di intestazione di colonna viene visualizzate nell'ordine che sono specificati gli elementi figlio.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableColumnHeader (formato)](./tablecolumnheader-element-format.md)|Elemento facoltativo.<br /><br /> Definisce l'etichetta, la larghezza e l'allineamento dei dati per una colonna di una visualizzazione tabella.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento Table (formato)](./tablecontrol-element-format.md)|Definisce un formato di tabella per una visualizzazione.|

## <a name="remarks"></a>Osservazioni

Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

Questo esempio viene illustrato un `TableHeaders` elemento che definisce due intestazioni di colonna.

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

[Creazione di una visualizzazione tabella](./creating-a-table-view.md)

[Elemento TableColumnHeader (formato)](./tablecolumnheader-element-format.md)

[Elemento Table (formato)](./tablecontrol-element-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
