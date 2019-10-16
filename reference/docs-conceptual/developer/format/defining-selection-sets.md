---
title: Definizione di set di selezione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368850"
---
# <a name="defining-selection-sets"></a>Definizione di set di selezione

Quando si creano più viste e controlli, è possibile definire set di oggetti definiti set di selezione. Un set di selezione consente di definire gli oggetti una volta, senza che sia necessario definirli ripetutamente per ogni visualizzazione o controllo. In genere, i set di selezione vengono usati quando si dispone di un set di oggetti .NET correlati. Ad esempio, il file di formattazione `FileSystem` (FileSystem. Format. ps1xml) definisce un set di selezione dei tipi di file system utilizzati da diverse visualizzazioni.

## <a name="where-selection-sets-are-defined-and-referenced"></a>Dove sono definiti e a cui viene fatto riferimento nei set di selezione

I set di selezione vengono definiti come parte dei dati comuni che possono essere utilizzati da tutte le visualizzazioni e i controlli definiti nel file di formattazione. Nell'esempio seguente viene illustrato come definire tre set di selezione.

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

È possibile fare riferimento a un set di selezione nei modi seguenti:

- Ogni visualizzazione dispone di un elemento `ViewSelectedBy` che definisce quali oggetti vengono visualizzati tramite la visualizzazione. L'elemento `ViewSelectedBy` ha un elemento figlio `SelectionSetName` che specifica il set di selezione usato da tutte le definizioni della visualizzazione. Non esiste alcuna restrizione al numero di set di selezione a cui è possibile fare riferimento da una vista.

- In ogni definizione di una vista o di un controllo, l'elemento `EntrySelectedBy` definisce quali oggetti vengono visualizzati tramite tale definizione. Una vista o un controllo ha in genere una sola definizione, quindi gli oggetti vengono definiti dall'elemento `ViewSelectedBy`. L'elemento `EntrySelectedBy` della definizione dispone di un elemento figlio `SelectionSetName` che specifica il set di selezione. Se si specifica il set di selezione per una definizione, non è possibile specificare gli altri elementi figlio dell'elemento `EntrySelectedBy`.

- In ogni definizione di una vista o di un controllo, è possibile usare l'elemento `SelectionCondition` per specificare una condizione per quando viene usata la definizione. L'elemento `SelectionCondition` ha un elemento figlio `SelectionSetName` che specifica il set di selezione che attiva la condizione. La condizione viene attivata quando viene visualizzato uno degli oggetti definiti nel set di selezione. Per ulteriori informazioni sull'impostazione di queste condizioni, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="selection-set-example"></a>Esempio di set di selezione

Nell'esempio seguente viene illustrato un set di selezione che viene ricavato direttamente dal file di formattazione `FileSystem` fornito da Windows PowerShell. Per altre informazioni sui file di formattazione di Windows PowerShell, vedere [file di formattazione di Windows PowerShell](./powershell-formatting-files.md).

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

Viene fatto riferimento al set di selezione precedente nell'elemento `ViewSelectedBy` di una vista tabella.

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

 Non esiste alcun limite al numero di set di selezione che è possibile definire. Per creare un set di selezione vengono utilizzati gli elementi XML seguenti.

- L'elemento [SelectionSets](./selectionsets-element-format.md) definisce i set di oggetti .NET a cui fanno riferimento le viste e i controlli del file di formattazione.

- L'elemento [SelectionSet](./selectionset-element-format.md) definisce un singolo set di oggetti .NET.

- L'elemento [Name](./name-element-for-selectionset-format.md) specifica il nome utilizzato per fare riferimento al set di selezione.

- L'elemento [types](./types-element-for-selectionset-format.md) specifica i tipi .NET degli oggetti del set di selezione. (All'interno dei file di formattazione, gli oggetti vengono specificati dal tipo .NET.)

 Gli elementi XML seguenti vengono utilizzati per specificare un set di selezione.

- L'elemento seguente specifica il set di selezione da usare in tutte le definizioni della vista:

    - [Elemento SelectionSetName per ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md)

    - [Elemento SelectionSetName per EntrySelectedBy per GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- Gli elementi seguenti specificano il set di selezione usato da una singola definizione di visualizzazione:

    - [Elemento SelectionSetName per EntrySelectedBy per ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [Elemento SelectionSetName per EntrySelectedBy per Table ((Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [Elemento SelectionSetName per EntrySelectedBy per WideControl (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [Elemento SelectionSetName per EntrySelectedBy per CustomControl per View (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- Gli elementi seguenti specificano il set di selezione usato dalle definizioni di controllo comuni e di visualizzazione:

    - [Elemento SelectionSetName per EntrySelectedBy per i controlli per la visualizzazione (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [Elemento SelectionSetName per EntrySelectedBy per i controlli per la configurazione (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- Gli elementi seguenti specificano il set di selezione usato quando si definisce l'oggetto da espandere:

    - [Elemento SelectionSetName per EntrySelectedBy per EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Gli elementi seguenti specificano il set di selezione usato dalle condizioni di selezione.

    - [Elemento SelectionSetName per SelectionCondition per i controlli per la configurazione (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [Elemento SelectionSetName per SelectionCondition per i controlli per la visualizzazione (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [Elemento SelectionSetName per SelectionCondition per CustomControl per View (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per ListEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per Table ((Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [Elemento SelectionSetName per SelectionCondition per GroupBy (Format)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>Vedere anche

[SelectionSets](./selectionsets-element-format.md)

[SelectionSet](./selectionset-element-format.md)

[Nome](./name-element-for-selectionset-format.md)

[Tipi](./types-element-for-selectionset-format.md)

[File di formattazione di PowerShell](./powershell-formatting-files.md)

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Scrittura di un file di formattazione e di tipi di PowerShell](./writing-a-powershell-formatting-file.md)
