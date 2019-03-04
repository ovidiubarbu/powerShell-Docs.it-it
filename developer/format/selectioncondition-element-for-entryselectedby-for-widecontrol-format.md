---
title: Elemento SelectionCondition per EntrySelectedBy per WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854117"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a>Elemento SelectionCondition per EntrySelectedBy per WideControl (formato)

Definisce la condizione che deve essere presente per questa definizione da usare. Non sono previsti limiti al numero di condizioni di selezione che è possibile specificare per una definizione di voce wide.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento di configurazione per elemento SelectionCondition WideEntry (formato) per EntrySelectedBy per WideEntry (formato)

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

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionCondition` elemento. È necessario specificare un unico `PropertyName` o `ScriptBlock` elemento. Il `SelectionSetName` e `TypeName` gli elementi sono facoltativi. È possibile specificare uno dei entrambi gli elementi.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET che attiva la condizione.|
|[Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica il blocco di script che genera la condizione.|
|[Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|Elemento facoltativo.<br /><br /> Specifica il set di tipi .NET che attiva la condizione.|
|[Elemento TypeName per SelectionCondition per EntrySelectedBy per WideEntry (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che attiva la condizione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md)|Definisce i tipi .NET che usano questa voce ampia o la condizione che deve essere presente per questa voce da usare.|

## <a name="remarks"></a>Osservazioni

Ogni voce wide deve avere almeno un nome di tipo, il set di selezione o condizione di selezione definiti.

Quando si definisce una condizione di selezione, si applicano i requisiti seguenti:

- La condizione di selezione è necessario specificare un nome di una proprietà minimi o un blocco di script, ma non è possibile specificare entrambi.

- La condizione di selezione può includere un numero qualsiasi di tipi .NET o selezione imposta, ma non è possibile specificare entrambi.

Per altre informazioni su come usare le condizioni di selezione, vedere [definizione di condizioni per quando una voce di visualizzazione o viene usato l'elemento](./defining-conditions-for-displaying-data.md).

Per altre informazioni sugli altri componenti di una visualizzazione più ampia, vedere [creazione di una visualizzazione più ampia](./creating-a-wide-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione più ampia](./creating-a-wide-view.md)

[La definizione delle condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md)

[Elemento EntrySelectedBy per WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md)

[Elemento PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Elemento TypeName per SelectionCondition per EntrySelectedBy per WideEntry (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
