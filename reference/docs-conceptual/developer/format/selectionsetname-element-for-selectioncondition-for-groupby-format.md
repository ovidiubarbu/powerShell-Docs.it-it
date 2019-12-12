---
title: Elemento SelectionSetName per SelectionCondition per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361860"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a>Elemento SelectionSetName per SelectionCondition per GroupBy (formato)

Specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presente, la condizione viene soddisfatta e l'oggetto viene visualizzato tramite questo controllo. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format) elemento EntrySelectedBy per CustomEntry per l'elemento SelectionCondition di GroupBy (Format) per EntrySelectedBy per SelectionSetName per l'elemento SelectionCondition di GroupBy (Format) per per GroupBy (Format)

## <a name="syntax"></a>Sintassi

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Definisce una condizione che deve esistere per la definizione del controllo da utilizzare.|

## <a name="text-value"></a>Valore testo

Consente di specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

I set di selezione sono gruppi comuni di oggetti .NET che possono essere utilizzati da qualsiasi visualizzazione definita dal file di formattazione. Per ulteriori informazioni sulla creazione e il riferimento a set di selezione, vedere [definizione di set di selezione](./defining-selection-sets.md).

Quando questo elemento viene specificato, non è possibile specificare l'elemento [typeName](./typename-element-for-selectioncondition-for-groupby-format.md) . Per ulteriori informazioni sulla definizione delle condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[Elemento TypeName per SelectionCondition per GroupBy (Format)](./typename-element-for-selectioncondition-for-groupby-format.md)

[Elemento SelectionCondition per EntrySelectedBy per GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Definizione di set di selezione](./defining-selection-sets.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
