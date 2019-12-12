---
title: Elemento DisplayError (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363990"
---
# <a name="displayerror-element-format"></a>Elemento DisplayError (formato)

Specifica che la stringa #ERR viene visualizzata quando si verifica un errore durante la visualizzazione di una porzione di dati.

Elemento Configuration (Format) elemento DefaultSettings (Format) elemento DisplayError (Format)

## <a name="syntax"></a>Sintassi

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `DisplayError`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento DefaultSettings (Format)](./defaultsettings-element-format.md)|Definisce le impostazioni comuni che si applicano a tutte le visualizzazioni del file di formattazione.|

## <a name="remarks"></a>Osservazioni

Per impostazione predefinita, quando si verifica un errore durante il tentativo di visualizzare una porzione di dati, la posizione dei dati viene lasciata vuota. Quando questo elemento è impostato su true, viene visualizzata la stringa #ERR.

## <a name="see-also"></a>Vedere anche

[Elemento DefaultSettings (Format)](./defaultsettings-element-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
