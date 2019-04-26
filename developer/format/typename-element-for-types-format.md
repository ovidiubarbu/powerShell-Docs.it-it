---
title: TypeName (elemento) per tipi (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083791"
---
# <a name="typename-element-for-types-format"></a>Elemento TypeName per Types (formato)

Specifica il tipo .NET dell'oggetto che appartiene al set di selezione.

Configurazione (formato) elemento SelectionSets (formato) SelectionSet elemento (formato) i tipi di elemento (formato) elemento TypeName di tipi (formato)

## <a name="syntax"></a>Sintassi

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `TypeName` elemento. Almeno un `TypeName` elemento deve essere incluso nel set di selezione.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento di Types (formato)](./types-element-for-selectionset-format.md)|Definisce gli oggetti .NET nella selezione impostate.|

## <a name="text-value"></a>Valore di testo

Specificare il nome completo per il tipo .NET.

## <a name="remarks"></a>Osservazioni

Quando si dispone di un set di oggetti correlati che si desidera fare riferimento tramite un solo nome, ad esempio un set di oggetti che sono correlati tramite l'ereditarietà, è possibile usare set di selezione. Quando si definiscono le visualizzazioni, è possibile specificare il set di oggetti utilizzando il nome della selezione set anziché elencare tutti gli oggetti all'interno di ogni visualizzazione.

Set di selezione comune vengono specificati in base al nome quando si definisce le viste del file di formattazione. In questi casi, il `SelectionSetName` elemento figlio dell'elemento di `ViewSelectedBy` (elemento) per la visualizzazione specifica del set. Tuttavia, diverse voci di una vista possono anche specificare un set di selezione che viene applicata solo tale voce della visualizzazione. Per altre informazioni sui set di selezione, vedere [definizione imposta di oggetti](./defining-selection-sets.md).

## <a name="example"></a>Esempio

L'esempio seguente mostra un `SelectionSet` elemento che definisce i quattro tipi di .NET.

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

[La definizione di set di selezione](./defining-selection-sets.md)

[Elemento SelectionSet (formato)](./selectionset-element-format.md)

[Elemento SelectionSets (formato)](./selectionsets-element-format.md)

[Elemento di Types (formato)](./types-element-for-selectionset-format.md)

[La scrittura di un File di formattazione di Windows PowerShell](./writing-a-powershell-formatting-file.md)
