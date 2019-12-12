---
title: Elemento Width per TableColumnHeader per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367870"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>Elemento Width per TableColumnHeader per TableControl (formato)

Definisce la larghezza (in caratteri) di una colonna.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableHeaders per Table ((Format) TableColumnHeader elemento TableHeaders per Table ((Format) elemento Width per TableColumnHeader per Table ((Format)

## <a name="syntax"></a>Sintassi

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Width` usato durante la definizione delle intestazioni di colonna.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableColumnHeader per TableHeaders per Table ((Format)](./tablecolumnheader-element-format.md)|Definisce un'etichetta, la larghezza e l'allineamento dei dati per una colonna della tabella.|

## <a name="text-value"></a>Valore testo

Quando possibile, specificare una larghezza (in caratteri) maggiore della lunghezza dei valori delle proprietà visualizzate.

## <a name="remarks"></a>Osservazioni

Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un elemento `TableColumnHeader` la cui larghezza è 16 caratteri.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Vedere anche

[Creazione di una vista tabella](./creating-a-table-view.md)

[Elemento TableColumnHeader per TableHeader per Table ((Format)](./tablecolumnheader-element-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
