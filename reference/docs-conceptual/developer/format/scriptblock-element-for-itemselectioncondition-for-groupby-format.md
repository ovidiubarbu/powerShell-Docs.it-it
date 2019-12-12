---
title: Elemento ScriptBlock per ItemSelectionCondition per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364830"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a>Elemento ScriptBlock per ItemSelectionCondition per GroupBy (formato)

Specifica lo script che attiva la condizione. Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzato il controllo. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per l'elemento CustomItem di GroupBy (Format) per CustomEntry per l'elemento di espressione GroupBy (Format) per CustomItem per l'elemento GroupBy (Format) ItemSelectionCondition per Expression per l'elemento GroupBy (Format) ScriptBlock per ItemSelectionCondition per GroupBy (Format)

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
|[Elemento ItemSelectionCondition per Expressiongroup per GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Definisce la condizione che deve esistere per il controllo da utilizzare.|

## <a name="text-value"></a>Valore testo

Specificare lo script che viene valutato.

## <a name="remarks"></a>Osservazioni

Se viene usato questo elemento, non è possibile specificare l'elemento [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) quando si definisce la condizione di selezione.

## <a name="see-also"></a>Vedere anche

[Elemento ItemSelectionCondition per Expressiongroup per GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Elemento PropertyName per ItemSelectionCondition per GroupBy (Format)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
