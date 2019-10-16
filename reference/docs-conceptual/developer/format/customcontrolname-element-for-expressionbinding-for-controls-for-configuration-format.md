---
title: Elemento CustomControlName per ExpressionName per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5242935-2782-4d23-84f5-2446b2b7ba83
caps.latest.revision: 8
ms.openlocfilehash: c9abd9f22907b87323c16d603a9f75bb3d375a03
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364120"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format"></a>Elemento CustomControlName per ExpressionBinding per Controls per Configuration (formato)

Specifica il nome di un controllo comune. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento CustomItem per CustomEntry per i controlli per l'elemento Expressionation di Configuration per CustomItem per i controlli per la configurazione (Format) CustomControlName Elemento per Expression per i controlli per la configurazione (Format)

## <a name="syntax"></a>Sintassi

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomControlName`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento expressiongroup per CustomItem per i controlli per la configurazione (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Definisce i dati visualizzati dal controllo.|

## <a name="text-value"></a>Valore di testo

Specificare il nome del controllo.

## <a name="remarks"></a>Osservazioni

È possibile creare controlli comuni che possono essere utilizzati da tutte le visualizzazioni di un file di formattazione ed è possibile creare controlli di visualizzazione che possono essere utilizzati da una visualizzazione specifica. Gli elementi seguenti specificano i nomi di questi controlli:

- [Elemento Name per il controllo per i controlli per la configurazione (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Elemento Name per il controllo per i controlli per la visualizzazione (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Vedere anche

[Elemento Name per il controllo per i controlli per la configurazione (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Elemento Name per il controllo per i controlli per la visualizzazione (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Elemento expressiongroup per CustomItem per i controlli per la configurazione (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
