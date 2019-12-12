---
title: Elemento ScriptBlock per ItemSelectionCondition per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364920"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a>Elemento ScriptBlock per ItemSelectionCondition per Controls per View (formato)

Specifica lo script che attiva la condizione. Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzato il controllo. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per la visualizzazione (Format) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato) elemento Expressiongroup per CustomItem per i controlli per la visualizzazione (formato) Elemento ItemSelectionCondition di Expression per i controlli per la visualizzazione (Format) elemento ScriptBlock per ItemSelectionCondition per i controlli per la visualizzazione (Format)

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
|[Elemento ItemSelectionCondition di Expression per i controlli per la visualizzazione (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Definisce la condizione che deve esistere per il controllo da utilizzare.|

## <a name="text-value"></a>Valore testo

Specificare lo script che viene valutato.

## <a name="remarks"></a>Osservazioni

Se viene usato questo elemento, non è possibile specificare l'elemento [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) quando si definisce la condizione di selezione.

## <a name="see-also"></a>Vedere anche

[Elemento PropertyName per ItemSelectionCondition per i controlli per la visualizzazione (Format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Elemento ItemSelectionCondition di Expression per i controlli per la visualizzazione (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
