---
title: Elemento SelectionCondition per EntrySelectedBy per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: f04a07c241268566eaedfe2b299c33d5be4dc19d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364820"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a>Elemento SelectionCondition per EntrySelectedBy per ListControl (formato)

Definisce la condizione che deve esistere per utilizzare questa definizione della visualizzazione elenco. Non esiste alcun limite al numero di condizioni di selezione che è possibile specificare per una definizione di elenco.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento EntrySelectedBy per ListEntry (Format) SelectionCondition elemento per EntrySelectedBy per ListEntry (Format)

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
|[Elemento PropertyName per SelectionCondition per EntrySelectedBy per ListEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET che attiva la condizione.|
|[Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per ListEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script che attiva la condizione.|
|[Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per ListEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|Elemento facoltativo.<br /><br /> Specifica il set di tipi .NET che attivano la condizione.|
|[Elemento TypeName per SelectionCondition per EntrySelectedBy per ListEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che attiva la condizione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per TableRowEntry (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Definisce i tipi .NET che utilizzano questa voce di tabella o la condizione che deve esistere affinché questa voce venga utilizzata.|

## <a name="remarks"></a>Osservazioni

lWhen si definisce una condizione di selezione, si applicano i requisiti seguenti:

- La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificarli entrambi.

- La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi.

Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

Per ulteriori informazioni sugli altri componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Elemento ListEntry (Format)](./listentry-element-for-listcontrol-format.md)

[Elemento SelectionSetName per EntrySelectedBy per ListEntry (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Elemento TypeName per EntrySelectedBy per ListEntry (Format)](/powershell/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
