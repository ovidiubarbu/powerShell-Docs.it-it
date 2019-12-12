---
title: Elemento PropertyName per ItemSelectionCondition per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362480"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a>Elemento PropertyName per ItemSelectionCondition per Controls per View (formato)

Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene utilizzato il controllo. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per la visualizzazione (Format) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato) elemento Expressiongroup per CustomItem per i controlli per la visualizzazione (formato) Elemento ItemSelectionCondition di Expression per i controlli per la visualizzazione (Format) PropertyName per ItemSelectionCondition per i controlli per la visualizzazione (Format)

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
|[Elemento ItemSelectionCondition di Expression per i controlli per la visualizzazione (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Definisce la condizione che deve esistere per il controllo da utilizzare.|

## <a name="text-value"></a>Valore testo

Specificare il nome della proprietà .NET che attiva la condizione.

## <a name="remarks"></a>Osservazioni

Se viene usato questo elemento, non è possibile specificare l'elemento [scriptblock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) quando si definisce la condizione di selezione.

## <a name="see-also"></a>Vedere anche

[Elemento ScriptBlock per ItemSelectionCondition per i controlli per la visualizzazione (Format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Elemento ItemSelectionCondition di Expression per i controlli per la visualizzazione (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
