---
title: Elemento EntrySelectedBy per CustomEntry per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363860"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a>Elemento EntrySelectedBy per CustomEntry per GroupBy (formato)

Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format) elemento EntrySelectedBy per CustomEntry per GroupBy (Format)

## <a name="syntax"></a>Sintassi

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `EntrySelectedBy`. Per una definizione è necessario specificare almeno un tipo, un set di selezione o una condizione di selezione. Non esiste un limite massimo per il numero di elementi figlio che è possibile usare.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve esistere affinché questa definizione venga utilizzata.|
|[Elemento SelectionSetName per EntrySelectedBy per GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica un set di tipi .NET che utilizzano questa definizione del controllo.|
|[Elemento TypeName per EntrySelectedBy per GroupBy (Format)](./typename-element-for-entryselectedby-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che usa questa definizione del controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntry per CustomControl per GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Fornisce una definizione del controllo.|

## <a name="remarks"></a>Osservazioni

Le condizioni di selezione vengono usate per definire una condizione che deve esistere per la definizione da usare, ad esempio quando un oggetto ha una proprietà specifica o quando uno script o un valore di proprietà specifico restituisce `true`. Per ulteriori informazioni sulle condizioni di selezione, vedere [definizione di condizioni per l'utilizzo di una voce o di un elemento della visualizzazione](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[Elemento SelectionCondition per EntrySelectedBy per GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Elemento SelectionSetName per EntrySelectedBy per GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[Elemento TypeName per EntrySelectedBy per GroupBy (Format)](./typename-element-for-entryselectedby-for-groupby-format.md)

[Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
