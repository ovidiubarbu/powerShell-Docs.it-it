---
title: Informazioni di riferimento sul formato XML dello schema | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac6f7aaa-d0cc-4c7b-a341-85e736174579
caps.latest.revision: 21
ms.openlocfilehash: 437b3d6bb62fdd3a74f3392ec71df360c01a1974
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363720"
---
# <a name="format-schema-xml-reference"></a>Guida di riferimento XML dello schema di formattazione

Negli argomenti di questa sezione vengono descritti gli elementi XML utilizzati dai file di formattazione (file format. ps1xml). I file di formattazione definiscono la modalità di visualizzazione dell'oggetto .NET; non modificano l'oggetto stesso.

## <a name="in-this-section"></a>Contenuto della sezione

[Elemento Alignment per TableColumnHeader per Table ((Format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) Definisce la modalità di visualizzazione dei dati in un'intestazione di colonna.

[Elemento Alignment per TableColumnItem per Table ((Format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) Definisce la modalità di visualizzazione dei dati nella riga.

[Elemento AutoSize per Table ((Format)](./autosize-element-for-tablecontrol-format.md) Specifica se le dimensioni della colonna e il numero di colonne vengono regolate in base alle dimensioni dei dati.

[Elemento AutoSize per WideControl (Format)](./autosize-element-for-widecontrol-format.md) Specifica se le dimensioni della colonna e il numero di colonne vengono regolate in base alle dimensioni dei dati.

[Elemento ColumnNumber per WideControl (Format)](./columnnumber-element-for-widecontrol-format.md) Specifica il numero di colonne visualizzate nella visualizzazione estesa.

[Elemento Configuration (Format)](./configuration-element-format.md) Rappresenta l'elemento di livello principale del file di formattazione.

[Elemento Control per Controls per Configuration (Format)](./control-element-for-controls-for-configuration-format.md) Definisce un controllo comune che può essere utilizzato da tutte le visualizzazioni del file di formattazione e dal nome utilizzato per fare riferimento al controllo.

[Elemento Control per Controls per View (Format)](./control-element-for-controls-for-view-format.md) Definisce un controllo che può essere utilizzato dalla visualizzazione e dal nome utilizzato per fare riferimento al controllo.

[Elemento Controls per Configuration (Format)](./controls-element-for-configuration-format.md) Definisce i controlli comuni che possono essere utilizzati da tutte le visualizzazioni del file di formattazione.

[Elemento Controls per View (Format)](./controls-element-for-view-format.md) Definisce i controlli di visualizzazione che possono essere utilizzati da una visualizzazione specifica.

[Elemento CustomControl per Control per Configuration (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md) Definisce un controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento CustomControl per il controllo per i controlli per la visualizzazione (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md) Definisce un controllo utilizzato dalla visualizzazione.

[Elemento CustomControl per GroupBy (Format)](./customcontrol-element-for-groupby-format.md) Definisce il controllo personalizzato che Visualizza il nuovo gruppo.

[Elemento CustomControl (Format)](./customcontrol-element-for-groupby-format.md) Definisce un formato di controllo personalizzato per la visualizzazione.

[Elemento CustomControlName per ExpressionName per i controlli per la configurazione (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md) Specifica il nome di un controllo comune. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento CustomControlName per ExpressionBindine per i controlli per la visualizzazione (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md) Specifica il nome di un controllo comune o di un controllo di visualizzazione. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento CustomControlName di GroupBy (Format)](./customcontrolname-element-for-groupby-format.md) Specifica il nome di un controllo personalizzato usato per visualizzare il nuovo gruppo. Questo elemento viene utilizzato quando si definisce una tabella, un elenco, una visualizzazione di controlli Wide o Custom.

[Elemento CustomEntry per CustomControl per i controlli per la configurazione (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md) Fornisce una definizione del controllo comune. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md) Fornisce una definizione del controllo. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento CustomEntry per CustomEntries per View (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md) Fornisce una definizione della visualizzazione controlli personalizzata.

[Elemento CustomEntry per CustomControl per GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md) Fornisce una definizione del controllo. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento CustomEntries per CustomControl per Configuration (Format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md) Fornisce le definizioni di un controllo comune. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento CustomEntries per CustomControl per i controlli per la visualizzazione (Format)](./customentries-element-for-customcontrol-for-controls-for-view-format.md) Fornisce le definizioni per il controllo. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento CustomEntries per CustomControl per GroupBy (Format)](./customentries-element-for-customcontrol-for-groupby-format.md) Fornisce le definizioni per il controllo. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento CustomEntries per CustomControl per View (Format)](./customentries-element-for-customcontrol-for-view-format.md) Fornisce le definizioni della visualizzazione controlli personalizzata. La visualizzazione controlli personalizzata deve specificare una o più definizioni.

[Elemento CustomItem per CustomEntry per i controlli per la configurazione](./customitem-element-for-customentry-for-controls-for-configuration-format.md) Definisce quali dati vengono visualizzati dal controllo e come vengono visualizzati. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md) Definisce quali dati vengono visualizzati dal controllo e come vengono visualizzati. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento CustomItem per CustomEntry per View (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md) Definisce quali dati vengono visualizzati dalla visualizzazione controlli personalizzati e come vengono visualizzati. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

[Elemento CustomItem per CustomEntry per GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md) Definisce quali dati vengono visualizzati dalla visualizzazione controlli personalizzati e come vengono visualizzati. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento DefaultSettings (Format)](./defaultsettings-element-format.md) Definisce le impostazioni comuni che si applicano a tutte le visualizzazioni del file di formattazione. Le impostazioni comuni includono la visualizzazione di errori, il wrapping del testo nelle tabelle, la definizione del modo in cui le raccolte vengono espanse e altro.

[Elemento DisplayError (Format)](./displayerror-element-format.md) Specifica che la stringa #ERR viene visualizzata quando si verifica un errore durante la visualizzazione di una porzione di dati.

[Elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md) Definisce i tipi .NET che usano la definizione del controllo comune o la condizione che deve esistere affinché questo controllo venga usato. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md) Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento EntrySelectedBy per CustomEntry per View (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) Definisce i tipi .NET che utilizzano questa voce personalizzata o la condizione che deve esistere affinché questa voce venga utilizzata.

