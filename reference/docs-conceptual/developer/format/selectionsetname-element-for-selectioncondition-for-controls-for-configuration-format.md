---
title: Elemento SelectionSetName per SelectionCondition per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368280"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a>Elemento SelectionSetName per SelectionCondition per Controls per Configuration (formato)

Specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presente, la condizione viene soddisfatta e l'oggetto viene visualizzato tramite questo controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per i controlli per Configuration (Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (Format) SelectionCondition elemento per EntrySelectedBy per i controlli per Configuration (Format) elemento SelectionSetName per SelectionCondition per i controlli per la configurazione (Format)

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
|[Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Definisce una condizione che deve esistere per la definizione del controllo da utilizzare.|

## <a name="text-value"></a>Valore di testo

Consente di specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

I set di selezione sono gruppi comuni di oggetti .NET che possono essere utilizzati da qualsiasi visualizzazione definita dal file di formattazione. Per ulteriori informazioni sulla creazione e il riferimento a set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).

La condizione di selezione può specificare un set di selezione o un tipo .NET, ma non è possibile specificarli entrambi. Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Definizione di set di selezione](./defining-selection-sets.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
