---
title: Elemento EntrySelectedBy per WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363330"
---
# <a name="entryselectedby-element-for-wideentry-format"></a>Elemento EntrySelectedBy per WideEntry (formato)

Definisce i tipi .NET che utilizzano questa definizione della visualizzazione estesa o la condizione che deve esistere affinché questa definizione venga utilizzata.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) elemento EntrySelectedBy per WideEntry (Format)

## <a name="syntax"></a>Sintassi

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `EntrySelectedBy`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve esistere per la definizione della vista estesa da usare.|
|[Elemento SelectionSetName per EntrySelectedBy per WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica un set di tipi .NET che utilizzano questa definizione di visualizzazione estesa.|
|[Elemento TypeName per EntrySelectedBy per WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che usa questa definizione di visualizzazione estesa.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)|Fornisce una definizione dell'ampia visualizzazione.|

## <a name="remarks"></a>Osservazioni

Per una definizione di visualizzazione estesa, è necessario specificare almeno un tipo, un set di selezione o una condizione di selezione. Non esiste un limite massimo per il numero di elementi figlio che è possibile usare.

Le condizioni di selezione vengono usate per definire una condizione che deve esistere per la definizione da usare, ad esempio quando un oggetto ha una proprietà specifica o che un valore di proprietà o un valore di script specifico restituisce `true`. Per ulteriori informazioni sulle condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

Per ulteriori informazioni su altri componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).

## <a name="see-also"></a>Vedere anche

[Elemento WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)

[Elemento SelectionCondition per EntrySelectedBy per WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento SelectionSetName per EntrySelectedBy per WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento TypeName per EntrySelectedBy per WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Creazione di una visualizzazione estesa](./creating-a-wide-view.md)

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
