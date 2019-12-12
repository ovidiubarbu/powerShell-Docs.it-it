---
title: Elemento FirstLineIndent per il frame per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f489720-11f6-4019-940e-07f423d4278d
caps.latest.revision: 6
ms.openlocfilehash: c5b2d971fe1590116f96b024ae8769334768acf2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363120"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-configuration-format"></a>Elemento FirstLineIndent per Frame per Controls per Configuration (formato)

Specifica il numero di caratteri che la prima riga di dati viene spostata a destra. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento CustomItem per CustomEntry per i controlli per l'elemento del frame di configurazione per CustomItem per i controlli per la configurazione (Format) elemento FirstLineIndent per frame per i controlli per la configurazione (Format)

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
|[Elemento frame per CustomItem per i controlli per la configurazione (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra.|

## <a name="text-value"></a>Valore testo

Consente di specificare il numero di caratteri che si desidera spostare nella prima riga dei dati.

## <a name="remarks"></a>Osservazioni

Se questo elemento è specificato, non è possibile specificare l'elemento [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) .

## <a name="see-also"></a>Vedere anche

[Elemento FirstLineHanging per il frame per i controlli per la configurazione (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[Elemento frame per CustomItem per i controlli per la configurazione (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
