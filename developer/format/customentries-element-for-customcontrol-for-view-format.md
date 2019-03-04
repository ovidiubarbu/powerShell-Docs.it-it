---
title: Elemento CustomEntries per CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861697"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>Elemento CustomEntries per CustomControl per View (formato)

Fornisce le definizioni della vista del controllo personalizzato. La visualizzazione controlli personalizzati è necessario specificare una o più definizioni.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl per visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomControlEntries` elemento. È necessario specificare uno o più elementi figlio.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntry per CustomEntries per visualizzazione (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Elemento obbligatorio.<br /><br /> Fornisce una definizione della vista del controllo personalizzato.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomControl per visualizzazione (formato)](./customcontrol-element-for-view-format.md)|Elemento obbligatorio.<br /><br /> Definisce un formato di controllo personalizzato per la visualizzazione.|

## <a name="remarks"></a>Osservazioni

Nella maggior parte dei casi, un controllo ha una sola definizione, di cui è definita in una singola `CustomEntry` elemento. Tuttavia è possibile avere più definizioni, se si desidera utilizzare lo stesso controllo per visualizzare diversi oggetti .NET. In questi casi, è possibile definire un `CustomEntry` (elemento) per ogni oggetto o un set di oggetti.

## <a name="see-also"></a>Vedere anche

[Elemento CustomControl per visualizzazione (formato)](./customcontrol-element-for-view-format.md)

[Elemento CustomEntry per CustomEntries per visualizzazione (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
