---
title: Elemento TypeName per EntrySelectedBy per EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0506928-db92-4ec4-855f-6f3592a383ae
caps.latest.revision: 6
ms.openlocfilehash: 5ead806d956ebbef95eeffc42bb39ef784208017
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361750"
---
# <a name="typename-element-for-entryselectedby-for-enumerableexpansion-format"></a>Elemento TypeName per EntrySelectedBy per EnumerableExpansion (formato)

Specifica un tipo .NET espanso da questa definizione. Questo elemento viene utilizzato quando si definiscono impostazioni predefinite.

Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format) elemento EntrySelectedBy per EnumerableExpansion (Format) TypeName elemento per EntrySelectedBy per EnumerableExpansion (formato)

## <a name="syntax"></a>Sintassi

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TypeName`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)|Definisce i tipi .NET che utilizzano questa definizione o la condizione che deve esistere affinché questa definizione venga utilizzata.|

## <a name="text-value"></a>Valore di testo

Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Osservazioni

## <a name="see-also"></a>Vedere anche

[Elemento EntrySelectedBy per EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
