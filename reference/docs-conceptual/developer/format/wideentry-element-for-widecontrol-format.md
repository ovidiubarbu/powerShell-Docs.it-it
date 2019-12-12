---
title: Elemento WideEntry per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367900"
---
# <a name="wideentry-element-for-widecontrol-format"></a>Elemento WideEntry per WideControl (formato)

Fornisce una definizione dell'ampia visualizzazione.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format)

## <a name="syntax"></a>Sintassi

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `WideEntry`. È necessario specificare un singolo elemento `WideItem` figlio.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Elemento facoltativo.<br /><br /> Definisce i tipi .NET che utilizzano questa definizione di voce estesa o la condizione che deve esistere affinché questa definizione venga utilizzata.|
|[Elemento WideItem (Format)](./wideitem-element-for-widecontrol-format.md)|Elemento obbligatorio.<br /><br /> Definisce la proprietà o lo script di cui viene visualizzato il valore.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento WideEntries (Format)](./wideentries-element-for-widecontrol-format.md)|Fornisce le definizioni della visualizzazione estesa.|

## <a name="remarks"></a>Osservazioni

Una visualizzazione estesa è un formato di elenco che consente di visualizzare un singolo valore di proprietà o un valore di script per ogni oggetto. Diversamente da altri tipi di viste, è possibile specificare un solo elemento Item per ogni definizione della vista. Per ulteriori informazioni sugli altri componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un elemento `WideEntry` che definisce un singolo elemento di `WideItem`. L'elemento `WideItem` definisce la proprietà il cui valore viene visualizzato nella visualizzazione.

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

Per un esempio completo di una visualizzazione estesa, vedere [Wide View (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione estesa](./creating-a-wide-view.md)

[Elemento SelectionCondition per WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento SelectionSetName per WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento TypeName per WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Elemento WideEntries (Format)](./wideentries-element-for-widecontrol-format.md)

[Elemento WideItem (Format)](./wideitem-element-for-widecontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
