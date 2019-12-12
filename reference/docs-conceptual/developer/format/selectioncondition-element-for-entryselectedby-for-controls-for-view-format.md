---
title: Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362050"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>Elemento SelectionCondition per EntrySelectedBy per Controls per View (formato)

Definisce una condizione che deve esistere per la definizione del controllo da utilizzare. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per i controlli per la visualizzazione (formato) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) EntrySelectedBy elemento per CustomEntry per i controlli per la visualizzazione (formato) SelectionCondition elemento per EntrySelectedBy per i controlli per la visualizzazione ( Formato

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

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionCondition`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento PropertyName per SelectionCondition per i controlli per la visualizzazione (Format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica una proprietà .NET che attiva la condizione.|
|[Elemento ScriptBlock per SelectionCondition per i controlli per la visualizzazione (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script che attiva la condizione.|
|[Elemento SelectionSetName per SelectionCondition per i controlli per la visualizzazione (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica il set di tipi .NET che attiva la condizione.|
|[Elemento TypeName per SelectionCondition per i controlli per la visualizzazione (Format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che attiva la condizione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata.|

## <a name="remarks"></a>Osservazioni

Quando si definisce una condizione di selezione, si applicano i requisiti seguenti:

- La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificarli entrambi.

- La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi.

Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[Elemento PropertyName per SelectionCondition per i controlli per la visualizzazione (Format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento ScriptBlock per SelectionCondition per i controlli per la visualizzazione (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento SelectionSetName per SelectionCondition per i controlli per la visualizzazione (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento TypeName per SelectionCondition per i controlli per la visualizzazione (Format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
