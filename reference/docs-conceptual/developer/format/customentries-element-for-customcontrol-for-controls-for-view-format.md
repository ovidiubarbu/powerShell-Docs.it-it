---
title: Elemento CustomEntries per CustomControl per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368810"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>Elemento CustomEntries per CustomControl per Controls per View (formato)

Fornisce le definizioni per il controllo. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per i controlli per la visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre dell'elemento `CustomEntries`. Non esiste un limite massimo per il numero di elementi figlio che è possibile specificare.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Elemento obbligatorio.<br /><br /> Fornisce una definizione del controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomControl per il controllo per i controlli per la visualizzazione (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Definisce il controllo utilizzato dalla visualizzazione.|

## <a name="remarks"></a>Osservazioni

Nella maggior parte dei casi, un controllo ha una sola definizione, specificata in un singolo elemento `CustomEntry`. Tuttavia, se si desidera utilizzare lo stesso controllo per visualizzare oggetti .NET diversi, è possibile specificare più definizioni. In questi casi, è possibile definire un elemento `CustomEntry` per ogni oggetto o set di oggetti.

## <a name="see-also"></a>Vedere anche

[Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Elemento CustomControl per il controllo per i controlli per la visualizzazione (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
