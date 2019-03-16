---
title: Riferimento allo Schema XML di formato | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac6f7aaa-d0cc-4c7b-a341-85e736174579
caps.latest.revision: 21
ms.openlocfilehash: 437b3d6bb62fdd3a74f3392ec71df360c01a1974
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056652"
---
# <a name="format-schema-xml-reference"></a>Guida di riferimento XML dello schema di formattazione

Negli argomenti di questa sezione vengono descritti gli elementi XML utilizzati per la formattazione (Format.ps1xml file). File di formattazione definiscono la modalità di visualizzazione; l'oggetto .NET l'oggetto stesso non cambiano.

## <a name="in-this-section"></a>Contenuto della sezione

[Elemento Alignment per TableColumnHeader per Table (formato)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) definisce la modalità di visualizzazione dati in un'intestazione di colonna.

[Elemento Alignment per TableColumnItem per Table (formato)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) definisce la modalità di visualizzazione di dati nella riga.

[AutoSize (elemento) per Table (formato)](./autosize-element-for-tablecontrol-format.md) specifica se la dimensione della colonna e il numero di colonne viene regolate in base alla dimensione dei dati.

[AutoSize (elemento) per WideControl (formato)](./autosize-element-for-widecontrol-format.md) specifica se la dimensione della colonna e il numero di colonne viene regolate in base alla dimensione dei dati.

[Elemento ColumnNumber per WideControl (formato)](./columnnumber-element-for-widecontrol-format.md) specifica il numero di colonne visualizzate in visualizzazione estesa.

[Elemento di configurazione (formato)](./configuration-element-format.md) rappresenta l'elemento di livello superiore del file di formattazione.

[Controllare l'elemento per i controlli per la configurazione (formato)](./control-element-for-controls-for-configuration-format.md) definisce un controllo comune che può essere usato da tutte le visualizzazioni del file di formattazione e il nome utilizzato per fare riferimento al controllo.

[Controllare l'elemento per i controlli per la visualizzazione (formato)](./control-element-for-controls-for-view-format.md) definisce un controllo che può essere utilizzato per la visualizzazione e il nome utilizzato per fare riferimento al controllo.

[Controlla l'elemento di configurazione (formato)](./controls-element-for-configuration-format.md) definisce i controlli comuni che possono essere usati da tutte le visualizzazioni del file di formattazione.

[Controlla l'elemento di visualizzazione (formato)](./controls-element-for-view-format.md) definisce i controlli di visualizzazione che possono essere usati da una visualizzazione specifica.

[Elemento CustomControl per il controllo per la configurazione (formato)](./customcontrol-element-for-control-for-controls-for-configuration-format.md) definisce un controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento CustomControl per il controllo per i controlli per la visualizzazione (formato)](./customcontrol-element-for-control-for-controls-for-view-format.md) definisce un controllo che viene utilizzato dalla visualizzazione.

[Elemento CustomControl per GroupBy (formato)](./customcontrol-element-for-groupby-format.md) definisce il controllo personalizzato che consente di visualizzare il nuovo gruppo.

[Elemento CustomControl (formato)](./customcontrol-element-for-groupby-format.md) definisce un formato di controllo personalizzato per la visualizzazione.

[Elemento CustomControlName per ExpressionBinding per i controlli per la configurazione (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md) specifica il nome di un controllo comune. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento CustomControlName per ExpressionBindine per i controlli per la visualizzazione (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md) specifica il nome di un controllo comune o un controllo di visualizzazione. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento CustomControlName di GroupBy (formato)](./customcontrolname-element-for-groupby-format.md) specifica il nome di un controllo personalizzato che consente di visualizzare il nuovo gruppo. Questo elemento viene usato quando si definisce una tabella, elenco, visualizzazione controllo wide o personalizzato.

[Elemento CustomEntry per CustomControl per i controlli per la configurazione (formato)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md) fornisce una definizione del controllo comune. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md) fornisce una definizione del controllo. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento CustomEntry per CustomEntries per visualizzazione (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md) fornisce una definizione della vista del controllo personalizzato.

[Elemento CustomEntry per CustomControl per GroupBy (formato)](./customentry-element-for-customcontrol-for-groupby-format.md) fornisce una definizione del controllo. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento CustomEntries per CustomControl per la configurazione (formato)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md) fornisce le definizioni di un controllo comune. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento CustomEntries per CustomControl per i controlli per la visualizzazione (formato)](./customentries-element-for-customcontrol-for-controls-for-view-format.md) fornisce le definizioni per il controllo. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento CustomEntries per CustomControl per GroupBy (formato)](./customentries-element-for-customcontrol-for-groupby-format.md) fornisce le definizioni per il controllo. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento CustomEntries per CustomControl per visualizzazione (formato)](./customentries-element-for-customcontrol-for-view-format.md) fornisce le definizioni della vista del controllo personalizzato. La visualizzazione controlli personalizzati è necessario specificare una o più definizioni.

