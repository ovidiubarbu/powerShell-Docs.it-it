---
title: Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368560"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a>Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideControl (formato)

Specifica lo script che attiva la condizione. Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene usata la definizione di voce estesa.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) elemento EntrySelectedBy per WideEntry (Format) SelectionCondition elemento per EntrySelectedBy per WideEntry (Format) elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideEntry (Format)

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
|[Elemento SelectionCondition per EntrySelectedBy per WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Definisce la condizione che deve esistere affinché questa definizione venga utilizzata.|

## <a name="text-value"></a>Valore di testo

Specificare lo script che viene valutato.

## <a name="remarks"></a>Osservazioni

La condizione di selezione deve specificare almeno un nome di script o di proprietà da valutare, ma non è possibile specificarli entrambi. Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

Per ulteriori informazioni su altri componenti di una visualizzazione estesa, vedere [visualizzazione estesa](./creating-a-wide-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione estesa](./creating-a-wide-view.md)

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Elemento PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Elemento SelectionCondition per EntrySelectedBy per WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
