---
title: La definizione di set di selezione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066312"
---
# <a name="defining-selection-sets"></a>Definizione di set di selezione

Durante la creazione di più controlli e visualizzazioni, è possibile definire set di oggetti che vengono definiti come set di selezione. Un set di selezione consente di definire gli oggetti di una sola volta, senza la necessità di definire più volte per ogni vista o un controllo. In genere, i set di selezione vengono usati quando si dispone di un set di oggetti .NET correlati. Ad esempio, il `FileSystem` file di formattazione (FileSystem.format.ps1xml) definisce un set di selezione dei tipi di sistema file che usano diverse visualizzazioni.

## <a name="where-selection-sets-are-defined-and-referenced"></a>In cui set di selezione sono definiti e riferimento

Set di selezione vengono definite come parte dei dati comuni che possono essere utilizzati da tutte le visualizzazioni e i controlli definiti nel file di formattazione. Nell'esempio seguente viene illustrato come definire tre set di selezione.

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

È possibile fare riferimento a una selezione imposta nei modi seguenti:

- Ogni visualizzazione dispone di un `ViewSelectedBy` elemento che definisce quali oggetti vengono visualizzati tramite la vista. Il `ViewSelectedBy` elemento ha un `SelectionSetName` elemento figlio che specifica la selezione del set che tutte le definizioni dell'utilizzo di visualizzazione. Non vi è alcuna restrizione al numero di set di selezione che è possibile fare riferimento da una vista.

- In ogni definizione di una vista o di un controllo, il `EntrySelectedBy` elemento definisce gli oggetti che vengono visualizzati tramite tale definizione. In genere una vista o un controllo dispone di una sola definizione in modo che gli oggetti vengono definiti dal `ViewSelectedBy` elemento. Il `EntrySelectedBy` della definizione dell'elemento ha un `SelectionSetName` elemento figlio che specifica il set di selezione. Se si specifica l'insieme per una definizione di selezione, è possibile specificare uno degli altri elementi figlio del `EntrySelectedBy` elemento.

- In ogni definizione di una vista o di un controllo, il `SelectionCondition` elemento può essere usato per specificare una condizione per quando viene utilizzata la definizione. Il `SelectionCondition` elemento ha un `SelectionSetName` elemento figlio che specifica set di selezione attiva la condizione. La condizione viene attivata quando viene visualizzato uno degli oggetti definiti nel set di selezione. Per altre informazioni su come impostare queste condizioni, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).

## <a name="selection-set-example"></a>Esempio di Set di selezione

L'esempio seguente mostra un set di selezione che viene recuperato direttamente dal `FileSystem` formattazione file fornito da Windows PowerShell. Per altre informazioni su altri PowerShell di Windows, file di formattazione, vedere [file di formattazione di Windows PowerShell](./powershell-formatting-files.md).

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

Il set di selezione precedente fa riferimento il `ViewSelectedBy` elemento della visualizzazione di una tabella.

```xml
<ViewDefinitions>
  <View>
    <Name>Files</Name>
    <ViewSelectedBy>
      <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="xml-elements"></a>Elementi XML

 Non sono previsti limiti al numero di set di selezione che è possibile definire. Gli elementi XML seguenti vengono utilizzati per creare un set di selezione.

- Il [SelectionSets](./selectionsets-element-format.md) elemento definisce i set di oggetti .NET che fanno riferimento le viste e i controlli del file di formattazione.

- Il [SelectionSet](./selectionset-element-format.md) elemento definisce un singolo set di oggetti .NET.

- Il [nome](./name-element-for-selectionset-format.md) elemento specifica il nome utilizzato per fare riferimento a set di selezione.

- Il [tipi](./types-element-for-selectionset-format.md) elemento specifica i tipi .NET degli oggetti del set di selezione. (All'interno di file di formattazione, gli oggetti vengono specificati in base al tipo .NET).

 Gli elementi XML seguenti consentono di specificare un set di selezione.

- L'elemento seguente specifica la selezione di set da utilizzare in tutte le definizioni della vista:

    - [Elemento SelectionSetName per ViewSelectedBy (formato)](./selectionsetname-element-for-viewselectedby-format.md)

    - [Elemento SelectionSetName per EntrySelectedBy per GroupBy (formato)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- Gli elementi seguenti specificano il set di selezione utilizzato dalla definizione di una singola vista:

    - [Elemento SelectionSetName per EntrySelectedBy per ListControl (formato)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [Elemento SelectionSetName per EntrySelectedBy per Table (formato)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [Elemento SelectionSetName per EntrySelectedBy per WideControl (formato)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [Elemento SelectionSetName per EntrySelectedBy per CustomControl per visualizzazione (formato)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- Gli elementi seguenti specificano il set di selezione utilizzato da più comuni e visualizzare le definizioni di controllo:

    - [Elemento SelectionSetName per EntrySelectedBy per i controlli per la visualizzazione (formato)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [Elemento SelectionSetName per EntrySelectedBy per i controlli per la configurazione (formato)](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- Gli elementi seguenti specificano il set di selezione utilizzato quando si definisce l'oggetto da espandere:

    - [Elemento SelectionSetName per EntrySelectedBy per EnumerableExpansion (formato)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Gli elementi seguenti specificano il set di selezione utilizzato da condizioni di selezione.

    - [Elemento SelectionSetName per SelectionCondition per i controlli per la configurazione (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [Elemento SelectionSetName per SelectionCondition per i controlli per la visualizzazione (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [Elemento SelectionSetName per SelectionCondition per CustomControl per visualizzazione (formato)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per ListEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per Table (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [Elemento SelectionSetName per SelectionCondition per GroupBy (formato)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>Vedere anche

[SelectionSets](./selectionsets-element-format.md)

[SelectionSet](./selectionset-element-format.md)

[Name](./name-element-for-selectionset-format.md)

[Tipi](./types-element-for-selectionset-format.md)

[File di formattazione di PowerShell](./powershell-formatting-files.md)

[La definizione delle condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md)

[La scrittura di una formattazione di PowerShell e dei tipi](./writing-a-powershell-formatting-file.md)