[Elemento CustomItem per CustomEntry per i controlli per la configurazione](./customitem-element-for-customentry-for-controls-for-configuration-format.md) definisce quali dati vengono visualizzati dal controllo e la modalità di visualizzazione. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato)](./customitem-element-for-customentry-for-controls-for-view-format.md) definisce quali dati vengono visualizzati dal controllo e la modalità di visualizzazione. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento CustomItem per CustomEntry per visualizzazione (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md) definisce quali dati vengono visualizzati dalla visualizzazione del controllo personalizzato e la modalità di visualizzazione. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

[Elemento CustomItem per CustomEntry per GroupBy (formato)](./customitem-element-for-customentry-for-groupby-format.md) definisce quali dati vengono visualizzati dalla visualizzazione del controllo personalizzato e la modalità di visualizzazione. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento DefaultSettings (formato)](./defaultsettings-element-format.md) definisce le impostazioni comuni che si applicano a tutte le visualizzazioni del file di formattazione. Impostazioni comuni includono la visualizzazione di errori, la disposizione del testo in tabelle, che definisce come vengono espanse le raccolte e così via.

[Elemento DisplayError (formato)](./displayerror-element-format.md) specifica che la stringa #ERR viene visualizzata quando si verifica un errore la visualizzazione di una porzione di dati.

[Elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (formato)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md) definisce i tipi .NET che usano la definizione di controllo comune o la condizione che deve essere presente per questo controllo da utilizzare. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (formato)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md) definisce i tipi .NET che usano questa definizione di controllo o la condizione che deve essere presente per questa definizione da usare. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento EntrySelectedBy per CustomEntry per visualizzazione (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) definisce i tipi .NET che usano questa voce personalizzata o la condizione che deve essere presente per questa voce da usare.

[Elemento EntrySelectedBy per EnumerableExpansion (formato)](./entryselectedby-element-for-enumerableexpansion-format.md) definisce i tipi .NET che usano questa definizione o la condizione che deve essere presente per questa definizione da usare.

[Elemento EntrySelectedBy per CustomEntry per GroupBy (formato)](./entryselectedby-element-for-customentry-for-groupby-format.md) definisce i tipi .NET che usano questa definizione di controllo o la condizione che deve essere presente per questa definizione da usare. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento EntrySelectedBy per ListEntry per ListControl (formato)](./entryselectedby-element-for-listentry-for-listcontrol-format.md) definisce i tipi .NET che usano questa definizione di visualizzazione elenco o la condizione che deve essere presente per questa definizione da usare. Nella maggior parte dei casi è necessaria una sola definizione per una visualizzazione elenco. Tuttavia, è possibile fornire più definizioni per la visualizzazione elenco se si desidera utilizzare la stessa visualizzazione elenco per visualizzare dati diversi per oggetti diversi.

[Elemento EntrySelectedBy per TableRowEntry (formato)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) definisce i tipi .NET nella riga vengono visualizzati i cui valori di proprietà.

[Elemento EntrySelectedBy per WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md) definisce i tipi .NET che usano questa definizione di visualizzazione estesa o la condizione che deve essere presente per questa definizione da usare.

[Elemento EnumerableExpansion (formato)](./enumerableexpansion-element-format.md) definisce raccolta .NET come specifica gli oggetti vengono espansi quando vengono visualizzati in una vista.

[Elemento EnumerableExpansions (formato)](./enumerableexpansions-element-format.md) definisce come oggetti della raccolta .NET vengono espanse quando vengono visualizzati in una vista.

[Elemento EnumerateCollection per ExpressionBinding per i controlli per la configurazione (formato)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md) specificato che gli elementi delle raccolte vengono visualizzati dal controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento EnumerateCollection per ExpressionBinding per i controlli per la visualizzazione (formato)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md) specificato vengono visualizzati gli elementi delle raccolte. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento EnumerateCollection per l'espressione di associazione per CustomControl per visualizzazione (formato)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md) specifica che vengono visualizzati gli elementi delle raccolte. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

[Elemento EnumerateCollection per ExpressionBinding per GroupBy (formato)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) specifica che vengono visualizzati gli elementi delle raccolte. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Espandere l'elemento (formato)](./expand-element-format.md) specifica come viene espanso l'oggetto raccolta per questa definizione.

