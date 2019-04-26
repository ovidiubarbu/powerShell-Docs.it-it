---
title: Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066499"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a>Elemento CustomEntry per CustomEntries per Controls per View (formato)

Fornisce una definizione del controllo. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli per la visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi, elementi figlio e gli elementi padre del `CustomEntry` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (formato)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Definisce i tipi .NET che usano questa definizione di controllo o la condizione che deve essere presente per questa definizione da usare.|
|[Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Elemento obbligatorio.<br /><br /> Definisce come il controllo Visualizza i dati.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntries per CustomControl per visualizzazione (formato)](./customentries-element-for-customcontrol-for-view-format.md)|Fornisce le definizioni per il controllo.|

## <a name="remarks"></a>Osservazioni

## <a name="see-also"></a>Vedere anche

[Elemento CustomEntries per CustomControl per visualizzazione (formato)](./customentries-element-for-customcontrol-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
