---
title: Elemento FormatString per TableColumnItem per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363710"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a>Elemento FormatString per TableColumnItem per TableControl (formato)

Specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script della tabella.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) elemento TableColumnItems (Format) elemento TableColumnItem (Format) Elemento FormatString per TableColumnItem (Format)

## <a name="syntax"></a>Sintassi

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `FormatString`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableColumnItem (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Definisce la proprietà o lo script il cui valore viene visualizzato nella colonna della riga.|

## <a name="text-value"></a>Valore testo

Specificare il modello usato per formattare i dati. Questo modello, ad esempio, può essere utilizzato per formattare il valore di qualsiasi proprietà di tipo [System. TimeSpan](/dotnet/api/System.TimeSpan): {0: mmm} {0: dd} {0: HH}: {0: mm}.

## <a name="remarks"></a>Osservazioni

Le stringhe di formato possono essere utilizzate durante la creazione di visualizzazioni di tabella, visualizzazioni di elenchi, visualizzazioni estese o visualizzazioni personalizzate. Per ulteriori informazioni sulla formattazione di un valore visualizzato in una visualizzazione, vedere [formattazione dei dati visualizzati](./formatting-displayed-data.md).

Per ulteriori informazioni sui componenti di una vista tabella, vedere [visualizzazione tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della proprietà `StartTime`.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a>Vedere anche

[Creazione di una vista tabella](./creating-a-table-view.md)

[Formattazione dei dati visualizzati](./formatting-displayed-data.md)

[Elemento TableColumnItem (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
