---
title: Elemento CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861257"
---
# <a name="customcontrol-element-for-view-format"></a>Elemento CustomControl per View (formato)

Definisce un formato di controllo personalizzato per la visualizzazione.

Configurazione (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) CustomControl elemento (formato)

## <a name="syntax"></a>Sintassi

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomControl` elemento. È necessario specificare un elemento figlio.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntries per CustomControl per visualizzazione (formato)](./customentries-element-for-customcontrol-for-view-format.md)|Elemento obbligatorio.<br /><br /> Fornisce le definizioni della vista del controllo personalizzato.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento di visualizzazione (formato)](./view-element-format.md)|Definisce una vista che consente di visualizzare uno o più oggetti .NET.|

## <a name="remarks"></a>Osservazioni

Nella maggior parte dei casi, una sola definizione è obbligatorio per ogni visualizzazione del controllo, ma è possibile fornire più definizioni, se si desidera utilizzare la stessa vista per visualizzare diversi oggetti .NET. In questi casi, è possibile fornire una definizione separata per ogni oggetto o un set di oggetti.

## <a name="see-also"></a>Vedere anche

[Elemento CustomEntries per CustomControl per visualizzazione (formato)](./customentries-element-for-customcontrol-for-view-format.md)

[Elemento di visualizzazione (formato)](./view-element-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
