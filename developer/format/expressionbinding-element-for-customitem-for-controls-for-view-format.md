---
title: Elemento ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858297"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>Elemento ExpressionBinding per CustomItem per Controls per View (formato)

Definisce i dati che vengano visualizzati dal controllo. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) CustomItem per CustomEntry per i controlli elemento di visualizzazione (formato) ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato)

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
|[Elemento CustomControlName per ExpressionBinding per i controlli per la visualizzazione (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica il nome di un controllo comune o un controllo di visualizzazione.|
|[Elemento EnumerateCollection per ExpressionBinding per i controlli per la visualizzazione (formato)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica che vengono visualizzati gli elementi delle raccolte.|
|[Elemento ItemSelectionCondition ExpressionBinding per i controlli per la visualizzazione (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve essere presente per questo controllo da utilizzare.|
|[Elemento PropertyName per ExpressionBinding per i controlli per la visualizzazione (formato)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET il cui valore viene visualizzato dal controllo.|
|[Elemento ScriptBlock per ExpressionBinding per i controlli per la visualizzazione (formato)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script il cui valore viene visualizzato dal controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Definisce i dati che vengano visualizzati dal controllo e la modalità di visualizzazione.|

## <a name="remarks"></a>Osservazioni

## <a name="see-also"></a>Vedere anche

[Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Elemento CustomControlName per ExpressionBinding per i controlli per la visualizzazione (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento EnumerateCollection per ExpressionBinding per i controlli per la visualizzazione (formato)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento ItemSelectionCondition ExpressionBinding per i controlli per la visualizzazione (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento PropertyName per ExpressionBinding per i controlli per la visualizzazione (formato)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento ScriptBlock per ExpressionBinding per i controlli per la visualizzazione (formato)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