[Elemento ExpressionBinding per CustomItem per i controlli per la configurazione (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md) definisce i dati che vengano visualizzati dal controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md) definisce i dati che vengano visualizzati dal controllo. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento ExpressionBinding per CustomItem per CustomControl per visualizzazione (formato)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md) definisce i dati che vengano visualizzati dal controllo. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

[Elemento ExpressionBinding per CustomItem per GroupBy (formato)](./expressionbinding-element-for-customitem-for-groupby-format.md) definisce i dati che vengano visualizzati dal controllo. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento FirstLineHanging per Frame per i controlli per la configurazione (formato)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) specifica quanti caratteri la prima riga di dati verrà spostata a sinistra. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento FirstLineHanging della cornice di controlli di visualizzazione (formato)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) specifica quanti caratteri la prima riga di dati verrà spostata a sinistra. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento FirstLineHanging per Frame per CustomControl per visualizzazione (formato)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) specifica quanti caratteri la prima riga di dati verrà spostata a sinistra. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

[Elemento FirstLineHanging per Frame per GroupBy (formato)](./firstlinehanging-element-for-frame-for-groupby-format.md) specifica quanti caratteri la prima riga di dati verrà spostata a sinistra. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento FirstLineIndent per Frame per i controlli per la configurazione (formato)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) specifica quanti caratteri la prima riga di dati verrà spostata a destra. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento FirstLineIndent della cornice di controlli di visualizzazione (formato)](./firstlineindent-element-for-frame-for-controls-for-view-format.md) specifica quanti caratteri la prima riga di dati verrà spostata a destra. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) specifica quanti caratteri la prima riga di dati verrà spostata a destra. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

[Elemento FirstLineIndent per Frame per GroupBy (formato)](./firstlineindent-element-for-frame-for-groupby-format.md) specifica quanti caratteri la prima riga di dati verrà spostata a destra. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento FormatString per ListItem (formato)](./formatstring-element-for-listitem-for-listcontrol-format.md) specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script.

[Elemento FormatString per TableColumnItem (formato)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md) specifica un modello di formato che definisce come viene visualizzato il valore di proprietà o lo script della tabella.

[Elemento FormatString per WideItem per WideControl (formato)](./formatstring-element-for-wideitem-for-widecontrol-format.md) specifica un modello di formato che definisce come viene visualizzato il valore di proprietà o lo script nella visualizzazione.

[Elemento dei frame per CustomItem per i controlli per la configurazione (formato)](./frame-element-for-customitem-for-controls-for-configuration-format.md) definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento dei frame per CustomItem per i controlli per la visualizzazione (formato)](./frame-element-for-customitem-for-controls-for-view-format.md) definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento dei frame per CustomItem per CustomControl per visualizzazione (formato)](./frame-element-for-customitem-for-customcontrol-for-view-format.md) definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

[Elemento dei frame per CustomItem per GroupBy (formato)](./frame-element-for-customitem-for-groupby-format.md) definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento GroupBy per visualizzazione (formato)](./groupby-element-for-view-format.md) definisce la modalità di visualizzazione di un nuovo gruppo di oggetti Windows PowerShell.

[Elemento HideTableHeaders (formato)](./hidetableheaders-element-format.md) specifica che le intestazioni della tabella non vengono visualizzate.

[Elemento ItemSelectionCondition per ExpressionBinding per i controlli per la configurazione (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md) definisce la condizione che deve essere presente per questo controllo da utilizzare. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento ItemSelectionCondition ExpressionBinding per i controlli per la visualizzazione (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md) definisce la condizione che deve essere presente per questo controllo da utilizzare. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento ItemSelectionCondition per l'espressione di associazione per CustomControl per visualizzazione (formato)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md) definisce la condizione che deve essere presente per questo controllo da utilizzare. Non sono previsti limiti al numero di condizioni di selezione che possono essere specificati per un elemento del controllo. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

[Elemento ItemSelectionCondition per ExpressionBinding per GroupBy (formato)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md) definisce la condizione che deve essere presente per questo controllo da utilizzare. Non sono previsti limiti al numero di condizioni di selezione che possono essere specificati per un elemento del controllo. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento ItemSelectionCondition per ListItem (formato)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) definisce la condizione che deve essere presente per questo elemento di elenco da utilizzare.

