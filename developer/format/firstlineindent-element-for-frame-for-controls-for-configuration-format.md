---
title: Elemento FirstLineIndent per Frame per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f489720-11f6-4019-940e-07f423d4278d
caps.latest.revision: 6
ms.openlocfilehash: c5b2d971fe1590116f96b024ae8769334768acf2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856347"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-configuration-format"></a>Elemento FirstLineIndent per Frame per Controls per Configuration (formato)

Specifica il numero di caratteri la prima riga di dati verrà spostata a destra. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli di configurazione (formato) CustomControl elemento per il controllo per elemento di configurazione (formato) CustomEntries per CustomControl per Configuration ( Elemento CustomEntry Format) per CustomControl per i controlli per elemento di configurazione (formato) CustomItem per CustomEntry per i controlli per la configurazione elemento Frame per CustomItem per i controlli per elemento di configurazione (formato) FirstLineIndent per Frame per i controlli per la configurazione (formato)

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
|[Elemento frame per CustomItem per i controlli per la configurazione (formato)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra.|

## <a name="text-value"></a>Valore di testo

Specificare il numero di caratteri che si desidera spostare la prima riga dei dati.

## <a name="remarks"></a>Osservazioni

Se questo elemento viene specificato, non è possibile specificare il [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) elemento.

## <a name="see-also"></a>Vedere anche

[Elemento FirstLineHanging per Frame per i controlli per la configurazione (formato)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[Elemento frame per CustomItem per i controlli per la configurazione (formato)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
