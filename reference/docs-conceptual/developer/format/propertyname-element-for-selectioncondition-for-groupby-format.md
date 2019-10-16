---
title: Elemento PropertyName per SelectionCondition per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1707317-6c26-4866-bcc1-8924103c9014
caps.latest.revision: 6
ms.openlocfilehash: 7241ea0ea364befa7ad4ab0af4c4209be72214a7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364950"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a>Elemento PropertyName per SelectionCondition per GroupBy (formato)

Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene usata la definizione. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per l'elemento EntrySelectedBy di GroupBy (Format) per CustomEntry per l'elemento SelectionCondition di GroupBy (Format) per EntrySelectedBy per SelectionCondition per l'elemento PropertyName (Format) PropertyName per per GroupBy (Format)

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
|[Elemento SelectionCondition per EntrySelectedBy per GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Definisce una condizione che deve esistere per la definizione del controllo da utilizzare.|

## <a name="text-value"></a>Valore di testo

Specificare il nome della proprietà .NET.

## <a name="remarks"></a>Osservazioni

La condizione di selezione deve specificare almeno un nome di proprietà o uno script, ma non è possibile specificarli entrambi. Per ulteriori informazioni sul modo in cui è possibile utilizzare le condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[Elemento SelectionCondition per EntrySelectedBy per GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