[Elemento EntrySelectedBy per EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md) Definisce i tipi .NET che utilizzano questa definizione o la condizione che deve esistere affinché questa definizione venga utilizzata.

[Elemento EntrySelectedBy per CustomEntry per GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md) Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento EntrySelectedBy per ListEntry per ListControl (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md) Definisce i tipi .NET che utilizzano questa definizione di visualizzazione elenco o la condizione che deve esistere affinché questa definizione venga utilizzata. Nella maggior parte dei casi è necessaria una sola definizione per una visualizzazione elenco. È tuttavia possibile specificare più definizioni per la visualizzazione elenco se si desidera utilizzare la stessa visualizzazione elenco per visualizzare dati diversi per oggetti diversi.

[Elemento EntrySelectedBy per TableRowEntry (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) Definisce i tipi .NET i cui valori delle proprietà vengono visualizzati nella riga.

[Elemento EntrySelectedBy per WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md) Definisce i tipi .NET che utilizzano questa definizione della visualizzazione estesa o la condizione che deve esistere affinché questa definizione venga utilizzata.

[Elemento EnumerableExpansion (Format)](./enumerableexpansion-element-format.md) Definisce la modalità di espansione degli oggetti raccolta .NET specifici quando vengono visualizzati in una visualizzazione.

[Elemento EnumerableExpansions (Format)](./enumerableexpansions-element-format.md) Definisce la modalità di espansione degli oggetti raccolta .NET quando vengono visualizzati in una visualizzazione.

[Elemento enumeratorcollection per Expressions per i controlli per Configuration (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md) Specifica che gli elementi delle raccolte vengono visualizzati dal controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento enumeratorcollection per expressiongroup per i controlli per la visualizzazione (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md) Specifica che vengono visualizzati gli elementi delle raccolte. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento enumeratorcollection per l'associazione di espressioni per CustomControl per View (Format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md) Specifica che gli elementi delle raccolte vengono visualizzati. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

[Elemento enumeratorcollection per expressiongroup per GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) Specifica che gli elementi delle raccolte vengono visualizzati. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento Expand (Format)](./expand-element-format.md) Specifica la modalità di espansione dell'oggetto raccolta per questa definizione.

[Elemento expressiongroup per CustomItem per i controlli per la configurazione (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md) Definisce i dati visualizzati dal controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento expressiongroup per CustomItem per i controlli per la visualizzazione (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md) Definisce i dati visualizzati dal controllo. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento expressiongroup per CustomItem per CustomControl per View (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md) Definisce i dati visualizzati dal controllo. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

[Elemento expressiongroup per CustomItem per GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md) Definisce i dati visualizzati dal controllo. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento FirstLineHanging per il frame per i controlli per la configurazione (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) Specifica il numero di caratteri che la prima riga di dati viene spostata a sinistra. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento FirstLineHanging del frame di controlli della visualizzazione (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) Specifica il numero di caratteri che la prima riga di dati viene spostata a sinistra. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento FirstLineHanging per frame per CustomControl per View (Format)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) Specifica il numero di caratteri che la prima riga di dati viene spostata a sinistra. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

[Elemento FirstLineHanging per frame per GroupBy (Format)](./firstlinehanging-element-for-frame-for-groupby-format.md) Specifica il numero di caratteri che la prima riga di dati viene spostata a sinistra. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento FirstLineIndent per il frame per i controlli per la configurazione (Format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) Specifica il numero di caratteri che la prima riga di dati viene spostata a destra. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento FirstLineIndent del frame di controlli della visualizzazione (Format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md) Specifica il numero di caratteri che la prima riga di dati viene spostata a destra. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) Specifica il numero di caratteri che la prima riga di dati viene spostata a destra. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

