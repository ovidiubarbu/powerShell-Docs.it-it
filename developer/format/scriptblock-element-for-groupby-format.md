---
title: Elemento ScriptBlock per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: f2f6b9af7740b1231881294c2f32bf97b5a1568b
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054426"
---
# <a name="scriptblock-element-for-groupby-format"></a>Elemento ScriptBlock per GroupBy (formato)

Specifica lo script che avvia un nuovo gruppo ogni volta che cambia il relativo valore.

Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) elemento di visualizzazione (formato) ScriptBlock per GroupBy (formato)

## <a name="syntax"></a>Sintassi

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ScriptBlock` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento GroupBy per visualizzazione (formato)](./groupby-element-for-view-format.md)|Definisce la modalità di visualizzazione di un gruppo di oggetti .NET.|

## <a name="text-value"></a>Valore di testo

Specificare lo script che viene valutato.

## <a name="remarks"></a>Osservazioni

Windows PowerShell avvia un nuovo gruppo ogni volta che cambia il valore di questo script.

Quando questo elemento viene specificato, non è possibile specificare il [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) elemento per avviare un nuovo gruppo.

## <a name="see-also"></a>Vedere anche

[Elemento PropertyName per GroupBy (formato)](./propertyname-element-for-groupby-format.md)

[Elemento GroupBy per visualizzazione (formato)](./groupby-element-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
