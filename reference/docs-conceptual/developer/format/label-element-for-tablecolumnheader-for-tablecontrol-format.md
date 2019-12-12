---
title: Elemento label per TableColumnHeader per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365170"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>Elemento Label per TableColumnHeader per TableControl (formato)

Definisce l'etichetta visualizzata nella parte superiore di una colonna. Questo elemento viene utilizzato quando si definisce una vista tabella.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableHeaders per Table ((Format) elemento TableColumnHeader per TableHeaders per l'elemento label Table ((Format) per TableColumnHeader per Table ((Format)

## <a name="syntax"></a>Sintassi

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Label`. È consentita una sola etichetta per ogni colonna.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableColumnHeader per TableHeaders per Table ((Format)](./tablecolumnheader-element-format.md)|Definisce un'etichetta, la larghezza e l'allineamento dei dati per una colonna della tabella.|

## <a name="text-value"></a>Valore testo

Consente di specificare il testo visualizzato nella parte superiore della colonna della tabella. Nessun carattere limitato per l'etichetta di colonna.

## <a name="remarks"></a>Osservazioni

Se non viene specificata alcuna etichetta, viene usato il nome della proprietà il cui valore viene visualizzato nelle righe.

Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

In questo esempio viene illustrato un elemento `TableColumnHeader` la cui etichetta è "Column 1".

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Vedere anche

[Creazione di una vista tabella](./creating-a-table-view.md)

[Elemento TableColumnHeader (Format)](./tablecolumnheader-element-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