[L'etichetta di elemento per elemento ListItem per ListControl(Format)](./label-element-for-listitem-for-listcontrol-format.md) specifica l'etichetta per il valore della proprietà o script della riga.

[L'etichetta di elemento per GroupBy (formato)](./label-element-for-groupby-format.md) specifica un'etichetta che viene visualizzata quando viene rilevato un nuovo gruppo.

[L'etichetta di elemento per TableColumnHeader (formato)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) definisce l'etichetta che viene visualizzato nella parte superiore di una colonna.

[Elemento LeftIndent per Frame per i controlli per la configurazione (formato)](./leftindent-element-for-frame-for-controls-for-configuration-format.md) specifica quanti caratteri di dati viene spostati dal margine sinistro. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento LeftIndent della cornice di controlli di visualizzazione (formato)](./leftindent-element-for-frame-for-controls-for-view-format.md) specifica quanti caratteri di dati viene spostati dal margine sinistro. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento LeftIndent per Frame per CustomControl per visualizzazione (formato)](./leftindent-element-for-frame-for-customcontrol-for-view-format.md) specifica quanti caratteri di dati viene spostati dal margine sinistro. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

[Elemento LeftIndent per Frame per GroupBy (formato)](./leftindent-element-for-frame-for-groupby-format.md) specifica quanti caratteri di dati viene spostati dal margine sinistro. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento dell'oggetto ListControl (formato)](./listcontrol-element-format.md) definisce un formato di elenco per la visualizzazione.

[Elemento ListEntry (formato)](./listentry-element-for-listcontrol-format.md) fornisce una definizione della visualizzazione elenco.

[Elemento ListEntries (formato)](./listentries-element-for-listcontrol-format.md) definisce come vengono visualizzate le righe della visualizzazione elenco.

[Elemento ListItem (formato)](./listitem-element-for-listitems-for-listcontrol-format.md) definisce proprietà o script il cui valore viene visualizzato in una riga della visualizzazione elenco.

[Elemento ListItems (formato)](./listitems-element-for-listentry-for-listcontrol-format.md) definisce le proprietà e gli script che vengono visualizzati nella visualizzazione elenco.

[Nome di elemento per il controllo per i controlli per la configurazione (formato)](./name-element-for-control-for-controls-for-configuration-format.md) specifica il nome del controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Nome elemento SelectionSet (formato)](./name-element-for-selectionset-format.md) specifica il nome utilizzato per fare riferimento il set di selezione.

[Nome elemento di visualizzazione (formato)](./name-element-for-view-format.md) specifica il nome utilizzato per identificare la vista.

[Elemento di una nuova riga per CustomItem per i controlli per la configurazione (formato)](./newline-element-for-customitem-for-controls-for-configuration-format.md) aggiunge una riga vuota alla visualizzazione del controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento di una nuova riga per CustomItem per i controlli per la visualizzazione (formato)](./newline-element-for-customitem-for-controls-for-view-format.md) aggiunge una riga vuota alla visualizzazione del controllo. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento di una nuova riga per CustomItem per CustomControl per visualizzazione (formato)](./newline-element-for-customitem-for-customcontrol-for-view-format.md) aggiunge una riga vuota alla visualizzazione del controllo. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

[Elemento di una nuova riga per CustomItem per GroupBy (formato)](./newline-element-for-customitem-for-groupby-format.md) aggiunge una riga vuota alla visualizzazione del controllo. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento PropertyName per ExpressionBinding per i controlli per la configurazione (formato)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md) specifica la proprietà .NET il cui valore viene visualizzato per il controllo comune. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento PropertyName per ExpressionBinding per i controlli per la visualizzazione (formato)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md) specifica la proprietà .NET il cui valore viene visualizzato dal controllo. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento PropertyName per ExpressionBinding per CustomControl per visualizzazione (formato)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md) specifica la proprietà .NET il cui valore viene visualizzato dal controllo. Questo elemento viene usato quando si definisce una vista di controllo personalizzato

[Elemento PropertyName per ExpressionBinding per GroupBy (formato)](./propertyname-element-for-expressionbinding-for-groupby-format.md) specifica la proprietà .NET il cui valore viene visualizzato dal controllo. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento PropertyName per GroupBy (formato)](./propertyname-element-for-groupby-format.md) specifica la proprietà .NET che avvia un nuovo gruppo ogni volta che cambia il relativo valore.

