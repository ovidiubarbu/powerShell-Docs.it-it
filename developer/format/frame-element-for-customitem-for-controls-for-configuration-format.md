---
title: Elemento dei frame per CustomItem per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862977"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>Elemento Frame per CustomItem per Controls per Configuration (formato)

Definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli di configurazione (formato) CustomControl elemento per il controllo per elemento di configurazione (formato) CustomEntries per CustomControl per Configuration ( Elemento CustomEntry Format) per CustomControl per i controlli per elemento di configurazione (formato) CustomItem per CustomEntry per i controlli per la configurazione elemento Frame per CustomItem per i controlli per la configurazione (formato)

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
|[Elemento FirstLineHanging per Frame per i controlli per la configurazione (formato)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri la prima riga di dati verrà spostata a sinistra.|
|[Elemento FirstLineIndent per Frame per i controlli per la configurazione (formato)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri la prima riga di dati verrà spostata a destra.|
|[Elemento LeftIndent per Frame per i controlli per la configurazione (formato)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica quanti caratteri di dati viene spostati dal margine sinistro.|
|[Elemento RightIndent per Frame per i controlli per la configurazione (formato)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica quanti caratteri di dati viene spostati dal margine destro.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomItem per CustomEntry per i controlli per la configurazione](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Definisce i dati che vengano visualizzati dal controllo e la modalità di visualizzazione.|

## <a name="remarks"></a>Osservazioni

Non è possibile specificare il [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) e il [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elementi nello stesso `Frame` elemento.

## <a name="see-also"></a>Vedere anche

[Elemento FirstLineHanging per Frame per i controlli per la configurazione (formato)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[Elemento FirstLineIndent per Frame per i controlli per la configurazione (formato)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[Elemento LeftIndent per Frame per i controlli per la configurazione (formato)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[Elemento RightIndent per Frame per i controlli per la configurazione (formato)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[Elemento CustomItem per CustomEntry per i controlli per la configurazione](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
