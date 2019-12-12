---
title: Definizione delle condizioni per la visualizzazione dei dati | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363900"
---
# <a name="defining-conditions-for-displaying-data"></a>Definizione delle condizioni per la visualizzazione dei dati

Quando si definiscono i dati visualizzati da una vista o un controllo, è possibile specificare una condizione che deve esistere per i dati da visualizzare. La condizione può essere attivata da una proprietà specifica o quando uno script o un valore della proprietà restituisce `true`. Quando viene soddisfatta la condizione di selezione, viene utilizzata la definizione della vista o del controllo.

## <a name="specifying-a-selection-condition-for-a-definition"></a>Specifica di una condizione di selezione per una definizione

Quando si crea una definizione per una vista o un controllo, l'elemento `EntrySelectedBy` viene usato per specificare quali oggetti utilizzeranno la definizione o quale condizione deve esistere per la definizione da usare. La condizione viene specificata dall'elemento `SelectionCondition`.

Nell'esempio seguente viene specificata una condizione di selezione per una definizione di una vista tabella. In questo esempio la definizione viene utilizzata solo quando lo script specificato viene valutato `true`.

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

Non esiste alcun limite al numero di condizioni di selezione che è possibile specificare per una definizione di una vista o di un controllo. Gli unici requisiti sono i seguenti:

- La condizione di selezione deve specificare un nome di proprietà o uno script per attivare la condizione, ma non è possibile specificarli entrambi.

- La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi.

## <a name="specifying-a-selection-condition-for-an-item"></a>Specifica di una condizione di selezione per un elemento

È inoltre possibile specificare quando viene utilizzato un elemento di una visualizzazione elenco o di un controllo includendo l'elemento `ItemSelectionCondition` nella definizione dell'elemento. Nell'esempio seguente viene specificata una condizione di selezione per un elemento di una visualizzazione elenco. In questo esempio l'elemento viene utilizzato solo quando lo script viene valutato `true`.

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

È possibile specificare una sola condizione di selezione per un elemento. E la condizione deve specificare un nome di proprietà o uno script per attivare la condizione, ma non è possibile specificarli entrambi.

## <a name="xml-elements"></a>Elementi XML

 Per creare una condizione di selezione vengono utilizzati gli elementi XML seguenti.

- Gli elementi seguenti specificano le condizioni di selezione per le definizioni delle viste:

    - [Elemento SelectionCondition per EntrySelectedBy per Table ((Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [Elemento SelectionCondition per EntrySelectedBy per ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [Elemento SelectionCondition per EntrySelectedBy per WideControl (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [Elemento SelectionCondition per EntrySelectedBy per CustomControl (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- Gli elementi seguenti specificano le condizioni di selezione per le definizioni di controllo comuni e di visualizzazione:

    - [Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- L'elemento seguente specifica la condizione di selezione per l'espansione degli oggetti Collection:

    - [Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- L'elemento seguente specifica la condizione di selezione per la visualizzazione di un nuovo gruppo di dati:

    - [Elemento SelectionCondition per EntrySelectedBy per GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- Nell'elemento seguente viene specificata una condizione di selezione degli elementi per una visualizzazione elenco:

    - [Elemento ItemSelectionCondition per ListItem per ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- Gli elementi seguenti specificano una condizione di selezione degli elementi per i controlli:

    - [Elemento ItemSelectionCondition per ExpressionName per i controlli per la configurazione (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [Elemento ItemSelectionCondition per Expressiongroup per i controlli per la visualizzazione (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [Elemento ItemSelectionCondition per ExpressionName per CustomControl (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>Vedere anche

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
