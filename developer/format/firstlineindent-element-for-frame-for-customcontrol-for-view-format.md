---
title: Elemento FirstLineIndent per Frame per CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 9ec6caedcb7cf20d4aab2216cd8a9707269d9452
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854957"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a>Elemento FirstLineIndent per Frame per CustomControl per View (formato)

Specifica il numero di caratteri la prima riga di dati verrà spostata a destra. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per elemento CustomItem visualizzazione (formato) CustomEntry per elemento Frame CutomControlView (formato) per CustomItem per CustomControl per elemento FirstLineIndent View (formato)

## <a name="syntax"></a>Sintassi

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono l'elemento padre di attributi e gli elementi figlio di `FirstLineIndent` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento frame per CustomItem per CustomControl per visualizzazione (formato)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra.|

## <a name="text-value"></a>Valore di testo

Specificare il numero di caratteri che si desidera spostare la prima riga dei dati.

## <a name="remarks"></a>Osservazioni

Se questo elemento viene specificato, non è possibile specificare il [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) elemento.

## <a name="see-also"></a>Vedere anche

[Elemento FirstLineHanging per Frame per CustomControl per visualizzazione (formato)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento frame per CustomItem per CustomControl per visualizzazione (formato)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
