---
title: Elemento types per SelectionSet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367960"
---
# <a name="types-element-for-selectionset-format"></a>Elemento Types per SelectionSet (formato)

Definisce gli oggetti .NET presenti nel set di selezione.

Elemento Configuration (Format) elemento SelectionSets (Format) elemento types (Format) elemento SelectionSet (Format)

## <a name="syntax"></a>Sintassi

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Types`. Deve essere presente almeno un elemento figlio, ma non esiste un limite massimo per il numero di elementi figlio che è possibile aggiungere.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento TypeName dei tipi (Format)](./typename-element-for-types-format.md)|Elemento obbligatorio.<br /><br /> Specifica l'oggetto .NET che appartiene al set di selezione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionSet (Format)](./selectionset-element-format.md)|Definisce un set di oggetti .NET a cui è possibile fare riferimento dal nome del set.|

## <a name="remarks"></a>Osservazioni

Gli oggetti definiti da questo elemento costituiscono un set di selezione che può essere utilizzato da una vista, da una definizione di una vista (le visualizzazioni possono avere più definizioni) o quando si specifica una condizione di selezione.  Per ulteriori informazioni sui set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).

## <a name="example"></a>Esempio

Questo esempio mostra un elemento `SelectionSet` che definisce quattro tipi .NET.

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

[Definizione di set di oggetti](./defining-selection-sets.md)

[Elemento SelectionSet (Format)](./selectionset-element-format.md)

[Elemento TypeName dei tipi (Format)](./typename-element-for-types-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
