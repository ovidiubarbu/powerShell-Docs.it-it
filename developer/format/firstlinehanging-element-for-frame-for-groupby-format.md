---
title: Elemento FirstLineHanging per Frame per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065833"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a>Elemento FirstLineHanging per Frame per GroupBy (formato)

Specifica il numero di caratteri la prima riga di dati verrà spostata a sinistra. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per elemento CustomItem GroupBy (formato) per CustomEntry per elemento Frame GroupBy (formato) per CustomItem per elemento FirstLineHanging GroupBy (formato) per il Frame per GroupBy (formato)

## <a name="syntax"></a>Sintassi

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono l'elemento padre di attributi e gli elementi figlio di `FirstLineHanging` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento frame per CustomItem per GroupBy (formato)](./frame-element-for-customitem-for-groupby-format.md)|Definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra.|

## <a name="text-value"></a>Valore di testo

Specificare il numero di caratteri che si desidera spostare la prima riga dei dati.

## <a name="remarks"></a>Osservazioni

Se questo elemento viene specificato, non è possibile specificare il [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elemento.

## <a name="see-also"></a>Vedere anche

[Elemento FirstLineIndent per Frame per GroupBy (formato)](./firstlineindent-element-for-frame-for-groupby-format.md)

[Elemento frame per CustomItem per GroupBy (formato)](./frame-element-for-customitem-for-groupby-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
