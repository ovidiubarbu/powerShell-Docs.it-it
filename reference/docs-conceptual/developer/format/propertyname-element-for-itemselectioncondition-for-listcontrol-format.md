---
title: Elemento PropertyName per ItemSelectionCondition per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362390"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a>Elemento PropertyName per ItemSelectionCondition per ListControl (formato)

Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene utilizzata la vista. Questo elemento viene utilizzato quando si definisce una visualizzazione elenco.

Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry per ListControl (Format) elemento ListItems per ListEntry per ListControl (Format) ListItem Elemento per ListItems per ListControl (Format) elemento ItemSelectionCondition per ListItem per elemento ListControls PropertyName per ItemSelectionCondition per ListControl (Format)

## <a name="syntax"></a>Sintassi

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre dell'elemento `PropertyName`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ItemSelectionCondition per ListItem per ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a>Valore testo

Consente di specificare il nome della proprietà di cui viene visualizzato il valore.

## <a name="remarks"></a>Osservazioni

Se viene usato questo elemento, non è possibile specificare l'elemento [scriptblock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) quando si definisce la condizione di selezione.

## <a name="see-also"></a>Vedere anche

[Elemento ScriptBlock per ItemSelectionCondition per ListIControl (Format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[Elemento ItemSelectionCondition per ListItem per ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
