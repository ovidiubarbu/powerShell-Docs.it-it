---
title: Elemento PropertyName per SelectionCondition per EntrySelectedBy per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362290"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>Elemento PropertyName per SelectionCondition per EntrySelectedBy per ListControl (formato)

Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene usata la voce dell'elenco.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento EntrySelectedBy per ListEntry (Format) SelectionCondition elemento per EntrySelectedBy per l'elemento ListEntry (Format) PropertyName per SelectionCondition per EntrySelectedBy per ListEntry (Format)

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
|[Elemento SelectionCondition per EntrySelectedBy per ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Definisce la condizione che deve esistere affinché questa voce di elenco venga utilizzata.|

## <a name="text-value"></a>Valore testo

Specificare il nome della proprietà .NET.

## <a name="remarks"></a>Osservazioni

La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificarli entrambi. Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per l'utilizzo di una voce o di un elemento della visualizzazione](./defining-conditions-for-displaying-data.md).

Per ulteriori informazioni sugli altri componenti di una visualizzazione elenco, vedere [creazione](./creating-a-list-view.md)di una visualizzazione elenco.

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Elemento ListEntry (Format)](./listentry-element-for-listcontrol-format.md)

[Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per ListEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
