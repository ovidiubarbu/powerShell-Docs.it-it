---
title: Elemento ExpressionBinding per CustomItem per CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065921"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>Elemento ExpressionBinding per CustomItem per CustomControl per View (formato)

Definisce i dati che vengano visualizzati dal controllo. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

Elemento di CustomControl elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) elemento di visualizzazione (formato) CustomEntries per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per CustomControl per visualizzazione ( Elemento CustomItem Format) per CustomEntry per CustomControl elemento di visualizzazione (formato) ExpressionBinding per CustomItem per CustomControl per visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ExpressionBinding` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|`CustomControl Element`|Elemento facoltativo.<br /><br /> Definisce un controllo che viene utilizzato da questo controllo.|
|[Elemento CustomControlName per ExpressionBinding per CustomControl per visualizzazione (formato)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica il nome di un controllo comune o un controllo di visualizzazione.|
|[Elemento EnumerateCollection per ExpressionBinding per CustomControl per visualizzazione (formato)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specificare che vengano visualizzati gli elementi delle raccolte.|
|[Elemento ItemSelectionCondition per ExpressionBinding per CustomControl per visualizzazione (formato)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve essere presente per questo controllo da utilizzare.|
|[Elemento PropertyName per ExpressionBinding per CustomControl per visualizzazione (formato)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET il cui valore viene visualizzato dal controllo.|
|[Elemento ScriptBlock per ExpressionBinding per CustomCustomControl per visualizzazione (formato)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script il cui valore viene visualizzato dal controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomItem per CustomEntry per CustomControl per visualizzazione (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Definisce i dati visualizzati dalla visualizzazione del controllo personalizzato e modalità di visualizzazione.|

## <a name="remarks"></a>Osservazioni

## <a name="see-also"></a>Vedere anche

[Elemento CustomControlName per ExpressionBinding per CustomControl per visualizzazione (formato)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento EnumerateCollection per ExpressionBinding per CustomControl per visualizzazione (formato)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento ItemSelectionCondition per ExpressionBinding per CustomControl per visualizzazione (formato)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Elemento PropertyName per ExpressionBinding per CustomControl per visualizzazione (formato)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento ScriptBlock per ExpressionBinding per CustomControl per visualizzazione (formato)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento CustomItem per CustomEntry per CustomControl per visualizzazione (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
