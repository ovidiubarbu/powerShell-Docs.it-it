---
title: Elemento TypeName per SelectionCondition per EntrySelectedBy per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368060"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a>Elemento TypeName per SelectionCondition per EntrySelectedBy per WideControl (formato)

Specifica un tipo .NET che attiva la condizione. Quando questo tipo è presente, viene usata la definizione.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) elemento EntrySelectedBy per WideEntry (Format) SelectionCondition elemento per EntrySelectedBy per WideEntry (Format) TypeName elemento per SelectionCondition per EntrySelectedBy per WideEntry (Format)

## <a name="syntax"></a>Sintassi

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TypeName`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Definisce la condizione che deve esistere affinché questa voce di tipo Wide venga utilizzata.|

## <a name="text-value"></a>Valore testo

Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Osservazioni

La condizione di selezione può specificare un tipo .NET o un set di selezione, ma non è possibile specificarli entrambi. Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

Per ulteriori informazioni su altri componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione estesa](./creating-a-wide-view.md)

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Elemento SelectionCondition per EntrySelectedBy per WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
