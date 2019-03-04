---
title: Elemento PropertyName per SelectionCondition per EntrySelectedBy per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: f857f5944b9e971215a06d6f5c39f7c22c6cf99f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853297"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>Elemento PropertyName per SelectionCondition per EntrySelectedBy per ListControl (formato)

Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene usata la voce dell'elenco.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) elemento ListEntries (formato) elemento ListEntry (formato) EntrySelectedBy elemento di configurazione per elemento SelectionCondition ListEntry (formato) EntrySelectedBy per elemento PropertyName ListEntry (formato) per SelectionCondition per EmtrySelectedBy per ListEntry (formato)

## <a name="syntax"></a>Sintassi

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `PropertyName` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per ListEntry (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Definisce la condizione che deve essere presente per questa voce di elenco da utilizzare.|

## <a name="text-value"></a>Valore di testo

Specificare il nome della proprietà .NET.

## <a name="remarks"></a>Osservazioni

La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificare entrambi. Per altre informazioni su come usare le condizioni di selezione, vedere [definizione di condizioni per quando una voce di visualizzazione o viene usato l'elemento](./defining-conditions-for-displaying-data.md).

Per altre informazioni sugli altri componenti di una visualizzazione elenco, vedere [creazione di visualizzazione elenco](./creating-a-list-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[La definizione delle condizioni per i dati quando viene visualizzata](./defining-conditions-for-displaying-data.md)

[Elemento ListEntry (formato)](./listentry-element-for-listcontrol-format.md)

[Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per ListEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
