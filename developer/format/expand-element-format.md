---
title: Espandere l'elemento (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066006"
---
# <a name="expand-element-format"></a>Elemento Expand (formato)

Specifica come viene espanso l'oggetto raccolta per questa definizione.

Configurazione (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) EnumerableExpansion elemento (formato) espandere l'elemento (formato)

## <a name="syntax"></a>Sintassi

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Expand` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EnumerableExpansion (formato)](./enumerableexpansion-element-format.md)|Definisce una raccolta .NET come specifica gli oggetti vengono espansi quando vengono visualizzati in una vista.|

## <a name="text-value"></a>Valore di testo

Specificare uno dei valori seguenti:

- EnumOnly: Visualizza solo le proprietà degli oggetti nella raccolta.

- CoreOnly: Visualizza solo le proprietà dell'oggetto della raccolta.

- Entrambi: Visualizza le proprietà degli oggetti nella raccolta e le proprietà dell'oggetto della raccolta.

## <a name="remarks"></a>Osservazioni

Questo elemento viene usato per definire come vengono visualizzati gli oggetti raccolta e gli oggetti nella raccolta. In questo caso, un oggetto raccolta fa riferimento a qualsiasi oggetto che supporta il **System.Collections.ICollection** interfaccia.

Il comportamento predefinito è per visualizzare solo le proprietà degli oggetti nella raccolta.

## <a name="see-also"></a>Vedere anche

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
