---
title: Elemento FirstLineHanging per il frame per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 679c8bcb-b49d-4bb4-91f5-ea1af6c217e3
caps.latest.revision: 8
ms.openlocfilehash: 4553f95e48a2b1440c00b4951bea56376b00628a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363170"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-configuration-format"></a>Elemento FirstLineHanging per Frame per Controls per Configuration (formato)

Specifica il numero di caratteri che la prima riga di dati viene spostata a sinistra. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento CustomItem per CustomEntry per i controlli per l'elemento del frame di configurazione per CustomItem per i controlli per la configurazione (Format) elemento FirstLineHanging per frame per i controlli per la configurazione (Format)

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
|[Elemento frame per CustomItem per i controlli per la configurazione (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra.|

## <a name="text-value"></a>Valore testo

Consente di specificare il numero di caratteri che si desidera spostare nella prima riga dei dati.

## <a name="remarks"></a>Osservazioni

Se questo elemento è specificato, non è possibile specificare l'elemento `FirstLineIndent`.

## <a name="see-also"></a>Vedere anche

[Elemento frame per CustomItem per i controlli per la configurazione (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
