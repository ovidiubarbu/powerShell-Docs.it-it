---
title: Elemento CustomControlName per Expressiongroup per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369150"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a>Elemento CustomControlName per ExpressionBinding per Controls per View (formato)

Specifica il nome di un controllo comune o di un controllo di visualizzazione. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per la visualizzazione (Format) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato) elemento Expressiongroup per CustomItem per i controlli per la visualizzazione (Format) CustomControlName Elemento per ExpressionBindine per i controlli per la visualizzazione (Format)

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
|[Elemento expressiongroup per CustomItem per i controlli per la visualizzazione (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Definisce i dati visualizzati dal controllo.|

## <a name="text-value"></a>Valore testo

Specificare il nome del controllo.

## <a name="remarks"></a>Osservazioni

È possibile creare controlli comuni che possono essere utilizzati da tutte le visualizzazioni di un file di formattazione ed è possibile creare controlli di visualizzazione che possono essere utilizzati da una visualizzazione specifica. Gli elementi seguenti specificano i nomi di questi controlli:

- [Elemento Name per il controllo per i controlli per la configurazione (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Elemento Name per il controllo per i controlli per la visualizzazione (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Vedere anche

[Elemento Name per il controllo per i controlli per la configurazione (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Elemento Name per il controllo per i controlli per la visualizzazione (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Elemento expressiongroup per CustomItem per i controlli per la visualizzazione (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
