---
title: Elemento ScriptBlock per SelectionCondition per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368640"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a>Elemento ScriptBlock per SelectionCondition per CustomControl per View (formato)

Specifica lo script che attiva la condizione. Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzata la definizione. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl per View (Format) elemento CustomEntries per CustomControl per la visualizzazione (Format) CustomEntry elemento per CustomEntries per CustomControl per la visualizzazione ( Format) elemento CustomItem per CustomEntry per CustomControl per la visualizzazione (Format) SelectionCondition elemento per EntrySelectedBy per CustomControl per la visualizzazione (Format) ScriptBlock elemento per SelectionCondition per CustomControl per View (Format)

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
|[Elemento SelectionCondition per EntrySelectedBy per CustomControl per View (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Definisce una condizione che deve esistere per la definizione del controllo da utilizzare.|

## <a name="text-value"></a>Valore testo

Specificare lo script che viene valutato.

## <a name="remarks"></a>Osservazioni

Per valutare la condizione di selezione, è necessario specificare almeno uno script o un nome di proprietà, ma non è possibile specificarli entrambi. Per ulteriori informazioni sul modo in cui è possibile utilizzare le condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[Elemento SelectionCondition per EntrySelectedBy per CustomControl per View (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
