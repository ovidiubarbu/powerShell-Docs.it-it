---
title: La definizione delle condizioni per la visualizzazione dei dati | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066329"
---
# <a name="defining-conditions-for-displaying-data"></a>Definizione delle condizioni per la visualizzazione dei dati

Quando si definiscono quali dati vengono visualizzati tramite una vista o un controllo, è possibile specificare una condizione che deve essere presente per i dati da visualizzare. La condizione può essere attivata da una proprietà specifica o quando uno script o restituisce il valore di proprietà `true`. Quando viene soddisfatta la condizione di selezione, verrà utilizzata la definizione della vista o del controllo.

## <a name="specifying-a-selection-condition-for-a-definition"></a>Specificare una condizione di selezione per una definizione

Quando si crea una definizione per una vista o un controllo, il `EntrySelectedBy` elemento viene usato per specificare gli oggetti che userà la definizione o la condizione deve esistere per la definizione da usare. La condizione viene specificata per il `SelectionCondition` elemento.

Nell'esempio seguente viene specificata una condizione di selezione per una definizione di una visualizzazione tabella. In questo esempio, la definizione viene utilizzata solo quando lo script specificato viene valutato per `true`.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <SelectionCondition>
      <ScriptBlock>ScriptToEvaluate</ScriptBlock>
    </SelectionCondition>
  </EntrySelectedBy>
  <TableColumnItems>
  </TableColumnItems>
</TableRowEntry>

```

Non sono previsti limiti al numero di condizioni di selezione che è possibile specificare per una definizione di un controllo o la vista. Gli unici requisiti sono i seguenti:

- La condizione di selezione deve specificare un nome di proprietà o script per attivare la condizione, ma non è possibile specificare entrambi.

- La condizione di selezione può includere un numero qualsiasi di tipi .NET o selezione imposta, ma non è possibile specificare entrambi.

## <a name="specifying-a-selection-condition-for-an-item"></a>Specificare una condizione di selezione per un elemento

È inoltre possibile specificare quando si usa un elemento della visualizzazione elenco o controllo, includendo il `ItemSelectionCondition` elemento nella definizione di elemento. Nell'esempio seguente viene specificata una condizione di selezione per un elemento di una visualizzazione elenco. In questo esempio, l'elemento viene utilizzato solo quando lo script viene valutato per `true`.

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

È possibile specificare solo una selezione condizione per un elemento. E la condizione deve specificare un nome di proprietà o script per attivare la condizione, ma non è possibile specificare entrambi.

## <a name="xml-elements"></a>Elementi XML

 Gli elementi XML seguenti vengono utilizzati per creare una condizione di selezione.

- I seguenti elementi specificano le condizioni di selezione per le definizioni delle viste:

    - [Elemento SelectionCondition per EntrySelectedBy per Table (formato)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [Elemento SelectionCondition per EntrySelectedBy per ListControl (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [Elemento SelectionCondition per EntrySelectedBy per WideControl (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [Elemento SelectionCondition per EntrySelectedBy per CustomControl (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- Gli elementi seguenti specificano la selezione le condizioni per comuni e visualizzazione controllo definizioni:

    - [Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- L'elemento seguente specifica la condizione di selezione per l'espansione di oggetti della raccolta:

    - [Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- L'elemento seguente specifica la condizione di selezione per la visualizzazione di un nuovo gruppo di dati:

    - [Elemento SelectionCondition per EntrySelectedBy per GroupBy (formato)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- L'elemento seguente specifica una condizione di selezione di elementi per una visualizzazione elenco:

    - [Elemento ItemSelectionCondition per ListItem per ListControl (formato)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- Gli elementi seguenti specificano una condizione di selezione di elementi per i controlli:

    - [Elemento ItemSelectionCondition per ExpressionBinding per i controlli per la configurazione (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [Elemento ItemSelectionCondition per ExpressionBinding per i controlli per la visualizzazione (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [Elemento ItemSelectionCondition per ExpressionBinding per CustomControl (formato)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>Vedere anche

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
