---
title: Elemento EntrySelectedBy per CustomEntry per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368780"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>Elemento EntrySelectedBy per CustomEntry per CustomControl per View (formato)

Definisce i tipi .NET che utilizzano questa voce personalizzata o la condizione che deve esistere affinché questa voce venga utilizzata.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per l'elemento View (Format) CustomEntry per CustomEntries per View (Format) EntrySelectedBy Elemento per CustomEntry per View (Format)

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
|[Elemento SelectionCondition per EntrySelectedBy per CustomEntry (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve esistere affinché questa definizione venga utilizzata.|
|[Elemento SelectionSetName per EntrySelectedBy per CustomEntry (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica un set di tipi .NET che utilizzano questa definizione della visualizzazione controlli.|
|[Elemento TypeName per EntrySelectedBy per CustomEntry (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che usa questa definizione della visualizzazione controlli.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntry per CustomEntries per View (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Definisce i controlli utilizzati da oggetti .NET specifici.|

## <a name="remarks"></a>Osservazioni

È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per una voce. Non esiste un limite massimo per il numero di elementi figlio che è possibile usare.

Le condizioni di selezione vengono usate per definire una condizione che deve esistere per la voce da usare, ad esempio quando un oggetto ha una proprietà specifica o quando uno script o un valore di proprietà specifico restituisce `true`. Per ulteriori informazioni sulle condizioni di selezione, vedere [definizione di condizioni per l'utilizzo di una voce o di un elemento della visualizzazione](./defining-conditions-for-displaying-data.md).

Per ulteriori informazioni sui componenti di una visualizzazione controlli personalizzata, vedere [visualizzazione controlli personalizzati](./creating-custom-controls.md).

## <a name="see-also"></a>Vedere anche

[Elemento SelectionCondition per EntrySelectedBy per CustomEntry (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Elemento SelectionSetName per EntrySelectedBy per CustomEntry (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[Elemento TypeName per EntrySelectedBy per CustomEntry (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento CustomEntry per CustomEntries per View (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Visualizzazione controlli personalizzati](./creating-custom-controls.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
