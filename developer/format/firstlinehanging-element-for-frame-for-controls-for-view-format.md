---
title: Elemento FirstLineHanging per Frame per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53694f08-57f7-4185-b443-1636a0918afc
caps.latest.revision: 8
ms.openlocfilehash: 387340cd9b0aae2ad0419b187d96ab4fee183d5a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065804"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-view-format"></a>Elemento FirstLineHanging per Frame per Controls per View (formato)

Specifica il numero di caratteri la prima riga di dati verrà spostata a sinistra. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per Elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) CustomItem per CustomEntry per i controlli elemento di visualizzazione (formato) Frame per CustomItem per i controlli elemento di visualizzazione (formato) FirstLineHanging di CustomControl Frame di controlli di visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono l'elemento padre di attributi e gli elementi figlio di `FirstLineHanging` elemento.

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

Se questo elemento viene specificato, non è possibile specificare il [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elemento.

## <a name="see-also"></a>Vedere anche

[Elemento FirstLineIndent per Frame per i controlli per la visualizzazione (formato)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[Elemento frame per CustomItem per i controlli per la visualizzazione (formato)](./frame-element-for-customitem-for-controls-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
