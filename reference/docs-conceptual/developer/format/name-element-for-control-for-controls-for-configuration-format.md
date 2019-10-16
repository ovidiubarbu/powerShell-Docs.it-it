---
title: Elemento Name per il controllo per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362710"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a>Elemento Name per Control per Controls per Configuration (formato)

Specifica il nome del controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento Name per il controllo per i controlli per la configurazione (Format)

## <a name="syntax"></a>Sintassi

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Name`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento Control per Controls per Configuration (Format)](./control-element-for-controls-for-configuration-format.md)|Definisce un controllo comune che può essere utilizzato da tutte le visualizzazioni del file di formattazione e dal nome utilizzato per fare riferimento al controllo.|

## <a name="text-value"></a>Valore di testo

Specificare il nome utilizzato per fare riferimento a questo controllo.

## <a name="remarks"></a>Osservazioni

Il nome specificato qui può essere usato negli elementi seguenti per fare riferimento a questo controllo.

- Quando si crea una tabella, un elenco, una visualizzazione di controlli di tipo Wide o Custom, il controllo può essere specificato dall'elemento [GroupBy per View (Format)](./groupby-element-for-view-format.md) .

- Quando si crea un altro controllo comune, questo controllo può essere specificato dall'elemento seguente: [elemento expressiongroup per CustomItem per i controlli per la configurazione (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- Quando si crea un controllo che può essere utilizzato da una vista, questo controllo può essere specificato dall'elemento di [espressione per CustomItem per i controlli per la visualizzazione (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md) .

## <a name="see-also"></a>Vedere anche

[Elemento Control per Controls per Configuration (Format)](./control-element-for-controls-for-configuration-format.md)

[Elemento expressiongroup per CustomItem per i controlli per la configurazione (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento expressiongroup per CustomItem per i controlli per la visualizzazione (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Elemento GroupBy per View (Format)](./groupby-element-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
