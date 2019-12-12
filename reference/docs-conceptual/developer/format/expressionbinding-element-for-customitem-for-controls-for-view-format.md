---
title: Elemento expressiongroup per CustomItem per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363780"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>Elemento ExpressionBinding per CustomItem per Controls per View (formato)

Definisce i dati visualizzati dal controllo. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per la visualizzazione (Format) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato) elemento Expressiongroup per CustomItem per i controlli per la visualizzazione (formato)

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

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ExpressionBinding`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|`CustomControl Element`|Elemento facoltativo.<br /><br /> Definisce un controllo utilizzato dal controllo.|
|[Elemento CustomControlName per Expressiongroup per i controlli per la visualizzazione (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica il nome di un controllo comune o di un controllo di visualizzazione.|
|[Elemento enumeratorcollection per Expressiongroup per i controlli per la visualizzazione (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica che gli elementi delle raccolte vengono visualizzati.|
|[Elemento ItemSelectionCondition di Expression per i controlli per la visualizzazione (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve esistere per il controllo da utilizzare.|
|[Elemento PropertyName per ExpressionName per i controlli per la visualizzazione (Format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET il cui valore viene visualizzato dal controllo.|
|[Elemento ScriptBlock per Expressiongroup per i controlli per la visualizzazione (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script il cui valore viene visualizzato dal controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Definisce quali dati vengono visualizzati dal controllo e come vengono visualizzati.|

## <a name="remarks"></a>Osservazioni

## <a name="see-also"></a>Vedere anche

[Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Elemento CustomControlName per Expressiongroup per i controlli per la visualizzazione (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento enumeratorcollection per Expressiongroup per i controlli per la visualizzazione (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento ItemSelectionCondition di Expression per i controlli per la visualizzazione (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento PropertyName per ExpressionName per i controlli per la visualizzazione (Format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento ScriptBlock per Expressiongroup per i controlli per la visualizzazione (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
