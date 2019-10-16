---
title: Elemento FormatString per WideItem per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363030"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a>Elemento FormatString per WideItem per WideControl (formato)

Specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script nella visualizzazione.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry per WideControl (Format) elemento WideItem per WideControl (Format) elemento FormatString per WideItem per WideControl (Format)

## <a name="syntax"></a>Sintassi

```xml
<FormatString>PropertyPattern</FormatString>
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
|[Elemento WideItem per WideControl (Format)](./wideitem-element-for-widecontrol-format.md)|Definisce la proprietà o lo script il cui valore viene visualizzato in una riga della visualizzazione elenco.|

## <a name="text-value"></a>Valore di testo

Specificare il modello usato per formattare i dati. Ad esempio, è possibile usare questo modello per formattare il valore di qualsiasi proprietà di tipo [System. TimeSpan](/dotnet/api/System.TimeSpan): {0: mmm} {0: dd} {0: HH}: {0: mm}.

## <a name="remarks"></a>Osservazioni

Le stringhe di formato possono essere utilizzate durante la creazione di visualizzazioni di tabella, visualizzazioni di elenchi, visualizzazioni estese o visualizzazioni personalizzate. Per ulteriori informazioni sulla formattazione di un valore visualizzato in una visualizzazione, vedere [formattazione dei dati visualizzati](./formatting-displayed-data.md).

Per ulteriori informazioni sull'utilizzo di stringhe di formato in visualizzazioni estese, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della proprietà `StartTime`.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione estesa](./creating-a-wide-view.md)

[Elemento WideItem per WideControl (Format)](./wideitem-element-for-widecontrol-format.md)

[Scrittura di un file di formattazione e di tipi di Windows PowerShell](./writing-a-powershell-formatting-file.md)
