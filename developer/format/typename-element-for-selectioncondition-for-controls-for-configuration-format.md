---
title: Elemento TypeName per SelectionCondition per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 477c8711-fffc-4f92-af45-6d4f80990474
caps.latest.revision: 7
ms.openlocfilehash: 60f02f3240c5574e1b1f9027b060bd9af89a11d2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853597"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a>Elemento TypeName per SelectionCondition per Controls per Configuration (formato)

Specifica un tipo .NET che attiva la condizione. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Configurazione (formato) i controlli elemento dell'elemento di controllo di configurazione (formato) per i controlli per Configuration (formato) CustomControl elemento per elemento Configuration (formato) CustomEntries CustomControl dei controlli per il controllo Elemento CustomEntry di configurazione (formato) per CustomControl per i controlli per elemento di configurazione (formato) EntrySelectedBy per CustomEntry per i controlli per elemento di configurazione (formato) SelectionCondition per EntrySelectedBy per CustomEntry per Elemento TypeName di configurazione (formato) per SelectionCondition per i controlli per la configurazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `TypeName` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per CustomEntry per la configurazione (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Definisce una condizione che deve essere presente per la definizione di controllo da utilizzare.|

## <a name="text-value"></a>Valore di testo

Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Osservazioni

## <a name="see-also"></a>Vedere anche

[Elemento SelectionCondition per EntrySelectedBy per CustomEntry per la configurazione (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
