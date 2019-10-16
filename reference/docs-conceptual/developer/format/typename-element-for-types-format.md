---
title: Elemento TypeName per types (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368030"
---
# <a name="typename-element-for-types-format"></a>Elemento TypeName per Types (formato)

Specifica il tipo .NET di un oggetto che appartiene al set di selezione.

Elemento Configuration (Format) elemento SelectionSets (Format) elemento SelectionSet (Format) elemento types (Format) elemento TypeName di tipi (Format)

## <a name="syntax"></a>Sintassi

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TypeName`. Nel set di selezione deve essere incluso almeno un elemento `TypeName`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento types (Format)](./types-element-for-selectionset-format.md)|Definisce gli oggetti .NET presenti nel set di selezione.|

## <a name="text-value"></a>Valore di testo

Specificare il nome completo per il tipo .NET.

## <a name="remarks"></a>Osservazioni

È possibile utilizzare i set di selezione quando si dispone di un set di oggetti correlati a cui si desidera fare riferimento utilizzando un solo nome, ad esempio un set di oggetti correlati tramite ereditarietà. Quando si definiscono le visualizzazioni, è possibile specificare il set di oggetti utilizzando il nome del set di selezione anziché elencare tutti gli oggetti all'interno di ogni visualizzazione.

I set di selezione comuni vengono specificati in base al relativo nome quando si definiscono le visualizzazioni del file di formattazione. In questi casi, l'elemento figlio `SelectionSetName` dell'elemento `ViewSelectedBy` per la vista specifica il set. Tuttavia, voci diverse di una vista possono anche specificare un set di selezione che si applica solo a tale voce della visualizzazione. Per ulteriori informazioni sui set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un elemento `SelectionSet` che definisce quattro tipi .NET.

```
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

[Elemento SelectionSets (Format)](./selectionsets-element-format.md)

[Elemento types (Format)](./types-element-for-selectionset-format.md)

[Scrittura di un file di formattazione di Windows PowerShell](./writing-a-powershell-formatting-file.md)
