---
title: Elemento EntrySelectedBy per EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368800"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a>Elemento EntrySelectedBy per EnumerableExpansion (formato)

Definisce i tipi .NET che utilizzano questa definizione o la condizione che deve esistere affinché questa definizione venga utilizzata.

Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format) elemento EntrySelectedBy per EnumerableExpansion (Format)

## <a name="syntax"></a>Sintassi

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `EntrySelectedBy`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve esistere per espandere gli oggetti della raccolta di questa definizione.|
|[Elemento SelectionSetName per EntrySelectedBy per EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento facoltativo.<br /><br /> Specifica un set di tipi .NET che utilizzano questa definizione del modo in cui gli oggetti della raccolta vengono espansi.|
|[Elemento TypeName per EntrySelectedBy per EnumerableExpansion (Format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che usa questa definizione della modalità di espansione degli oggetti raccolta.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EnumerableExpansion (Format)](./enumerableexpansion-element-format.md)|Definisce la modalità di espansione degli oggetti raccolta .NET specifici quando vengono visualizzati in una visualizzazione.|

## <a name="remarks"></a>Osservazioni

È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per una voce di definizione. Non esiste un limite massimo per il numero di elementi figlio che è possibile usare.

Le condizioni di selezione vengono usate per definire una condizione che deve esistere per la definizione da usare, ad esempio quando un oggetto ha una proprietà specifica o che un valore di proprietà o uno script specifico restituisce `true`. Per ulteriori informazioni sulle condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Elemento EnumerableExpansion (Format)](./enumerableexpansion-element-format.md)

[Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Elemento SelectionSetName per EntrySelectedBy per EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Elemento TypeName per EntrySelectedBy per EnumerableExpansion (Format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
