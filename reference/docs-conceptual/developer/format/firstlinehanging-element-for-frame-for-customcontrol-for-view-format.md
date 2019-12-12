---
title: Elemento FirstLineHanging per frame per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6ac3d86-0529-4b93-9bc7-ee94fcef9618
caps.latest.revision: 8
ms.openlocfilehash: ea43e025f5f653ff000e1d7591b535e73da5c9e5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363160"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a>Elemento FirstLineHanging per Frame per CustomControl per View (formato)

Specifica il numero di caratteri che la prima riga di dati viene spostata a sinistra. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per la vista (Format) CustomEntry elemento per CustomEntries per la visualizzazione (Format) CustomItem elemento per CustomEntry per l'elemento frame CustomControlView (Format) per CustomItem per CustomControl per l'elemento View (Format) FirstLineHanging per frame for CustomControl per View (Format)

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
|[Elemento frame per CustomItem per CustomControl per View (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra.|

## <a name="text-value"></a>Valore testo

Consente di specificare il numero di caratteri che si desidera spostare nella prima riga dei dati.

## <a name="remarks"></a>Osservazioni

Se questo elemento è specificato, non è possibile specificare l'elemento [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) .

## <a name="see-also"></a>Vedere anche

[Elemento FirstLineIndent per frame per CustomControl per View (Format)](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento frame per CustomItem per CustomControl per View (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
