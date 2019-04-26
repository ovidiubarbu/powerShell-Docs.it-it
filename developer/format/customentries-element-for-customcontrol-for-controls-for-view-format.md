---
title: Elemento CustomEntries per CustomControl per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066584"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>Elemento CustomEntries per CustomControl per Controls per View (formato)

Fornisce le definizioni per il controllo. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl per i controlli per la visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi, elementi figlio e gli elementi padre del `CustomEntries` elemento. Non è definito alcun limite massimo al numero di elementi figlio che possono essere specificati.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Elemento obbligatorio.<br /><br /> Fornisce una definizione del controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomControl per il controllo per i controlli per la visualizzazione (formato)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Definisce il controllo utilizzato dalla visualizzazione.|

## <a name="remarks"></a>Osservazioni

Nella maggior parte dei casi, un controllo ha una sola definizione, di cui è specificata in un singolo `CustomEntry` elemento. Tuttavia, è possibile fornire più definizioni, se si desidera utilizzare lo stesso controllo per visualizzare diversi oggetti .NET. In questi casi, è possibile definire un `CustomEntry` (elemento) per ogni oggetto o un set di oggetti.

## <a name="see-also"></a>Vedere anche

[Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Elemento CustomControl per il controllo per i controlli per la visualizzazione (formato)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