[Elemento PropertyName per ItemSeclectionCondition per i controlli per la configurazione (formato)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene utilizzato il controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento PropertyName per ItemSelectionCondition per i controlli per la visualizzazione (formato)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene utilizzato il controllo. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento PropertyName per ItemSelectionCondition per CustomControl per visualizzazione (formato](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene utilizzato il controllo. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

[Elemento PropertyName per ItemSelectionCondition per GroupBy (formato)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene utilizzato il controllo. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento PropertyName per ItemSelectionCondition per ListItem (formato)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md) specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene utilizzata la vista. Questo elemento viene usato quando si definisce una visualizzazione elenco.

[Elemento PropertyName per ListItem per ListControl (formato)](./propertyname-element-for-listitem-for-listcontrol-format.md) specifica la proprietà .NET il cui valore viene visualizzato nell'elenco.

[Elemento PropertyName per SelectionCondition per EntrySelectedBy per ListEntry (formato)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md) specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e la voce viene usata. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento PropertyName per SelectionCondition per i controlli per la visualizzazione (formato)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md) specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e la voce viene usata. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento PropertyName per SelectionCondition per CustomControl per visualizzazione (formato)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md) specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene utilizzata la definizione. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

[Elemento PropertyName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene utilizzata la definizione.

[Elemento PropertyName per SelectionCondition per GroupBy (formato)](./propertyname-element-for-selectioncondition-for-groupby-format.md) specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene utilizzata la definizione. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento PropertyName per SelectionCondition per EntrySelectedBy per ListEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene usata la voce dell'elenco.

[Elemento PropertyName per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md) specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene usata la voce della tabella.

[Elemento PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando viene restituito `true`, viene soddisfatta la condizione e viene utilizzata la definizione.

[Elemento PropertyName per TableColumnItem (formato)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) specifica la proprietà il cui valore viene visualizzato nella colonna della riga.

[Elemento PropertyName per WideItem (formato)](./propertyname-element-for-wideitem-for-widecontrol-format.md) specifica la proprietà dell'oggetto il cui valore viene visualizzato in visualizzazione estesa.

[Elemento RightIndent per Frame per i controlli per la configurazione (formato)](./rightindent-element-for-frame-for-controls-for-configuration-format.md) specifica quanti caratteri di dati viene spostati dal margine destro. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento RightIndent della cornice di controlli di visualizzazione (formato)](./rightindent-element-for-frame-for-controls-for-view-format.md) specifica quanti caratteri di dati viene spostati dal margine destro. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento RightIndent](./rightindent-element-for-frame-for-customcontrol-for-view-format.md) specifica quanti caratteri di dati viene spostati dal margine destro. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

[Elemento RightIndent per Frame per GroupBy (formato)](./rightindent-element-for-frame-for-groupby-format.md) specifica quanti caratteri di dati viene spostati dal margine destro. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento ScriptBlock per ExpressionBinding per i controlli per la configurazione (formato)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md) specifica lo script il cui valore viene visualizzato per il controllo comune. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento ScriptBlock per ExpressionBinding per i controlli per la visualizzazione (formato)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md) specifica lo script il cui valore viene visualizzato dal controllo. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento ScriptBlock per ExpressionBinding per CustomCustomControl per visualizzazione (formato)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md) specifica lo script il cui valore viene visualizzato dal controllo. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

[Elemento ScriptBlock per ExpressionBinding per GroupBy (formato)](./scriptblock-element-for-expressionbinding-for-groupby-format.md) specifica lo script il cui valore viene visualizzato dal controllo. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento ScriptBlock per GroupBy (formato)](./scriptblock-element-for-groupby-format.md) specifica lo script che avvia un nuovo gruppo ogni volta che cambia il relativo valore.

[Elemento ScriptBlock per ItemSelectionCondition per i controlli per la configurazione (formato)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) specifica lo script che genera la condizione. Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene utilizzato il controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento ScriptBlock per ItemSelectionCondition per i controlli per la visualizzazione (formato)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) specifica lo script che genera la condizione. Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene utilizzato il controllo. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento ScriptBlock per ItemSelectionCondition per CustomControl per visualizzazione (formato)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) specifica lo script che genera la condizione. Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene utilizzato il controllo. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

[Elemento ScriptBlock per ItemSelectionCondition per GroupBy (formato)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) specifica lo script che genera la condizione. Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene utilizzato il controllo. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento ScriptBlock per ItemSelectionCondition per ListControl (formato)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) specifica lo script che genera la condizione. Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene usato l'elemento dell'elenco. Questo elemento viene usato quando si definisce una visualizzazione elenco.

[Elemento ScriptBlock per ListItem (formato)](./scriptblock-element-for-listitem-for-listcontrol-format.md) specifica lo script il cui valore viene visualizzato nella riga dell'elenco.

