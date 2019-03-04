---
title: Elemento WideEntry per WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856527"
---
# <a name="wideentry-element-for-widecontrol-format"></a>Elemento WideEntry per WideControl (formato)

Fornisce una definizione della vista wide.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) WideEntry elemento di configurazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `WideEntry` elemento. È necessario specificare un singolo `WideItem` elemento figlio.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md)|Elemento facoltativo.<br /><br /> Definisce i tipi .NET che usano questa definizione voce ampia o la condizione che deve essere presente per questa definizione da usare.|
|[Elemento WideItem (formato)](./wideitem-element-for-widecontrol-format.md)|Elemento obbligatorio.<br /><br /> Definisce le proprietà il cui valore viene visualizzato lo script.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento WideEntries (formato)](./wideentries-element-for-widecontrol-format.md)|Fornisce le definizioni di visualizzazione estesa.|

## <a name="remarks"></a>Osservazioni

Una visualizzazione più ampia è un formato di elenco che viene visualizzato un singolo valore di proprietà o script per ogni oggetto. A differenza di altri tipi di visualizzazioni, è possibile specificare un solo elemento per ogni definizione della vista. Per altre informazioni su altri componenti di una visualizzazione più ampia, vedere [creazione di una visualizzazione più ampia](./creating-a-wide-view.md).

## <a name="example"></a>Esempio

L'esempio seguente mostra una `WideEntry` che definisce un singolo elemento `WideItem` elemento. Il `WideItem` elemento definisce le proprietà il cui valore viene visualizzato nella vista.

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

Per un esempio completo di una visualizzazione più ampia, vedere [visualizzazione più ampia (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione più ampia](./creating-a-wide-view.md)

[Elemento SelectionCondition per WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento SelectionSetName per WideEntry (formato)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento TypeName per WideEntry (formato)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Elemento WideEntries (formato)](./wideentries-element-for-widecontrol-format.md)

[Elemento WideItem (formato)](./wideitem-element-for-widecontrol-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
