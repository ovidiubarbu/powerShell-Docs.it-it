---
title: Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362010"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a>Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)

Definisce la condizione che deve esistere per espandere gli oggetti della raccolta di questa definizione.

Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format) elemento EntrySelectedBy per EnumerableExpansion (Format) SelectionCondition elemento per EntrySelectedBy per EnumerableExpansion (formato)

## <a name="syntax"></a>Sintassi

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionCondition`. È necessario specificare un singolo elemento `PropertyName` o `ScriptBlock`. Gli elementi `SelectionSetName` e `TypeName` sono facoltativi. È possibile specificare uno dei due elementi.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento PropertyName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET che attiva la condizione.|
|[Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script che attiva la condizione.|
|[Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento facoltativo.<br /><br /> Specifica il set di tipi .NET che attiva la condizione.|
|[Elemento TypeName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che attiva la condizione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)|Definisce gli oggetti della raccolta .NET espansi da questa definizione.|

## <a name="remarks"></a>Osservazioni

Per ogni definizione è necessario definire almeno un nome di tipo, un set di selezione o una condizione di selezione.

Quando si definisce una condizione di selezione, si applicano i requisiti seguenti:

- La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificarli entrambi.

- La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi.

Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la riproduzione di dati](./defining-conditions-for-displaying-data.md).

Per ulteriori informazioni su altri componenti di una visualizzazione estesa, vedere [visualizzazione estesa](./creating-a-wide-view.md).

## <a name="see-also"></a>Vedere anche

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
