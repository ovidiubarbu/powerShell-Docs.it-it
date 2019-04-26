---
title: Elemento di configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066822"
---
# <a name="configuration-element-format"></a>Elemento Configuration (formato)

Rappresenta l'elemento di livello superiore di un file di formattazione.

Elemento di configurazione

## <a name="syntax"></a>Sintassi

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Configuration` elemento. Questo elemento deve essere l'elemento radice per ogni file di formattazione e questo elemento deve contenere almeno un elemento figlio.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[I controlli elemento di configurazione (formato)](./controls-element-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Definisce i controlli comuni che possono essere usati da tutte le visualizzazioni del file di formattazione.|
|[Elemento DefaultSettings (formato)](./defaultsettings-element-format.md)|Elemento facoltativo.<br /><br /> Definisce le impostazioni comuni che si applicano a tutte le visualizzazioni del file di formattazione.|
|[Formato elemento SelectionSets](./selectionsets-element-format.md)|Elemento facoltativo.<br /><br /> Definisce il set di oggetti .NET che possono essere usati da tutte le visualizzazioni del file di formattazione comuni.|
|[Elemento ViewDefinitions (formato)](./viewdefinitions-element-format.md)|Elemento facoltativo.<br /><br /> Definisce le viste utilizzate per visualizzare gli oggetti.|

### <a name="parent-elements"></a>Elementi padre

Nessuna.

## <a name="remarks"></a>Osservazioni

File di formattazione definiscono come gli oggetti vengono visualizzati. Nella maggior parte dei casi, questo elemento radice contiene un [ViewDefinitions](./viewdefinitions-element-format.md) elemento che definisce la tabella, elenco e visualizzazioni ampie del file di formattazione. Oltre alle definizioni delle viste, è possibile definire il file di formattazione comuni selezione set, impostazioni e i controlli che è possono utilizzare tali viste.

## <a name="see-also"></a>Vedere anche

[I controlli elemento di configurazione (formato)](./controls-element-for-configuration-format.md)

[Elemento DefaultSettings (formato)](./defaultsettings-element-format.md)

[Elemento SelectionSets (formato)](./selectionsets-element-format.md)

[Elemento ViewDefinitions (formato)](./viewdefinitions-element-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
