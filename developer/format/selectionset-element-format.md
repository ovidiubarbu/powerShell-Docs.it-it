---
title: Elemento SelectionSet (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861157"
---
# <a name="selectionset-element-format"></a>Elemento SelectionSet (formato)

Definisce un set di oggetti .NET che possono fare riferimento il nome del set.

Configurazione (formato) elemento SelectionSets (formato) SelectionSet elemento (formato)

## <a name="syntax"></a>Sintassi

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSet` elemento. Ogni set di selezione deve avere un nome e deve specificare gli oggetti .NET del set.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento Name per SelectionSet (formato)](./name-element-for-selectionset-format.md)|Elemento obbligatorio.<br /><br /> Specifica il nome utilizzato per fare riferimento il set di selezione.|
|[Elemento di Types (formato)](./types-element-for-selectionset-format.md)|Elemento obbligatorio.<br /><br /> Definisce gli oggetti .NET nella selezione impostate.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Formato elemento SelectionSets](./selectionsets-element-format.md)|Definisce il set di oggetti .NET che possono essere usati da tutte le visualizzazioni del file di formattazione comuni.|

## <a name="remarks"></a>Osservazioni

Quando si dispone di un set di oggetti correlati che si desidera fare riferimento tramite un solo nome, ad esempio un set di oggetti che sono correlati tramite l'ereditarietà, è possibile usare set di selezione. Quando si definiscono le visualizzazioni, è possibile specificare il set di oggetti utilizzando il nome della selezione set anziché elencare tutti gli oggetti all'interno di ogni visualizzazione.

Set di selezione comune vengono specificati in base al nome quando si definisce le viste del file di formattazione e le definizioni delle viste. In questi casi, il `SelectionSetName` elemento figlio dell'elemento di `ViewSelectedBy` e `EntrySelectedBy` elementi specifica il set da utilizzare. Per altre informazioni sui set di selezione, vedere [definizione imposta di oggetti](./defining-selection-sets.md).

## <a name="example"></a>Esempio

L'esempio seguente mostra un `SelectionSet` elemento che definisce i quattro tipi di .NET.

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

[La definizione di set di selezione](./defining-selection-sets.md)

[Elemento Name di SelectionSet (formato)](./name-element-for-selectionset-format.md)

[Elemento SelectionSets (formato)](./selectionsets-element-format.md)

[Elemento di Types (formato)](./types-element-for-selectionset-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
