---
title: Elemento SelectionSetName per EntrySelectedBy per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364750"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a>Elemento SelectionSetName per EntrySelectedBy per CustomControl per View (formato)

Specifica un set di oggetti .NET per la voce dell'elenco. Non esiste alcun limite al numero di set di selezione che è possibile specificare per una voce.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per l'elemento View (Format) CustomEntry per CustomEntries per View (Format) EntrySelectedBy Elemento per CustomEntry per la visualizzazione (Format) elemento SelectionSetName per EntrySelectedBy per CustomEntry (Format)

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
|[Elemento EntrySelectedBy per CustomEntry per View (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Definisce i tipi .NET che utilizzano questa voce personalizzata o la condizione che deve esistere affinché questa voce venga utilizzata.|

## <a name="text-value"></a>Valore testo

Consente di specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

Per ogni voce di controllo personalizzata è necessario definire almeno un nome di tipo, un set di selezione o una condizione di selezione.

I set di selezione vengono in genere utilizzati quando si desidera definire un gruppo di oggetti utilizzati in più viste. Ad esempio, potrebbe essere necessario creare una visualizzazione tabella e una visualizzazione elenco per lo stesso set di oggetti. Per ulteriori informazioni sulla definizione di set di selezione, vedere [definizione di set di selezione](./defining-selection-sets.md).

Per ulteriori informazioni sui componenti di una visualizzazione controlli personalizzata, vedere [creazione di controlli personalizzati](./creating-custom-controls.md).

## <a name="see-also"></a>Vedere anche

[Elemento EntrySelectedBy per CustomEntry per View (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Visualizzazione controlli personalizzati](./creating-custom-controls.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
