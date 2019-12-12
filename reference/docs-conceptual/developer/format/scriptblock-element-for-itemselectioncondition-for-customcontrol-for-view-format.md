---
title: Elemento ScriptBlock per ItemSelectionCondition per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362070"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>Elemento ScriptBlock per ItemSelectionCondition per CustomControl per View (formato)

Specifica lo script che attiva la condizione. Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzato il controllo. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per la vista (Format) CustomEntry elemento per CustomEntries per la visualizzazione (Format) CustomItem elemento per CustomEntry per la visualizzazione (formato) elemento Expressiongroup per CustomItem per CustomControl per la visualizzazione (Format) ItemSelectionCondition elemento per l'associazione di espressioni per CustomControl per la visualizzazione (formato) ScriptBlock elemento per ItemSelectionCondition per CustomControl per la visualizzazione (formato)

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
|[Elemento ItemSelectionCondition per l'associazione di espressioni per CustomControl per View (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Definisce la condizione che deve esistere per il controllo da utilizzare.|

## <a name="text-value"></a>Valore testo

Specificare lo script che viene valutato.

## <a name="remarks"></a>Osservazioni

Se viene usato questo elemento, non è possibile specificare l'elemento [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) quando si definisce la condizione di selezione.

## <a name="see-also"></a>Vedere anche

[Elemento PropertyName per ItemSelectionCondition per CustomControl per View (Format)](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[Elemento ItemSelectionCondition per l'associazione di espressioni per CustomControl per View (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
