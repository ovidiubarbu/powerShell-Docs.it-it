---
title: Elemento EnumerableExpansions (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363300"
---
# <a name="enumerableexpansions-element-format"></a>Elemento EnumerableExpansions (formato)

Definisce la modalità di espansione degli oggetti raccolta .NET quando vengono visualizzati in una visualizzazione.

Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format)

## <a name="syntax"></a>Sintassi

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `EnumerableExpansions`. Non esiste alcun limite al numero di elementi figlio che è possibile utilizzare.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento EnumerableExpansion (Format)](./enumerableexpansion-element-format.md)|Elemento facoltativo.<br /><br /> Definisce gli oggetti della raccolta .NET specifici che vengono espansi quando vengono visualizzati in una visualizzazione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento DefaultSettings (Format)](./defaultsettings-element-format.md)|Definisce le impostazioni comuni che si applicano a tutte le visualizzazioni del file di formattazione.|

## <a name="remarks"></a>Osservazioni

Questo elemento viene utilizzato per definire la modalità di visualizzazione degli oggetti raccolta e degli oggetti nella raccolta. In questo caso, un oggetto della raccolta fa riferimento a qualsiasi oggetto che supporta l'interfaccia **System. Collections. ICollection** .

## <a name="see-also"></a>Vedere anche

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
