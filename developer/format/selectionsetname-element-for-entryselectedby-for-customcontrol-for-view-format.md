---
title: Elemento SelectionSetName per EntrySelectedBy per CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855027"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a>Elemento SelectionSetName per EntrySelectedBy per CustomControl per View (formato)

Specifica un set di oggetti .NET per la voce dell'elenco. Non sono previsti limiti al numero di set di selezione che è possibile specificare per una voce.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per EntrySelectedBy visualizzazione (formato) Elemento per CustomEntry elemento di visualizzazione (formato) SelectionSetName per EntrySelectedBy per CustomEntry (formato)

## <a name="syntax"></a>Sintassi

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSetName` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per CustomEntry per visualizzazione (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Definisce i tipi .NET che usano questa voce personalizzata o la condizione che deve essere presente per questa voce da usare.|

## <a name="text-value"></a>Valore di testo

Specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

Ogni voce di controllo personalizzato deve avere almeno un nome di tipo, il set di selezione o condizione di selezione definiti.

Set di selezione vengono usati quando si desidera definire un gruppo di oggetti utilizzati in più viste. Ad esempio, è possibile creare una visualizzazione tabella e una visualizzazione elenco per lo stesso set di oggetti. Per altre informazioni sulla definizione di set di selezione, vedere [definizione di selezione imposta](./defining-selection-sets.md).

Per altre informazioni sui componenti di una vista di controllo personalizzato, vedere [Creating Custom Controls](./creating-custom-controls.md).

## <a name="see-also"></a>Vedere anche

[Elemento EntrySelectedBy per CustomEntry per visualizzazione (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Visualizzazione controlli personalizzati](./creating-custom-controls.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
