---
title: Elemento ItemSelectionCondition per ListItem per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065445"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>Elemento ItemSelectionCondition per ListItem per ListControl (formato)

Definisce la condizione che deve essere presente per questo elemento di elenco da utilizzare.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) ListEntries elemento di configurazione per elemento dell'oggetto ListControl (formato) ListEntry ListEntries per elemento ListItems dell'oggetto ListControl (formato) per ListEntry elemento ListItem ListControl (formato) per ListItems per elemento dell'oggetto ListControl (formato) ItemSelectionCondition ListItem per ListControl (formato)

## <a name="syntax"></a>Sintassi

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ItemSelectionCondition` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento PropertyName per ItemSelectionCondition per ListControl (formato)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET che attiva la condizione.|
|[Elemento ScriptBlock per ItemSelectionCondition per ListControl (formato)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script che genera la condizione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ListItem per ListItems per ListControl (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definisce proprietà o script il cui valore viene visualizzato in una riga della visualizzazione elenco.|

## <a name="remarks"></a>Osservazioni

È possibile specificare un nome di proprietà o uno script per questa condizione, ma non è possibile specificare entrambi.

## <a name="see-also"></a>Vedere anche

[Elemento ListItem per ListItems per ListControl (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Elemento PropertyName per ItemSelectionCondition per ListControl (formato)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[Elemento ScriptBlock per ItemSelectionCondition per ListControl (formato)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
