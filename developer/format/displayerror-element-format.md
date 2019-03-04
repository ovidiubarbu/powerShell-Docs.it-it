---
title: Elemento DisplayError (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 431e5d8407b9f689a5224b329d8c7b52802e19e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854917"
---
# <a name="displayerror-element-format"></a>Elemento DisplayError (formato)

Specifica che la stringa #ERR viene visualizzata quando si verifica un errore la visualizzazione di una porzione di dati.

Configurazione (formato) elemento DefaultSettings (formato) DisplayError elemento (Frmat)

## <a name="syntax"></a>Sintassi

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `DisplayError` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento DefaultSettings (formato)](./defaultsettings-element-format.md)|Definisce le impostazioni comuni che si applicano a tutte le visualizzazioni del file di formattazione.|

## <a name="remarks"></a>Osservazioni

Per impostazione predefinita, quando si verifica un errore durante il tentativo di visualizzare una porzione di dati, è possibile che il percorso dei dati viene lasciato vuoto. Quando questo elemento è impostato su true, la stringa #ERR verrà visualizzato.

## <a name="see-also"></a>Vedere anche

[Elemento DefaultSettings (formato)](./defaultsettings-element-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
