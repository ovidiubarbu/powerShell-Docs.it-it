---
title: Elemento Name per il controllo per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365100"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a>Elemento Name per Control per Controls per View (formato)

Specifica il nome del controllo.

Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento nome per il controllo per visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<Name>ControlName</Name>
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
|[Elemento Control per Controls per View (Format)](./control-element-for-controls-for-view-format.md)|Definisce un controllo che può essere utilizzato dalla visualizzazione e dal nome utilizzato per fare riferimento al controllo.|

## <a name="text-value"></a>Valore di testo

Specificare il nome utilizzato per fare riferimento al controllo.

## <a name="remarks"></a>Osservazioni

Il nome specificato qui può essere usato negli elementi seguenti per fare riferimento a questo controllo.

- Quando si crea una tabella, un elenco, una visualizzazione di controlli di tipo Wide o Custom, il controllo può essere specificato dall'elemento [GroupBy per View (Format)](./groupby-element-for-view-format.md) .

- Quando si crea un altro controllo che può essere usato da una vista, questo controllo può essere specificato dal seguente elemento: [espressione di espressione per CustomItem per i controlli per la visualizzazione (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Vedere anche

[Elemento GroupBy per View (Format)](./groupby-element-for-view-format.md)

[Elemento expressiongroup per CustomItem per i controlli per la visualizzazione (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Elemento Control per Controls per View (Format)](./control-element-for-controls-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
