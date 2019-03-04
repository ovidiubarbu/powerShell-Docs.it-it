---
title: Elemento SelectionSetName per SelectionCondition per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856757"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a>Elemento SelectionSetName per SelectionCondition per GroupBy (formato)

Specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presentano, viene soddisfatta la condizione e l'oggetto viene visualizzato tramite questo controllo. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per elemento EntrySelectedBy GroupBy (formato) per CustomEntry per elemento SelectionCondition GroupBy (formato) per EntrySelectedBy per elemento SelectionSetName GroupBy (formato) per SelectionCondition per GroupBy (formato)

## <a name="syntax"></a>Sintassi

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSetName` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per GroupBy (formato)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Definisce una condizione che deve essere presente per la definizione di controllo da utilizzare.|

## <a name="text-value"></a>Valore di testo

Specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

Set di selezione sono i gruppi di oggetti .NET che possono essere usati da qualsiasi vista che definisce il file di formattazione comuni. Per altre informazioni sulla creazione e che fanno riferimento a set di selezione, vedere [definizione di selezione imposta](./defining-selection-sets.md).

Quando questo elemento viene specificato, non è possibile specificare il [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) elemento. Per altre informazioni sulla definizione di condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[Elemento TypeName per SelectionCondition per GroupBy (formato)](./typename-element-for-selectioncondition-for-groupby-format.md)

[Elemento SelectionCondition per EntrySelectedBy per GroupBy (formato)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[La definizione delle condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md)

[La definizione di set di selezione](./defining-selection-sets.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
