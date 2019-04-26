---
title: Elemento Control per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066794"
---
# <a name="control-element-for-controls-for-configuration-format"></a>Elemento Control per Controls per Configuration (formato)

Definisce un controllo comune che può essere usato da tutte le visualizzazioni del file di formattazione e il nome utilizzato per fare riferimento al controllo.

Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli per la configurazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi, elementi figlio e l'elemento padre per il `Control` elemento. È necessario specificare solo uno di ogni elemento figlio.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomControl per il controllo per i controlli per la configurazione (formato)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Elemento obbligatorio.<br /><br /> Definisce il controllo.|
|[Elemento Name per il controllo per la configurazione (formato)](./name-element-for-control-for-controls-for-configuration-format.md)|Elemento obbligatorio.<br /><br /> Specifica il nome usato per fare riferimento al controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[I controlli elemento di configurazione (formato)](./controls-element-for-configuration-format.md)|Definisce i controlli comuni che possono essere utilizzati da tutte le visualizzazioni del file di formattazione o da altri controlli.|

## <a name="remarks"></a>Osservazioni

Il nome assegnato a questo controllo può farvi riferimento negli elementi seguenti:

- [Elemento ExpressionBinding per CustomItem (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [Elemento GroupBy per View(Format)](./groupby-element-for-view-format.md)

## <a name="see-also"></a>Vedere anche

[I controlli elemento di configurazione (formato)](./controls-element-for-configuration-format.md)

[Elemento CustomControl per il controllo per la configurazione (formato)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[Elemento ExpressionBinding per CustomItem (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento GroupBy per View(Format)](./groupby-element-for-view-format.md)

[Elemento Name per il controllo per i controlli per la configurazione (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
