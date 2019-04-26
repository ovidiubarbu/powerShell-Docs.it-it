---
title: Nome elemento SelectionSet (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065156"
---
# <a name="name-element-for-selectionset-format"></a>Elemento Name per SelectionSet (formato)

Specifica il nome utilizzato per fare riferimento il set di selezione.

Nome elemento di configurazione elemento (formato) elemento SelectionSets (formato) elemento SelectionSet (formato) di SelectionSet (formato)

## <a name="syntax"></a>Sintassi

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `Name` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionSet (formato)](./selectionset-element-format.md)|Definisce un singolo set di oggetti .NET che possono fare riferimento il nome del set.|

## <a name="text-value"></a>Valore di testo

Specificare il nome per fare riferimento a set di selezione. Sono disponibili non possono essere utilizzati restrizioni per quanto riguarda i caratteri.

## <a name="remarks"></a>Osservazioni

Il nome specificato in questo campo viene usato nel `SelectionSetName` elemento. Il set di selezione che può essere utilizzato da una visualizzazione, da una definizione di una vista (visualizzazioni possono avere più definizioni,) o quando si specifica una condizione di selezione. Per altre informazioni sui set di selezione, vedere [definizione imposta di oggetti](./defining-selection-sets.md).

## <a name="example"></a>Esempio

Questo esempio viene illustrato un `SelectionSet` elemento che definisce i quattro tipi di .NET. Il nome del set di selezione è "FileSystemTypes".

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

[Elemento SelectionSet (formato)](./selectionset-element-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
