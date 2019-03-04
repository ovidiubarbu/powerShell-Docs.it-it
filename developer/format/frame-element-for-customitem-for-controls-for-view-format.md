---
title: Elemento dei frame per CustomItem per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859817"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>Elemento Frame per CustomItem per Controls per View (formato)

Definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) CustomItem per CustomEntry per i controlli elemento di visualizzazione (formato) Frame per CustomItem per i controlli per la visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Frame` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|`CustomItem Element`|Elemento obbligatorio|
|[Elemento FirstLineHanging del Frame di controlli di visualizzazione (formato)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri nella prima riga viene spostata a sinistra.|
|[Elemento FirstLineIndent del Frame di controlli di visualizzazione (formato)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri nella prima riga viene spostata a destra.|
|[Elemento LeftIndent del Frame di controlli di visualizzazione (formato)](./leftindent-element-for-frame-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica quanti caratteri di dati viene spostati dal margine sinistro.|
|[Elemento RightIndent del Frame di controlli di visualizzazione (formato)](./rightindent-element-for-frame-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica quanti caratteri di dati viene spostati dal margine destro.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Definisce i dati che vengano visualizzati dal controllo e la modalità di visualizzazione.|

## <a name="remarks"></a>Osservazioni

Non è possibile specificare il [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) e il [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elementi nello stesso `Frame` elemento.

## <a name="see-also"></a>Vedere anche

[Elemento FirstLineHanging del Frame di controlli di visualizzazione (formato)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[Elemento FirstLineIndent del Frame di controlli di visualizzazione (formato)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[Elemento LeftIndent del Frame di controlli di visualizzazione (formato)](./leftindent-element-for-frame-for-controls-for-view-format.md)

[Elemento RightIndent del Frame di controlli di visualizzazione (formato)](./rightindent-element-for-frame-for-controls-for-view-format.md)

[Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
