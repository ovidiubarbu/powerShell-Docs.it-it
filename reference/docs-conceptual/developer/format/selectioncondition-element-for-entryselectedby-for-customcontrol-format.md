---
title: Elemento SelectionCondition per EntrySelectedBy per CustomControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368440"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a>Elemento SelectionCondition per EntrySelectedBy per CustomControl (formato)

Definisce una condizione che deve esistere per la definizione di un controllo da utilizzare. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl per View (Format) elemento CustomEntries per CustomControl per la visualizzazione (Format) CustomEntry elemento per CustomEntries per CustomControl per la visualizzazione ( Format) elemento CustomItem per CustomEntry per CustomControl per la visualizzazione (Format) EntrySelectedBy elemento per CustomEntry per CustomControl per la visualizzazione (Format) SelectionCondition elemento per EntrySelectedBy per CustomControl per View (Format)

## <a name="syntax"></a>Sintassi

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionCondition`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento PropertyName per SelectionCondition per CustomControl per View (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica una proprietà .NET che attiva la condizione.|
|[Elemento ScriptBlock per SelectionCondition per CustomControl per View (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script che attiva la condizione.|
|[Elemento SelectionSetName per SelectionCondition per il controllo personalizzato per la visualizzazione (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica il set di tipi .NET che attiva la condizione.|
|[Elemento TypeName per SelectionCondition per CustomControl per View (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che attiva la condizione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per CustomEntry per CustomControl per View (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata.|

## <a name="remarks"></a>Osservazioni

Quando si definisce una condizione di selezione, si applicano i requisiti seguenti:

- La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificarli entrambi.

- La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi.

Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[Elemento PropertyName per SelectionCondition per CustomControl per View (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento ScriptBlock per SelectionCondition per CustomControl per View (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento SelectionSetName per SelectionCondition per il controllo personalizzato per la visualizzazione (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento TypeName per SelectionCondition per CustomControl per View (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento EntrySelectedBy per CustomEntry per CustomControl per View (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
