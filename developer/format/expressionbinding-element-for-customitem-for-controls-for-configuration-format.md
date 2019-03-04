---
title: Elemento ExpressionBinding per CustomItem per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855137"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a>Elemento ExpressionBinding per CustomItem per Controls per Configuration (formato)

Definisce i dati che vengano visualizzati dal controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli di configurazione (formato) CustomControl elemento per il controllo per elemento di configurazione (formato) CustomEntries per CustomControl per Configuration ( Elemento CustomEntry Format) per CustomControl per i controlli per elemento di configurazione (formato) CustomItem per CustomEntry per i controlli per configurazione ExpressionBinding elemento CustomItem per i controlli per la configurazione (formato)

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
|[Elemento CustomControlName per ExpressionBinding per i controlli per la configurazione (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica il nome di un controllo comune o un controllo di visualizzazione.|
|[Elemento EnumerateCollection per ExpressionBinding per i controlli per la configurazione (formato)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specificare che gli elementi delle raccolte vengono visualizzati dal controllo.|
|[Elemento ItemSelectionCondition per ExpressionBinding per i controlli per la configurazione (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve essere presente per questo controllo comune da usare.|
|[Elemento PropertyName per ExpressionBinding per i controlli per la configurazione (formato)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET il cui valore viene visualizzato per il controllo comune.|
|[Elemento ScriptBlock per ExpressionBinding per i controlli per la configurazione (formato)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script il cui valore viene visualizzato per il controllo comune.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomItem per CustomEntry per i controlli per la configurazione](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Definisce i dati visualizzati dalla visualizzazione del controllo personalizzato e modalità di visualizzazione.|

## <a name="remarks"></a>Osservazioni

## <a name="see-also"></a>Vedere anche

[Elemento CustomItem per CustomEntry per i controlli per la configurazione](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
