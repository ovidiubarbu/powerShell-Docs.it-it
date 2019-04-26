---
title: Elemento dei frame per CustomItem per CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065581"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a>Elemento Frame per CustomItem per CustomControl per View (formato)

Definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per elemento CustomItem visualizzazione (formato) CustomEntry per elemento Frame CustomControlView (formato) per CustomItem per CustomControl per visualizzazione (formato)

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

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Frame` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|`CustomItem Element`|Elemento obbligatorio|
|[Elemento FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri la prima riga di dati verrà spostata a sinistra.|
|[Elemento FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di caratteri la prima riga di dati verrà spostata a destra.|
|[Elemento LeftIndent](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica quanti caratteri di dati viene spostati dal margine sinistro.|
|[Elemento RightIndent](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica quanti caratteri di dati viene spostati dal margine destro.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomItem per CustomEntry per visualizzazione (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Definisce i dati che vengano visualizzati dal controllo e la modalità di visualizzazione.|

## <a name="remarks"></a>Osservazioni

Non è possibile specificare il [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) e il [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elementi nello stesso `Frame` elemento.

## <a name="see-also"></a>Vedere anche

[Elemento FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento LeftIndent](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento RightIndent](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento CustomItem per CustomEntry per visualizzazione (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
