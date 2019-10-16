---
title: Elemento frame per CustomItem per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363640"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a>Elemento Frame per CustomItem per CustomControl per View (formato)

Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per la vista (Format) CustomEntry elemento per CustomEntries per la visualizzazione (Format) CustomItem elemento per CustomEntry per l'elemento frame CustomControlView (Format) per CustomItem per CustomControl per la visualizzazione (Format)

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
|[Elemento FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri che la prima riga di dati viene spostata a sinistra.|
|[Elemento FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri che la prima riga di dati viene spostata a destra.|
|[Elemento LeftIndent](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri spostati al di fuori del margine sinistro.|
|[Elemento RightIndent](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri spostati al di fuori del margine destro da parte dei dati.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomItem per CustomEntry per View (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Definisce quali dati vengono visualizzati dal controllo e come vengono visualizzati.|

## <a name="remarks"></a>Osservazioni

Non è possibile specificare gli elementi [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) e [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) nello stesso elemento `Frame`.

## <a name="see-also"></a>Vedere anche

[Elemento FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento LeftIndent](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento RightIndent](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento CustomItem per CustomEntry per View (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
