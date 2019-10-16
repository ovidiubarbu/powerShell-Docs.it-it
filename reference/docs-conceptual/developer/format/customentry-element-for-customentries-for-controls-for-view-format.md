---
title: Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364050"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a>Elemento CustomEntry per CustomEntries per Controls per View (formato)

Fornisce una definizione del controllo. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per la visualizzazione (formato) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre dell'elemento `CustomEntry`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per CustomEntry per i controlli per la visualizzazione (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata.|
|[Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Elemento obbligatorio.<br /><br /> Definisce la modalità di visualizzazione dei dati da parte del controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntries per CustomControl per View (Format)](./customentries-element-for-customcontrol-for-view-format.md)|Fornisce le definizioni per il controllo.|

## <a name="remarks"></a>Osservazioni

## <a name="see-also"></a>Vedere anche

[Elemento CustomEntries per CustomControl per View (Format)](./customentries-element-for-customcontrol-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
