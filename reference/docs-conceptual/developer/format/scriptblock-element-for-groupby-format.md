---
title: Elemento ScriptBlock per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364930"
---
# <a name="scriptblock-element-for-groupby-format"></a>Elemento ScriptBlock per GroupBy (formato)

Specifica lo script che avvia un nuovo gruppo ogni volta che cambia il valore.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento ScriptBlock per GroupBy (Format)

## <a name="syntax"></a>Sintassi

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ScriptBlock`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento GroupBy per View (Format)](./groupby-element-for-view-format.md)|Definisce la modalità di visualizzazione di un gruppo di oggetti .NET.|

## <a name="text-value"></a>Valore testo

Specificare lo script che viene valutato.

## <a name="remarks"></a>Osservazioni

PowerShell avvia un nuovo gruppo ogni volta che viene modificato il valore di questo script.

Quando questo elemento viene specificato, non è possibile specificare l'elemento [PropertyName](propertyname-element-for-groupby-format.md) per avviare un nuovo gruppo.

## <a name="see-also"></a>Vedere anche

[Elemento PropertyName per GroupBy (Format)](propertyname-element-for-groupby-format.md)

[Elemento GroupBy per View (Format)](groupby-element-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](writing-a-powershell-formatting-file.md)
