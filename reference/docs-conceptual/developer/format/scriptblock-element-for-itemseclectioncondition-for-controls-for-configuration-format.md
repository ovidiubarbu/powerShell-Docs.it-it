---
title: Elemento ScriptBlock per ItemSeclectionCondition per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51f7aec9-7b01-4370-84f4-1e58508a851f
caps.latest.revision: 6
ms.openlocfilehash: e92b2dfff07358132c480c47c34279e5365fe400
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362120"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a>Elemento ScriptBlock per ItemSelectionCondition per Controls per Configuration (formato)

Specifica lo script che attiva la condizione. Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzato il controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento CustomItem per CustomEntry per i controlli per l'elemento Expressionation di Configuration per CustomItem per i controlli per la configurazione (Format) Elemento ItemSelectionCondition per Expression per i controlli per la configurazione (Format) elemento ScriptBlock per ItemSelectionCondition per i controlli per la configurazione (Format)

## <a name="syntax"></a>Sintassi

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ScriptBlock`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ItemSelectionCondition per ExpressionName per i controlli per la configurazione (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Definisce la condizione che deve esistere per il controllo da utilizzare.|

## <a name="text-value"></a>Valore testo

Specificare lo script che viene valutato.

## <a name="remarks"></a>Osservazioni

Se viene usato questo elemento, non è possibile specificare l'elemento [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) quando si definisce la condizione di selezione.

## <a name="see-also"></a>Vedere anche

[Elemento PropertyName per ItemSeclectionCondition per i controlli per la configurazione (Format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Elemento ItemSelectionCondition per ExpressionName per i controlli per la configurazione (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
