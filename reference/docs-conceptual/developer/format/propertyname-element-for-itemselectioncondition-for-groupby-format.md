---
title: Elemento PropertyName per ItemSelectionCondition per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362410"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a>Elemento PropertyName per ItemSelectionCondition per GroupBy (formato)

Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene utilizzato il controllo. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per l'elemento CustomItem di GroupBy (Format) per CustomEntry per l'elemento di espressione GroupBy (Format) per CustomItem per l'elemento GroupBy (Format) ItemSelectionCondition per Expression per l'elemento GroupBy (Format) PropertyName per ItemSelectionCondition per GroupBy (Format)

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
|[Elemento ItemSelectionCondition per Expressiongroup per GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Definisce la condizione che deve esistere per il controllo da utilizzare.|

## <a name="text-value"></a>Valore di testo

Specificare il nome della proprietà .NET che attiva la condizione.

## <a name="remarks"></a>Osservazioni

Se viene usato questo elemento, non è possibile specificare l'elemento [scriptblock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) quando si definisce la condizione di selezione.

## <a name="see-also"></a>Vedere anche

[Elemento ScriptBlock per ItemSelectionCondition per GroupBy (Format)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[Elemento ItemSelectionCondition per Expressiongroup per GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
