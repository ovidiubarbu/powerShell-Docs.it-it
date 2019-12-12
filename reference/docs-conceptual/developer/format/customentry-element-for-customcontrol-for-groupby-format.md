---
title: Elemento CustomEntry per CustomControl per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364060"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a>Elemento CustomEntry per CustomControl per GroupBy (formato)

Fornisce una definizione del controllo. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format)

## <a name="syntax"></a>Sintassi

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre dell'elemento `CustomEntry`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per CustomEntry per GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata.|
|[Elemento CustomItem per CustomEntry per GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)|Elemento obbligatorio.<br /><br /> Definisce la modalità di visualizzazione dei dati da parte del controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntries per CustomControl per GroupBy (Format)](./customentries-element-for-customcontrol-for-groupby-format.md)|Fornisce le definizioni per il controllo.|

## <a name="remarks"></a>Osservazioni

## <a name="see-also"></a>Vedere anche

[Elemento EntrySelectedBy per CustomEntry per GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Elemento CustomItem per CustomEntry per GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)

[Elemento CustomEntries per CustomControl per GroupBy (Format)](./customentries-element-for-customcontrol-for-groupby-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
