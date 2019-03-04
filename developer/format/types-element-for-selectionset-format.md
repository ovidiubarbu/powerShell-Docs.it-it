---
title: I tipi di elemento per SelectionSet (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862377"
---
# <a name="types-element-for-selectionset-format"></a>Elemento Types per SelectionSet (formato)

Definisce gli oggetti .NET nella selezione impostate.

Configurazione (formato) elemento SelectionSets (formato) SelectionSet elemento (formato) i tipi di elemento (formato)

## <a name="syntax"></a>Sintassi

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Types` elemento. Deve esistere almeno un elemento figlio, ma non è definito alcun limite massimo al numero di elementi figlio che possono essere aggiunti.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento TypeName di tipi (formato)](./typename-element-for-types-format.md)|Elemento obbligatorio.<br /><br /> Specifica l'oggetto .NET a cui appartiene il set di selezione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionSet (formato)](./selectionset-element-format.md)|Definisce un set di oggetti .NET che possono fare riferimento il nome del set.|

## <a name="remarks"></a>Osservazioni

Gli oggetti definiti da questo elemento costituiscono un set di selezione che può essere utilizzato da una visualizzazione, da una definizione di una vista (visualizzazioni possono avere più definizioni,) o quando si specifica una condizione di selezione.  Per altre informazioni sui set di selezione, vedere [definizione imposta di oggetti](./defining-selection-sets.md).

## <a name="example"></a>Esempio

Questo esempio viene illustrato un `SelectionSet` elemento che definisce i quattro tipi di .NET.

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a>Vedere anche

[La definizione di set di oggetti](./defining-selection-sets.md)

[Elemento SelectionSet (formato)](./selectionset-element-format.md)

[Elemento TypeName di tipi (formato)](./typename-element-for-types-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
