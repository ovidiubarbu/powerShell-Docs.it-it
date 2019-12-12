---
title: Elemento CustomEntries per CustomControl per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368820"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a>Elemento CustomEntries per CustomControl per Controls per Configuration (formato)

Fornisce le definizioni di un controllo comune. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Formato

## <a name="syntax"></a>Sintassi

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomEntries`. È necessario specificare uno o più elementi figlio.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntry per CustomControl per i controlli per la configurazione (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Fornisce una definizione del controllo comune.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomControl per Control per Configuration (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Definisce un controllo comune.|

## <a name="remarks"></a>Osservazioni

Nella maggior parte dei casi, un controllo ha una sola definizione, definita in un singolo elemento `CustomEntry`. Tuttavia, se si desidera utilizzare lo stesso controllo per visualizzare oggetti .NET diversi, è possibile disporre di più definizioni. In questi casi, è possibile definire un elemento `CustomEntry` per ogni oggetto o set di oggetti.

## <a name="see-also"></a>Vedere anche

[Elemento CustomControl per Control per Configuration (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[Elemento CustomEntry per CustomControl per i controlli per la configurazione (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
