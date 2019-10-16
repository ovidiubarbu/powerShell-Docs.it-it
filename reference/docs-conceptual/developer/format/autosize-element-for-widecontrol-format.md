---
title: Elemento AutoSize per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369050"
---
# <a name="autosize-element-for-widecontrol-format"></a>Elemento AutoSize per WideControl (formato)

Specifica se le dimensioni della colonna e il numero di colonne vengono regolate in base alle dimensioni dei dati.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento AutoSize per WideControl (Format)

## <a name="syntax"></a>Sintassi

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `AutoSize`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuno

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento WideControl (Format)](./widecontrol-element-format.md)|Definisce un formato di elenco Wide (valore singolo) per la visualizzazione.|

## <a name="remarks"></a>Osservazioni

Quando si definisce una visualizzazione estesa, è possibile aggiungere l'elemento `AutoSize` o l'elemento [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) , ma non è possibile aggiungere entrambi.

Per ulteriori informazioni sui componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).

Per un esempio di visualizzazione estesa, vedere [Wide View (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Vedere anche

[Elemento ColumnNumber per WideControl (Format)](./columnnumber-element-for-widecontrol-format.md)

[Creazione di una visualizzazione estesa](./creating-a-wide-view.md)

[Elemento WideControl (Format)](./widecontrol-element-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
