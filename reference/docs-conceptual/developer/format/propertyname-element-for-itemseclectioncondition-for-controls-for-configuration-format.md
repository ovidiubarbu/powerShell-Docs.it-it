---
title: Elemento PropertyName per ItemSeclectionCondition per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8ab181-c559-492e-a0cf-299e381fdcc3
caps.latest.revision: 6
ms.openlocfilehash: ce25789bdfc2679372ca9e42f99dcc6a30ae2def
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362530"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a>Elemento PropertyName per ItemSelectionCondition per Controls per Configuration (formato)

Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene utilizzato il controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento CustomItem per CustomEntry per i controlli per l'elemento Expressionation di Configuration per CustomItem per i controlli per la configurazione (Format) Elemento ItemSelectionCondition per Expression per i controlli per la configurazione (Format) PropertyName per ItemSeclectionCondition per i controlli per la configurazione (Format)

## <a name="syntax"></a>Sintassi

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `PropertyName`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ItemSelectionCondition per ExpressionName per i controlli per la configurazione (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Definisce la condizione che deve esistere per il controllo da utilizzare.|

## <a name="text-value"></a>Valore di testo

Specificare il nome della proprietà .NET che attiva la condizione.

## <a name="remarks"></a>Osservazioni

Se viene usato questo elemento, non è possibile specificare l'elemento [scriptblock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) quando si definisce la condizione di selezione.

## <a name="see-also"></a>Vedere anche

[Elemento ScriptBlock per ItemSeclectionCondition per i controlli per la configurazione (Format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Elemento ItemSelectionCondition per ExpressionName per i controlli per la configurazione (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
