---
title: Elemento EntrySelectedBy per EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066210"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a>Elemento EntrySelectedBy per EnumerableExpansion (formato)

Definisce i tipi .NET che usano questa definizione o la condizione che deve essere presente per questa definizione da usare.

Configurazione (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) elemento EnumerableExpansion (formato) EntrySelectedBy elemento dell'elemento EnumerableExpansion (formato)

## <a name="syntax"></a>Sintassi

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `EntrySelectedBy` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve essere presente per espandere gli oggetti dell'insieme di questa definizione.|
|[Elemento SelectionSetName per EntrySelectedBy per EnumerableExpansion (formato)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento facoltativo.<br /><br /> Specifica un set di tipi .NET che usano questa definizione del modo in cui gli oggetti di raccolta vengono espansi.|
|[Elemento TypeName per EntrySelectedBy per EnumerableExpansion (formato)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che usa questa definizione del modo in cui gli oggetti di raccolta vengono espansi.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EnumerableExpansion (formato)](./enumerableexpansion-element-format.md)|Definisce una raccolta .NET come specifica gli oggetti vengono espansi quando vengono visualizzati in una vista.|

## <a name="remarks"></a>Osservazioni

È necessario specificare almeno un tipo, il set di selezione o condizione di selezione per una voce di definizione. Non è definito alcun limite massimo al numero di elementi figlio che è possibile usare.

Condizioni di selezione vengono usate per definire una condizione che deve essere presente per la definizione da usare, ad esempio quando un oggetto dispone di una proprietà specifica o che restituisce un valore della proprietà specifica o uno script `true`. Per altre informazioni sulle condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[La definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Elemento EnumerableExpansion (formato)](./enumerableexpansion-element-format.md)

[Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Elemento SelectionSetName per EntrySelectedBy per EnumerableExpansion (formato)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Elemento TypeName per EntrySelectedBy per EnumerableExpansion (formato)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