[Elemento FirstLineIndent per frame per GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md) Specifica il numero di caratteri che la prima riga di dati viene spostata a destra. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento FormatString per ListItem (Format)](./formatstring-element-for-listitem-for-listcontrol-format.md) Specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script.

[Elemento FormatString per TableColumnItem (Format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md) Specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script della tabella.

[Elemento FormatString per WideItem per WideControl (Format)](./formatstring-element-for-wideitem-for-widecontrol-format.md) Specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script nella visualizzazione.

[Elemento frame per CustomItem per i controlli per la configurazione (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md) Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento frame per CustomItem per i controlli per la visualizzazione (Format)](./frame-element-for-customitem-for-controls-for-view-format.md) Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento frame per CustomItem per CustomControl per View (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md) Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

[Elemento frame per CustomItem per GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md) Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento GroupBy per View (Format)](./groupby-element-for-view-format.md) Definisce la modalità di visualizzazione di un nuovo gruppo di oggetti in Windows PowerShell.

[Elemento HideTableHeaders (Format)](./hidetableheaders-element-format.md) Specifica che le intestazioni della tabella non vengono visualizzate.

[Elemento ItemSelectionCondition per ExpressionName per i controlli per la configurazione (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md) Definisce la condizione che deve esistere per il controllo da utilizzare. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento ItemSelectionCondition di Expression per i controlli per la visualizzazione (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md) Definisce la condizione che deve esistere per il controllo da utilizzare. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento ItemSelectionCondition per l'associazione di espressioni per CustomControl per View (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md) Definisce la condizione che deve esistere per il controllo da utilizzare. Non esiste alcun limite al numero di condizioni di selezione che è possibile specificare per un elemento di controllo. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

[Elemento ItemSelectionCondition per expressiongroup per GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md) Definisce la condizione che deve esistere per il controllo da utilizzare. Non esiste alcun limite al numero di condizioni di selezione che è possibile specificare per un elemento di controllo. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento ItemSelectionCondition per ListItem (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) Definisce la condizione che deve esistere per l'uso di questo elemento elenco.

[Elemento label per ListItem per ListControl (Format)](./label-element-for-listitem-for-listcontrol-format.md) Specifica l'etichetta per la proprietà o il valore dello script nella riga.

[Elemento label per GroupBy (Format)](./label-element-for-groupby-format.md) Specifica un'etichetta visualizzata quando viene rilevato un nuovo gruppo.

[Elemento label per TableColumnHeader (Format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) Definisce l'etichetta visualizzata nella parte superiore di una colonna.

[Elemento LeftIndent per il frame per i controlli per la configurazione (Format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md) Specifica il numero di caratteri spostati al di fuori del margine sinistro. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento LeftIndent del frame di controlli della visualizzazione (Format)](./leftindent-element-for-frame-for-controls-for-view-format.md) Specifica il numero di caratteri spostati al di fuori del margine sinistro. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento LeftIndent per frame per CustomControl per View (Format)](./leftindent-element-for-frame-for-customcontrol-for-view-format.md) Specifica il numero di caratteri spostati al di fuori del margine sinistro. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

[Elemento LeftIndent per frame per GroupBy (Format)](./leftindent-element-for-frame-for-groupby-format.md) Specifica il numero di caratteri spostati al di fuori del margine sinistro. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento ListControl (Format)](./listcontrol-element-format.md) Definisce un formato di elenco per la visualizzazione.

