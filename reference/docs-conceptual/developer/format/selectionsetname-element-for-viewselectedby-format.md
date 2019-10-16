---
title: Elemento SelectionSetName per ViewSelectedBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368260"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>Elemento SelectionSetName per ViewSelectedBy (formato)

Specifica un set di oggetti .NET visualizzati dalla visualizzazione.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ViewSelectedBy (Format) elemento SelectionSetName per ViewSelectedBy (Format)

## <a name="syntax"></a>Sintassi

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ViewSelectedBy (Format)](./viewselectedby-element-format.md)|Definisce gli oggetti .NET visualizzati dalla visualizzazione.|

## <a name="text-value"></a>Valore di testo

Consente di specificare il nome del set di selezione definito dall'elemento `Name` per il set di selezione.

## <a name="remarks"></a>Osservazioni

È possibile utilizzare i set di selezione quando si dispone di un set di oggetti correlati a cui si desidera fare riferimento utilizzando un solo nome, ad esempio un set di oggetti correlati tramite ereditarietà. Per ulteriori informazioni sulla definizione e il riferimento a set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come specificare un set di selezione per una visualizzazione elenco. Lo stesso schema viene utilizzato per le visualizzazioni tabella, Wide e Custom.

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Vedere anche

[Definizione di set di selezione](./defining-selection-sets.md)

[Elemento ViewSelectedBy (Format)](./viewselectedby-element-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
