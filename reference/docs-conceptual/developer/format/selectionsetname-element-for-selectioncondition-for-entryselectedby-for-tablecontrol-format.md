---
title: Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361920"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per TableControl (formato)

Specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presente, la condizione viene soddisfatta e l'oggetto viene visualizzato utilizzando questa definizione della vista tabella.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) elemento EntrySelectedBy per TableRowEntry (Format) Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format) SelectionSetName elemento per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)

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
|[Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Definisce la condizione che deve esistere per utilizzare per questa definizione della visualizzazione tabella.|

## <a name="text-value"></a>Valore di testo

Consente di specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

La condizione di selezione può specificare un set di selezione o un tipo .NET, ma non è possibile specificarli entrambi. Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

I set di selezione sono gruppi comuni di oggetti .NET che possono essere utilizzati da qualsiasi visualizzazione definita dal file di formattazione. Per ulteriori informazioni sulla creazione e il riferimento a set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).

Per ulteriori informazioni su altri componenti di una visualizzazione estesa, vedere [creazione di una vista tabella](./creating-a-table-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una vista tabella](./creating-a-table-view.md)

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Elemento TypeName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
