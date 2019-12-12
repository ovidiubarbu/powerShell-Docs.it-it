---
title: Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per ListEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368400"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a>Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per ListEntry (formato)

Specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presente, la condizione viene soddisfatta e l'oggetto viene visualizzato utilizzando questa definizione della visualizzazione elenco.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento EntrySelectedBy per ListEntry (Format) SelectionCondition elemento per EntrySelectedBy per ListEntry (Format) elemento SelectionSetName per SelectionCondition per EntrySelectedBy per ListEntry (Format)

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
|[Elemento SelectionCondition per EntrySelectedBy per ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Definisce la condizione che deve esistere per utilizzare questa definizione della visualizzazione elenco.|

## <a name="text-value"></a>Valore testo

Consente di specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

La condizione di selezione può specificare un set di selezione o un tipo .NET, ma non è possibile specificarli entrambi. Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

I set di selezione sono gruppi comuni di oggetti .NET che possono essere utilizzati da qualsiasi visualizzazione definita dal file di formattazione. Per ulteriori informazioni sulla creazione e il riferimento a set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).

Per ulteriori informazioni sugli altri componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Elemento SelectionCondition per EntrySelectedBy per ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
