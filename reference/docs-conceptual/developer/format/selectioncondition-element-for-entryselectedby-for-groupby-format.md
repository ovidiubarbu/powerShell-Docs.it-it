---
title: Elemento SelectionCondition per EntrySelectedBy per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368430"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a>Elemento SelectionCondition per EntrySelectedBy per GroupBy (formato)

Definisce una condizione che deve esistere per la definizione di un controllo da utilizzare. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format) elemento EntrySelectedBy per CustomEntry per GroupBy (Format) SelectionCondition elemento per EntrySelectedBy per GroupBy (Format)

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

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionCondition`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento PropertyName per SelectionCondition per GroupBy (Format)](./propertyname-element-for-selectioncondition-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica una proprietà .NET che attiva la condizione.|
|[Elemento ScriptBlock per SelectionCondition per GroupBy (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script che attiva la condizione.|
|[Elemento SelectionSetName per SelectionCondition per GroupBy (Format)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica il set di tipi .NET che attiva la condizione.|
|[Elemento TypeName per SelectionCondition per GroupBy (Format)](./typename-element-for-selectioncondition-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che attiva la condizione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per CustomEntry per GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata.|

## <a name="remarks"></a>Osservazioni

Quando si definisce una condizione di selezione, si applicano i requisiti seguenti:

- La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificarli entrambi.

- La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi.

Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[Elemento PropertyName per SelectionCondition per CustomControl per View (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento ScriptBlock per SelectionCondition per CustomControl per View (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento SelectionSetName per SelectionCondition per il controllo personalizzato per la visualizzazione (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento TypeName per SelectionCondition per GroupBy (Format)](./typename-element-for-selectioncondition-for-groupby-format.md)

[Elemento EntrySelectedBy per CustomEntry per GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
