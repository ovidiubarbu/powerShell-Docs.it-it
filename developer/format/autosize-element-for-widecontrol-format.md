---
title: AutoSize (elemento) per WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066924"
---
# <a name="autosize-element-for-widecontrol-format"></a>Elemento AutoSize per WideControl (formato)

Specifica se la dimensione della colonna e il numero di colonne vengono adattate in base alla dimensione dei dati.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) Autosize elemento di configurazione per WideControl (formato)

## <a name="syntax"></a>Sintassi

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `AutoSize` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuno

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento WideControl (formato)](./widecontrol-element-format.md)|Definisce un'ampia (valore singolo) formato di elenco per la visualizzazione.|

## <a name="remarks"></a>Osservazioni

Quando si definisce una visualizzazione più ampia, è possibile aggiungere il `AutoSize` elemento o il [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) elemento, ma è possibile aggiungere entrambi.

Per altre informazioni sui componenti di una visualizzazione più ampia, vedere [creazione di una visualizzazione più ampia](./creating-a-wide-view.md).

Per un esempio di una visualizzazione più ampia, vedere [visualizzazione più ampia (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Vedere anche

[Elemento ColumnNumber per WideControl (formato)](./columnnumber-element-for-widecontrol-format.md)

[Creazione di una visualizzazione più ampia](./creating-a-wide-view.md)

[Elemento WideControl (formato)](./widecontrol-element-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
