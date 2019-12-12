---
title: Elemento Controls per Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369000"
---
# <a name="controls-element-for-configuration-format"></a>Elemento Controls per Configuration (formato)

Definisce i controlli comuni che possono essere utilizzati da tutte le visualizzazioni del file di formattazione.

Elemento Configuration (Format) controlla l'elemento di configurazione (Format)

## <a name="syntax"></a>Sintassi

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Controls`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento Control per Controls per Configuration (Format)](./control-element-for-controls-for-configuration-format.md)|Elemento obbligatorio.<br /><br /> Definisce un controllo comune che può essere usato da tutte le visualizzazioni del file di formattazione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento Configuration (Format)](./configuration-element-format.md)|Rappresenta l'elemento di primo livello di un file di formattazione.|

## <a name="remarks"></a>Osservazioni

È possibile creare un numero qualsiasi di controlli comuni. Per ogni controllo è necessario specificare il nome usato per fare riferimento al controllo e ai componenti del controllo.

## <a name="see-also"></a>Vedere anche

[Elemento Configuration (Format)](./configuration-element-format.md)

[Elemento Control per Controls per Configuration (Format)](./control-element-for-controls-for-configuration-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