[Elemento ListEntry (Format)](./listentry-element-for-listcontrol-format.md) Fornisce una definizione della visualizzazione elenco.

[Elemento ListEntries (Format)](./listentries-element-for-listcontrol-format.md) Definisce la modalità di visualizzazione delle righe della visualizzazione elenco.

[Elemento ListItem (Format)](./listitem-element-for-listitems-for-listcontrol-format.md) Definisce la proprietà o lo script il cui valore viene visualizzato in una riga della visualizzazione elenco.

[Elemento ListItems (Format)](./listitems-element-for-listentry-for-listcontrol-format.md) Definisce le proprietà e gli script visualizzati nella visualizzazione elenco.

[Elemento Name per il controllo per i controlli per la configurazione (Format)](./name-element-for-control-for-controls-for-configuration-format.md) Specifica il nome del controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento Name per SelectionSet (Format)](./name-element-for-selectionset-format.md) Specifica il nome utilizzato per fare riferimento al set di selezione.

[Elemento Name per View (Format)](./name-element-for-view-format.md) Specifica il nome utilizzato per identificare la visualizzazione.

[Elemento NewLine per CustomItem per i controlli per la configurazione (Format)](./newline-element-for-customitem-for-controls-for-configuration-format.md) Aggiunge una riga vuota alla visualizzazione del controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento NewLine per CustomItem per i controlli per la visualizzazione (Format)](./newline-element-for-customitem-for-controls-for-view-format.md) Aggiunge una riga vuota alla visualizzazione del controllo. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento NewLine per CustomItem per CustomControl per View (Format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md) Aggiunge una riga vuota alla visualizzazione del controllo. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

[Elemento NewLine per CustomItem per GroupBy (Format)](./newline-element-for-customitem-for-groupby-format.md) Aggiunge una riga vuota alla visualizzazione del controllo. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento PropertyName per ExpressionName per i controlli per la configurazione (Format)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md) Specifica la proprietà .NET il cui valore viene visualizzato dal controllo comune. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento PropertyName per ExpressionName per i controlli per la visualizzazione (Format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md) Specifica la proprietà .NET il cui valore viene visualizzato dal controllo. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento PropertyName per Expression per CustomControl per View (Format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md) Specifica la proprietà .NET il cui valore viene visualizzato dal controllo. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata

[Elemento PropertyName per ExpressionName per GroupBy (Format)](./propertyname-element-for-expressionbinding-for-groupby-format.md) Specifica la proprietà .NET il cui valore viene visualizzato dal controllo. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento PropertyName per GroupBy (Format)](./propertyname-element-for-groupby-format.md) Specifica la proprietà .NET che avvia un nuovo gruppo ogni volta che il relativo valore viene modificato.

