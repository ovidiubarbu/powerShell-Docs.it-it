---
title: Elemento EntrySelectedBy per TableRowEntry per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: e18564c10898c73128e0a4bc7d077e7c7ffb1c22
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862327"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a>Elemento EntrySelectedBy per TableRowEntry per TableControl (formato)

Definisce i tipi .NET che usano questa definizione di visualizzazione della tabella o la condizione che deve essere presente per questa definizione da usare.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento di configurazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `EntrySelectedBy` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per Table (formato)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve essere presente per questa definizione di visualizzazione tabella da utilizzare.|
|[Elemento SelectionSetName per EntrySelectedBy per Table (formato)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica un set di tipi .NET che usano questa definizione di vista della tabella.|
|[Elemento TypeName per EntrySelectedBy per Table (formato)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che usa questa definizione di vista della tabella.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableRowEntry per Table (formato)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|Definisce i dati che viene visualizzati in una riga della tabella.|

## <a name="remarks"></a>Osservazioni

È necessario specificare almeno un tipo, set di selezione o condizione di selezione per una definizione di vista della tabella. Non è definito alcun limite massimo al numero di elementi figlio che è possibile usare.

Condizioni di selezione vengono usate per definire una condizione che deve essere presente per la definizione da usare, ad esempio quando un oggetto dispone di una proprietà specifica o che restituisce un valore della proprietà specifica o uno script `true`. Per altre informazioni sulle condizioni di selezione, vedere [definizione di condizioni per quando una voce di visualizzazione o viene usato l'elemento](./defining-conditions-for-displaying-data.md).

Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

L'esempio seguente mostra una `TableRowEntry` elemento utilizzato per visualizzare le proprietà del [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione tabella](./creating-a-table-view.md)

[Elemento SelectionCondition per EntrySelectedBy per Table (formato)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Elemento SelectionSetName per EntrySelectedBy per Table (formato)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[Elemento TableRowEntry per Table (formato)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[Elemento TypeName per EntrySelectedBy per Table (formato)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
