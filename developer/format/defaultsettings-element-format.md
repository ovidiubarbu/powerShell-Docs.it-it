---
title: Elemento DefaultSettings (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066346"
---
# <a name="defaultsettings-element-format"></a>Elemento DefaultSettings (formato)

Definisce le impostazioni comuni che si applicano a tutte le visualizzazioni del file di formattazione. Impostazioni comuni includono la visualizzazione di errori, la disposizione del testo in tabelle, che definisce come vengono espanse le raccolte e così via.

Elemento di configurazione elemento (formato) DefaultSettings (formato)

## <a name="syntax"></a>Sintassi

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `DefaultSettings` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento DisplayError (formato)](./displayerror-element-format.md)|Elemento facoltativo.<br /><br /> Specifica che la stringa #ERR viene visualizzata quando si verifica un errore durante la visualizzazione di una porzione di dati.|
|[Elemento EnumerableExpansions (formato)](./enumerableexpansions-element-format.md)|Elemento facoltativo.<br /><br /> Definisce i diversi modi in cui gli oggetti .NET vengono espanse quando vengono visualizzati in una vista.|
|[PropertyCountForTable (formato)](./propertycountfortable-element-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero minimo di proprietà che deve avere un oggetto per visualizzare l'oggetto in una visualizzazione tabella.|
|[Elemento ShowError (formato)](./showerror-element-format.md)|Elemento facoltativo.<br /><br /> Specifica che il record di errore completo viene visualizzato quando si verifica un errore durante la visualizzazione di una porzione di dati.|
|[Elemento WrapTables (formato)](./wraptables-element-format.md)|Elemento facoltativo.<br /><br /> Specifica che i dati in una tabella vengano spostati alla riga successiva se non adattarsi alla larghezza della colonna.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento di configurazione](./configuration-element-format.md)|Rappresenta l'elemento di livello superiore di un file di formattazione.|

## <a name="remarks"></a>Osservazioni

## <a name="see-also"></a>Vedere anche

[Elemento di configurazione](./configuration-element-format.md)

[Elemento DisplayError (formato)](./displayerror-element-format.md)

[Elemento EnumerableExpansions (formato)](./enumerableexpansions-element-format.md)

[PropertyCountForTable (formato)](./propertycountfortable-element-format.md)

[Elemento ShowError (formato)](./showerror-element-format.md)

[Elemento WrapTables (formato)](./wraptables-element-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
