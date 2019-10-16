---
title: Elemento FirstLineIndent per frame per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 3130ecc69f7d1568bcbd392dd24e8cdcc3382905
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363060"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a>Elemento FirstLineIndent per Frame per CustomControl per View (formato)

Specifica il numero di caratteri che la prima riga di dati viene spostata a destra. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per la vista (Format) CustomEntry elemento per CustomEntries per la visualizzazione (Format) CustomItem elemento per CustomEntry per l'elemento frame CustomControlView (Format) per CustomItem per CustomControl per l'elemento View (Format) FirstLineIndent

## <a name="syntax"></a>Sintassi

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `FirstLineIndent`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento frame per CustomItem per CustomControl per View (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra.|

## <a name="text-value"></a>Valore di testo

Consente di specificare il numero di caratteri che si desidera spostare nella prima riga dei dati.

## <a name="remarks"></a>Osservazioni

Se questo elemento è specificato, non è possibile specificare l'elemento [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) .

## <a name="see-also"></a>Vedere anche

[Elemento FirstLineHanging per frame per CustomControl per View (Format)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento frame per CustomItem per CustomControl per View (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
