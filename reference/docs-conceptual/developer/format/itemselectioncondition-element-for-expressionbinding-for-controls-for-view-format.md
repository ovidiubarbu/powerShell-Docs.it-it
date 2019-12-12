---
title: Elemento ItemSelectionCondition per Expressiongroup per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362940"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a>Elemento ItemSelectionCondition per ExpressionBinding per Controls per View (formato)

Definisce la condizione che deve esistere per il controllo da utilizzare. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per la visualizzazione (Format) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato) elemento Expressiongroup per CustomItem per i controlli per la visualizzazione (formato) Elemento ItemSelectionCondition di Expression per i controlli per la visualizzazione (Format)

## <a name="syntax"></a>Sintassi

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ItemSelectionCondition`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento PropertyName per ItemSelectionCondition per i controlli per la visualizzazione (Format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET che attiva la condizione.|
|[Elemento ScriptBlock per ItemSelectionCondition per i controlli per la visualizzazione (Format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script che attiva la condizione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento expressiongroup per CustomItem per i controlli per la visualizzazione (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Definisce i dati visualizzati dal controllo.|

## <a name="remarks"></a>Osservazioni

È possibile specificare un nome di proprietà o uno script per questa condizione, ma non è possibile specificarli entrambi.

## <a name="see-also"></a>Vedere anche

[Elemento PropertyName per ItemSelectionCondition per i controlli per la visualizzazione (Format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Elemento ScriptBlock per ItemSelectionCondition per i controlli per la visualizzazione (Format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Elemento expressiongroup per CustomItem per i controlli per la visualizzazione (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
