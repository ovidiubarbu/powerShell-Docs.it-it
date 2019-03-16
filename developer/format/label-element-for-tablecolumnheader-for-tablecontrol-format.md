---
title: L'etichetta di elemento per TableColumnHeader per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054510"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>Elemento Label per TableColumnHeader per TableControl (formato)

Definisce l'etichetta che viene visualizzato nella parte superiore di una colonna. Questo elemento viene usato quando si definisce una visualizzazione tabella.

Configurazione elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) TableHeaders elemento per elemento TableColumnHeader Table (formato) per TableHeaders per elemento etichetta Table (formato) TableColumnHeader per Table (formato)

## <a name="syntax"></a>Sintassi

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Label` elemento. È consentita solo un'etichetta per ogni colonna.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableColumnHeader per TableHeaders per Table (formato)](./tablecolumnheader-element-format.md)|Definisce un'etichetta, la larghezza e l'allineamento dei dati per una colonna della tabella.|

## <a name="text-value"></a>Valore di testo

Specificare il testo visualizzato nella parte superiore della colonna della tabella. Non sono presenti caratteri limitati per l'etichetta di colonna.

## <a name="remarks"></a>Osservazioni

Se viene specificata alcuna etichetta, viene utilizzato il nome della proprietà il cui valore viene visualizzato nelle righe.

Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

Questo esempio viene illustrato un `TableColumnHeader` elemento la cui etichetta è "Column 1".

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione tabella](./creating-a-table-view.md)

[Elemento TableColumnHeader (formato)](./tablecolumnheader-element-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
