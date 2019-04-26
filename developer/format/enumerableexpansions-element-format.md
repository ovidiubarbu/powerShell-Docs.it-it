---
title: Elemento EnumerableExpansions (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066091"
---
# <a name="enumerableexpansions-element-format"></a>Elemento EnumerableExpansions (formato)

Definisce come oggetti della raccolta .NET vengono espanse quando vengono visualizzati in una vista.

Configurazione (formato) elemento DefaultSettings (formato) EnumerableExpansions elemento (formato)

## <a name="syntax"></a>Sintassi

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `EnumerableExpansions` elemento. Non sono previsti limiti al numero di elementi figlio che è possibile usare.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento EnumerableExpansion (formato)](./enumerableexpansion-element-format.md)|Elemento facoltativo.<br /><br /> Definisce gli oggetti della raccolta .NET specifici che vengono espanse quando vengono visualizzati in una vista.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento DefaultSettings (formato)](./defaultsettings-element-format.md)|Definisce le impostazioni comuni che si applicano a tutte le visualizzazioni del file di formattazione.|

## <a name="remarks"></a>Osservazioni

Questo elemento viene usato per definire come vengono visualizzati gli oggetti raccolta e gli oggetti nella raccolta. In questo caso, un oggetto raccolta fa riferimento a qualsiasi oggetto che supporta il **System.Collections.ICollection** interfaccia.

## <a name="see-also"></a>Vedere anche

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
