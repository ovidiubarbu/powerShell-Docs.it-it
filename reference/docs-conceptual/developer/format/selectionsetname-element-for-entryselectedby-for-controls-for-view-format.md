---
title: Elemento SelectionSetName per EntrySelectedBy per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b594a064-746f-4900-99e4-7be7bf5aa5a2
caps.latest.revision: 7
ms.openlocfilehash: d540c99707f4e0796b2d408f2161a9208257ab32
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368350"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a>Elemento SelectionSetName per EntrySelectedBy per Controls per View (formato)

Specifica un set di tipi .NET che utilizzano questa definizione del controllo. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per i controlli per la visualizzazione (formato) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) EntrySelectedBy elemento per CustomEntry per i controlli per la visualizzazione (formato) SelectionSetName elemento per EntrySelectedBy per i controlli per la visualizzazione ( Formato

## <a name="syntax"></a>Sintassi

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.

### <a name="attributes"></a>Attributi

Nessuno

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata.|

## <a name="text-value"></a>Valore testo

Consente di specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

Per ogni definizione di controllo deve essere definito almeno un nome di tipo, un set di selezione o una condizione di selezione.

I set di selezione vengono in genere utilizzati quando si desidera definire un gruppo di oggetti utilizzati in più viste. Per ulteriori informazioni sulla definizione di set di selezione, vedere [definizione di set di selezione](./defining-selection-sets.md).

## <a name="see-also"></a>Vedere anche

[Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
