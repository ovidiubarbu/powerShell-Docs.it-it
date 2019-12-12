---
title: Elemento SelectionCondition per EntrySelectedBy per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368390"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a>Elemento SelectionCondition per EntrySelectedBy per TableControl (formato)

Definisce la condizione che deve esistere per utilizzare per questa definizione della visualizzazione tabella. Non esiste alcun limite al numero di condizioni di selezione che è possibile specificare per una definizione di tabella.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) elemento EntrySelectedBy per TableRowEntry (Format) Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format)

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

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento SelectionCondition.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento PropertyName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET che attiva la condizione.|
|[Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script che attiva la condizione.|
|[Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica il set di tipi .NET che attivano la condizione.|
|[Elemento TypeName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che attiva la condizione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per TableRowEntry (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Definisce i tipi .NET che utilizzano questa voce di tabella o la condizione che deve esistere affinché questa voce venga utilizzata.|

## <a name="remarks"></a>Osservazioni

Per ogni voce di elenco è necessario definire almeno un nome di tipo, un set di selezione o una condizione di selezione.

Quando si definisce una condizione di selezione, si applicano i requisiti seguenti:

- La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificarli entrambi.

- La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi.

Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per l'utilizzo di una voce o di un elemento della visualizzazione](./defining-conditions-for-displaying-data.md).

Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una vista tabella](./creating-a-table-view.md)

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Elemento EntrySelectedBy (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Elemento PropertyName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Elemento TypeName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Scrittura di un file di formattazione e di tipi di Windows PowerShell](./writing-a-powershell-formatting-file.md)
