---
title: Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064323"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a>Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideControl (formato)

Specifica lo script che genera la condizione. Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene utilizzata la definizione di voce wide.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento di configurazione per elemento SelectionCondition WideEntry (formato) per EntrySelectedBy per elemento ScriptBlock WideEntry (formato) per SelectionCondition per EntrySelectedBy per WideEntry (formato)

## <a name="syntax"></a>Sintassi

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ScriptBlock` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Definisce la condizione che deve essere presente per questa definizione da usare.|

## <a name="text-value"></a>Valore di testo

Specificare lo script che viene valutato.

## <a name="remarks"></a>Osservazioni

La condizione di selezione è necessario specificare almeno un nome di uno script o una proprietà da valutare, ma non è possibile specificare entrambi. Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).

Per altre informazioni sugli altri componenti di una visualizzazione più ampia, vedere [visualizzazione estesa](./creating-a-wide-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione più ampia](./creating-a-wide-view.md)

[La definizione delle condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md)

[Elemento PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Elemento SelectionCondition per EntrySelectedBy per WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
