---
title: Elemento CustomControl per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2472e256-8f4f-4288-8b67-a3300649dafa
caps.latest.revision: 9
ms.openlocfilehash: 2e84e770a345e272d4c5917b00afe7520840e1db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368960"
---
# <a name="customcontrol-element-for-groupby-format"></a>Elemento CustomControl per GroupBy (formato)

Definisce il controllo personalizzato che Visualizza il nuovo gruppo.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per GroupBy (Format)

## <a name="syntax"></a>Sintassi

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
<CustomControl>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomControl`. È possibile specificare un numero qualsiasi di elementi figlio ed elencarli in qualsiasi ordine.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntries per CustomControl per GroupBy (Format)](./customentries-element-for-customcontrol-for-groupby-format.md)|Elemento obbligatorio.<br /><br /> Fornisce le definizioni per il controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento GroupBy per View (Format)](./groupby-element-for-view-format.md)|Definisce la modalità di visualizzazione di un nuovo gruppo di oggetti in Windows PowerShell.|

## <a name="remarks"></a>Osservazioni

## <a name="see-also"></a>Vedere anche

[Elemento CustomEntries per CustomControl per GroupBy (Format)](./customentries-element-for-customcontrol-for-groupby-format.md)

[Elemento GroupBy per View (Format)](./groupby-element-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
