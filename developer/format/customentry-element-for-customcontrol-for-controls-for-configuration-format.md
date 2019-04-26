---
title: Elemento CustomEntry per CustomControl per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066473"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a>Elemento CustomEntry per CustomControl per Controls per Configuration (formato)

Fornisce una definizione del controllo comune. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli di configurazione (formato) CustomControl elemento per il controllo per elemento di configurazione (formato) CustomEntries per CustomControl per Configuration ( Elemento CustomEntry Format) per CustomControl per i controlli per la configurazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomEntry` elemento. È necessario specificare gli elementi visualizzati dalla definizione.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (formato)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Definisce i tipi .NET che usano la definizione di controllo comune o la condizione che deve essere presente per questo controllo da utilizzare.|
|[Elemento CustomItem per CustomEntry per i controlli per la configurazione](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Elemento obbligatorio.<br /><br /> Definisce i dati che vengano visualizzati dal controllo e la modalità di visualizzazione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntries per CustomControl per la configurazione (formato)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|Fornisce le definizioni del controllo comune.|

## <a name="remarks"></a>Osservazioni

Nella maggior parte dei casi, è necessaria per ogni controllo personalizzato comune una sola definizione, ma è possibile avere più definizioni, se si desidera utilizzare lo stesso controllo per visualizzare diversi oggetti .NET. In questi casi, è possibile fornire una definizione separata per ogni oggetto o un set di oggetti.

## <a name="see-also"></a>Vedere anche

[Elemento CustomEntries per CustomControl per la configurazione (formato)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[Elemento CustomItem per CustomEntry per i controlli per la configurazione](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
