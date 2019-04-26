---
title: Elemento EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066142"
---
# <a name="enumerableexpansion-element-format"></a>Elemento EnumerableExpansion (formato)

Definisce una raccolta .NET come specifica gli oggetti vengono espansi quando vengono visualizzati in una vista.

Configurazione (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) EnumerableExpansion elemento (formato)

## <a name="syntax"></a>Sintassi

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `EnumerableExpansion` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per EnumerableExpansion (formato)](./entryselectedby-element-for-enumerableexpansion-format.md)|Elemento facoltativo.<br /><br /> Definisce quali oggetti della raccolta .NET vengono espanse per questa definizione.|
|[Espandere l'elemento (formato)](./expand-element-format.md)|Specifica come viene espanso l'oggetto raccolta per questa definizione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EnumerableExpansions (formato)](./enumerableexpansions-element-format.md)|Definisce i diversi modi di tale raccolta .NET gli oggetti vengono espansi quando vengono visualizzati in una vista.|

## <a name="remarks"></a>Osservazioni

Questo elemento viene usato per definire come vengono visualizzati gli oggetti raccolta e gli oggetti nella raccolta. In questo caso, un oggetto raccolta fa riferimento a qualsiasi oggetto che supporta il **System.Collections.ICollection** interfaccia.

Il comportamento predefinito è per visualizzare solo le proprietà degli oggetti nella raccolta.

## <a name="see-also"></a>Vedere anche

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
