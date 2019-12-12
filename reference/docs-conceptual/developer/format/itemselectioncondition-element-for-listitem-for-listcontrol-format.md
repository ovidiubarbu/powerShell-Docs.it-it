---
title: Elemento ItemSelectionCondition per ListItem per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365190"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>Elemento ItemSelectionCondition per ListItem per ListControl (formato)

Definisce la condizione che deve esistere per l'uso di questo elemento elenco.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries per l'elemento ListControl (Format) ListEntry per ListEntries per l'elemento ListItem (Format) ListItems per ListEntry per l'elemento ListItem (Format) ListItem per ListItems per l'elemento ListControl (Format) ItemSelectionCondition per ListItem per ListControl (Format)

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
|[Elemento PropertyName per ItemSelectionCondition per ListControl (Format)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET che attiva la condizione.|
|[Elemento ScriptBlock per ItemSelectionCondition per ListControl (Format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script che attiva la condizione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ListItem per ListItems per ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definisce la proprietà o lo script il cui valore viene visualizzato in una riga della visualizzazione elenco.|

## <a name="remarks"></a>Osservazioni

È possibile specificare un nome di proprietà o uno script per questa condizione, ma non è possibile specificarli entrambi.

## <a name="see-also"></a>Vedere anche

[Elemento ListItem per ListItems per ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Elemento PropertyName per ItemSelectionCondition per ListControl (Format)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[Elemento ScriptBlock per ItemSelectionCondition per ListControl (Format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
