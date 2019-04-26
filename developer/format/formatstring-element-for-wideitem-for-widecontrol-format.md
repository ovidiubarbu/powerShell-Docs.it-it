---
title: Elemento FormatString per WideItem per WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065683"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a>Elemento FormatString per WideItem per WideControl (formato)

Specifica un modello di formato che definisce come viene visualizzato il valore di proprietà o lo script nella visualizzazione.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) WideEntry elemento di configurazione per WideControl (formato) WideItem elemento per elemento FormatString WideControl (formato) per WideItem per WideControl (formato)

## <a name="syntax"></a>Sintassi

```xml
<FormatString>PropertyPattern</FormatString>
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
|[Elemento WideItem per WideControl (formato)](./wideitem-element-for-widecontrol-format.md)|Definisce proprietà o script il cui valore viene visualizzato in una riga della visualizzazione elenco.|

## <a name="text-value"></a>Valore di testo

Specificare il modello utilizzato per formattare i dati. Ad esempio, è possibile usare questo modello per formattare il valore di qualsiasi proprietà che è di tipo [System. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {{0:hh}: {0:mm}.

## <a name="remarks"></a>Osservazioni

Stringhe di formato possono essere usate durante la creazione di viste delle tabelle, elencare le visualizzazioni, visualizzazioni ampie o visualizzazioni personalizzate. Per altre informazioni sulla formattazione di un valore visualizzato in una vista, vedere [formattazione dei dati visualizzati](./formatting-displayed-data.md).

Per altre informazioni sull'uso di stringhe di formato in visualizzazioni ampie, vedere [creazione di una visualizzazione più ampia](./creating-a-wide-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della `StartTime` proprietà.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione più ampia](./creating-a-wide-view.md)

[Elemento WideItem per WideControl (formato)](./wideitem-element-for-widecontrol-format.md)

[La scrittura di un metodo di formattazione di Windows PowerShell e i tipi di File](./writing-a-powershell-formatting-file.md)
