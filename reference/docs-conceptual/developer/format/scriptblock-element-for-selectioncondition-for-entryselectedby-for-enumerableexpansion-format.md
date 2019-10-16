---
title: Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368610"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)

Specifica lo script che attiva la condizione.

Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format) elemento EntrySelectedBy per EnumerableExpansion (Format) SelectionCondition elemento per EntrySelectedBy per EnumerableExpansion (Format) elemento ScriptBlock per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)

## <a name="syntax"></a>Sintassi

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ScriptBlock`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Definisce la condizione che deve esistere per espandere gli oggetti della raccolta di questa definizione.|

## <a name="text-value"></a>Valore di testo

Specificare lo script che viene valutato.

## <a name="remarks"></a>Osservazioni

La condizione di selezione deve specificare almeno un nome di script o di proprietà da valutare, ma non è possibile specificarli entrambi. Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Elemento PropertyName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
