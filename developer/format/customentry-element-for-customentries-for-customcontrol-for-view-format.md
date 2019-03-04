---
title: Elemento CustomEntry per CustomEntries per CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861817"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a>Elemento CustomEntry per CustomEntries per CustomControl per View (formato)

Fornisce una definizione della vista del controllo personalizzato.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomEntry` elemento. È necessario specificare gli elementi visualizzati dalla definizione.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per CustomEntry per visualizzazione (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Definisce i tipi .NET che usano la definizione della vista del controllo personalizzato oppure la condizione che deve essere presente per questa definizione da usare.|
|[Elemento CustomItem per CustomEntry per visualizzazione (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Definisce un controllo per la definizione del controllo personalizzato.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntries per CustomControl per visualizzazione (formato)](./customentries-element-for-customcontrol-for-view-format.md)|Fornisce le definizioni della vista del controllo personalizzato. La visualizzazione controlli personalizzati è necessario specificare una o più definizioni.|

## <a name="remarks"></a>Osservazioni

Nella maggior parte dei casi, una sola definizione è obbligatorio per ogni visualizzazione del controllo personalizzato, ma è possibile avere più definizioni, se si desidera utilizzare la stessa vista per visualizzare diversi oggetti .NET. In questi casi, è possibile fornire una definizione separata per ogni oggetto o un set di oggetti.

## <a name="see-also"></a>Vedere anche

[Elemento CustomControl per visualizzazione (formato)](./customcontrol-element-for-view-format.md)

[Elemento CustomItem per CustomEntry per visualizzazione (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Elemento EntrySelectedBy per CustomEntry per visualizzazione (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
