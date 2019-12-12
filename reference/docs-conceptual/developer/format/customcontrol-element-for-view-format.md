---
title: Elemento CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363360"
---
# <a name="customcontrol-element-for-view-format"></a>Elemento CustomControl per View (formato)

Definisce un formato di controllo personalizzato per la visualizzazione.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format)

## <a name="syntax"></a>Sintassi

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomControl`. È necessario specificare un elemento figlio.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntries per CustomControl per View (Format)](./customentries-element-for-customcontrol-for-view-format.md)|Elemento obbligatorio.<br /><br /> Fornisce le definizioni della visualizzazione controlli personalizzata.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento View (Format)](./view-element-format.md)|Definisce una vista utilizzata per visualizzare uno o più oggetti .NET.|

## <a name="remarks"></a>Osservazioni

Nella maggior parte dei casi, è necessaria una sola definizione per ogni visualizzazione controlli, ma è possibile specificare più definizioni se si desidera utilizzare la stessa visualizzazione per visualizzare oggetti .NET diversi. In questi casi, è possibile specificare una definizione separata per ogni oggetto o set di oggetti.

## <a name="see-also"></a>Vedere anche

[Elemento CustomEntries per CustomControl per View (Format)](./customentries-element-for-customcontrol-for-view-format.md)

[Elemento View (Format)](./view-element-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
