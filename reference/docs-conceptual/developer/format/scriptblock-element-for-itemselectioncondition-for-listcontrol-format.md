---
title: Elemento ScriptBlock per ItemSelectionCondition per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362100"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a>Elemento ScriptBlock per ItemSelectionCondition per ListControl (formato)

Specifica lo script che attiva la condizione. Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzato l'elemento dell'elenco. Questo elemento viene utilizzato quando si definisce una visualizzazione elenco.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries per l'elemento ListControl (Format) ListEntry per ListEntries per l'elemento ListItem (Format) ListItems per ListEntry per l'elemento ListItem (Format) ListItem per ListItems per il controllo elenco (Format) elemento ItemSelectionCondition per ListItem per ListControl (Format) elemento ScriptBlock per ItemSelectionCondition per ListControl (Format)

## <a name="syntax"></a>Sintassi

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre dell'elemento `ScriptBlock`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ItemSelectionCondition per ListItem per ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Definisce la condizione che deve esistere per l'uso di questo elemento elenco.|

## <a name="text-value"></a>Valore testo

Specificare lo script che viene valutato.

## <a name="remarks"></a>Osservazioni

Se viene usato questo elemento, non è possibile specificare l'elemento `PropertyName` quando si definisce la condizione di selezione.

## <a name="see-also"></a>Vedere anche

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
