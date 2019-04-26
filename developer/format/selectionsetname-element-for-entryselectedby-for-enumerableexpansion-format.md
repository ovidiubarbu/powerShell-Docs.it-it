---
title: Elemento SelectionSetName per EntrySelectedBy per EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076260"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a>Elemento SelectionSetName per EntrySelectedBy per EnumerableExpansion (formato)

Specifica il set di tipi .NET che vengono espanse per questa definizione.

Configurazione (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) elemento EnumerableExpansion (formato) EntrySelectedBy elemento per elemento SelectionSetName EnumerableExpansion (formato) per EntrySelectedBy per EnumerableExpansion (formato)

## <a name="syntax"></a>Sintassi

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSetName` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per EnumerableExpansion (formato)](./entryselectedby-element-for-enumerableexpansion-format.md)|Definisce gli oggetti della raccolta .NET che vengono espanse per questa definizione.|

## <a name="text-value"></a>Valore di testo

Specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

Ogni definizione deve specificare uno o più nomi di tipo, un set di selezione o una condizione di selezione.

Set di selezione vengono usati quando si desidera definire un gruppo di oggetti utilizzati in più viste. Ad esempio, è possibile creare una visualizzazione tabella e una visualizzazione elenco per lo stesso set di oggetti. Per altre informazioni sulla definizione di set di selezione, vedere [definizione imposta di oggetti per una visualizzazione](./defining-selection-sets.md).

## <a name="see-also"></a>Vedere anche

[La definizione di set di selezione](./defining-selection-sets.md)

[Elemento EntrySelectedBy per EnumerableExpansion (formato)](./entryselectedby-element-for-enumerableexpansion-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
