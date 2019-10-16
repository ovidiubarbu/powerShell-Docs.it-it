---
title: Elemento SelectionSet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368380"
---
# <a name="selectionset-element-format"></a>Elemento SelectionSet (formato)

Definisce un set di oggetti .NET a cui è possibile fare riferimento dal nome del set.

Elemento Configuration (Format) elemento SelectionSets (Format) elemento SelectionSet (Format)

## <a name="syntax"></a>Sintassi

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSet`. Ogni set di selezione deve avere un nome e deve specificare gli oggetti .NET del set.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento Name per SelectionSet (Format)](./name-element-for-selectionset-format.md)|Elemento obbligatorio.<br /><br /> Specifica il nome utilizzato per fare riferimento al set di selezione.|
|[Elemento types (Format)](./types-element-for-selectionset-format.md)|Elemento obbligatorio.<br /><br /> Definisce gli oggetti .NET presenti nel set di selezione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Formato elemento SelectionSets](./selectionsets-element-format.md)|Definisce i set comuni di oggetti .NET che possono essere utilizzati da tutte le visualizzazioni del file di formattazione.|

## <a name="remarks"></a>Osservazioni

È possibile utilizzare i set di selezione quando si dispone di un set di oggetti correlati a cui si desidera fare riferimento utilizzando un solo nome, ad esempio un set di oggetti correlati tramite ereditarietà. Quando si definiscono le visualizzazioni, è possibile specificare il set di oggetti utilizzando il nome del set di selezione anziché elencare tutti gli oggetti all'interno di ogni visualizzazione.

I set di selezione comuni vengono specificati in base al relativo nome quando si definiscono le visualizzazioni del file di formattazione o le definizioni delle viste. In questi casi, l'elemento figlio `SelectionSetName` degli elementi `ViewSelectedBy` e `EntrySelectedBy` specifica il set da usare. Per ulteriori informazioni sui set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un elemento `SelectionSet` che definisce quattro tipi .NET.

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

[Definizione di set di selezione](./defining-selection-sets.md)

[Elemento Name di SelectionSet (Format)](./name-element-for-selectionset-format.md)

[Elemento SelectionSets (Format)](./selectionsets-element-format.md)

[Elemento types (Format)](./types-element-for-selectionset-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
