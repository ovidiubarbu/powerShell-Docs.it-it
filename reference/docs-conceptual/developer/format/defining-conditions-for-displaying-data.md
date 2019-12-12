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
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="469c7-102">Definizione delle condizioni per la visualizzazione dei dati</span><span class="sxs-lookup"><span data-stu-id="469c7-102">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="469c7-103">Quando si definiscono i dati visualizzati da una vista o un controllo, è possibile specificare una condizione che deve esistere per i dati da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="469c7-103">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="469c7-104">La condizione può essere attivata da una proprietà specifica o quando uno script o un valore della proprietà restituisce `true`.</span><span class="sxs-lookup"><span data-stu-id="469c7-104">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="469c7-105">Quando viene soddisfatta la condizione di selezione, viene utilizzata la definizione della vista o del controllo.</span><span class="sxs-lookup"><span data-stu-id="469c7-105">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="469c7-106">Specifica di una condizione di selezione per una definizione</span><span class="sxs-lookup"><span data-stu-id="469c7-106">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="469c7-107">Quando si crea una definizione per una vista o un controllo, l'elemento `EntrySelectedBy` viene usato per specificare quali oggetti utilizzeranno la definizione o quale condizione deve esistere per la definizione da usare.</span><span class="sxs-lookup"><span data-stu-id="469c7-107">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="469c7-108">La condizione viene specificata dall'elemento `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="469c7-108">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="469c7-109">Nell'esempio seguente viene specificata una condizione di selezione per una definizione di una vista tabella.</span><span class="sxs-lookup"><span data-stu-id="469c7-109">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="469c7-110">In questo esempio la definizione viene utilizzata solo quando lo script specificato viene valutato `true`.</span><span class="sxs-lookup"><span data-stu-id="469c7-110">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

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

<span data-ttu-id="469c7-111">Non esiste alcun limite al numero di condizioni di selezione che è possibile specificare per una definizione di una vista o di un controllo.</span><span class="sxs-lookup"><span data-stu-id="469c7-111">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="469c7-112">Gli unici requisiti sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="469c7-112">The only requirements are the following:</span></span>

- <span data-ttu-id="469c7-113">La condizione di selezione deve specificare un nome di proprietà o uno script per attivare la condizione, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="469c7-113">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="469c7-114">La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="469c7-114">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="469c7-115">Specifica di una condizione di selezione per un elemento</span><span class="sxs-lookup"><span data-stu-id="469c7-115">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="469c7-116">È inoltre possibile specificare quando viene utilizzato un elemento di una visualizzazione elenco o di un controllo includendo l'elemento `ItemSelectionCondition` nella definizione dell'elemento.</span><span class="sxs-lookup"><span data-stu-id="469c7-116">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="469c7-117">Nell'esempio seguente viene specificata una condizione di selezione per un elemento di una visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="469c7-117">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="469c7-118">In questo esempio l'elemento viene utilizzato solo quando lo script viene valutato `true`.</span><span class="sxs-lookup"><span data-stu-id="469c7-118">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="469c7-119">È possibile specificare una sola condizione di selezione per un elemento.</span><span class="sxs-lookup"><span data-stu-id="469c7-119">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="469c7-120">E la condizione deve specificare un nome di proprietà o uno script per attivare la condizione, ma non è possibile specificarli entrambi.</span><span class="sxs-lookup"><span data-stu-id="469c7-120">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="469c7-121">Elementi XML</span><span class="sxs-lookup"><span data-stu-id="469c7-121">XML Elements</span></span>

 <span data-ttu-id="469c7-122">Per creare una condizione di selezione vengono utilizzati gli elementi XML seguenti.</span><span class="sxs-lookup"><span data-stu-id="469c7-122">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="469c7-123">Gli elementi seguenti specificano le condizioni di selezione per le definizioni delle viste:</span><span class="sxs-lookup"><span data-stu-id="469c7-123">The following elements specify selection conditions for view definitions:</span></span>

    - [<span data-ttu-id="469c7-124">Elemento SelectionCondition per EntrySelectedBy per Table ((Format)</span><span class="sxs-lookup"><span data-stu-id="469c7-124">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="469c7-125">Elemento SelectionCondition per EntrySelectedBy per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="469c7-125">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="469c7-126">Elemento SelectionCondition per EntrySelectedBy per WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="469c7-126">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="469c7-127">Elemento SelectionCondition per EntrySelectedBy per CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="469c7-127">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="469c7-128">Gli elementi seguenti specificano le condizioni di selezione per le definizioni di controllo comuni e di visualizzazione:</span><span class="sxs-lookup"><span data-stu-id="469c7-128">The following elements specify selection conditions for common and view control definitions:</span></span>

    - [<span data-ttu-id="469c7-129">Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="469c7-129">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="469c7-130">Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="469c7-130">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="469c7-131">L'elemento seguente specifica la condizione di selezione per l'espansione degli oggetti Collection:</span><span class="sxs-lookup"><span data-stu-id="469c7-131">The following element specifies the selection condition for expanding collection objects:</span></span>

    - [<span data-ttu-id="469c7-132">Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="469c7-132">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="469c7-133">L'elemento seguente specifica la condizione di selezione per la visualizzazione di un nuovo gruppo di dati:</span><span class="sxs-lookup"><span data-stu-id="469c7-133">The following element specifies the selection condition for displaying a new group of data:</span></span>

    - [<span data-ttu-id="469c7-134">Elemento SelectionCondition per EntrySelectedBy per GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="469c7-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="469c7-135">Nell'elemento seguente viene specificata una condizione di selezione degli elementi per una visualizzazione elenco:</span><span class="sxs-lookup"><span data-stu-id="469c7-135">The following element specifies an item selection condition for a list view:</span></span>

    - [<span data-ttu-id="469c7-136">Elemento ItemSelectionCondition per ListItem per ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="469c7-136">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="469c7-137">Gli elementi seguenti specificano una condizione di selezione degli elementi per i controlli:</span><span class="sxs-lookup"><span data-stu-id="469c7-137">The following elements specify an item selection condition for controls:</span></span>

    - [<span data-ttu-id="469c7-138">Elemento ItemSelectionCondition per ExpressionName per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="469c7-138">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="469c7-139">Elemento ItemSelectionCondition per Expressiongroup per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="469c7-139">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [<span data-ttu-id="469c7-140">Elemento ItemSelectionCondition per ExpressionName per CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="469c7-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="469c7-141">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="469c7-141">See Also</span></span>

[<span data-ttu-id="469c7-142">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="469c7-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
