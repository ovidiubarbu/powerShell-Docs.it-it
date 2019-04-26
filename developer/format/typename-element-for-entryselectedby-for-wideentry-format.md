---
title: Elemento TypeName per EntrySelectedBy per WideEntry (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083927"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a>Elemento TypeName per EntrySelectedBy per WideEntry (formato)

Specifica un tipo .NET per la definizione. La definizione viene utilizzata ogni volta che viene visualizzato questo oggetto.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento di configurazione per TypeName WideEntry (formato) (elemento) per WideEntry ( Formato)

## <a name="syntax"></a>Sintassi

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `TypeName` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md)|Definisce i tipi .NET che usano questa voce ampia o la condizione che deve essere presente per questa voce da usare.|

## <a name="text-value"></a>Valore di testo

Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Osservazioni

Ogni voce ampia è necessario specificare uno o più tipi di .NET, un set di selezione o la condizione di selezione che deve essere presente per la definizione da usare.

Per altre informazioni sugli altri componenti di una visualizzazione più ampia, vedere [creazione di una visualizzazione più ampia](./creating-a-wide-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione più ampia](./creating-a-wide-view.md)

[Elemento EntrySelectedBy per WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
