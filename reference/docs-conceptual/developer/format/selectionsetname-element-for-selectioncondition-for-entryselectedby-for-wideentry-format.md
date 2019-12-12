---
title: Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a13a429c-a31b-4e29-828c-c0c0917b5415
caps.latest.revision: 11
ms.openlocfilehash: baea89e4b259611dfa45b6bcf94fa0bf2df6b9de
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368410"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a>Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (formato)

Specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presente, la condizione viene soddisfatta e l'oggetto viene visualizzato utilizzando questa definizione della visualizzazione estesa.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) elemento EntrySelectedBy per WideEntry (Format) SelectionCondition elemento per EntrySelectedBy per WideEntry (Format) elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (Format)

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
|[Elemento SelectionCondition per EntrySelectedBy per WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Definisce la condizione che deve esistere affinché questa definizione venga utilizzata.|

## <a name="text-value"></a>Valore testo

Consente di specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

La condizione di selezione può specificare un set di selezione o un tipo .NET, ma non è possibile specificarli entrambi. Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

I set di selezione sono gruppi comuni di oggetti .NET che possono essere utilizzati da qualsiasi visualizzazione definita dal file di formattazione. Per ulteriori informazioni sulla creazione e il riferimento a set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).

Per ulteriori informazioni su altri componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione estesa](./creating-a-wide-view.md)

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Definizione di set di selezione](./defining-selection-sets.md)

[Elemento SelectionCondition per EntrySelectedBy per WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento TypeName per SelectionCondition per EntrySelectedBy per WideEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
