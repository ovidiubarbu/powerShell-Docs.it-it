---
title: Elemento EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368750"
---
# <a name="enumerableexpansion-element-format"></a>Elemento EnumerableExpansion (formato)

Definisce la modalità di espansione degli oggetti raccolta .NET specifici quando vengono visualizzati in una visualizzazione.

Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format)

## <a name="syntax"></a>Sintassi

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `EnumerableExpansion`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)|Elemento facoltativo.<br /><br /> Definisce gli oggetti della raccolta .NET espansi da questa definizione.|
|[Elemento Expand (Format)](./expand-element-format.md)|Specifica la modalità di espansione dell'oggetto raccolta per questa definizione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EnumerableExpansions (Format)](./enumerableexpansions-element-format.md)|Definisce le diverse modalità di espansione degli oggetti raccolta .NET quando vengono visualizzati in una visualizzazione.|

## <a name="remarks"></a>Osservazioni

Questo elemento viene utilizzato per definire la modalità di visualizzazione degli oggetti raccolta e degli oggetti nella raccolta. In questo caso, un oggetto della raccolta fa riferimento a qualsiasi oggetto che supporta l'interfaccia **System. Collections. ICollection** .

Il comportamento predefinito consiste nel visualizzare solo le proprietà degli oggetti nella raccolta.

## <a name="see-also"></a>Vedere anche

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
