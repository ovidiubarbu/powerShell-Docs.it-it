---
title: Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368580"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per TableControl (formato)

Specifica il blocco di script che attiva la condizione. Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzata la voce della tabella.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) elemento EntrySelectedBy per TableRowEntry (Format) Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format) ScriptBlock elemento per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)

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
|[Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Definisce la condizione che deve esistere per la voce della tabella da utilizzare.|

## <a name="text-value"></a>Valore di testo

Specificare lo script che viene valutato.

## <a name="remarks"></a>Osservazioni

La condizione di selezione deve specificare almeno un blocco di script o un nome di proprietà, ma non è possibile specificarli entrambi. Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per l'utilizzo di una voce o di un elemento della visualizzazione](./defining-conditions-for-displaying-data.md).

Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una vista tabella](./creating-a-table-view.md)

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Elemento PropertyName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
