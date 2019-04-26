---
title: Elemento PropertyName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ae11924-0072-451e-bf70-c5ffb25dccc0
caps.latest.revision: 13
ms.openlocfilehash: 0c20512e660c8d2b61d063dbd7078b55b23efeb8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064952"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>Elemento PropertyName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)

Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene utilizzata la definizione.

Configurazione (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) elemento EnumerableExpansion (formato) EntrySelectedBy elemento per elemento SelectionCondition EnumerableExpansion (formato) per EntrySelectedBy per Elemento PropertyName EnumerableExpansion (formato) per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)

## <a name="syntax"></a>Sintassi

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `PropertyName` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Definisce la condizione che deve essere presente per espandere gli oggetti dell'insieme di questa definizione.|

## <a name="text-value"></a>Valore di testo

Specificare il nome della proprietà .NET.

## <a name="remarks"></a>Osservazioni

La condizione di selezione è necessario specificare almeno un nome di proprietà o uno script per valutare, ma non è possibile specificare entrambi. Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[La definizione delle condizioni per i dati quando viene visualizzata](./defining-conditions-for-displaying-data.md)

[Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
