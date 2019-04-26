---
title: Elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066295"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>Elemento EntrySelectedBy per CustomEntry per Controls per Configuration (formato)

Definisce i tipi .NET che usano la definizione di controllo comune o la condizione che deve essere presente per questo controllo da utilizzare. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli di configurazione (formato) CustomControl elemento per il controllo per elemento di configurazione (formato) CustomEntries per CustomControl per Configuration ( Elemento CustomEntry Format) per CustomControl per i controlli per elemento di configurazione (formato) EntrySelectedBy per CustomEntry per i controlli per la configurazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `EntrySelectedBy` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve essere presente per la definizione di controllo comuni da usare.|
|[Elemento SelectionSetName per EntrySelectedBy per i controlli per la configurazione (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica un set di tipi .NET che usano questa definizione del controllo comune.|
|[Elemento TypeName per EntrySelectedBy per i controlli per la configurazione (formato)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che usa questa definizione del controllo comune.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntry per CustomControl per i controlli per la configurazione (formato)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Fornisce una definizione del controllo comune.|

## <a name="remarks"></a>Osservazioni

Come minimo, ogni definizione deve avere almeno un tipo, set di selezione o condizione di selezione specificata .NET. Non è definito alcun limite massimo al numero di tipi, set di selezione o condizioni di selezione che è possibile specificare.

## <a name="see-also"></a>Vedere anche

[Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Elemento SelectionSetName per EntrySelectedBy per i controlli per la configurazione (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elemento CustomEntry per CustomControl per i controlli per la configurazione (formato)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Elemento TypeName per EntrySelectedBy per i controlli per la configurazione (formato)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
