---
title: Elemento FirstLineHanging per il frame per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53694f08-57f7-4185-b443-1636a0918afc
caps.latest.revision: 8
ms.openlocfilehash: 387340cd9b0aae2ad0419b187d96ab4fee183d5a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363790"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-view-format"></a>Elemento FirstLineHanging per Frame per Controls per View (formato)

Specifica il numero di caratteri che la prima riga di dati viene spostata a sinistra. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per la visualizzazione (Format) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) CustomItem elemento per CustomEntry per i controlli per la visualizzazione (formato) elemento del frame per CustomItem per i controlli per la visualizzazione (formato) FirstLineHanging elemento di Frame di controlli della visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `FirstLineHanging`.

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

Se questo elemento è specificato, non è possibile specificare l'elemento [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) .

## <a name="see-also"></a>Vedere anche

[Elemento FirstLineIndent per il frame per i controlli per la visualizzazione (Format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[Elemento frame per CustomItem per i controlli per la visualizzazione (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
