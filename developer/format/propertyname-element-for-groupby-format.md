---
title: Elemento PropertyName per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863267"
---
# <a name="propertyname-element-for-groupby-format"></a>Elemento PropertyName per GroupBy (formato)

Specifica la proprietà .NET che avvia un nuovo gruppo ogni volta che cambia il relativo valore.

Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) elemento di visualizzazione (formato) PropertyName per GroupBy (formato)

## <a name="syntax"></a>Sintassi

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `PropertyName` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento GroupBy per visualizzazione (formato)](./groupby-element-for-view-format.md)|Definisce la modalità di visualizzazione di un gruppo di oggetti .NET.|

## <a name="text-value"></a>Valore di testo

Specificare il nome della proprietà .NET.

## <a name="remarks"></a>Osservazioni

Windows PowerShell avvia un nuovo gruppo ogni volta che il valore di questa proprietà viene modificato.

Quando questo elemento viene specificato, non è possibile specificare il [ScriptBlock](./scriptblock-element-for-groupby-format.md) elemento per avviare un nuovo gruppo.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come avviare un nuovo gruppo quando cambia il valore di una proprietà.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Per un esempio di un file di formattazione completato che include questo elemento, vedere [visualizzazione più ampia (GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Vedere anche

[Elemento GroupBy per visualizzazione (formato)](./groupby-element-for-view-format.md)

[Elemento ScriptBlock per GroupBy (formato)](./scriptblock-element-for-groupby-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
