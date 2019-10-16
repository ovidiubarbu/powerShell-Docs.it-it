---
title: Elemento SelectionSetName per EntrySelectedBy per EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368330"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a>Elemento SelectionSetName per EntrySelectedBy per EnumerableExpansion (formato)

Specifica il set di tipi .NET espansi da questa definizione.

Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format) elemento EntrySelectedBy per EnumerableExpansion (Format) SelectionSetName elemento per EntrySelectedBy per EnumerableExpansion (formato)

## <a name="syntax"></a>Sintassi

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)|Definisce gli oggetti della raccolta .NET espansi da questa definizione.|

## <a name="text-value"></a>Valore di testo

Consente di specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

Ogni definizione deve specificare uno o più nomi di tipo, un set di selezione o una condizione di selezione.

I set di selezione vengono in genere utilizzati quando si desidera definire un gruppo di oggetti utilizzati in più viste. Ad esempio, potrebbe essere necessario creare una visualizzazione tabella e una visualizzazione elenco per lo stesso set di oggetti. Per ulteriori informazioni sulla definizione di set di selezione, vedere [definizione di set di oggetti per una vista](./defining-selection-sets.md).

## <a name="see-also"></a>Vedere anche

[Definizione di set di selezione](./defining-selection-sets.md)

[Elemento EntrySelectedBy per EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
