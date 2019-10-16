---
title: Elemento Expand (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368740"
---
# <a name="expand-element-format"></a>Elemento Expand (formato)

Specifica la modalità di espansione dell'oggetto raccolta per questa definizione.

Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format) elemento Expand (Format)

## <a name="syntax"></a>Sintassi

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Expand`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EnumerableExpansion (Format)](./enumerableexpansion-element-format.md)|Definisce la modalità di espansione degli oggetti raccolta .NET specifici quando vengono visualizzati in una visualizzazione.|

## <a name="text-value"></a>Valore di testo

Specificare uno dei valori seguenti:

- EnumOnly: Visualizza solo le proprietà degli oggetti nella raccolta.

- CoreOnly: Visualizza solo le proprietà dell'oggetto raccolta.

- Both: Visualizza le proprietà degli oggetti nella raccolta e le proprietà dell'oggetto raccolta.

## <a name="remarks"></a>Osservazioni

Questo elemento viene utilizzato per definire la modalità di visualizzazione degli oggetti raccolta e degli oggetti nella raccolta. In questo caso, un oggetto della raccolta fa riferimento a qualsiasi oggetto che supporta l'interfaccia **System. Collections. ICollection** .

Il comportamento predefinito consiste nel visualizzare solo le proprietà degli oggetti nella raccolta.

## <a name="see-also"></a>Vedere anche

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
