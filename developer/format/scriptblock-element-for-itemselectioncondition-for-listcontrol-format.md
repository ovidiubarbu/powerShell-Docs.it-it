---
title: Elemento ScriptBlock per ItemSelectionCondition per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064408"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a>Elemento ScriptBlock per ItemSelectionCondition per ListControl (formato)

Specifica lo script che genera la condizione. Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene usato l'elemento dell'elenco. Questo elemento viene usato quando si definisce una visualizzazione elenco.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) ListEntries elemento di configurazione per elemento dell'oggetto ListControl (formato) ListEntry ListEntries per elemento ListItems dell'oggetto ListControl (formato) per ListEntry elemento ListItem ListControl (formato) per ListItems per elenco (Format) ItemSelectionCondition elemento Control per ListItem per elemento dell'oggetto ListControl (formato) ScriptBlock ItemSelectionCondition per ListControl (formato)

## <a name="syntax"></a>Sintassi

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi, elementi figlio e gli elementi padre del `ScriptBlock` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ItemSelectionCondition per ListItem per ListControl (formato)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Definisce la condizione che deve essere presente per questo elemento di elenco da utilizzare.|

## <a name="text-value"></a>Valore di testo

Specificare lo script che viene valutato.

## <a name="remarks"></a>Osservazioni

Se questo elemento viene usato, è possibile specificare il `PropertyName` elemento quando si definisce la condizione di selezione.

## <a name="see-also"></a>Vedere anche

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
