---
title: Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: b65d953169f6daf15fb617ce4d0303cf4cb584ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064357"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per ListControl (formato)

Specifica lo script che genera la condizione. Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene usata la voce dell'elenco.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) elemento ListEntries (formato) elemento ListEntry (formato) EntrySelectedBy elemento di configurazione per elemento SelectionCondition ListEntry (formato) EntrySelectedBy per elemento ScriptBlock ListEntry (formato) per SelectionCondition per EntrySelectedBy per ListEntry (formato)

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
|[Elemento SelectionCondition per EntrySelectedBy per ListEntry (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Definisce la condizione che deve essere presente per questa voce di elenco da utilizzare.|

## <a name="text-value"></a>Valore di testo

Specificare lo script che viene valutato.

## <a name="remarks"></a>Osservazioni

La condizione di selezione è necessario specificare un nome di script o proprietà uno minimi per valutare, ma non è possibile specificare entrambi. (Per altre informazioni sull'utilizzo di condizioni di selezione, vedere [definizione di condizioni per quando una voce di visualizzazione o viene usato l'elemento](./defining-conditions-for-displaying-data.md).)

Per altre informazioni su altri componenti di una visualizzazione elenco, vedere [visualizzazione elenco](./creating-a-list-view.md).

## <a name="see-also"></a>Vedere anche

[Elemento ListEntry (formato)](./listentry-element-for-listcontrol-format.md)

[Elemento PropertyName per SelectionCondition per EntrySelectedBy per ListEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[Elemento SelectionCondition per EntrySelectedBy per ListEntry (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Visualizzazione elenco](./creating-a-list-view.md)

[La definizione delle condizioni per quando viene utilizzata una voce di visualizzazione o un elemento](./defining-conditions-for-displaying-data.md)

[La scrittura di un metodo di formattazione di Windows PowerShell e i tipi di File](./writing-a-powershell-formatting-file.md)
