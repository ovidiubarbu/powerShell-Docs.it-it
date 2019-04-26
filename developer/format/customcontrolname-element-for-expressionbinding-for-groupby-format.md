---
title: Elemento CustomControlName per ExpressionBinding per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066569"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>Elemento CustomControlName per ExpressionBinding per GroupBy (formato)

Specifica il nome di un controllo comune o un controllo di visualizzazione. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per elemento CustomItem GroupBy (formato) per CustomEntry per elemento ExpressionBinding GroupBy (formato) per CustomItem per elemento CustomControlName GroupBy (formato) per ExpressionBinding per GroupBy (formato)

## <a name="syntax"></a>Sintassi

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomControlName` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ExpressionBinding per CustomItem per GroupBy (formato)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Definisce i dati che vengano visualizzati dal controllo.|

## <a name="text-value"></a>Valore di testo

Specificare il nome del controllo.

## <a name="remarks"></a>Osservazioni

È possibile creare controlli comuni che possono essere usati da tutte le visualizzazioni di un file di formattazione ed è possibile creare controlli di visualizzazione che possono essere usati da una visualizzazione specifica. Gli elementi seguenti specificano i nomi di questi controlli:

- [Elemento Name per il controllo per i controlli per la configurazione (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Elemento Name per il controllo per i controlli per la visualizzazione (formato)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Vedere anche

[Elemento Name per il controllo per i controlli per la configurazione (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

[Elemento Name per il controllo per i controlli per la visualizzazione (formato)](./name-element-for-control-for-controls-for-view-format.md)

[Elemento ExpressionBinding per CustomItem per GroupBy (formato)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
