---
title: Elemento Control per Controls per Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369010"
---
# <a name="control-element-for-controls-for-configuration-format"></a>Elemento Control per Controls per Configuration (formato)

Definisce un controllo comune che può essere utilizzato da tutte le visualizzazioni del file di formattazione e dal nome utilizzato per fare riferimento al controllo.

Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format)

## <a name="syntax"></a>Sintassi

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre per l'elemento `Control`. È necessario specificare un solo elemento figlio.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomControl per Control per Controls per Configuration (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Elemento obbligatorio.<br /><br /> Definisce il controllo.|
|[Elemento Name per Control per Configuration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)|Elemento obbligatorio.<br /><br /> Specifica il nome utilizzato per fare riferimento al controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento Controls di Configuration (Format)](./controls-element-for-configuration-format.md)|Definisce i controlli comuni che possono essere utilizzati da tutte le visualizzazioni del file di formattazione o da altri controlli.|

## <a name="remarks"></a>Osservazioni

È possibile fare riferimento al nome assegnato a questo controllo negli elementi seguenti:

- [Elemento expressiongroup per CustomItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [Elemento GroupBy per View (Format)](./groupby-element-for-view-format.md)

## <a name="see-also"></a>Vedere anche

[Elemento Controls di Configuration (Format)](./controls-element-for-configuration-format.md)

[Elemento CustomControl per Control per Configuration (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[Elemento expressiongroup per CustomItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento GroupBy per View (Format)](./groupby-element-for-view-format.md)

[Elemento Name per il controllo per i controlli per la configurazione (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
