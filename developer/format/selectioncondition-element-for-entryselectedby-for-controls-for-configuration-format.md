---
title: Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075767"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a>Elemento SelectionCondition per EntrySelectedBy per Controls per Configuration (formato)

Definisce una condizione che deve essere presente per la definizione di un controllo comune da usare. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Configurazione (formato) i controlli elemento dell'elemento di controllo di configurazione (formato) per i controlli per Configuration (formato) CustomControl elemento per elemento Configuration (formato) CustomEntries CustomControl dei controlli per il controllo Elemento CustomEntry di configurazione (formato) per CustomControl per i controlli per elemento di configurazione (formato) EntrySelectedBy per CustomEntry per i controlli per elemento di configurazione (formato) SelectionCondition per EntrySelectedBy per CustomEntry per Configurazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionCondition` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento PropertyName per SelectionCondition per i controlli per la configurazione (formato)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica una proprietà .NET che attiva la condizione.|
|[Elemento ScriptBlock per SelectionCondition per i controlli per la configurazione (formato)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script che genera la condizione.|
|[Elemento SelectionSetName per SelectionCondition per i controlli per la configurazione (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica il set di tipi .NET che attiva la condizione.|
|[Elemento TypeName per SelectionCondition per i controlli per la configurazione (formato)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che attiva la condizione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (formato)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Definisce i tipi .NET che usano questa voce della definizione di controllo comuni.|

## <a name="remarks"></a>Osservazioni

Quando si definisce una condizione di selezione, è necessario eseguire le linee guida seguenti:

- La condizione di selezione è necessario specificare un nome di una proprietà minimi o un blocco di script, ma non è possibile specificare entrambi.

- La condizione di selezione può includere un numero qualsiasi di tipi .NET o selezione imposta, ma non è possibile specificare entrambi.

Per altre informazioni sull'utilizzo di condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[Elemento PropertyName per SelectionCondition per i controlli per la configurazione (formato)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elemento ScriptBlock per SelectionCondition per i controlli per la configurazione (formato)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elemento SelectionSetName per SelectionCondition per i controlli per la configurazione (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elemento TypeName per SelectionCondition per i controlli per la configurazione (formato)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (formato)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[La scrittura di un metodo di formattazione di Windows PowerShell e i tipi di File](./writing-a-powershell-formatting-file.md)
