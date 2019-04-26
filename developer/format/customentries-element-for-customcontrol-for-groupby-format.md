---
title: Elemento CustomEntries per CustomControl per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066541"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>Elemento CustomEntries per CustomControl per GroupBy (formato)

Fornisce le definizioni per il controllo. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per la visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per GroupBy (formato)

## <a name="syntax"></a>Sintassi

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi, elementi figlio e gli elementi padre del `CustomEntries` elemento. Non è definito alcun limite massimo al numero di elementi figlio che possono essere specificati.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntry per CustomControl per GroupBy (formato)](./customentry-element-for-customcontrol-for-groupby-format.md)|Elemento obbligatorio.<br /><br /> Fornisce una definizione del controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomControl per GroupBy (formato)](./customcontrol-element-for-groupby-format.md)|Definisce il controllo personalizzato che consente di visualizzare il nuovo gruppo.|

## <a name="remarks"></a>Osservazioni

Nella maggior parte dei casi, un controllo ha una sola definizione, di cui è specificata in un singolo `CustomEntry` elemento. Tuttavia, è possibile fornire più definizioni, se si desidera utilizzare lo stesso controllo per visualizzare gruppi diversi. In questi casi, è possibile definire un `CustomEntry` (elemento) per un gruppo.

## <a name="see-also"></a>Vedere anche

[Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Elemento CustomControl per GroupBy (formato)](./customcontrol-element-for-groupby-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