[Elemento ScriptBlock per SelectionCondition per i controlli per la configurazione (formato)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md) specifica lo script che genera la condizione. Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene utilizzata la definizione. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento ScriptBlock per SelectionCondition per i controlli per la visualizzazione (formato)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md) specifica lo script che genera la condizione. Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene utilizzata la definizione. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento ScriptBlock per SelectionCondition per CustomControl per visualizzazione (formato)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md) specifica lo script che genera la condizione. Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene utilizzata la definizione. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

[Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) specifica lo script che genera la condizione.

[Elemento ScriptBlock per SelectionCondition per GroupBy (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md) specifica lo script che genera la condizione. Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene utilizzata la definizione. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per ListEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) specifica lo script che genera la condizione. Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene usata la voce dell'elenco.

[Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) specifica il blocco di script che genera la condizione. Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene usata la voce della tabella.

[Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) specifica lo script che genera la condizione. Quando questo script viene valutato per `true`, viene soddisfatta la condizione e viene utilizzata la definizione di voce wide.

[Elemento ScriptBlock per TableColumnItem (formato)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) specifica lo script il cui valore viene visualizzato nella colonna della riga.

[Elemento ScriptBlock per WideItem (formato)](./scriptblock-element-for-wideitem-for-widecontrol-format.md) specifica lo script il cui valore viene visualizzato in visualizzazione estesa.

[Elemento SelectionCondition per EntrySelectedBy per CustomEntry per la configurazione (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md) definisce una condizione che deve essere presente per la definizione di un controllo comune da usare. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md) definisce una condizione che deve essere presente per la definizione di controllo da utilizzare. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento SelectionCondition per EntrySelectedBy per CustomControl per visualizzazione (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md) definisce una condizione che deve essere presente per una definizione di controllo da utilizzare. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

[Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md) definisce la condizione che deve essere presente per espandere gli oggetti dell'insieme di questa definizione.

[Elemento SelectionCondition per EntrySelectedBy per GroupBy (formato)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md) definisce una condizione che deve essere presente per una definizione di controllo da utilizzare. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento SelectionCondition per EntrySelectedBy per ListEntry (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) definisce la condizione che deve essere presente per usare questa definizione della visualizzazione elenco. Non sono previsti limiti al numero di condizioni di selezione che è possibile specificare per una definizione di elenco.

[Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (formato)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md) definisce la condizione che deve essere presente per l'utilizzo per questa definizione della visualizzazione della tabella. Non sono previsti limiti al numero di condizioni di selezione che è possibile specificare per una definizione di tabella.

[Elemento SelectionCondition per EntrySelectedBy per WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) definisce la condizione che deve essere presente per questa definizione da usare. Non sono previsti limiti al numero di condizioni di selezione che è possibile specificare per una definizione di voce wide.

[Elemento SelectionSet (formato)](./selectionset-element-format.md) definisce un set di oggetti .NET che possono fare riferimento il nome del set.

[Elemento SelectionSetName per EntrySelectedBy per i controlli per la configurazione (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) specifica un set di tipi .NET che usano questa definizione del controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento SelectionSetName per EntrySelectedBy per i controlli per la visualizzazione (formato)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md) specifica un set di tipi .NET che usano questa definizione del controllo. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento SelectionSetName per EntrySelectedBy per CustomEntry (formato)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md) specifica un set di oggetti .NET per la voce dell'elenco. Non sono previsti limiti al numero di set di selezione che è possibile specificare per una voce.

[Elemento SelectionSetName per EntrySelectedBy per EnumerableExpansion (formato)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md) specifica il set di tipi .NET che vengono espanse per questa definizione.

[Elemento SelectionSetName per EntrySelectedBy per GroupBy (formato)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md) specifica un set di oggetti .NET per la voce dell'elenco. Non sono previsti limiti al numero di set di selezione che è possibile specificare per una voce. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento SelectionSetName per EntrySelectedBy per ListEntry (formato)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) specifica un set di oggetti .NET per la voce dell'elenco. Non sono previsti limiti al numero di set di selezione che è possibile specificare per una voce.

[Elemento SelectionSetName per EntrySelectedBy per TableRowEntry (formato)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md) specifica un set di .NET tipi l'uso di questa voce della visualizzazione della tabella. Non sono previsti limiti al numero di set di selezione che è possibile specificare per una voce.

[Elemento SelectionSetName per EntrySelectedBy per WideEntry (formato)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md) specifica un set di oggetti .NET per la definizione. La definizione viene utilizzata ogni volta che viene visualizzato uno di questi oggetti.

