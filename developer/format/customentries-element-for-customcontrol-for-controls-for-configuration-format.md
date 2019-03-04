---
title: Elemento CustomEntries per CustomControl per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856307"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a>Elemento CustomEntries per CustomControl per Controls per Configuration (formato)

Fornisce le definizioni di un controllo comune. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli di configurazione (formato) CustomControl elemento per il controllo per elemento di configurazione (formato) CustomEntries per CustomControl per Configuration ( Formato)

## <a name="syntax"></a>Sintassi

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomEntries` elemento. È necessario specificare uno o più elementi figlio.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntry per CustomControl per i controlli per la configurazione (formato)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Fornisce una definizione del controllo comune.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomControl per il controllo per la configurazione (formato)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Definisce un controllo comune.|

## <a name="remarks"></a>Osservazioni

Nella maggior parte dei casi, un controllo ha una sola definizione, di cui è definita in una singola `CustomEntry` elemento. Tuttavia è possibile avere più definizioni, se si desidera utilizzare lo stesso controllo per visualizzare diversi oggetti .NET. In questi casi, è possibile definire un `CustomEntry` (elemento) per ogni oggetto o un set di oggetti.

## <a name="see-also"></a>Vedere anche

[Elemento CustomControl per il controllo per la configurazione (formato)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[Elemento CustomEntry per CustomControl per i controlli per la configurazione (formato)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
