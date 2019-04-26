---
title: Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064051"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per TableControl (formato)

Specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presentano, viene soddisfatta la condizione e l'oggetto viene visualizzato utilizzando questa definizione della visualizzazione della tabella.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento di configurazione per TableRowEntry (formato) Elemento SelectionCondition per EntrySelectedBy per elemento SelectionSetName TableRowEntry (formato) per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)

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
|[Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (formato)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Definisce la condizione che deve essere presente per l'utilizzo per questa definizione della visualizzazione della tabella.|

## <a name="text-value"></a>Valore di testo

Specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

La condizione di selezione è possibile specificare un set di selezione o un tipo .NET, ma non è possibile specificare entrambi. Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).

Set di selezione sono i gruppi di oggetti .NET che possono essere usati da qualsiasi vista che definisce il file di formattazione comuni. Per altre informazioni sulla creazione e che fanno riferimento a set di selezione, vedere [definizione imposta di oggetti](./defining-selection-sets.md).

Per altre informazioni sugli altri componenti di una visualizzazione più ampia, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione tabella](./creating-a-table-view.md)

[La definizione delle condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md)

[Elemento TypeName per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (formato)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
