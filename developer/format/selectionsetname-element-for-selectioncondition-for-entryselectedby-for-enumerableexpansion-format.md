---
title: Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063861"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)

Specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set sono presente, la condizione viene soddisfatta.

Configurazione elemento elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) EnumerableExpansions (formato) EntrySelectedBy elemento per elemento SelectionCondition EnumerableExpansion (formato) per EntrySelectedBy per Elemento SelectionSetName EnumerableExpansion (formato) per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)

## <a name="syntax"></a>Sintassi

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono l'elemento padre di attributi e gli elementi figlio di `SelectionSetName` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Definisce la condizione che deve essere presente per espandere gli oggetti dell'insieme di questa definizione.|

## <a name="text-value"></a>Valore di testo

Specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

La condizione di selezione è possibile specificare un set di selezione o un tipo .NET, ma non è possibile specificare entrambi. Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

Set di selezione sono i gruppi di oggetti .NET che possono essere usati da qualsiasi vista che definisce il file di formattazione comuni. Per altre informazioni sulla creazione e che fanno riferimento a set di selezione, vedere [definizione di selezione imposta](./defining-selection-sets.md).

## <a name="see-also"></a>Vedere anche

[La definizione di set di selezione](./defining-selection-sets.md)

[Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
