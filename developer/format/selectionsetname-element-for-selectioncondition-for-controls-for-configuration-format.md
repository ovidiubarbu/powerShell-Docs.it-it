---
title: Elemento SelectionSetName per SelectionCondition per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064023"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a>Elemento SelectionSetName per SelectionCondition per Controls per Configuration (formato)

Specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presentano, viene soddisfatta la condizione e l'oggetto viene visualizzato tramite questo controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Configurazione (formato) i controlli elemento dell'elemento di controllo di configurazione (formato) per i controlli per Configuration (formato) CustomControl elemento per elemento Configuration (formato) CustomEntries CustomControl dei controlli per il controllo Elemento CustomEntry di configurazione (formato) per CustomControl per i controlli per Configuration (formato) EntrySelectedBy elemento CustomEntry per i controlli per Configuration (formato) SelectionCondition elemento EntrySelectedBy per i controlli per Elemento SelectionSetName di configurazione (formato) per SelectionCondition per i controlli per la configurazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSetName` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Definisce una condizione che deve essere presente per la definizione di controllo da utilizzare.|

## <a name="text-value"></a>Valore di testo

Specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

Set di selezione sono i gruppi di oggetti .NET che possono essere usati da qualsiasi vista che definisce il file di formattazione comuni. Per altre informazioni sulla creazione e che fanno riferimento a set di selezione, vedere [definizione imposta di oggetti](./defining-selection-sets.md).

La condizione di selezione è possibile specificare un set di selezione o un tipo .NET, ma non è possibile specificare entrambi. Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[La definizione delle condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md)

[La definizione di set di selezione](./defining-selection-sets.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
