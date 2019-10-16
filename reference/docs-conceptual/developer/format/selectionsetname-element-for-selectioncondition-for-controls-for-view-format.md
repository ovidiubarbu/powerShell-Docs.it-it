---
title: Elemento SelectionSetName per SelectionCondition per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361970"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a>Elemento SelectionSetName per SelectionCondition per Controls per View (formato)

Specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presente, la condizione viene soddisfatta e l'oggetto viene visualizzato utilizzando questo controllo. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per i controlli per la visualizzazione (formato) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) EntrySelectedBy elemento per CustomEntry per i controlli per la visualizzazione (formato) SelectionCondition elemento per EntrySelectedBy per i controlli per la visualizzazione ( Format) elemento SelectionSetName per SelectionCondition per i controlli per la visualizzazione (Format)

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
|[Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Definisce una condizione che deve esistere per la definizione del controllo da utilizzare.|

## <a name="text-value"></a>Valore di testo

Consente di specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

I set di selezione sono gruppi comuni di oggetti .NET che possono essere utilizzati da qualsiasi visualizzazione definita dal file di formattazione. Per ulteriori informazioni sulla creazione e il riferimento a set di selezione, vedere [definizione di set di selezione](./defining-selection-sets.md).

La condizione di selezione può specificare un set di selezione o un tipo .NET, ma non è possibile specificarli entrambi. Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Definizione di set di selezione](./defining-selection-sets.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
