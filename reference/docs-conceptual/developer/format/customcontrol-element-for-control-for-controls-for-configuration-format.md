---
title: Elemento CustomControl per Control per Controls per Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9d92a9e-c680-46ca-962e-e82452726953
caps.latest.revision: 10
ms.openlocfilehash: 1d72ce5b18e89bd81c7f81b27f4b8c60bed99764
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368970"
---
# <a name="customcontrol-element-for-control-for-controls-for-configuration-format"></a>Elemento CustomControl per Control per Controls per Configuration (formato)

Definisce un controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format)

## <a name="syntax"></a>Sintassi

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomControl`. Questo elemento deve contenere almeno un elemento figlio. Non esiste un limite massimo per il numero di elementi figlio che è possibile specificare.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntries per CustomControl per Configuration (Format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|Elemento obbligatorio.<br /><br /> Fornisce le definizioni di un controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento Control per Controls per Configuration (Format)](./control-element-for-controls-for-configuration-format.md)|Definisce un controllo comune che può essere utilizzato da tutte le visualizzazioni del file di formattazione e dal nome utilizzato per fare riferimento al controllo.|

## <a name="remarks"></a>Osservazioni

## <a name="see-also"></a>Vedere anche

[Elemento Control per Controls per Configuration (Format)](./control-element-for-controls-for-configuration-format.md)

[Elemento CustomEntries per CustomControl per Configuration (Format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
