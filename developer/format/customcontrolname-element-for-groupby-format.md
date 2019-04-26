---
title: Elemento CustomControlName per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066542"
---
# <a name="customcontrolname-element-for-groupby-format"></a>Elemento CustomControlName per GroupBy (formato)

Specifica il nome di un controllo personalizzato che consente di visualizzare il nuovo gruppo. Questo elemento viene usato quando si definisce una tabella, elenco, visualizzazione controllo wide o personalizzato.

Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) elemento di visualizzazione (formato) CustomControlName di GroupBy (formato)

## <a name="syntax"></a>Sintassi

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi, elementi figlio e gli elementi padre del `CustomControlName` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento GroupBy per visualizzazione (formato)](./groupby-element-for-view-format.md)|Definisce la modalità di visualizzazione di un nuovo gruppo di oggetti Windows PowerShell.|

## <a name="text-value"></a>Valore di testo

Specificare il nome del controllo personalizzato che consente di visualizzare un nuovo gruppo.

## <a name="remarks"></a>Osservazioni

È possibile creare controlli comuni che possono essere usati da tutte le visualizzazioni di un file di formattazione ed è possibile creare controlli di visualizzazione che possono essere usati da una visualizzazione specifica. Gli elementi seguenti specificano i nomi di questi controlli personalizzati:

- [Elemento Name per il controllo per i controlli per la configurazione (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Elemento Name per il controllo per i controlli per la visualizzazione (formato)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Vedere anche

[Elemento GroupBy per visualizzazione (formato)](./groupby-element-for-view-format.md)

[Elemento Name per il controllo per i controlli per la configurazione (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

[Elemento Name per il controllo per i controlli per la visualizzazione (formato)](./name-element-for-control-for-controls-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
