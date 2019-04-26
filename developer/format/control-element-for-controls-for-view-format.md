---
title: Elemento Control per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066771"
---
# <a name="control-element-for-controls-for-view--format"></a>Elemento Control per Controls per View (formato)

Definisce un controllo che può essere utilizzato per la visualizzazione e il nome utilizzato per fare riferimento al controllo.

Elemento di visualizzazione configurazione elemento (formato) elemento ViewDefinitions (formato) (formato) controlla controllo elemento (formato) per i controlli per visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Control` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento Name per il controllo di visualizzazione (formato)](./name-element-for-control-for-controls-for-view-format.md)|Elemento obbligatorio.<br /><br /> Specifica il nome del controllo.|
|[Elemento CustomControl per il controllo per i controlli per la visualizzazione (formato)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Elemento obbligatorio.<br /><br /> Definisce il controllo utilizzato da questa vista.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento Controls (formato)](./controls-element-for-view-format.md)|Definisce i controlli di visualizzazione che possono essere usati da una visualizzazione specifica.|

## <a name="remarks"></a>Osservazioni

Questo controllo può essere specificato dagli elementi seguenti:

- [Elemento CustomControlName per ExpressionBinding per i controlli per la visualizzazione (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [Elemento CustomControlName per ExpressionBinding per CustomControl per visualizzazione (formato)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [Elemento CustomControlName per ExpressionBinding per GroupBy (formato)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [Elemento CustomControlName per GroupBy (formato)](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>Vedere anche

[Elemento CustomControl per il controllo per i controlli per la visualizzazione (formato)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Elemento CustomControlName per ExpressionBinding per i controlli per la visualizzazione (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento CustomControlName per ExpressionBinding per CustomControl per visualizzazione (formato)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento CustomControlName per ExpressionBinding per GroupBy (formato)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Elemento CustomControlName per ExpressionBinding per GroupBy (formato)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Elemento Controls (formato)](./controls-element-for-view-format.md)

[Elemento Name per il controllo per i controlli per la visualizzazione (formato)](./name-element-for-control-for-controls-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
