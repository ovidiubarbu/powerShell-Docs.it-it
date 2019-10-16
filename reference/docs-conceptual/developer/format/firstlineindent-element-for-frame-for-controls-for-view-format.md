---
title: Elemento FirstLineIndent per il frame per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec63f4f9-8858-4529-8646-ffbbc278f83e
caps.latest.revision: 7
ms.openlocfilehash: 694c5baaa5e90a772257276ba139d90acf7ec0e3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363090"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-view-format"></a>Elemento FirstLineIndent per Frame per Controls per View (formato)

Specifica il numero di caratteri che la prima riga di dati viene spostata a destra. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per la visualizzazione (Format) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) CustomItem elemento per CustomEntry per i controlli per la visualizzazione (formato) elemento del frame per CustomItem per i controlli per la visualizzazione (formato) FirstLineIndent elemento del frame dei controlli di visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `FirstLineIndent`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento frame per CustomItem per i controlli per la visualizzazione (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)|Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra.|

## <a name="text-value"></a>Valore di testo

Consente di specificare il numero di caratteri che si desidera spostare nella prima riga dei dati.

## <a name="remarks"></a>Osservazioni

Se questo elemento è specificato, non è possibile specificare l'elemento [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) .

## <a name="see-also"></a>Vedere anche

[Elemento FirstLineHanging per il frame per i controlli per la visualizzazione (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[Elemento frame per CustomItem per i controlli per la visualizzazione (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
