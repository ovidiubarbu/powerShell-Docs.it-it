---
title: Elemento SelectionCondition per EntrySelectedBy per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: f04a07c241268566eaedfe2b299c33d5be4dc19d
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735093"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a>Elemento SelectionCondition per EntrySelectedBy per ListControl (formato)

Definisce la condizione che deve essere presente per usare questa definizione della visualizzazione elenco. Non sono previsti limiti al numero di condizioni di selezione che è possibile specificare per una definizione di elenco.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) elemento ListEntries (formato) elemento ListEntry (formato) EntrySelectedBy elemento di configurazione per elemento SelectionCondition ListEntry (formato) EntrySelectedBy per ListEntry (formato)

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

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionCondition` elemento.

### <a name="attributes"></a>Attributi

Nessuno.

### <a name="child-elements"></a>Elementi figlio

|Elemento|DESCRIZIONE|
|-------------|-----------------|
|[Elemento PropertyName per SelectionCondition per EntrySelectedBy per ListEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET che attiva la condizione.|
|[Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per ListEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script che genera la condizione.|
|[Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per ListEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|Elemento facoltativo.<br /><br /> Specifica il set di tipi .NET che attivano la condizione.|
|[Elemento TypeName per SelectionCondition per EntrySelectedBy per ListEntry (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che attiva la condizione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|DESCRIZIONE|
|-------------|-----------------|
|[Elemento EntrySelectedBy per TableRowEntry (formato)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Definisce i tipi .NET che usano la voce della tabella o la condizione che deve essere presente per questa voce da usare.|

## <a name="remarks"></a>Osservazioni

lWhen si sta definendo una condizione di selezione, applicano i requisiti seguenti:

- La condizione di selezione è necessario specificare un nome di una proprietà minimi o un blocco di script, ma non è possibile specificare entrambi.

- La condizione di selezione può includere un numero qualsiasi di tipi .NET o selezione imposta, ma non è possibile specificare entrambi.

Per altre informazioni su come usare le condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).

Per altre informazioni sugli altri componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[La definizione delle condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md)

[Elemento ListEntry (formato)](./listentry-element-for-listcontrol-format.md)

[Elemento SelectionSetName per EntrySelectedBy per ListEntry (formato)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Elemento TypeName per EntrySelectedBy per ListEntry (formato)](/powershell/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
