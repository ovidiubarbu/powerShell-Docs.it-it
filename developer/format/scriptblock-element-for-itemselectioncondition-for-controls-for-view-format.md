---
title: Elemento ScriptBlock per ItemSelectionCondition per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856737"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a>Elemento ScriptBlock per ItemSelectionCondition per Controls per View (formato)

Specifica lo script che genera la condizione. Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene utilizzato il controllo. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) CustomItem per CustomEntry per i controlli elemento di visualizzazione (formato) ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato) Elemento ItemSelectionCondition ExpressionBinding per i controlli elemento di visualizzazione (formato) ScriptBlock per ItemSelectionCondition per i controlli per la visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ScriptBlock` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ItemSelectionCondition ExpressionBinding per i controlli per la visualizzazione (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Definisce la condizione che deve essere presente per questo controllo da utilizzare.|

## <a name="text-value"></a>Valore di testo

Specificare lo script che viene valutato.

## <a name="remarks"></a>Osservazioni

Se questo elemento viene usato, è possibile specificare il [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) elemento quando si definisce la condizione di selezione.

## <a name="see-also"></a>Vedere anche

[Elemento PropertyName per ItemSelectionCondition per i controlli per la visualizzazione (formato)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Elemento ItemSelectionCondition ExpressionBinding per i controlli per la visualizzazione (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
