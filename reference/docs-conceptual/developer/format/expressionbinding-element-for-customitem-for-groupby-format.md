---
title: Elemento expressiongroup per CustomItem per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368630"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>Elemento ExpressionBinding per CustomItem per GroupBy (formato)

Definisce i dati visualizzati dal controllo. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format) elemento CustomItem per CustomEntry per l'elemento di espressione GroupBy (Format) per CustomItem per GroupBy (Format)

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
|[Elemento CustomControlName per Expressiongroup per GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica il nome di un controllo comune o di un controllo di visualizzazione.|
|[Elemento enumeratorcollection per expressiongroup per GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) Elemento enumeratorcollection per Expressiongroup per GroupBy (Format)|Elemento facoltativo.<br /><br /> Specifica che vengono visualizzati gli elementi delle raccolte.|
|[Elemento ItemSelectionCondition per Expressiongroup per GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve esistere per il controllo da utilizzare.|
|[Elemento PropertyName per ExpressionName per GroupBy (Format)](./propertyname-element-for-expressionbinding-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET il cui valore viene visualizzato dal controllo.|
|[Elemento ScriptBlock per Expressiongroup per GroupBy (Format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script il cui valore viene visualizzato dal controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomItem per CustomEntry per GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)|Definisce quali dati vengono visualizzati dalla visualizzazione controlli personalizzati e come vengono visualizzati.|

## <a name="see-also"></a>Vedere anche

[Elemento CustomControlName per Expressiongroup per GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Elemento enumeratorcollection per Expressiongroup per GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[Elemento ItemSelectionCondition per Expressiongroup per GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Elemento PropertyName per ExpressionName per GroupBy (Format)](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[Elemento ScriptBlock per Expressiongroup per GroupBy (Format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[Elemento CustomItem per CustomEntry per GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
