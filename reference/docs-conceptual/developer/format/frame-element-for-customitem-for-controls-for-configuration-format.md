---
title: Elemento frame per CustomItem per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363660"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>Elemento Frame per CustomItem per Controls per Configuration (formato)

Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento CustomItem per CustomEntry per i controlli per l'elemento del frame di configurazione per CustomItem per i controlli per la configurazione (Format)

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
|[Elemento FirstLineHanging per il frame per i controlli per la configurazione (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri che la prima riga di dati viene spostata a sinistra.|
|[Elemento FirstLineIndent per il frame per i controlli per la configurazione (Format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri che la prima riga di dati viene spostata a destra.|
|[Elemento LeftIndent per il frame per i controlli per la configurazione (Format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri spostati al di fuori del margine sinistro.|
|[Elemento RightIndent per il frame per i controlli per la configurazione (Format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri spostati al di fuori del margine destro da parte dei dati.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomItem per CustomEntry per i controlli per la configurazione](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Definisce quali dati vengono visualizzati dal controllo e come vengono visualizzati.|

## <a name="remarks"></a>Osservazioni

Non è possibile specificare gli elementi [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) e [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) nello stesso elemento `Frame`.

## <a name="see-also"></a>Vedere anche

[Elemento FirstLineHanging per il frame per i controlli per la configurazione (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[Elemento FirstLineIndent per il frame per i controlli per la configurazione (Format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[Elemento LeftIndent per il frame per i controlli per la configurazione (Format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[Elemento RightIndent per il frame per i controlli per la configurazione (Format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[Elemento CustomItem per CustomEntry per i controlli per la configurazione](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
