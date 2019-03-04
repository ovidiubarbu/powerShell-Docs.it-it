---
title: Elemento SelectionSetName per ViewSelectedBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858337"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>Elemento SelectionSetName per ViewSelectedBy (formato)

Specifica un set di oggetti .NET che vengono visualizzati nella visualizzazione.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento ViewSelectedBy (formato) SelectionSetName elemento di configurazione per ViewSelectedBy (formato)

## <a name="syntax"></a>Sintassi

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSetName` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ViewSelectedBy (formato)](./viewselectedby-element-format.md)|Definisce gli oggetti .NET che vengono visualizzati nella visualizzazione.|

## <a name="text-value"></a>Valore di testo

Specificare il nome del set di selezione definito dal `Name` (elemento) per il set di selezione.

## <a name="remarks"></a>Osservazioni

Quando si dispone di un set di oggetti correlati che si desidera fare riferimento tramite un solo nome, ad esempio un set di oggetti che sono correlati tramite l'ereditarietà, è possibile usare set di selezione. Per altre informazioni sulla definizione e riferimento a set di selezione, vedere [definizione imposta di oggetti](./defining-selection-sets.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come specificare un insieme per una visualizzazione elenco di selezione. Lo stesso schema viene utilizzato per le visualizzazioni di tabella, ampia e personalizzati.

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

[La definizione di set di selezione](./defining-selection-sets.md)

[Elemento ViewSelectedBy (formato)](./viewselectedby-element-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
