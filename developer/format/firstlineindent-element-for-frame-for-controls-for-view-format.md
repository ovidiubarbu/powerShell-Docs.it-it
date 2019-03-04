---
title: Elemento FirstLineIndent per Frame per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec63f4f9-8858-4529-8646-ffbbc278f83e
caps.latest.revision: 7
ms.openlocfilehash: 694c5baaa5e90a772257276ba139d90acf7ec0e3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854317"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-view-format"></a>Elemento FirstLineIndent per Frame per Controls per View (formato)

Specifica il numero di caratteri la prima riga di dati verrà spostata a destra. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) CustomItem per CustomEntry per i controlli elemento di visualizzazione (formato) Frame per CustomItem per i controlli elemento di visualizzazione (formato) FirstLineIndent del Frame controlli della visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono l'elemento padre di attributi e gli elementi figlio di `FirstLineIndent` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento frame per CustomItem per i controlli per la visualizzazione (formato)](./frame-element-for-customitem-for-controls-for-view-format.md)|Definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra.|

## <a name="text-value"></a>Valore di testo

Specificare il numero di caratteri che si desidera spostare la prima riga dei dati.

## <a name="remarks"></a>Osservazioni

Se questo elemento viene specificato, non è possibile specificare il [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) elemento.

## <a name="see-also"></a>Vedere anche

[Elemento FirstLineHanging per Frame per i controlli per la visualizzazione (formato)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[Elemento frame per CustomItem per i controlli per la visualizzazione (formato)](./frame-element-for-customitem-for-controls-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)