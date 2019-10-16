---
title: Elemento CustomEntries per CustomControl per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364090"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>Elemento CustomEntries per CustomControl per GroupBy (formato)

Fornisce le definizioni per il controllo. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per GroupBy (Format) elemento CustomEntries per CustomControl per GroupBy (Format)

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
|[Elemento CustomEntry per CustomControl per GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Elemento obbligatorio.<br /><br /> Fornisce una definizione del controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomControl per GroupBy (Format)](./customcontrol-element-for-groupby-format.md)|Definisce il controllo personalizzato che Visualizza il nuovo gruppo.|

## <a name="remarks"></a>Osservazioni

Nella maggior parte dei casi, un controllo ha una sola definizione, specificata in un singolo elemento `CustomEntry`. Tuttavia, se si desidera utilizzare lo stesso controllo per visualizzare gruppi diversi, è possibile specificare più definizioni. In questi casi, è possibile definire un elemento `CustomEntry` per un gruppo.

## <a name="see-also"></a>Vedere anche

[Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Elemento CustomControl per GroupBy (Format)](./customcontrol-element-for-groupby-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
