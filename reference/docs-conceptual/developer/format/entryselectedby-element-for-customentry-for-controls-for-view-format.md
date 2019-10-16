---
title: Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363890"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a>Elemento EntrySelectedBy per CustomEntry per Controls per View (formato)

Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per i controlli per la visualizzazione (formato) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) EntrySelectedBy elemento per CustomEntry per i controlli per la visualizzazione (formato)

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
|[Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve esistere affinché questa definizione venga utilizzata.|
|[Elemento SelectionSetName per EntrySelectedBy per i controlli per la visualizzazione (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica un set di tipi .NET che utilizzano questa definizione del controllo.|
|[Elemento TypeName per EntrySelectedBy per i controlli per la visualizzazione (Format)](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che usa questa definizione del controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Fornisce una definizione del controllo.|

## <a name="remarks"></a>Osservazioni

Le condizioni di selezione vengono usate per definire una condizione che deve esistere per la definizione da usare, ad esempio quando un oggetto ha una proprietà specifica o quando uno script o un valore di proprietà specifico restituisce `true`. Per ulteriori informazioni sulle condizioni di selezione, vedere [definizione di condizioni per l'utilizzo di una voce o di un elemento della visualizzazione](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
