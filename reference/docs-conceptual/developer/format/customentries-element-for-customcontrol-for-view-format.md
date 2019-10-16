---
title: Elemento CustomEntries per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364080"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>Elemento CustomEntries per CustomControl per View (formato)

Fornisce le definizioni della visualizzazione controlli personalizzata. La visualizzazione controlli personalizzata deve specificare una o più definizioni.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per View (Format)

## <a name="syntax"></a>Sintassi

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomControlEntries`. È necessario specificare uno o più elementi figlio.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntry per CustomEntries per View (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Elemento obbligatorio.<br /><br /> Fornisce una definizione della visualizzazione controlli personalizzata.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomControl per View (Format)](./customcontrol-element-for-view-format.md)|Elemento obbligatorio.<br /><br /> Definisce un formato di controllo personalizzato per la visualizzazione.|

## <a name="remarks"></a>Osservazioni

Nella maggior parte dei casi, un controllo ha una sola definizione, definita in un singolo elemento `CustomEntry`. Tuttavia, se si desidera utilizzare lo stesso controllo per visualizzare oggetti .NET diversi, è possibile disporre di più definizioni. In questi casi, è possibile definire un elemento `CustomEntry` per ogni oggetto o set di oggetti.

## <a name="see-also"></a>Vedere anche

[Elemento CustomControl per View (Format)](./customcontrol-element-for-view-format.md)

[Elemento CustomEntry per CustomEntries per View (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
