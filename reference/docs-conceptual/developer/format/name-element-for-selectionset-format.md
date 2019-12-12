---
title: Elemento Name per SelectionSet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362670"
---
# <a name="name-element-for-selectionset-format"></a>Elemento Name per SelectionSet (formato)

Specifica il nome utilizzato per fare riferimento al set di selezione.

Elemento Configuration (Format) elemento SelectionSets (Format) elemento SelectionSet (Format) elemento Name di SelectionSet (Format)

## <a name="syntax"></a>Sintassi

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Name`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionSet (Format)](./selectionset-element-format.md)|Definisce un singolo set di oggetti .NET a cui è possibile fare riferimento dal nome del set.|

## <a name="text-value"></a>Valore testo

Specificare il nome per fare riferimento al set di selezione. Non esistono restrizioni per quanto riguarda i caratteri che possono essere usati.

## <a name="remarks"></a>Osservazioni

Il nome specificato qui viene usato nell'elemento `SelectionSetName`. Set di selezione che può essere utilizzato da una vista, da una definizione di una vista (le visualizzazioni possono avere più definizioni) o quando si specifica una condizione di selezione. Per ulteriori informazioni sui set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).

## <a name="example"></a>Esempio

Questo esempio illustra un elemento `SelectionSet` che definisce quattro tipi .NET. Il nome del set di selezione è "FileSystemTypes".

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

[Elemento SelectionSet (Format)](./selectionset-element-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
