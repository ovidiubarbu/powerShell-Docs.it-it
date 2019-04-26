---
title: Elemento PropertyName per ItemSelectionCondition per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075852"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a>Elemento PropertyName per ItemSelectionCondition per Controls per View (formato)

Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene utilizzato il controllo. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) CustomItem per CustomEntry per i controlli elemento di visualizzazione (formato) ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato) Elemento ItemSelectionCondition ExpressionBinding per i controlli elemento di visualizzazione (formato) PropertyName per ItemSelectionCondition per i controlli per la visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `PropertyName` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ItemSelectionCondition ExpressionBinding per i controlli per la visualizzazione (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Definisce la condizione che deve essere presente per questo controllo da utilizzare.|

## <a name="text-value"></a>Valore di testo

Specificare il nome della proprietà .NET che attiva la condizione.

## <a name="remarks"></a>Osservazioni

Se questo elemento viene usato, è possibile specificare il [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) elemento quando si definisce la condizione di selezione.

## <a name="see-also"></a>Vedere anche

[Elemento ScriptBlock per ItemSelectionCondition per i controlli per la visualizzazione (formato)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Elemento ItemSelectionCondition ExpressionBinding per i controlli per la visualizzazione (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
