---
title: Elemento PropertyName per ItemSelectionCondition per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064748"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a>Elemento PropertyName per ItemSelectionCondition per ListControl (formato)

Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene utilizzata la vista. Questo elemento viene usato quando si definisce una visualizzazione elenco.

Configurazione elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) ListEntries (formato) ListEntry elemento per elemento ListItems dell'oggetto ListControl (formato) per ListEntry per ListItem ListControl (formato) Elemento ListItems per elemento dell'oggetto ListControl (formato) ItemSelectionCondition ListItem per elemento PropertyName ListControls ItemSelectionCondition per ListControl (formato)

## <a name="syntax"></a>Sintassi

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi, elementi figlio e gli elementi padre del `PropertyName` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ItemSelectionCondition per ListItem per ListControl (formato)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a>Valore di testo

Specificare il nome della proprietà il cui valore viene visualizzato.

## <a name="remarks"></a>Osservazioni

Se questo elemento viene usato, è possibile specificare il [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) elemento quando si definisce la condizione di selezione.

## <a name="see-also"></a>Vedere anche

[Elemento ScriptBlock per ItemSelectionCondition per ListIControl (formato)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[Elemento ItemSelectionCondition per ListItem per ListControl (formato)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
