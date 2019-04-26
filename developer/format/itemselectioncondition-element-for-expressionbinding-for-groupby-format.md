---
title: Elemento ItemSelectionCondition per ExpressionBinding per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065462"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a>Elemento ItemSelectionCondition per ExpressionBinding per GroupBy (formato)

Definisce la condizione che deve essere presente per questo controllo da utilizzare. Non sono previsti limiti al numero di condizioni di selezione che possono essere specificati per un elemento del controllo. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per elemento CustomItem GroupBy (formato) per CustomEntry per elemento ExpressionBinding GroupBy (formato) per CustomItem per elemento ItemSelectionCondition GroupBy (formato) per ExpressionBinding per GroupBy (formato)

## <a name="syntax"></a>Sintassi

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ItemSelectionCondition` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento PropertyName per ItemSelectionCondition per GroupBy (formato)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET che attiva la condizione.|
|[Elemento ScriptBlock per ItemSelectionCondition per GroupBy (formato)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script che genera la condizione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ExpressionBinding per CustomItem per GroupBy (formato)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Definisce i dati che vengano visualizzati dal controllo.|

## <a name="remarks"></a>Osservazioni

È possibile specificare un nome di proprietà o uno script per questa condizione, ma non è possibile specificare entrambi.

## <a name="see-also"></a>Vedere anche

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)

[Elemento ExpressionBinding per CustomItem per GroupBy (formato)](./expressionbinding-element-for-customitem-for-groupby-format.md)
