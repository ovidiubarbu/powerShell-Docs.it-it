---
title: Elemento CustomEntry per CustomControl per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860367"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a>Elemento CustomEntry per CustomControl per GroupBy (formato)

Fornisce una definizione del controllo. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomEntry GroupBy (formato) CustomControl per GroupBy (formato)

## <a name="syntax"></a>Sintassi

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi, elementi figlio e gli elementi padre del `CustomEntry` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per CustomEntry per GroupBy (formato)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Definisce i tipi .NET che usano questa definizione di controllo o la condizione che deve essere presente per questa definizione da usare.|
|[Elemento CustomItem per CustomEntry per GroupBy (formato)](./customitem-element-for-customentry-for-groupby-format.md)|Elemento obbligatorio.<br /><br /> Definisce come il controllo Visualizza i dati.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntries per CustomControl per GroupBy (formato)](./customentries-element-for-customcontrol-for-groupby-format.md)|Fornisce le definizioni per il controllo.|

## <a name="remarks"></a>Osservazioni

## <a name="see-also"></a>Vedere anche

[Elemento EntrySelectedBy per CustomEntry per GroupBy (formato)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Elemento CustomItem per CustomEntry per GroupBy (formato)](./customitem-element-for-customentry-for-groupby-format.md)

[Elemento CustomEntries per CustomControl per GroupBy (formato)](./customentries-element-for-customcontrol-for-groupby-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
