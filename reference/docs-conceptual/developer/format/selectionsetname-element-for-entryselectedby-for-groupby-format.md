---
title: Elemento SelectionSetName per EntrySelectedBy per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364740"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a>Elemento SelectionSetName per EntrySelectedBy per GroupBy (formato)

Specifica un set di oggetti .NET per la voce dell'elenco. Non esiste alcun limite al numero di set di selezione che è possibile specificare per una voce. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format) elemento EntrySelectedBy per CustomEntry per GroupBy (Format) SelectionSetName elemento per EntrySelectedBy per GroupBy (Format)

## <a name="syntax"></a>Sintassi

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per CustomEntry per GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Definisce i tipi .NET che utilizzano questa voce personalizzata o la condizione che deve esistere affinché questa voce venga utilizzata.|

## <a name="text-value"></a>Valore testo

Consente di specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

Per ogni definizione di controllo personalizzato deve essere definito almeno un nome di tipo, un set di selezione o una condizione di selezione.

I set di selezione vengono in genere utilizzati quando si desidera definire un gruppo di oggetti utilizzati in più viste. È ad esempio possibile creare una visualizzazione tabella e una visualizzazione elenco per lo stesso set di oggetti. Per ulteriori informazioni sulla definizione di set di selezione, vedere [definizione di set di selezione](./defining-selection-sets.md).

Per ulteriori informazioni sui componenti di una visualizzazione controlli personalizzata, vedere [creazione di controlli personalizzati](./creating-custom-controls.md).

## <a name="see-also"></a>Vedere anche

[Elemento EntrySelectedBy per CustomEntry per GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Creazione di controlli personalizzati](./creating-custom-controls.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
