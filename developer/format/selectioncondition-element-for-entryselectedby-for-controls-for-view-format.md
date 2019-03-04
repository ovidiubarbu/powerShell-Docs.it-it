---
title: Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858017"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>Elemento SelectionCondition per EntrySelectedBy per Controls per View (formato)

Definisce una condizione che deve essere presente per la definizione di controllo da utilizzare. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl per i controlli elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) EntrySelectedBy per CustomEntry per i controlli elemento di visualizzazione (formato) SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione ( Formato)

## <a name="syntax"></a>Sintassi

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionCondition` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento PropertyName per SelectionCondition per i controlli per la visualizzazione (formato)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica una proprietà .NET che attiva la condizione.|
|[Elemento ScriptBlock per SelectionCondition per i controlli per la visualizzazione (formato)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script che genera la condizione.|
|[Elemento SelectionSetName per SelectionCondition per i controlli per la visualizzazione (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica il set di tipi .NET che attiva la condizione.|
|[Elemento TypeName per SelectionCondition per i controlli per la visualizzazione (formato)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che attiva la condizione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (formato)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Definisce i tipi .NET che usano questa definizione di controllo o la condizione che deve essere presente per questa definizione da usare.|

## <a name="remarks"></a>Osservazioni

Quando si definisce una condizione di selezione, si applicano i requisiti seguenti:

- La condizione di selezione è necessario specificare un nome di una proprietà minimi o un blocco di script, ma non è possibile specificare entrambi.

- La condizione di selezione può includere un numero qualsiasi di tipi .NET o selezione imposta, ma non è possibile specificare entrambi.

Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[Elemento PropertyName per SelectionCondition per i controlli per la visualizzazione (formato)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento ScriptBlock per SelectionCondition per i controlli per la visualizzazione (formato)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento SelectionSetName per SelectionCondition per i controlli per la visualizzazione (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento TypeName per SelectionCondition per i controlli per la visualizzazione (formato)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (formato)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
