---
title: Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361990"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)

Specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presente, viene soddisfatta la condizione.

Elemento di configurazione elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansions (Format) elemento EntrySelectedBy per EnumerableExpansion (Format) SelectionCondition elemento per EntrySelectedBy per EnumerableExpansion (Format) elemento SelectionSetName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)

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
|[Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Definisce la condizione che deve esistere per espandere gli oggetti della raccolta di questa definizione.|

## <a name="text-value"></a>Valore di testo

Consente di specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

La condizione di selezione può specificare un set di selezione o un tipo .NET, ma non è possibile specificarli entrambi. Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

I set di selezione sono gruppi comuni di oggetti .NET che possono essere utilizzati da qualsiasi visualizzazione definita dal file di formattazione. Per ulteriori informazioni sulla creazione e il riferimento a set di selezione, vedere [definizione di set di selezione](./defining-selection-sets.md).

## <a name="see-also"></a>Vedere anche

[Definizione di set di selezione](./defining-selection-sets.md)

[Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
