---
title: Elemento SelectionSets (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361870"
---
# <a name="selectionsets-element-format"></a>Elemento SelectionSet (formato)

Definisce i set comuni di oggetti .NET che possono essere utilizzati da tutte le visualizzazioni del file di formattazione. Le visualizzazioni e i controlli del file di formattazione possono fare riferimento al set completo di oggetti utilizzando solo il nome del set di selezione.

Formato dell'elemento SelectionSets dell'elemento di configurazione

## <a name="syntax"></a>Sintassi

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSets`. Ogni elemento figlio definisce un set di oggetti a cui è possibile fare riferimento dal nome del set. L'ordine degli elementi figlio non è significativo.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionSet (Format)](./selectionset-element-format.md)|Elemento obbligatorio.<br /><br /> Definisce un singolo set di oggetti .NET a cui è possibile fare riferimento dal nome del set.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento Configuration](./configuration-element-format.md)|Rappresenta l'elemento di primo livello di un file di formattazione.|

## <a name="remarks"></a>Osservazioni

È possibile utilizzare i set di selezione quando si dispone di un set di oggetti correlati a cui si desidera fare riferimento utilizzando un solo nome, ad esempio un set di oggetti correlati tramite ereditarietà. Quando si definiscono le visualizzazioni, è possibile specificare il set di oggetti utilizzando il nome del set di selezione anziché elencare tutti gli oggetti all'interno di ogni visualizzazione.

I set di selezione comuni vengono specificati in base al relativo nome quando si definiscono le visualizzazioni del file di formattazione o le definizioni delle viste. In questi casi, il `SelectionSetName` elemento figlio degli elementi `ViewSelectedBy` e `EntrySelectedBy` specifica il set da usare. Per ulteriori informazioni sui set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).

## <a name="see-also"></a>Vedere anche

[Elemento Configuration](./configuration-element-format.md)

[Definizione di set di selezione](./defining-selection-sets.md)

[Elemento SelectionSet (Format)](./selectionset-element-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
