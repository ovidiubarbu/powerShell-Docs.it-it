---
title: Elemento EntrySelectedBy per WideEntry (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066176"
---
# <a name="entryselectedby-element-for-wideentry-format"></a>Elemento EntrySelectedBy per WideEntry (formato)

Definisce i tipi .NET che usano questa definizione di visualizzazione estesa o la condizione che deve essere presente per questa definizione da usare.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento di configurazione per WideEntry (formato)

## <a name="syntax"></a>Sintassi

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `EntrySelectedBy` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve essere presente per questa definizione di visualizzazione estesa da utilizzare.|
|[Elemento SelectionSetName per EntrySelectedBy per WideEntry (formato)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica un set di tipi .NET che usano questa definizione di visualizzazione più ampia.|
|[Elemento TypeName per EntrySelectedBy per WideEntry (formato)](./typename-element-for-entryselectedby-for-wideentry-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che usa questa definizione di visualizzazione più ampia.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)|Fornisce una definizione della vista wide.|

## <a name="remarks"></a>Osservazioni

È necessario specificare almeno un tipo, il set di selezione o condizione di selezione per una definizione di visualizzazione più ampia. Non è definito alcun limite massimo al numero di elementi figlio che è possibile usare.

Condizioni di selezione vengono usate per definire una condizione che deve essere presente per la definizione da usare, ad esempio quando un oggetto dispone di una proprietà specifica o che restituisce un valore di uno script o il valore della proprietà specifico `true`. Per altre informazioni sulle condizioni di selezione, vedere [che definisce le condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

Per altre informazioni sugli altri componenti di una visualizzazione più ampia, vedere [creazione di una visualizzazione più ampia](./creating-a-wide-view.md).

## <a name="see-also"></a>Vedere anche

[Elemento WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)

[Elemento SelectionCondition per EntrySelectedBy per WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento SelectionSetName per EntrySelectedBy per WideEntry (formato)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento TypeName per EntrySelectedBy per WideEntry (formato)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Creazione di una visualizzazione più ampia](./creating-a-wide-view.md)

[La definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
