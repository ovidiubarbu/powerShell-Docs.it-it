---
title: Elemento SelectionSetName per EntrySelectedBy per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364790"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a>Elemento SelectionSetName per EntrySelectedBy per Controls per Configuration (formato)

Specifica un set di tipi .NET che utilizzano questa definizione del controllo. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (Format) SelectionSetName elemento per EntrySelectedBy per i controlli per la configurazione (Format)

## <a name="syntax"></a>Sintassi

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.

### <a name="attributes"></a>Attributi

Nessuno

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata.|

## <a name="text-value"></a>Valore di testo

Consente di specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

Per ogni definizione di controllo deve essere definito almeno un nome di tipo, un set di selezione o una condizione di selezione.

I set di selezione vengono in genere utilizzati quando si desidera definire un gruppo di oggetti utilizzati in più viste. Per ulteriori informazioni sulla definizione di set di selezione, vedere [definizione di set di selezione](./defining-selection-sets.md).

## <a name="see-also"></a>Vedere anche

[Elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
