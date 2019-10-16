---
title: Elemento SelectionCondition per EntrySelectedBy per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364780"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a>Elemento SelectionCondition per EntrySelectedBy per WideControl (formato)

Definisce la condizione che deve esistere affinché questa definizione venga utilizzata. Non esiste alcun limite al numero di condizioni di selezione che è possibile specificare per una definizione di voce ampia.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) elemento EntrySelectedBy per WideEntry (Format) SelectionCondition elemento per EntrySelectedBy per WideEntry (Format)

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
|[Elemento PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET che attiva la condizione.|
|[Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica il blocco di script che attiva la condizione.|
|[Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|Elemento facoltativo.<br /><br /> Specifica il set di tipi .NET che attiva la condizione.|
|[Elemento TypeName per SelectionCondition per EntrySelectedBy per WideEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che attiva la condizione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Definisce i tipi .NET che utilizzano questa voce estesa o la condizione che deve esistere affinché questa voce venga utilizzata.|

## <a name="remarks"></a>Osservazioni

Per ogni voce di tipo Wide è necessario definire almeno un nome di tipo, un set di selezione o una condizione di selezione.

Quando si definisce una condizione di selezione, si applicano i requisiti seguenti:

- La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificarli entrambi.

- La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi.

Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per l'utilizzo di una voce o di un elemento della visualizzazione](./defining-conditions-for-displaying-data.md).

Per ulteriori informazioni su altri componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione estesa](./creating-a-wide-view.md)

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Elemento EntrySelectedBy per WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)

[Elemento PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Elemento TypeName per SelectionCondition per EntrySelectedBy per WideEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
