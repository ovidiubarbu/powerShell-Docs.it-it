---
title: Elemento ScriptBlock per ItemSeclectionCondition per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51f7aec9-7b01-4370-84f4-1e58508a851f
caps.latest.revision: 6
ms.openlocfilehash: e92b2dfff07358132c480c47c34279e5365fe400
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064442"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a>Elemento ScriptBlock per ItemSelectionCondition per Controls per Configuration (formato)

Specifica lo script che genera la condizione. Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene utilizzato il controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli di configurazione (formato) CustomControl elemento per il controllo per elemento di configurazione (formato) CustomEntries per CustomControl per Configuration ( Elemento CustomEntry Format) per CustomControl per i controlli per elemento di configurazione (formato) CustomItem per CustomEntry per i controlli per configurazione ExpressionBinding elemento CustomItem per i controlli per la configurazione (formato) Elemento ItemSelectionCondition per ExpressionBinding per i controlli per elemento di configurazione (formato) ScriptBlock per ItemSelectionCondition per i controlli per la configurazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ScriptBlock` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ItemSelectionCondition per ExpressionBinding per i controlli per la configurazione (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Definisce la condizione che deve essere presente per questo controllo da utilizzare.|

## <a name="text-value"></a>Valore di testo

Specificare lo script che viene valutato.

## <a name="remarks"></a>Osservazioni

Se questo elemento viene usato, è possibile specificare il [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) elemento quando si definisce la condizione di selezione.

## <a name="see-also"></a>Vedere anche

[Elemento PropertyName per ItemSeclectionCondition per i controlli per la configurazione (formato)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Elemento ItemSelectionCondition per ExpressionBinding per i controlli per la configurazione (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
