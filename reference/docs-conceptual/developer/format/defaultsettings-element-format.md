---
title: Elemento DefaultSettings (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363870"
---
# <a name="defaultsettings-element-format"></a>Elemento DefaultSettings (formato)

Definisce le impostazioni comuni che si applicano a tutte le visualizzazioni del file di formattazione. Le impostazioni comuni includono la visualizzazione di errori, il wrapping del testo nelle tabelle, la definizione del modo in cui le raccolte vengono espanse e altro.

Elemento Configuration (Format) elemento DefaultSettings (Format)

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

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `DefaultSettings`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento DisplayError (Format)](./displayerror-element-format.md)|Elemento facoltativo.<br /><br /> Specifica che la stringa #ERR viene visualizzata quando si verifica un errore durante la visualizzazione di una porzione di dati.|
|[Elemento EnumerableExpansions (Format)](./enumerableexpansions-element-format.md)|Elemento facoltativo.<br /><br /> Definisce le diverse modalità di espansione degli oggetti .NET quando vengono visualizzati in una visualizzazione.|
|[PropertyCountForTable (formato)](./propertycountfortable-element-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero minimo di proprietà che un oggetto deve avere per visualizzare l'oggetto in una visualizzazione tabella.|
|[Elemento ShowError (Format)](./showerror-element-format.md)|Elemento facoltativo.<br /><br /> Specifica che il record di errore completo viene visualizzato quando si verifica un errore durante la visualizzazione di una porzione di dati.|
|[Elemento WrapTables (Format)](./wraptables-element-format.md)|Elemento facoltativo.<br /><br /> Specifica che i dati di una tabella vengono spostati alla riga successiva se non rientra nella larghezza della colonna.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento Configuration](./configuration-element-format.md)|Rappresenta l'elemento di primo livello di un file di formattazione.|

## <a name="remarks"></a>Osservazioni

## <a name="see-also"></a>Vedere anche

[Elemento Configuration](./configuration-element-format.md)

[Elemento DisplayError (Format)](./displayerror-element-format.md)

[Elemento EnumerableExpansions (Format)](./enumerableexpansions-element-format.md)

[PropertyCountForTable (formato)](./propertycountfortable-element-format.md)

[Elemento ShowError (Format)](./showerror-element-format.md)

[Elemento WrapTables (Format)](./wraptables-element-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
