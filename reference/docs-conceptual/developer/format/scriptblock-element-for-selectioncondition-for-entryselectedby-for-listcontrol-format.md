---
title: Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: b65d953169f6daf15fb617ce4d0303cf4cb584ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368590"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per ListControl (formato)

Specifica lo script che attiva la condizione. Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzata la voce dell'elenco.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento EntrySelectedBy per ListEntry (Format) SelectionCondition elemento per EntrySelectedBy per ListEntry (Format) elemento ScriptBlock per SelectionCondition per EntrySelectedBy per ListEntry (Format)

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
|[Elemento SelectionCondition per EntrySelectedBy per ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Definisce la condizione che deve esistere affinché questa voce di elenco venga utilizzata.|

## <a name="text-value"></a>Valore testo

Specificare lo script che viene valutato.

## <a name="remarks"></a>Osservazioni

Per valutare la condizione di selezione, è necessario specificare almeno uno script o un nome di proprietà, ma non è possibile specificarli entrambi. Per ulteriori informazioni sul modo in cui è possibile utilizzare le condizioni di selezione, vedere [definizione di condizioni per l'utilizzo di una voce di visualizzazione o di un elemento](./defining-conditions-for-displaying-data.md).

Per ulteriori informazioni sugli altri componenti di una visualizzazione elenco, vedere [visualizzazione elenco](./creating-a-list-view.md).

## <a name="see-also"></a>Vedere anche

[Elemento ListEntry (Format)](./listentry-element-for-listcontrol-format.md)

[Elemento PropertyName per SelectionCondition per EntrySelectedBy per ListEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[Elemento SelectionCondition per EntrySelectedBy per ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Visualizzazione elenco](./creating-a-list-view.md)

[Definizione delle condizioni per l'utilizzo di una voce o un elemento della visualizzazione](./defining-conditions-for-displaying-data.md)

[Scrittura di un file di formattazione e di tipi di Windows PowerShell](./writing-a-powershell-formatting-file.md)
