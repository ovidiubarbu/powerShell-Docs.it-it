---
title: Elemento EntrySelectedBy per CustomEntry per CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859587"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>Elemento EntrySelectedBy per CustomEntry per CustomControl per View (formato)

Definisce i tipi .NET che usano questa voce personalizzata o la condizione che deve essere presente per questa voce da usare.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per EntrySelectedBy visualizzazione (formato) Elemento per CustomEntry per visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `EntrySelectedBy` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per CustomEntry (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve essere presente per questa definizione da usare.|
|[Elemento SelectionSetName per EntrySelectedBy per CustomEntry (formato)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica un set di tipi .NET che usano questa definizione della vista del controllo.|
|[Elemento TypeName per EntrySelectedBy per CustomEntry (formato)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che usa questa definizione della vista del controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntry per CustomEntries per visualizzazione (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Definisce i controlli usati da specifici oggetti .NET.|

## <a name="remarks"></a>Osservazioni

È necessario specificare almeno un tipo, il set di selezione o condizione di selezione per una voce. Non è definito alcun limite massimo al numero di elementi figlio che è possibile usare.

Condizioni di selezione vengono usate per definire una condizione che deve essere presente per la voce da usare, ad esempio quando un oggetto dispone di una proprietà specifica o quando un valore di proprietà specifica o lo script restituisce `true`. Per altre informazioni sulle condizioni di selezione, vedere [definizione di condizioni per quando una voce di visualizzazione o viene usato l'elemento](./defining-conditions-for-displaying-data.md).

Per altre informazioni sui componenti di una vista di controllo personalizzato, vedere [visualizzazione di controlli personalizzati](./creating-custom-controls.md).

## <a name="see-also"></a>Vedere anche

[Elemento SelectionCondition per EntrySelectedBy per CustomEntry (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Elemento SelectionSetName per EntrySelectedBy per CustomEntry (formato)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[Elemento TypeName per EntrySelectedBy per CustomEntry (formato)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento CustomEntry per CustomEntries per visualizzazione (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Visualizzazione controlli personalizzati](./creating-custom-controls.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
