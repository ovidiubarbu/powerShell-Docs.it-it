---
title: Elemento Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363500"
---
# <a name="configuration-element-format"></a>Elemento Configuration (formato)

Rappresenta l'elemento di primo livello di un file di formattazione.

Elemento Configuration

## <a name="syntax"></a>Sintassi

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Configuration`. Questo elemento deve essere l'elemento radice per ogni file di formattazione e questo elemento deve contenere almeno un elemento figlio.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento Controls per Configuration (Format)](./controls-element-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Definisce i controlli comuni che possono essere utilizzati da tutte le visualizzazioni del file di formattazione.|
|[Elemento DefaultSettings (Format)](./defaultsettings-element-format.md)|Elemento facoltativo.<br /><br /> Definisce le impostazioni comuni che si applicano a tutte le visualizzazioni del file di formattazione.|
|[Formato elemento SelectionSets](./selectionsets-element-format.md)|Elemento facoltativo.<br /><br /> Definisce i set comuni di oggetti .NET che possono essere utilizzati da tutte le visualizzazioni del file di formattazione.|
|[Elemento ViewDefinitions (Format)](./viewdefinitions-element-format.md)|Elemento facoltativo.<br /><br /> Definisce le visualizzazioni utilizzate per visualizzare gli oggetti.|

### <a name="parent-elements"></a>Elementi padre

Nessuna.

## <a name="remarks"></a>Osservazioni

I file di formattazione definiscono la modalità di visualizzazione degli oggetti. Nella maggior parte dei casi, questo elemento radice contiene un elemento [ViewDefinitions](./viewdefinitions-element-format.md) che definisce la tabella, l'elenco e le visualizzazioni estese del file di formattazione. Oltre alle definizioni delle viste, il file di formattazione può definire set di selezione, impostazioni e controlli comuni che tali visualizzazioni possono usare.

## <a name="see-also"></a>Vedere anche

[Elemento Controls per Configuration (Format)](./controls-element-for-configuration-format.md)

[Elemento DefaultSettings (Format)](./defaultsettings-element-format.md)

[Elemento SelectionSets (Format)](./selectionsets-element-format.md)

[Elemento ViewDefinitions (Format)](./viewdefinitions-element-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
