---
title: Elemento ItemSelectionCondition per ExpressionName per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365290"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a>Elemento ItemSelectionCondition per ExpressionBinding per GroupBy (formato)

Definisce la condizione che deve esistere per il controllo da utilizzare. Non esiste alcun limite al numero di condizioni di selezione che è possibile specificare per un elemento di controllo. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format) elemento CustomItem per CustomEntry per l'elemento di espressione GroupBy (Format) per CustomItem per l'elemento GroupBy (Format) ItemSelectionCondition per Expression per GroupBy (Format)

## <a name="syntax"></a>Sintassi

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ItemSelectionCondition`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento PropertyName per ItemSelectionCondition per GroupBy (Format)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET che attiva la condizione.|
|[Elemento ScriptBlock per ItemSelectionCondition per GroupBy (Format)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script che attiva la condizione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento expressiongroup per CustomItem per GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Definisce i dati visualizzati dal controllo.|

## <a name="remarks"></a>Osservazioni

È possibile specificare un nome di proprietà o uno script per questa condizione, ma non è possibile specificarli entrambi.

## <a name="see-also"></a>Vedere anche

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)

[Elemento expressiongroup per CustomItem per GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)
