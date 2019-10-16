---
title: Elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368770"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>Elemento EntrySelectedBy per CustomEntry per Controls per Configuration (formato)

Definisce i tipi .NET che usano la definizione del controllo comune o la condizione che deve esistere affinché questo controllo venga usato. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (Format)

## <a name="syntax"></a>Sintassi

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `EntrySelectedBy`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve esistere per la definizione del controllo comune da utilizzare.|
|[Elemento SelectionSetName per EntrySelectedBy per i controlli per la configurazione (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica un set di tipi .NET che utilizzano questa definizione del controllo comune.|
|[Elemento TypeName per EntrySelectedBy per i controlli per la configurazione (Format)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che usa questa definizione del controllo comune.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntry per CustomControl per i controlli per la configurazione (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Fornisce una definizione del controllo comune.|

## <a name="remarks"></a>Osservazioni

Come minimo, ogni definizione deve avere almeno un tipo .NET, un set di selezione o una condizione di selezione specificata. Non esiste un limite massimo per il numero di tipi, set di selezione o condizioni di selezione che è possibile specificare.

## <a name="see-also"></a>Vedere anche

[Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Elemento SelectionSetName per EntrySelectedBy per i controlli per la configurazione (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elemento CustomEntry per CustomControl per i controlli per la configurazione (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Elemento TypeName per EntrySelectedBy per i controlli per la configurazione (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
