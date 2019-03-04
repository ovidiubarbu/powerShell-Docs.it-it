---
title: Nome elemento per il controllo per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860087"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a>Elemento Name per Control per Controls per Configuration (formato)

Specifica il nome del controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli per la configurazione (formato) elemento Name per il controllo per i controlli per la configurazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<Name>NameOfControl</Name>

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
|[Elemento di controllo per i controlli per la configurazione (formato)](./control-element-for-controls-for-configuration-format.md)|Definisce un controllo comune che può essere usato da tutte le visualizzazioni del file di formattazione e il nome utilizzato per fare riferimento al controllo.|

## <a name="text-value"></a>Valore di testo

Specificare il nome utilizzato per fare riferimento a questo controllo.

## <a name="remarks"></a>Osservazioni

Il nome specificato qui è utilizzabile negli elementi seguenti per fare riferimento a questo controllo.

- Quando si crea una tabella, elenco, visualizzazione controllo wide o personalizzato, il controllo può essere specificato dal seguente elemento: [Elemento GroupBy per visualizzazione (formato)](./groupby-element-for-view-format.md)

- Quando si crea un altro controllo comune, questo controllo può essere specificato per l'elemento seguente: [Elemento ExpressionBinding per CustomItem per i controlli per la configurazione (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- Quando la creazione di un controllo che può essere usata da una vista, questo controllo può essere specificato per l'elemento seguente: [Elemento ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Vedere anche

[Elemento di controllo per i controlli per la configurazione (formato)](./control-element-for-controls-for-configuration-format.md)

[Elemento ExpressionBinding per CustomItem per i controlli per la configurazione (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Elemento GroupBy per visualizzazione (formato)](./groupby-element-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
