---
title: Elemento FirstLineIndent per frame per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33be3b9e-53c8-433f-8c11-c65b0d46744c
caps.latest.revision: 6
ms.openlocfilehash: 9ba6fc1b9924a4b0d5b56ee15290a2293217403c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363080"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a>Elemento FirstLineIndent per Frame per GroupBy (formato)

Specifica il numero di caratteri che la prima riga di dati viene spostata a destra. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format) elemento CustomItem per CustomEntry per l'elemento frame GroupBy (Format) per CustomItem per l'elemento GroupBy (Format) FirstLineIndent per frame per GroupBy (Format)

## <a name="syntax"></a>Sintassi

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `FirstLineIndent`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento frame per CustomItem per GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)|Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra.|

## <a name="text-value"></a>Valore di testo

Consente di specificare il numero di caratteri che si desidera spostare nella prima riga dei dati.

## <a name="remarks"></a>Osservazioni

Se questo elemento è specificato, non è possibile specificare l'elemento [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) .

## <a name="see-also"></a>Vedere anche

[Elemento FirstLineHanging per frame per GroupBy (Format)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[Elemento frame per CustomItem per GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
