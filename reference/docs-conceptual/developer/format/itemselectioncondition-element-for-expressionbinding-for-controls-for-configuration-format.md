---
title: Elemento ItemSelectionCondition per ExpressionName per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362920"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a>Elemento ItemSelectionCondition per ExpressionBinding per Controls per Configuration (formato)

Definisce la condizione che deve esistere per il controllo da utilizzare. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento CustomItem per CustomEntry per i controlli per l'elemento Expressionation di Configuration per CustomItem per i controlli per la configurazione (Format) Elemento ItemSelectionCondition per ExpressionName per i controlli per la configurazione (Format)

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
|[Elemento PropertyName per ItemSelectionCondition per i controlli per la configurazione (Format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET che attiva la condizione.|
|[Elemento ScriptBlock per ItemSelectionCondition per i controlli per la configurazione (Format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script che attiva la condizione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento expressiongroup per CustomItem per i controlli per la configurazione (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Definisce i dati visualizzati dal controllo.|

## <a name="remarks"></a>Osservazioni

È possibile specificare un nome di proprietà o uno script per questa condizione, ma non è possibile specificarli entrambi.

## <a name="see-also"></a>Vedere anche

[Elemento PropertyName per ItemSelectionCondition per i controlli per la configurazione (Format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Elemento ScriptBlock per ItemSelectionCondition per i controlli per la configurazione (Format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Elemento expressiongroup per CustomItem per i controlli per la configurazione (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
