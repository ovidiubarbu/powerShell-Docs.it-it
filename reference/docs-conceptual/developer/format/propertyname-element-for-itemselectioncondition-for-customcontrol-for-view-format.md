---
title: Elemento PropertyName per ItemSelectionCondition per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362440"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>Elemento PropertyName per ItemSelectionCondition per CustomControl per View (formato)

Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene utilizzato il controllo. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per la vista (Format) CustomEntry elemento per CustomEntries per la visualizzazione (Format) CustomItem elemento per CustomEntry per la visualizzazione (formato) elemento Expressiongroup per CustomItem per CustomControl per la visualizzazione (Format) ItemSelectionCondition elemento per l'associazione di espressioni per CustomControl per la visualizzazione (Format) PropertyName elemento per ItemSelectionCondition per CustomControl per la visualizzazione (formato

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
|[Elemento ItemSelectionCondition per l'associazione di espressioni per CustomControl per View (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Definisce la condizione che deve esistere per il controllo da utilizzare.|

## <a name="text-value"></a>Valore testo

Specificare il nome della proprietà .NET che attiva la condizione.

## <a name="remarks"></a>Osservazioni

Se viene usato questo elemento, non è possibile specificare l'elemento [scriptblock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) quando si definisce la condizione di selezione.

## <a name="see-also"></a>Vedere anche

[Elemento ScriptBlock per ItemSelectionCondition per CustomControl per View (Format)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[Elemento ItemSelectionCondition per l'associazione di espressioni per CustomControl per View (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
