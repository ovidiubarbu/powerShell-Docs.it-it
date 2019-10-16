---
title: Elemento PropertyName per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362520"
---
# <a name="propertyname-element-for-groupby-format"></a>Elemento PropertyName per GroupBy (formato)

Specifica la proprietà .NET che avvia un nuovo gruppo ogni volta che il relativo valore viene modificato.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per la visualizzazione (formato) elemento PropertyName per GroupBy (Format)

## <a name="syntax"></a>Sintassi

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `PropertyName`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento GroupBy per View (Format)](./groupby-element-for-view-format.md)|Definisce la modalità di visualizzazione di un gruppo di oggetti .NET.|

## <a name="text-value"></a>Valore di testo

Specificare il nome della proprietà .NET.

## <a name="remarks"></a>Osservazioni

Windows PowerShell avvia un nuovo gruppo ogni volta che il valore di questa proprietà viene modificato.

Quando questo elemento viene specificato, non è possibile specificare l'elemento [scriptblock](./scriptblock-element-for-groupby-format.md) per avviare un nuovo gruppo.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come avviare un nuovo gruppo quando viene modificato il valore di una proprietà.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Per un esempio di un file di formattazione completo che include questo elemento, vedere [visualizzazione estesa (GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Vedere anche

[Elemento GroupBy per View (Format)](./groupby-element-for-view-format.md)

[Elemento ScriptBlock per GroupBy (Format)](./scriptblock-element-for-groupby-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
