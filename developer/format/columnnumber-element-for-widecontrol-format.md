---
title: Elemento ColumnNumber per WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856227"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>Elemento ColumnNumber per WideControl (formato)

Specifica il numero di colonne visualizzate in visualizzazione estesa.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) ColumnNumber elemento di configurazione per WideControl (formato)

## <a name="syntax"></a>Sintassi

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ColumnNumber` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento WideControl (formato)](./widecontrol-element-format.md)|Definisce un'ampia (valore singolo) formato di elenco per la visualizzazione.|

## <a name="text-value"></a>Valore di testo

Specificare un valore intero positivo.

## <a name="remarks"></a>Osservazioni

Quando si definisce una visualizzazione più ampia, è possibile aggiungere il `AutoSize` elemento o `ColumnNumber` elemento, ma è possibile aggiungere entrambi.

Per altre informazioni sui componenti di una visualizzazione più ampia, vedere [creazione di una visualizzazione più ampia](./creating-a-wide-view.md).

Per un esempio di una visualizzazione più ampia, vedere [visualizzazione più ampia (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Vedere anche

[AutoSize (elemento) per WideControl (formato)](./autosize-element-for-widecontrol-format.md)

[Creazione di una visualizzazione più ampia](./creating-a-wide-view.md)

[Visualizzazione più ampia (Basic)](./wide-view-basic.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