[Elemento SelectionSetName per SelectionCondition per i controlli per la configurazione (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presentano, viene soddisfatta la condizione e l'oggetto viene visualizzato tramite questo controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento SelectionSetName per SelectionCondition per i controlli per la visualizzazione (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md) specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presentano, viene soddisfatta la condizione e l'oggetto viene visualizzato l'utilizzo di questo controllo. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento EntrySelectedBy per CustomEntry per visualizzazione (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presentano, viene soddisfatta la condizione e l'oggetto viene visualizzato l'utilizzo di questo controllo. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

[Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set sono presente, la condizione viene soddisfatta.

[Elemento SelectionSetName per SelectionCondition per GroupBy (formato)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md) specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presentano, viene soddisfatta la condizione e l'oggetto viene visualizzato tramite questo controllo. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per ListEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md) specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presentano, viene soddisfatta la condizione e l'oggetto viene visualizzato utilizzando questa definizione della visualizzazione elenco.

[Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presentano, viene soddisfatta la condizione e l'oggetto viene visualizzato utilizzando questa definizione della visualizzazione della tabella.

[Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presentano, viene soddisfatta la condizione e l'oggetto viene visualizzato utilizzando questa definizione della vista wide.

[Elemento SelectionSetName per ViewSelectedBy (formato)](./selectionsetname-element-for-viewselectedby-format.md) specifica un set di oggetti .NET che vengono visualizzati nella visualizzazione.

[Elemento SelectionSets (formato)](./selectionsets-element-format.md) definisce i set di oggetti .NET che possono essere utilizzati dalle visualizzazioni di formato singoli.

[Elemento ShowError (formato)](./showerror-element-format.md) specifica che il record di errore completo viene visualizzato quando si verifica un errore durante la visualizzazione di una porzione di dati.

[Elemento TableColumnHeader per TableHeaders per Table (formato)](./tablecolumnheader-element-format.md) definisce l'etichetta, la larghezza della colonna e l'allineamento dell'etichetta per una colonna della tabella.

[Elemento TableColumnItem (formato)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) definisce le proprietà il cui valore viene visualizzato nella colonna della riga di script.

[Elemento TableColumnItems (formato)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) definisce le proprietà o gli script i cui valori vengono visualizzati nella riga.

[Elemento Table (formato)](./tablecontrol-element-format.md) definisce un formato di tabella per una vista.

[Elemento TableHeaders (formato)](./tableheaders-element-format.md) definisce le intestazioni per le colonne di una tabella.

[Elemento TableRowEntries (formato)](./tablerowentries-element-for-tablecontrol-format.md) definisce le righe della tabella.

[Elemento TableRowEntry (formato)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) definisce i dati che viene visualizzati in una riga della tabella.

[Elemento di testo per CustomItem per i controlli per la configurazione (formato)](./text-element-for-customitem-for-controls-for-configuration-format.md) specifica testo che viene aggiunto ai dati che viene visualizzati dal controllo, ad esempio un'etichetta, le parentesi per racchiudere i dati e gli spazi per far rientrare i dati. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento di testo per CustomItem per i controlli per la visualizzazione (formato)](./text-element-for-customitem-for-controls-for-view-format.md) specifica testo che viene aggiunto ai dati che viene visualizzati dal controllo, ad esempio un'etichetta, le parentesi per racchiudere i dati e gli spazi per far rientrare i dati. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento di testo per CustomItem (formato)](./text-element-for-customitem-for-customview-for-view-format.md) specifica testo che viene aggiunto ai dati che viene visualizzati dal controllo, ad esempio un'etichetta, le parentesi per racchiudere i dati e gli spazi per far rientrare i dati. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

[Elemento di testo per CustomItem per GroupBy (formato)](./text-element-for-customitem-for-groupby-format.md) specifica testo che viene aggiunto ai dati che viene visualizzati dal controllo, ad esempio un'etichetta, le parentesi per racchiudere i dati e gli spazi per far rientrare i dati. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento TypeName per EntrySelectedBy per i controlli per la configurazione (formato)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md) specifica un tipo .NET che usa questa definizione del controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento TypeName per EntrySelectedBy per i controlli per la visualizzazione (formato)](./typename-element-for-entryselectedby-for-controls-for-view-format.md) specifica un tipo .NET che usa questa definizione del controllo. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento TypeName per EntrySelectedBy per CustomEntry per visualizzazione (formato)](./typename-element-for-entryselectedby-for-customentry-for-view-format.md) specifica un tipo .NET che usa questa definizione della vista del controllo personalizzato. Non sono previsti limiti al numero di tipi che possono essere specificati per una definizione.

[Elemento TypeName per EntrySelectedBy per EnumerableExpansion (formato)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md) specifica un tipo .NET che viene espanso per questa definizione. Questo elemento viene usato durante la definizione di impostazioni predefinite.

[Elemento TypeName per EntrySelectedBy per GroupBy (formato)](./typename-element-for-entryselectedby-for-groupby-format.md) specifica un tipo .NET che usa questa definizione del controllo personalizzato. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento TypeName per EntrySelectedBy per ListControl (formato)](./typename-element-for-entryselectedby-for-listcontrol-format.md) specifica un tipo .NET che usa questa voce della visualizzazione elenco. Non sono previsti limiti al numero di tipi che possono essere specificati per una voce dell'elenco.

[Elemento TypeName per EntrySelectedBy per TableRowEntry (formato)](./typename-element-for-entryselectedby-for-tablecontrol-format.md) specifica un tipo .NET che usa questa voce della visualizzazione della tabella. Non sono previsti limiti al numero di tipi che possono essere specificati per una voce della tabella.

[Elemento TypeName per EntrySelectedBy per WideEntry (formato)](./typename-element-for-entryselectedby-for-wideentry-format.md) specifica un tipo .NET per la definizione. La definizione viene utilizzata ogni volta che viene visualizzato questo oggetto.

[Elemento TypeName per SelectionCondition per i controlli per la configurazione (formato)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md) specifica un tipo .NET che attiva la condizione. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento TypeName per SelectionCondition per i controlli per la visualizzazione (formato)](./typename-element-for-selectioncondition-for-controls-for-view-format.md) specifica un tipo .NET che attiva la condizione. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

[Elemento TypeName per SelectionCondition per CustomControl per visualizzazione (formato)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md) specifica un tipo .NET che attiva la condizione. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

[Elemento TypeName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) specifica un tipo .NET che attiva la condizione.

[Elemento TypeName per SelectionCondition per GroupBy (formato)](./typename-element-for-selectioncondition-for-groupby-format.md) specifica un tipo .NET che attiva la condizione. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

[Elemento TypeName per SelectionCondition per EntrySelectedBy per ListControl (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) specifica un tipo .NET che attiva la condizione. Quando questo tipo è presente, viene usata la voce dell'elenco.

[Elemento TypeName per SelectionCondition per EntrySelectedBy per TableRowEntry (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) specifica un tipo .NET che attiva la condizione. Quando questo tipo è presente, viene soddisfatta la condizione e viene utilizzata la riga della tabella.

[Elemento TypeName per SelectionCondition per EntrySelectedBy per WideEntry (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) specifica un tipo .NET che attiva la condizione. Quando questo tipo è presente, la definizione viene utilizzata.

[TypeName (elemento) per tipi (formato)](./typename-element-for-types-format.md) specifica il tipo .NET dell'oggetto che appartiene al set di selezione.

[Elemento TypeName per ViewSelectedBy (formato)](./typename-element-for-viewselectedby-format.md) specifica un oggetto .NET che viene visualizzato nella visualizzazione.

[I tipi di elemento (formato)](./types-element-for-selectionset-format.md) definisce gli oggetti .NET nella selezione impostate.

[Visualizzare l'elemento (formato)](./view-element-format.md) definisce una vista che consente di visualizzare uno o più oggetti .NET.

[Elemento ViewDefinitions (formato)](./viewdefinitions-element-format.md) definisce le viste utilizzate per visualizzare gli oggetti.

[Elemento ViewSelectedBy (formato)](./viewselectedby-element-format.md) definisce gli oggetti .NET che vengono visualizzati nella visualizzazione.

[Elemento WideControl (formato)](./widecontrol-element-format.md) definisce un elenco di tutto (singolo valore) di formato per la visualizzazione. Questa vista sono riportati un singolo valore di proprietà o valore di uno script per ogni oggetto.

[Elemento WideEntries (formato)](./wideentries-element-for-widecontrol-format.md) fornisce le definizioni di visualizzazione estesa. La visualizzazione più ampia è necessario specificare una o più definizioni.

[Elemento WideEntry (formato)](./wideentry-element-for-widecontrol-format.md) fornisce una definizione della vista wide.

[Elemento WideItem (formato)](./wideitem-element-for-widecontrol-format.md) definisce le proprietà il cui valore viene visualizzato lo script.

[Larghezza elemento (formato)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) definisce la larghezza (in caratteri) di una colonna.

[Eseguire il wrapping elemento (formato)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) specifica che il testo che supera la larghezza della colonna viene visualizzato nella riga successiva.

[Elemento WrapTables (formato)](./wraptables-element-format.md) specifica che i dati in una cella della tabella vengano spostati alla riga successiva se i dati sono più lunghi rispetto alla larghezza della colonna.

## <a name="see-also"></a>Vedere anche

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
