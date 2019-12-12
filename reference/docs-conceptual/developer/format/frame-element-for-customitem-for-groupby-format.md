---
title: Elemento frame per CustomItem per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362950"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>Elemento Frame per CustomItem per GroupBy (formato)

Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format) elemento CustomItem per CustomEntry per l'elemento frame GroupBy (Format) per CustomItem per GroupBy (Format)

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

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Frame`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|`CustomItem Element`|Elemento obbligatorio|
|[Elemento FirstLineHanging per frame per GroupBy (Format)](./firstlinehanging-element-for-frame-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri che la prima riga di dati viene spostata a sinistra.|
|[Elemento FirstLineIndent per frame per GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri che la prima riga di dati viene spostata a destra.|
|[Elemento LeftIndent per frame per GroupBy (Format)](./leftindent-element-for-frame-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri spostati al di fuori del margine sinistro.|
|[Elemento RightIndent per frame per GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md) Elemento RightIndent|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri spostati al di fuori del margine destro da parte dei dati.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomItem per CustomEntry per GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)|Definisce quali dati vengono visualizzati dal controllo e come vengono visualizzati.|

## <a name="remarks"></a>Osservazioni

Non è possibile specificare gli elementi [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) e [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) nello stesso elemento `Frame`.

## <a name="see-also"></a>Vedere anche

[Elemento FirstLineHanging per frame per GroupBy (Format)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[Elemento FirstLineIndent per frame per GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md)

[Elemento LeftIndent per frame per GroupBy (Format)](./leftindent-element-for-frame-for-groupby-format.md)

[Elemento RightIndent per frame per GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)

[Elemento CustomItem per CustomEntry per GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
