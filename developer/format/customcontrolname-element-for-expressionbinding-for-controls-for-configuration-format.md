---
title: Elemento CustomControlName per ExpressionBinding per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5242935-2782-4d23-84f5-2446b2b7ba83
caps.latest.revision: 8
ms.openlocfilehash: c9abd9f22907b87323c16d603a9f75bb3d375a03
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856317"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format"></a>Elemento CustomControlName per ExpressionBinding per Controls per Configuration (formato)

Specifica il nome di un controllo comune. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli di configurazione (formato) CustomControl elemento per il controllo per elemento di configurazione (formato) CustomEntries per CustomControl per Configuration ( Elemento CustomEntry Format) per CustomControl per i controlli per Configuration (formato) CustomItem elemento CustomEntry per i controlli per configurazione ExpressionBinding elemento CustomItem per i controlli per CustomControlName Configuration (formato) Elemento per ExpressionBinding per i controlli per la configurazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomControlName` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ExpressionBinding per CustomItem per i controlli per la configurazione (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Definisce i dati che vengano visualizzati dal controllo.|

## <a name="text-value"></a>Valore di testo

Specificare il nome del controllo.

## <a name="remarks"></a>Osservazioni

È possibile creare controlli comuni che possono essere usati da tutte le visualizzazioni di un file di formattazione ed è possibile creare controlli di visualizzazione che possono essere usati da una visualizzazione specifica. Gli elementi seguenti specificano i nomi di questi controlli:

- [Elemento Name per il controllo per i controlli per la configurazione (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Elemento Name per il controllo per i controlli per la visualizzazione (formato)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Vedere anche

[Elemento Name per il controllo per i controlli per la configurazione (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

[Elemento Name per il controllo per i controlli per la visualizzazione (formato)](./name-element-for-control-for-controls-for-view-format.md)

[Elemento ExpressionBinding per CustomItem per i controlli per la configurazione (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
