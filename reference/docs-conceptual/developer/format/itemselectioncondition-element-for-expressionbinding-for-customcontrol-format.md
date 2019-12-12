---
title: Elemento ItemSelectionCondition per ExpressionName per CustomControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362910"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a>Elemento ItemSelectionCondition per ExpressionBinding per CustomControl (formato)

Definisce la condizione che deve esistere per il controllo da utilizzare. Non esiste alcun limite al numero di condizioni di selezione che è possibile specificare per un elemento di controllo. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per la vista (Format) CustomEntry elemento per CustomEntries per la visualizzazione (Format) CustomItem elemento per Elemento CustomEntry per la vista (Format) espressione per CustomItem per CustomControl per la visualizzazione (Format) ItemSelectionCondition elemento per l'associazione di espressioni per CustomControl per la visualizzazione (formato)

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
|[Elemento PropertyName per ItemSelectionCondition per CustomControl per View (format](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET che attiva la condizione.|
|[Elemento ScriptBlock per ItemSelectionCondition per CustomControl per View (Format)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script che attiva la condizione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento expressiongroup per CustomItem per CustomControl per View (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Definisce i dati visualizzati dal controllo.|

## <a name="remarks"></a>Osservazioni

È possibile specificare un nome di proprietà o uno script per questa condizione, ma non è possibile specificarli entrambi.

## <a name="see-also"></a>Vedere anche

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)

[Elemento expressiongroup per CustomItem per CustomControl per View (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
