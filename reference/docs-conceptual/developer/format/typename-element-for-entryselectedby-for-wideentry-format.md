---
title: Elemento TypeName per EntrySelectedBy per WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361620"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a>Elemento TypeName per EntrySelectedBy per WideEntry (formato)

Specifica un tipo .NET per la definizione. La definizione viene utilizzata ogni volta che l'oggetto viene visualizzato.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) EntrySelectedBy elemento per WideEntry (Format) TypeName elemento per WideEntry ( Formato

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
|[Elemento EntrySelectedBy per WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Definisce i tipi .NET che utilizzano questa voce estesa o la condizione che deve esistere affinché questa voce venga utilizzata.|

## <a name="text-value"></a>Valore di testo

Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Osservazioni

Ogni voce estesa deve specificare uno o più tipi .NET, un set di selezione o la condizione di selezione che deve esistere per la definizione da usare.

Per ulteriori informazioni su altri componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione estesa](./creating-a-wide-view.md)

[Elemento EntrySelectedBy per WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
