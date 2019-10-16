---
title: Elemento expressiongroup per CustomItem per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363150"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>Elemento ExpressionBinding per CustomItem per CustomControl per View (formato)

Definisce i dati visualizzati dal controllo. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl per View (Format) elemento CustomEntries per CustomControl per la visualizzazione (Format) CustomEntry elemento per CustomEntries per CustomControl per la visualizzazione ( Format) elemento CustomItem per CustomEntry per CustomControl per la visualizzazione (Format) elemento Expressiongroup per CustomItem per CustomControl per View (Format)

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
|[Elemento CustomControlName per Expression per CustomControl per View (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica il nome di un controllo comune o di un controllo di visualizzazione.|
|[Elemento Enumerator per Expression per CustomControl per View (Format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica che vengono visualizzati gli elementi delle raccolte.|
|[Elemento ItemSelectionCondition per Expression per CustomControl per View (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve esistere per il controllo da utilizzare.|
|[Elemento PropertyName per Expression per CustomControl per View (Format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET il cui valore viene visualizzato dal controllo.|
|[Elemento ScriptBlock per Expression per CustomCustomControl per View (Format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script il cui valore viene visualizzato dal controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomItem per CustomEntry per CustomControl per View (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Definisce quali dati vengono visualizzati dalla visualizzazione controlli personalizzati e come vengono visualizzati.|

## <a name="remarks"></a>Osservazioni

## <a name="see-also"></a>Vedere anche

[Elemento CustomControlName per Expression per CustomControl per View (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento Enumerator per Expression per CustomControl per View (Format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento ItemSelectionCondition per Expression per CustomControl per View (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Elemento PropertyName per Expression per CustomControl per View (Format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento ScriptBlock per Expression per CustomControl per View (Format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento CustomItem per CustomEntry per CustomControl per View (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
