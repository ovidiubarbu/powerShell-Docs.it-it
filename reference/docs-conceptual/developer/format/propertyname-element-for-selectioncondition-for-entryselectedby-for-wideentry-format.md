---
title: Elemento PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362240"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a>Elemento PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (formato)

Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene usata la definizione.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) elemento EntrySelectedBy per WideEntry (Format) SelectionCondition elemento per EntrySelectedBy per l'elemento WideEntry (Format) PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (Format)

## <a name="syntax"></a>Sintassi

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

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
|[Elemento SelectionCondition per EntrySelectedBy per WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Definisce la condizione che deve esistere affinché questa definizione venga utilizzata.|

## <a name="text-value"></a>Valore testo

Specificare il nome della proprietà .NET.

## <a name="remarks"></a>Osservazioni

La condizione di selezione deve specificare almeno un nome di proprietà o uno script da valutare, ma non è possibile specificarli entrambi. Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

Per ulteriori informazioni su altri componenti di una visualizzazione estesa, vedere [visualizzazione estesa](./creating-a-wide-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione estesa](./creating-a-wide-view.md)

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[Elemento SelectionCondition per EntrySelectedBy per WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
