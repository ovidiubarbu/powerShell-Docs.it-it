---
title: Elemento ColumnNumber per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364220"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>Elemento ColumnNumber per WideControl (formato)

Specifica il numero di colonne visualizzate nella visualizzazione estesa.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento ColumnNumber per WideControl (Format)

## <a name="syntax"></a>Sintassi

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ColumnNumber`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento WideControl (Format)](./widecontrol-element-format.md)|Definisce un formato di elenco Wide (valore singolo) per la visualizzazione.|

## <a name="text-value"></a>Valore testo

Specificare un valore intero positivo.

## <a name="remarks"></a>Osservazioni

Quando si definisce una visualizzazione estesa, è possibile aggiungere l'elemento `AutoSize` o l'elemento `ColumnNumber`, ma non è possibile aggiungere entrambi.

Per ulteriori informazioni sui componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).

Per un esempio di visualizzazione estesa, vedere [Wide View (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Vedere anche

[Elemento AutoSize per WideControl (Format)](./autosize-element-for-widecontrol-format.md)

[Creazione di una visualizzazione estesa](./creating-a-wide-view.md)

[Visualizzazione estesa (di base)](./wide-view-basic.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
