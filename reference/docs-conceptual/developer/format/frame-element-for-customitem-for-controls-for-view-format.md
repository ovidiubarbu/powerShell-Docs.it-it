---
title: Elemento frame per CustomItem per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363650"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>Elemento Frame per CustomItem per Controls per View (formato)

Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per la visualizzazione (Format) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) CustomItem elemento per CustomEntry per i controlli per la visualizzazione (formato) elemento frame per CustomItem per i controlli per la visualizzazione (formato)

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
|[Elemento FirstLineHanging del frame di controlli della visualizzazione (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri che la prima riga viene spostata a sinistra.|
|[Elemento FirstLineIndent del frame di controlli della visualizzazione (Format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri che la prima riga viene spostata a destra.|
|[Elemento LeftIndent del frame di controlli della visualizzazione (Format)](./leftindent-element-for-frame-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri spostati al di fuori del margine sinistro.|
|[Elemento RightIndent del frame di controlli della visualizzazione (Format)](./rightindent-element-for-frame-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri spostati al di fuori del margine destro da parte dei dati.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Definisce quali dati vengono visualizzati dal controllo e come vengono visualizzati.|

## <a name="remarks"></a>Osservazioni

Non è possibile specificare gli elementi [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) e [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) nello stesso elemento `Frame`.

## <a name="see-also"></a>Vedere anche

[Elemento FirstLineHanging del frame di controlli della visualizzazione (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[Elemento FirstLineIndent del frame di controlli della visualizzazione (Format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[Elemento LeftIndent del frame di controlli della visualizzazione (Format)](./leftindent-element-for-frame-for-controls-for-view-format.md)

[Elemento RightIndent del frame di controlli della visualizzazione (Format)](./rightindent-element-for-frame-for-controls-for-view-format.md)

[Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
