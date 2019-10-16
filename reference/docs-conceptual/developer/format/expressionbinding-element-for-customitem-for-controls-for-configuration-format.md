---
title: Elemento expressiongroup per CustomItem per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363190"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a>Elemento ExpressionBinding per CustomItem per Controls per Configuration (formato)

Definisce i dati visualizzati dal controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento CustomItem per CustomEntry per i controlli per l'elemento Expressionation di Configuration per CustomItem per i controlli per la configurazione (Format)

## <a name="syntax"></a>Sintassi

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ExpressionBinding`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|`CustomControl Element`|Elemento facoltativo.<br /><br /> Definisce un controllo utilizzato dal controllo.|
|[Elemento CustomControlName per ExpressionName per i controlli per la configurazione (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica il nome di un controllo comune o di un controllo di visualizzazione.|
|[Elemento enumeratorcollection per Expressions per i controlli per Configuration (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica che gli elementi delle raccolte vengono visualizzati dal controllo.|
|[Elemento ItemSelectionCondition per ExpressionName per i controlli per la configurazione (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve esistere affinché questo controllo comune venga usato.|
|[Elemento PropertyName per ExpressionName per i controlli per la configurazione (Format)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET il cui valore viene visualizzato dal controllo comune.|
|[Elemento ScriptBlock per ExpressionName per i controlli per la configurazione (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script il cui valore viene visualizzato dal controllo comune.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomItem per CustomEntry per i controlli per la configurazione](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Definisce quali dati vengono visualizzati dalla visualizzazione controlli personalizzati e come vengono visualizzati.|

## <a name="remarks"></a>Osservazioni

## <a name="see-also"></a>Vedere anche

[Elemento CustomItem per CustomEntry per i controlli per la configurazione](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
