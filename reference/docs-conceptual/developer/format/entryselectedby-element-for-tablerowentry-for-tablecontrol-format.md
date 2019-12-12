---
title: Elemento EntrySelectedBy per TableRowEntry per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363340"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a>Elemento EntrySelectedBy per TableRowEntry per TableControl (formato)

Definisce i tipi .NET che utilizzano questa definizione della vista tabella o la condizione che deve esistere affinché questa definizione venga utilizzata.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) elemento EntrySelectedBy (Format)

## <a name="syntax"></a>Sintassi

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `EntrySelectedBy`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per Table ((Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve esistere per la definizione della vista tabella da utilizzare.|
|[Elemento SelectionSetName per EntrySelectedBy per Table ((Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica un set di tipi .NET che utilizzano questa definizione della vista tabella.|
|[Elemento TypeName per EntrySelectedBy per Table ((Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che usa questa definizione della vista tabella.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableRowEntry per Table ((Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Definisce i dati visualizzati in una riga della tabella.|

## <a name="remarks"></a>Osservazioni

È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per una definizione di vista tabella. Non esiste un limite massimo per il numero di elementi figlio che è possibile usare.

Le condizioni di selezione vengono usate per definire una condizione che deve esistere per la definizione da usare, ad esempio quando un oggetto ha una proprietà specifica o che un valore di proprietà o uno script specifico restituisce `true`. Per ulteriori informazioni sulle condizioni di selezione, vedere [definizione di condizioni per l'utilizzo di una voce o di un elemento della visualizzazione](./defining-conditions-for-displaying-data.md).

Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un elemento `TableRowEntry` usato per visualizzare le proprietà dell'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

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

[Creazione di una vista tabella](./creating-a-table-view.md)

[Elemento SelectionCondition per EntrySelectedBy per Table ((Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Elemento SelectionSetName per EntrySelectedBy per Table ((Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[Elemento TableRowEntry per Table ((Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Elemento TypeName per EntrySelectedBy per Table ((Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
