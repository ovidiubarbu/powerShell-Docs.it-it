---
title: Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066244"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a>Elemento EntrySelectedBy per CustomEntry per Controls per View (formato)

Definisce i tipi .NET che usano questa definizione di controllo o la condizione che deve essere presente per questa definizione da usare. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl per i controlli elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono l'elemento padre di attributi e gli elementi figlio di `EntrySelectedBy` elemento. È necessario specificare almeno un tipo, set di selezione o condizione di selezione per una definizione. Non è definito alcun limite massimo al numero di elementi figlio che è possibile usare.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per i controlli per la visualizzazione (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve essere presente per questa definizione da usare.|
|[Elemento SelectionSetName per EntrySelectedBy per i controlli per la visualizzazione (formato)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica un set di tipi .NET che usano questa definizione del controllo.|
|[Elemento TypeName per EntrySelectedBy per i controlli per la visualizzazione (formato)](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che usa questa definizione del controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Fornisce una definizione del controllo.|

## <a name="remarks"></a>Osservazioni

Condizioni di selezione vengono usate per definire una condizione che deve essere presente per la definizione da usare, ad esempio quando un oggetto dispone di una proprietà specifica o quando un valore di proprietà specifica o lo script restituisce `true`. Per altre informazioni sulle condizioni di selezione, vedere [definizione di condizioni per quando una voce di visualizzazione o viene usato l'elemento](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
