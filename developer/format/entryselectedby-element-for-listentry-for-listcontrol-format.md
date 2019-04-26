---
title: Elemento EntrySelectedBy per ListEntry per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066193"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>Elemento EntrySelectedBy per ListEntry per ListControl (formato)

Definisce i tipi .NET che usano questa definizione di visualizzazione elenco o la condizione che deve essere presente per questa definizione da usare. Nella maggior parte dei casi è necessaria una sola definizione per una visualizzazione elenco. Tuttavia, è possibile fornire più definizioni per la visualizzazione elenco se si desidera utilizzare la stessa visualizzazione elenco per visualizzare dati diversi per oggetti diversi.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) ListEntries elemento di configurazione per elemento dell'oggetto ListControl (formato) ListEntry ListEntry per elemento EntrySelectedBy ListControl (formato) per ListEntry per ListControl (formato)

## <a name="syntax"></a>Sintassi

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `EntrySelectedBy` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per ListControl (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve essere presente per questa definizione della vista elenco da utilizzare.|
|[Elemento SelectionSetName per EntrySelectedBy per ListControl (formato)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica un set di tipi .NET che usano questa definizione della vista elenco.|
|[Elemento TypeName per EntrySelectedBy per ListControl (formato)](./typename-element-for-entryselectedby-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che usa questa definizione della vista elenco.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ListEntry per ListControl (formato)](./listentry-element-for-listcontrol-format.md)|Definisce come vengono visualizzate le righe dell'elenco.|

## <a name="remarks"></a>Osservazioni

È necessario specificare almeno un tipo, il set di selezione o condizione di selezione per una definizione della vista elenco. Non è definito alcun limite massimo al numero di elementi figlio che è possibile usare.

Condizioni di selezione vengono usate per definire una condizione che deve essere presente per la definizione da usare, ad esempio quando un oggetto dispone di una proprietà specifica o che restituisce un valore della proprietà specifica o uno script `true`. Per altre informazioni sulle condizioni di selezione, vedere [che definisce le condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md).

Per altre informazioni sui componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come definire gli oggetti per una visualizzazione elenco utilizzando il nome del tipo .NET.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a>Vedere anche

[Elemento ListEntry per ListControl (formato)](./listentry-element-for-listcontrol-format.md)

[Elemento SelectionCondition per EntrySelectedBy per ListControl (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Elemento SelectionSetName per EntrySelectedBy per ListControl (formato)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Elemento TypeName per EntrySelectedBy per ListControl (formato)](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[La definizione delle condizioni per quando i dati vengono visualizzati](./defining-conditions-for-displaying-data.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
