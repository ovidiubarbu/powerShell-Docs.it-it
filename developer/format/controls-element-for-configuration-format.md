---
title: Controlla l'elemento di configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066873"
---
# <a name="controls-element-for-configuration-format"></a>Elemento Controls per Configuration (formato)

Definisce i controlli comuni che possono essere usati da tutte le visualizzazioni del file di formattazione.

Configurazione (formato) i controlli elemento di configurazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Controls` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento di controllo per i controlli per la configurazione (formato)](./control-element-for-controls-for-configuration-format.md)|Elemento obbligatorio.<br /><br /> Definisce un controllo comune che può essere usato da tutte le visualizzazioni del file di formattazione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento di configurazione (formato)](./configuration-element-format.md)|Rappresenta l'elemento di livello superiore di un file di formattazione.|

## <a name="remarks"></a>Osservazioni

È possibile creare qualsiasi numero di controlli comuni. Per ogni controllo, è necessario specificare il nome utilizzato per fare riferimento al controllo e i componenti del controllo.

## <a name="see-also"></a>Vedere anche

[Elemento di configurazione (formato)](./configuration-element-format.md)

[Elemento di controllo per i controlli per la configurazione (formato)](./control-element-for-controls-for-configuration-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
