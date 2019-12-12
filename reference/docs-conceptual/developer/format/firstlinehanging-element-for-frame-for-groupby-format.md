---
title: Elemento FirstLineHanging per frame per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363820"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a>Elemento FirstLineHanging per Frame per GroupBy (formato)

Specifica il numero di caratteri che la prima riga di dati viene spostata a sinistra. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format) elemento CustomItem per CustomEntry per l'elemento frame GroupBy (Format) per CustomItem per l'elemento GroupBy (Format) FirstLineHanging per frame per GroupBy (Format)

## <a name="syntax"></a>Sintassi

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `FirstLineHanging`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento frame per CustomItem per GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)|Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra.|

## <a name="text-value"></a>Valore testo

Consente di specificare il numero di caratteri che si desidera spostare nella prima riga dei dati.

## <a name="remarks"></a>Osservazioni

Se questo elemento è specificato, non è possibile specificare l'elemento [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) .

## <a name="see-also"></a>Vedere anche

[Elemento FirstLineIndent per frame per GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md)

[Elemento frame per CustomItem per GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
