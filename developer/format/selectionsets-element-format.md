---
title: Elemento SelectionSets (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853567"
---
# <a name="selectionsets-element-format"></a>Elemento SelectionSet (formato)

Definisce il set di oggetti .NET che possono essere usati da tutte le visualizzazioni del file di formattazione comuni. I controlli del file di formattazione e le visualizzazioni possono fare riferimento il set completo di oggetti utilizzando solo il nome del set di selezione.

Formato elemento SelectionSets elemento di configurazione

## <a name="syntax"></a>Sintassi

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `SelectionSets` elemento. Ogni elemento figlio definisce un set di oggetti che possono fare riferimento il nome del set. L'ordine degli elementi figlio non è significativo.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionSet (formato)](./selectionset-element-format.md)|Elemento obbligatorio.<br /><br /> Definisce un singolo set di oggetti .NET che possono fare riferimento il nome del set.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento di configurazione](./configuration-element-format.md)|Rappresenta l'elemento di livello superiore di un file di formattazione.|

## <a name="remarks"></a>Osservazioni

Quando si dispone di un set di oggetti correlati che si desidera fare riferimento tramite un solo nome, ad esempio un set di oggetti che sono correlati tramite l'ereditarietà, è possibile usare set di selezione. Quando si definiscono le visualizzazioni, è possibile specificare il set di oggetti utilizzando il nome della selezione set anziché elencare tutti gli oggetti all'interno di ogni visualizzazione.

Set di selezione comune vengono specificati in base al nome quando si definisce le viste del file di formattazione e le definizioni delle viste. In questi casi, il `SelectionSetName` elemento figlio dell'elemento di `ViewSelectedBy` e `EntrySelectedBy` elementi specifica il set da utilizzare. Per altre informazioni sui set di selezione, vedere [definizione imposta di oggetti](./defining-selection-sets.md).

## <a name="see-also"></a>Vedere anche

[Elemento di configurazione](./configuration-element-format.md)

[La definizione di set di selezione](./defining-selection-sets.md)

[Elemento SelectionSet (formato)](./selectionset-element-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
