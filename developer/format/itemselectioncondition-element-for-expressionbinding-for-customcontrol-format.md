---
title: Elemento ItemSelectionCondition per ExpressionBinding per CustomControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065825"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a>Elemento ItemSelectionCondition per ExpressionBinding per CustomControl (formato)

Definisce la condizione che deve essere presente per questo controllo da utilizzare. Non sono previsti limiti al numero di condizioni di selezione che possono essere specificati per un elemento del controllo. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per elemento CustomItem visualizzazione (formato) CustomEntry elemento di visualizzazione (formato) ExpressionBinding per CustomItem per CustomControl elemento di visualizzazione (formato) ItemSelectionCondition per associazione di espressioni per CustomControl per visualizzazione (formato)

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
|[Elemento PropertyName per ItemSelectionCondition per CustomControl per visualizzazione (formato](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET che attiva la condizione.|
|[Elemento ScriptBlock per ItemSelectionCondition per CustomControl per visualizzazione (formato)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script che genera la condizione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ExpressionBinding per CustomItem per CustomControl per visualizzazione (formato)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Definisce i dati che vengano visualizzati dal controllo.|

## <a name="remarks"></a>Osservazioni

È possibile specificare un nome di proprietà o uno script per questa condizione, ma non è possibile specificare entrambi.

## <a name="see-also"></a>Vedere anche

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)

[Elemento ExpressionBinding per CustomItem per CustomControl per visualizzazione (formato)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
