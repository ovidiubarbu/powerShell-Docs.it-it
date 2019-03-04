---
title: Nome elemento per il controllo per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862387"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a>Elemento Name per Control per Controls per View (formato)

Specifica il nome del controllo.

Elemento (formato) elemento ViewDefinitions (formato) Visualizza elemento di configurazione (formato) controlla controllo elemento (formato) per i controlli elemento di visualizzazione (formato) nome per il controllo per la visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Name` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento di controllo per i controlli per la visualizzazione (formato)](./control-element-for-controls-for-view-format.md)|Definisce un controllo che può essere utilizzato per la visualizzazione e il nome utilizzato per fare riferimento al controllo.|

## <a name="text-value"></a>Valore di testo

Specificare il nome utilizzato per fare riferimento al controllo.

## <a name="remarks"></a>Osservazioni

Il nome specificato qui è utilizzabile negli elementi seguenti per fare riferimento a questo controllo.

- Quando si crea una tabella, elenco, visualizzazione controllo wide o personalizzato, il controllo può essere specificato dal seguente elemento: [Elemento GroupBy per visualizzazione (formato)](./groupby-element-for-view-format.md)

- Quando la creazione di un altro controllo che può essere usata da una vista, questo controllo può essere specificato per l'elemento seguente: [Elemento ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Vedere anche

[Elemento GroupBy per visualizzazione (formato)](./groupby-element-for-view-format.md)

[Elemento ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Elemento di controllo per i controlli per la visualizzazione (formato)](./control-element-for-controls-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
