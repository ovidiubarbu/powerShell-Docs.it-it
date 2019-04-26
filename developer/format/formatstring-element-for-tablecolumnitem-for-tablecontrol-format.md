---
title: Elemento FormatString per TableColumnItem per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065632"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a>Elemento FormatString per TableColumnItem per TableControl (formato)

Specifica un modello di formato che definisce come viene visualizzato il valore di proprietà o lo script della tabella.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) elemento TableColumnItems (formato) TableColumnItem elemento di configurazione (formato) Elemento FormatString per TableColumnItem (formato)

## <a name="syntax"></a>Sintassi

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `FormatString` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableColumnItem (formato)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Definisce le proprietà il cui valore viene visualizzato nella colonna della riga di script.|

## <a name="text-value"></a>Valore di testo

Specificare il modello utilizzato per formattare i dati. Ad esempio, questo modello è utilizzabile per formattare il valore di qualsiasi proprietà che è di tipo [System. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {{0:hh}: {0:mm}.

## <a name="remarks"></a>Osservazioni

Stringhe di formato possono essere usate durante la creazione di viste delle tabelle, elencare le visualizzazioni, visualizzazioni ampie o visualizzazioni personalizzate. Per altre informazioni sulla formattazione di un valore visualizzato in una vista, vedere [formattazione dei dati visualizzati](./formatting-displayed-data.md).

Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [vista tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della `StartTime` proprietà.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione tabella](./creating-a-table-view.md)

[Formattazione dei dati visualizzati](./formatting-displayed-data.md)

[Elemento TableColumnItem (formato)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
