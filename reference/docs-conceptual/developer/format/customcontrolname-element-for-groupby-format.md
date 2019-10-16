---
title: Elemento CustomControlName per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368880"
---
# <a name="customcontrolname-element-for-groupby-format"></a>Elemento CustomControlName per GroupBy (formato)

Specifica il nome di un controllo personalizzato usato per visualizzare il nuovo gruppo. Questo elemento viene utilizzato quando si definisce una tabella, un elenco, una visualizzazione di controlli Wide o Custom.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControlName di GroupBy (Format)

## <a name="syntax"></a>Sintassi

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre dell'elemento `CustomControlName`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento GroupBy per View (Format)](./groupby-element-for-view-format.md)|Definisce la modalità di visualizzazione di un nuovo gruppo di oggetti in Windows PowerShell.|

## <a name="text-value"></a>Valore di testo

Specificare il nome del controllo personalizzato usato per visualizzare un nuovo gruppo.

## <a name="remarks"></a>Osservazioni

È possibile creare controlli comuni che possono essere utilizzati da tutte le visualizzazioni di un file di formattazione ed è possibile creare controlli di visualizzazione che possono essere utilizzati da una visualizzazione specifica. Gli elementi seguenti specificano i nomi di questi controlli personalizzati:

- [Elemento Name per il controllo per i controlli per la configurazione (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Elemento Name per il controllo per i controlli per la visualizzazione (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Vedere anche

[Elemento GroupBy per View (Format)](./groupby-element-for-view-format.md)

[Elemento Name per il controllo per i controlli per la configurazione (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Elemento Name per il controllo per i controlli per la visualizzazione (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
