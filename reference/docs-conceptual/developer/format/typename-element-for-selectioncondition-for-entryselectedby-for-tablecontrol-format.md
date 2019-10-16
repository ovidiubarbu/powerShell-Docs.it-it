---
title: Elemento TypeName per SelectionCondition per EntrySelectedBy per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361470"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>Elemento TypeName per SelectionCondition per EntrySelectedBy per TableControl (formato)

Specifica un tipo .NET che attiva la condizione. Quando questo tipo è presente, la condizione viene soddisfatta e viene utilizzata la riga della tabella.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) elemento EntrySelectedBy per TableRowEntry (Format) Elemento SelectionCondition per EntrySelectedBy per l'elemento TableRowEntry (Format) TypeName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)

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
|[Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Definisce la condizione che deve esistere per la riga della tabella da utilizzare.|

## <a name="text-value"></a>Valore di testo

Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Osservazioni

La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi. Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per l'utilizzo di una voce o di un elemento della visualizzazione](./defining-conditions-for-displaying-data.md).

Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una vista tabella](./creating-a-table-view.md)

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Elemento SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Elemento SelectionSetName per SelectionCondition per EntrySelectedBy per TableRowEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