[Elemento PropertyName per ItemSeclectionCondition per i controlli per la configurazione (Format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene utilizzato il controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento PropertyName per ItemSelectionCondition per i controlli per la visualizzazione (Format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene utilizzato il controllo. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento PropertyName per ItemSelectionCondition per CustomControl per View (format](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene utilizzato il controllo. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

[Elemento PropertyName per ItemSelectionCondition per GroupBy (Format)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene utilizzato il controllo. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento PropertyName per ItemSelectionCondition per ListItem (Format)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md) Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene utilizzata la vista. Questo elemento viene utilizzato quando si definisce una visualizzazione elenco.

[Elemento PropertyName per ListItem per ListControl (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md) Specifica la proprietà .NET il cui valore viene visualizzato nell'elenco.

[Elemento PropertyName per SelectionCondition per EntrySelectedBy per ListEntry (Format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md) Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene usata la voce. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento PropertyName per SelectionCondition per i controlli per la visualizzazione (Format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md) Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene usata la voce. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento PropertyName per SelectionCondition per CustomControl per View (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md) Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene usata la definizione. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

[Elemento PropertyName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene usata la definizione.

[Elemento PropertyName per SelectionCondition per GroupBy (Format)](./propertyname-element-for-selectioncondition-for-groupby-format.md) Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene usata la definizione. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento PropertyName per SelectionCondition per EntrySelectedBy per ListEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene usata la voce dell'elenco.

[Elemento PropertyName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md) Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene utilizzata la voce della tabella.

[Elemento PropertyName per SelectionCondition per EntrySelectedBy per WideEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) Specifica la proprietà .NET che attiva la condizione. Quando questa proprietà è presente o quando restituisce `true`, la condizione viene soddisfatta e viene usata la definizione.

[Elemento PropertyName per TableColumnItem (Format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) Specifica la proprietà il cui valore viene visualizzato nella colonna della riga.

[Elemento PropertyName per WideItem (Format)](./propertyname-element-for-wideitem-for-widecontrol-format.md) Specifica la proprietà dell'oggetto il cui valore viene visualizzato nella visualizzazione estesa.

[Elemento RightIndent per il frame per i controlli per la configurazione (Format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md) Specifica il numero di caratteri spostati al di fuori del margine destro da parte dei dati. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento RightIndent del frame di controlli della visualizzazione (Format)](./rightindent-element-for-frame-for-controls-for-view-format.md) Specifica il numero di caratteri spostati al di fuori del margine destro da parte dei dati. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento RightIndent](./rightindent-element-for-frame-for-customcontrol-for-view-format.md) Specifica il numero di caratteri spostati al di fuori del margine destro da parte dei dati. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

[Elemento RightIndent per frame per GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md) Specifica il numero di caratteri spostati al di fuori del margine destro da parte dei dati. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento ScriptBlock per ExpressionName per i controlli per la configurazione (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md) Specifica lo script il cui valore viene visualizzato dal controllo comune. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento ScriptBlock per expressiongroup per i controlli per la visualizzazione (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md) Specifica lo script il cui valore viene visualizzato dal controllo. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento ScriptBlock per Expression per CustomCustomControl per View (Format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md) Specifica lo script il cui valore viene visualizzato dal controllo. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

[Elemento ScriptBlock per expressiongroup per GroupBy (Format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md) Specifica lo script il cui valore viene visualizzato dal controllo. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento ScriptBlock per GroupBy (Format)](./scriptblock-element-for-groupby-format.md) Specifica lo script che avvia un nuovo gruppo ogni volta che cambia il valore.

[Elemento ScriptBlock per ItemSelectionCondition per i controlli per la configurazione (Format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) Specifica lo script che attiva la condizione. Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzato il controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento ScriptBlock per ItemSelectionCondition per i controlli per la visualizzazione (Format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) Specifica lo script che attiva la condizione. Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzato il controllo. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento ScriptBlock per ItemSelectionCondition per CustomControl per View (Format)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) Specifica lo script che attiva la condizione. Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzato il controllo. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

[Elemento ScriptBlock per ItemSelectionCondition per GroupBy (Format)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) Specifica lo script che attiva la condizione. Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzato il controllo. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento ScriptBlock per ItemSelectionCondition per ListControl (Format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) Specifica lo script che attiva la condizione. Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzato l'elemento dell'elenco. Questo elemento viene utilizzato quando si definisce una visualizzazione elenco.

[Elemento ScriptBlock per ListItem (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md) Specifica lo script il cui valore viene visualizzato nella riga dell'elenco.

[Elemento ScriptBlock per SelectionCondition per i controlli per la configurazione (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md) Specifica lo script che attiva la condizione. Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene usata la definizione. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento ScriptBlock per SelectionCondition per i controlli per la visualizzazione (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md) Specifica lo script che attiva la condizione. Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene usata la definizione. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento ScriptBlock per SelectionCondition per CustomControl per View (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md) Specifica lo script che attiva la condizione. Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene usata la definizione. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

[Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Specifica lo script che attiva la condizione.

[Elemento ScriptBlock per SelectionCondition per GroupBy (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md) Specifica lo script che attiva la condizione. Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene usata la definizione. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per ListEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Specifica lo script che attiva la condizione. Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzata la voce dell'elenco.

[Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Specifica il blocco di script che attiva la condizione. Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene utilizzata la voce della tabella.

[Elemento ScriptBlock per SelectionCondition per EntrySelectedBy per WideEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) Specifica lo script che attiva la condizione. Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene usata la definizione di voce estesa.

[Elemento ScriptBlock per TableColumnItem (Format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) Specifica lo script il cui valore viene visualizzato nella colonna della riga.

[Elemento ScriptBlock per WideItem (Format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md) Specifica lo script il cui valore viene visualizzato nella visualizzazione estesa.

[Elemento SelectionCondition per EntrySelectedBy per CustomEntry per Configuration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md) Definisce una condizione che deve esistere per la definizione di un controllo comune da utilizzare. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md) Definisce una condizione che deve esistere per la definizione del controllo da utilizzare. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento SelectionCondition per EntrySelectedBy per CustomControl per View (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md) Definisce una condizione che deve esistere per la definizione di un controllo da utilizzare. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

[Elemento SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md) Definisce la condizione che deve esistere per espandere gli oggetti della raccolta di questa definizione.

[Elemento SelectionCondition per EntrySelectedBy per GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md) Definisce una condizione che deve esistere per la definizione di un controllo da utilizzare. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento SelectionCondition per EntrySelectedBy per ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) Definisce la condizione che deve esistere per utilizzare questa definizione della visualizzazione elenco. Non esiste alcun limite al numero di condizioni di selezione che è possibile specificare per una definizione di elenco.

[Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md) Definisce la condizione che deve esistere per utilizzare per questa definizione della visualizzazione tabella. Non esiste alcun limite al numero di condizioni di selezione che è possibile specificare per una definizione di tabella.

[Elemento SelectionCondition per EntrySelectedBy per WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) Definisce la condizione che deve esistere affinché questa definizione venga utilizzata. Non esiste alcun limite al numero di condizioni di selezione che è possibile specificare per una definizione di voce ampia.

[Elemento SelectionSet (Format)](./selectionset-element-format.md) Definisce un set di oggetti .NET a cui è possibile fare riferimento dal nome del set.

[Elemento SelectionSetName per EntrySelectedBy per i controlli per la configurazione (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) Specifica un set di tipi .NET che utilizzano questa definizione del controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento SelectionSetName per EntrySelectedBy per i controlli per la visualizzazione (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md) Specifica un set di tipi .NET che utilizzano questa definizione del controllo. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento SelectionSetName per EntrySelectedBy per CustomEntry (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md) Specifica un set di oggetti .NET per la voce dell'elenco. Non esiste alcun limite al numero di set di selezione che è possibile specificare per una voce.

[Elemento SelectionSetName per EntrySelectedBy per EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md) Specifica il set di tipi .NET espansi da questa definizione.

[Elemento SelectionSetName per EntrySelectedBy per GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md) Specifica un set di oggetti .NET per la voce dell'elenco. Non esiste alcun limite al numero di set di selezione che è possibile specificare per una voce. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento SelectionSetName per EntrySelectedBy per ListEntry (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) Specifica un set di oggetti .NET per la voce dell'elenco. Non esiste alcun limite al numero di set di selezione che è possibile specificare per una voce.

[Elemento SelectionSetName per EntrySelectedBy per TableRowEntry (Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md) Specifica un set di tipi .NET che utilizzano questa voce della visualizzazione tabella. Non esiste alcun limite al numero di set di selezione che è possibile specificare per una voce.

[Elemento SelectionSetName per EntrySelectedBy per WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md) Specifica un set di oggetti .NET per la definizione. La definizione viene utilizzata ogni volta che viene visualizzato uno di questi oggetti.

[Elemento SelectionSetName per SelectionCondition per i controlli per la configurazione (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) Specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presente, la condizione viene soddisfatta e l'oggetto viene visualizzato tramite questo controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento SelectionSetName per SelectionCondition per i controlli per la visualizzazione (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md) Specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presente, la condizione viene soddisfatta e l'oggetto viene visualizzato utilizzando questo controllo. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento EntrySelectedBy per CustomEntry per View (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) Specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presente, la condizione viene soddisfatta e l'oggetto viene visualizzato utilizzando questo controllo. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

[Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presente, viene soddisfatta la condizione.

[Elemento SelectionSetName per SelectionCondition per GroupBy (Format)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md) Specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presente, la condizione viene soddisfatta e l'oggetto viene visualizzato tramite questo controllo. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per ListEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md) Specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presente, la condizione viene soddisfatta e l'oggetto viene visualizzato utilizzando questa definizione della visualizzazione elenco.

[Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presente, la condizione viene soddisfatta e l'oggetto viene visualizzato utilizzando questa definizione della vista tabella.

[Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) Specifica il set di tipi .NET che attivano la condizione. Quando uno dei tipi in questo set è presente, la condizione viene soddisfatta e l'oggetto viene visualizzato utilizzando questa definizione della visualizzazione estesa.

[Elemento SelectionSetName per ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md) Specifica un set di oggetti .NET visualizzati dalla visualizzazione.

[Elemento SelectionSets (Format)](./selectionsets-element-format.md) Definisce i set di oggetti .NET che possono essere utilizzati dalle singole visualizzazioni di formato.

[Elemento ShowError (Format)](./showerror-element-format.md) Specifica che il record di errore completo viene visualizzato quando si verifica un errore durante la visualizzazione di una porzione di dati.

[Elemento TableColumnHeader per TableHeaders per Table ((Format)](./tablecolumnheader-element-format.md) Definisce l'etichetta, la larghezza della colonna e l'allineamento dell'etichetta per una colonna della tabella.

[Elemento TableColumnItem (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) Definisce la proprietà o lo script il cui valore viene visualizzato nella colonna della riga.

[Elemento TableColumnItems (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) Definisce le proprietà o gli script i cui valori vengono visualizzati nella riga.

[Elemento Table ((Format)](./tablecontrol-element-format.md) Definisce un formato di tabella per una visualizzazione.

[Elemento TableHeaders (Format)](./tableheaders-element-format.md) Definisce le intestazioni per le colonne di una tabella.

[Elemento TableRowEntries (Format)](./tablerowentries-element-for-tablecontrol-format.md) Definisce le righe della tabella.

[Elemento TableRowEntry (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) Definisce i dati visualizzati in una riga della tabella.

[Elemento text per CustomItem per i controlli per la configurazione (Format)](./text-element-for-customitem-for-controls-for-configuration-format.md) Specifica il testo aggiunto ai dati visualizzati dal controllo, ad esempio un'etichetta, le parentesi quadre per racchiudere i dati e gli spazi per rientrare i dati. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento text per CustomItem per i controlli per la visualizzazione (Format)](./text-element-for-customitem-for-controls-for-view-format.md) Specifica il testo aggiunto ai dati visualizzati dal controllo, ad esempio un'etichetta, le parentesi quadre per racchiudere i dati e gli spazi per rientrare i dati. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento text per CustomItem (Format)](./text-element-for-customitem-for-customview-for-view-format.md) Specifica il testo aggiunto ai dati visualizzati dal controllo, ad esempio un'etichetta, le parentesi quadre per racchiudere i dati e gli spazi per rientrare i dati. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

[Elemento text per CustomItem per GroupBy (Format)](./text-element-for-customitem-for-groupby-format.md) Specifica il testo aggiunto ai dati visualizzati dal controllo, ad esempio un'etichetta, le parentesi quadre per racchiudere i dati e gli spazi per rientrare i dati. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento TypeName per EntrySelectedBy per i controlli per la configurazione (Format)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md) Specifica un tipo .NET che usa questa definizione del controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento TypeName per EntrySelectedBy per i controlli per la visualizzazione (Format)](./typename-element-for-entryselectedby-for-controls-for-view-format.md) Specifica un tipo .NET che usa questa definizione del controllo. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento TypeName per EntrySelectedBy per CustomEntry per View (Format)](./typename-element-for-entryselectedby-for-customentry-for-view-format.md) Specifica un tipo .NET che usa questa definizione della visualizzazione del controllo personalizzato. Non esiste alcun limite al numero di tipi che è possibile specificare per una definizione.

[Elemento TypeName per EntrySelectedBy per EnumerableExpansion (Format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md) Specifica un tipo .NET espanso da questa definizione. Questo elemento viene utilizzato quando si definiscono impostazioni predefinite.

[Elemento TypeName per EntrySelectedBy per GroupBy (Format)](./typename-element-for-entryselectedby-for-groupby-format.md) Specifica un tipo .NET che usa questa definizione del controllo personalizzato. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento TypeName per EntrySelectedBy per ListControl (Format)](./typename-element-for-entryselectedby-for-listcontrol-format.md) Specifica un tipo .NET che usa questa voce della visualizzazione elenco. Non esiste alcun limite al numero di tipi che è possibile specificare per una voce di elenco.

[Elemento TypeName per EntrySelectedBy per TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md) Specifica un tipo .NET che usa questa voce della visualizzazione tabella. Non esiste alcun limite al numero di tipi che è possibile specificare per una voce di tabella.

[Elemento TypeName per EntrySelectedBy per WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md) Specifica un tipo .NET per la definizione. La definizione viene utilizzata ogni volta che l'oggetto viene visualizzato.

[Elemento TypeName per SelectionCondition per i controlli per la configurazione (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md) Specifica un tipo .NET che attiva la condizione. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

[Elemento TypeName per SelectionCondition per i controlli per la visualizzazione (Format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md) Specifica un tipo .NET che attiva la condizione. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

[Elemento TypeName per SelectionCondition per CustomControl per View (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md) Specifica un tipo .NET che attiva la condizione. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

[Elemento TypeName per SelectionCondition per EntrySelectedBy per EnumerableExpansion (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Specifica un tipo .NET che attiva la condizione.

[Elemento TypeName per SelectionCondition per GroupBy (Format)](./typename-element-for-selectioncondition-for-groupby-format.md) Specifica un tipo .NET che attiva la condizione. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

[Elemento TypeName per SelectionCondition per EntrySelectedBy per ListControl (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Specifica un tipo .NET che attiva la condizione. Quando questo tipo è presente, viene usata la voce dell'elenco.

[Elemento TypeName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Specifica un tipo .NET che attiva la condizione. Quando questo tipo è presente, la condizione viene soddisfatta e viene utilizzata la riga della tabella.

[Elemento TypeName per SelectionCondition per EntrySelectedBy per WideEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) Specifica un tipo .NET che attiva la condizione. Quando questo tipo è presente, viene usata la definizione.

[Elemento TypeName per types (Format)](./typename-element-for-types-format.md) Specifica il tipo .NET di un oggetto che appartiene al set di selezione.

[Elemento TypeName per ViewSelectedBy (Format)](./typename-element-for-viewselectedby-format.md) Specifica un oggetto .NET visualizzato dalla visualizzazione.

[Elemento types (Format)](./types-element-for-selectionset-format.md) Definisce gli oggetti .NET presenti nel set di selezione.

[Elemento View (Format)](./view-element-format.md) Definisce una vista utilizzata per visualizzare uno o più oggetti .NET.

[Elemento ViewDefinitions (Format)](./viewdefinitions-element-format.md) Definisce le visualizzazioni utilizzate per visualizzare gli oggetti.

[Elemento ViewSelectedBy (Format)](./viewselectedby-element-format.md) Definisce gli oggetti .NET visualizzati dalla visualizzazione.

[Elemento WideControl (Format)](./widecontrol-element-format.md) Definisce un formato di elenco Wide (valore singolo) per la visualizzazione. Questa vista consente di visualizzare un singolo valore di proprietà o un valore di script per ogni oggetto.

[Elemento WideEntries (Format)](./wideentries-element-for-widecontrol-format.md) Fornisce le definizioni della visualizzazione estesa. La visualizzazione estesa deve specificare una o più definizioni.

[Elemento WideEntry (Format)](./wideentry-element-for-widecontrol-format.md) Fornisce una definizione dell'ampia visualizzazione.

[Elemento WideItem (Format)](./wideitem-element-for-widecontrol-format.md) Definisce la proprietà o lo script di cui viene visualizzato il valore.

[Elemento Width (Format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) Definisce la larghezza (in caratteri) di una colonna.

[Elemento wrap (Format)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) Specifica che il testo che supera la larghezza della colonna viene visualizzato nella riga successiva.

[Elemento WrapTables (Format)](./wraptables-element-format.md) Specifica che i dati in una cella della tabella vengono spostati nella riga successiva se i dati sono più lunghi della larghezza della colonna.

## <a name="see-also"></a>Vedere anche

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
