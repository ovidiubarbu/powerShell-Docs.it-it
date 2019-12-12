---
title: Elemento PropertyName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365000"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a>Elemento PropertyName per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)

Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene utilizzata la voce della tabella.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) elemento EntrySelectedBy per TableRowEntry (Format) Elemento SelectionCondition per EntrySelectedBy per l'elemento TableRowEntry (Format) PropertyName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)

## <a name="syntax"></a>Sintassi

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `PropertyName`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Definisce la condizione che deve esistere per la voce della tabella da utilizzare.|

## <a name="text-value"></a>Valore testo

Specificare il nome della proprietà .NET.

## <a name="remarks"></a>Osservazioni

La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificarli entrambi. Per ulteriori informazioni sul modo in cui è possibile utilizzare le condizioni di selezione, vedere [definizione di condizioni per l'utilizzo di una voce o di un elemento della visualizzazione](./defining-conditions-for-displaying-data.md).

Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una vista tabella](./creating-a-table-view.md)

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
