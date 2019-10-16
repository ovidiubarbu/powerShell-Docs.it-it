---
title: Elemento CustomEntry per CustomEntries per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364020"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a>Elemento CustomEntry per CustomEntries per CustomControl per View (formato)

Fornisce una definizione della visualizzazione controlli personalizzata.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per l'elemento View (Format) CustomEntry per CustomEntries per View (Format)

## <a name="syntax"></a>Sintassi

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomEntry`. È necessario specificare gli elementi visualizzati dalla definizione.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per CustomEntry per View (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Definisce i tipi .NET che utilizzano la definizione della visualizzazione controlli personalizzata o la condizione che deve esistere affinché questa definizione venga utilizzata.|
|[Elemento CustomItem per CustomEntry per View (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Definisce un controllo per la definizione del controllo personalizzato.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntries per CustomControl per View (Format)](./customentries-element-for-customcontrol-for-view-format.md)|Fornisce le definizioni della visualizzazione controlli personalizzata. La visualizzazione controlli personalizzata deve specificare una o più definizioni.|

## <a name="remarks"></a>Osservazioni

Nella maggior parte dei casi, è necessaria una sola definizione per ogni visualizzazione controlli personalizzata, ma è possibile avere più definizioni se si vuole usare la stessa vista per visualizzare oggetti .NET diversi. In questi casi, è possibile specificare una definizione separata per ogni oggetto o set di oggetti.

## <a name="see-also"></a>Vedere anche

[Elemento CustomControl per View (Format)](./customcontrol-element-for-view-format.md)

[Elemento CustomItem per CustomEntry per View (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Elemento EntrySelectedBy per CustomEntry per View (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
