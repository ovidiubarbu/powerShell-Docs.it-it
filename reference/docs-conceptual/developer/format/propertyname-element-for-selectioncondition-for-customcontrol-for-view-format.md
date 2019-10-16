---
title: Elemento PropertyName per SelectionCondition per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48a417-2083-46d4-ac38-16c12e65b6b9
caps.latest.revision: 7
ms.openlocfilehash: e08037d5d051d3be51e90193c7e87cc2e738f78a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362350"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a>Elemento PropertyName per SelectionCondition per CustomControl per View (formato)

Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene usata la definizione. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl per View (Format) elemento CustomEntries per CustomControl per la visualizzazione (Format) CustomEntry elemento per CustomEntries per CustomControl per la visualizzazione ( Format) elemento CustomItem per CustomEntry per CustomControl per la vista (Format) elemento EntrySelectedBy per CustomEntry per CustomControl per SelectionCondition per la visualizzazione (formato) EntrySelectedBy elemento per CustomControl per per la visualizzazione (Format) PropertyName Elemento per SelectionCondition per CustomControl per View (Format)

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
|[Elemento SelectionCondition per EntrySelectedBy per CustomControl per View (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Definisce una condizione che deve esistere per la definizione del controllo da utilizzare.|

## <a name="text-value"></a>Valore di testo

Specificare il nome della proprietà .NET.

## <a name="remarks"></a>Osservazioni

La condizione di selezione deve specificare almeno un nome di proprietà o uno script, ma non è possibile specificarli entrambi. Per ulteriori informazioni sul modo in cui è possibile utilizzare le condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[Elemento SelectionCondition per EntrySelectedBy per CustomControl per View (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
