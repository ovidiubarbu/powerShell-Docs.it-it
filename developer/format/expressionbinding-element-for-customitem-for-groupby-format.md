---
title: Elemento ExpressionBinding per CustomItem per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854927"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>Elemento ExpressionBinding per CustomItem per GroupBy (formato)

Definisce i dati che vengano visualizzati dal controllo. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per elemento CustomItem GroupBy (formato) per CustomEntry per elemento ExpressionBinding GroupBy (formato) per CustomItem per GroupBy (formato)

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

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ExpressionBinding` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|`CustomControl Element`|Elemento facoltativo.<br /><br /> Definisce un controllo che viene utilizzato da questo controllo.|
|[Elemento CustomControlName per ExpressionBinding per GroupBy (formato)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica il nome di un controllo comune o un controllo di visualizzazione.|
|[Elemento EnumerateCollection per ExpressionBinding per GroupBy (formato)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)elemento EnumerateCollection per ExpressionBinding per GroupBy (formato)|Elemento facoltativo.<br /><br /> Specificare che vengano visualizzati gli elementi delle raccolte.|
|[Elemento ItemSelectionCondition per ExpressionBinding per GroupBy (formato)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve essere presente per questo controllo da utilizzare.|
|[Elemento PropertyName per ExpressionBinding per GroupBy (formato)](./propertyname-element-for-expressionbinding-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET il cui valore viene visualizzato dal controllo.|
|[Elemento ScriptBlock per ExpressionBinding per GroupBy (formato)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script il cui valore viene visualizzato dal controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomItem per CustomEntry per GroupBy (formato)](./customitem-element-for-customentry-for-groupby-format.md)|Definisce i dati visualizzati dalla visualizzazione del controllo personalizzato e modalità di visualizzazione.|

## <a name="see-also"></a>Vedere anche

[Elemento CustomControlName per ExpressionBinding per GroupBy (formato)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Elemento EnumerateCollection per ExpressionBinding per GroupBy (formato)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[Elemento ItemSelectionCondition per ExpressionBinding per GroupBy (formato)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Elemento PropertyName per ExpressionBinding per GroupBy (formato)](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[Elemento ScriptBlock per ExpressionBinding per GroupBy (formato)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[Elemento CustomItem per CustomEntry per GroupBy (formato)](./customitem-element-for-customentry-for-groupby-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
