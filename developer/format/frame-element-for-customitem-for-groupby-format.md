---
title: Elemento dei frame per CustomItem per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854847"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>Elemento Frame per CustomItem per GroupBy (formato)

Definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per elemento CustomItem GroupBy (formato) per CustomEntry per elemento Frame GroupBy (formato) per CustomItem per GroupBy (formato)

## <a name="syntax"></a>Sintassi

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Frame` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|`CustomItem Element`|Elemento obbligatorio|
|[Elemento FirstLineHanging per Frame per GroupBy (formato)](./firstlinehanging-element-for-frame-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri la prima riga di dati verrà spostata a sinistra.|
|[Elemento FirstLineIndent per Frame per GroupBy (formato)](./firstlineindent-element-for-frame-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri la prima riga di dati verrà spostata a destra.|
|[Elemento LeftIndent per Frame per GroupBy (formato)](./leftindent-element-for-frame-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica quanti caratteri di dati viene spostati dal margine sinistro.|
|[Elemento RightIndent per Frame per GroupBy (formato)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent elemento|Elemento facoltativo.<br /><br /> Specifica quanti caratteri di dati viene spostati dal margine destro.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomItem per CustomEntry per GroupBy (formato)](./customitem-element-for-customentry-for-groupby-format.md)|Definisce i dati che vengano visualizzati dal controllo e la modalità di visualizzazione.|

## <a name="remarks"></a>Osservazioni

Non è possibile specificare il [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) e il [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elementi nello stesso `Frame` elemento.

## <a name="see-also"></a>Vedere anche

[Elemento FirstLineHanging per Frame per GroupBy (formato)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[Elemento FirstLineIndent per Frame per GroupBy (formato)](./firstlineindent-element-for-frame-for-groupby-format.md)

[Elemento LeftIndent per Frame per GroupBy (formato)](./leftindent-element-for-frame-for-groupby-format.md)

[Elemento RightIndent per Frame per GroupBy (formato)](./rightindent-element-for-frame-for-groupby-format.md)

[Elemento CustomItem per CustomEntry per GroupBy (formato)](./customitem-element-for-customentry-for-groupby-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
