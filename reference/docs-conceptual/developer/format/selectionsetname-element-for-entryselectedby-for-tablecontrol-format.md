---
title: Elemento SelectionSetName per EntrySelectedBy per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368320"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a>Elemento SelectionSetName per EntrySelectedBy per TableControl (formato)

Specifica un set di tipi .NET che utilizzano questa voce della visualizzazione tabella. Non esiste alcun limite al numero di set di selezione che è possibile specificare per una voce.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) elemento EntrySelectedBy (Format) SelectionSetName elemento per EntrySelectedBy per TableRowEntry (Format)

## <a name="syntax"></a>Sintassi

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Definisce i tipi .NET che utilizzano questa voce o la condizione che deve esistere affinché questa voce venga utilizzata.|

## <a name="text-value"></a>Valore di testo

Consente di specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

I set di selezione vengono in genere utilizzati quando si desidera definire un gruppo di oggetti utilizzati in più viste. Ad esempio, potrebbe essere necessario creare una visualizzazione tabella e una visualizzazione elenco per lo stesso set di oggetti. Per ulteriori informazioni sulla definizione di set di selezione, vedere [definizione di set di oggetti per una vista](./defining-selection-sets.md).

Se si specifica un set di selezione per una voce, non è possibile specificare un nome di tipo. Per ulteriori informazioni su come specificare un tipo .NET, vedere [elemento TypeName per EntrySelectedBy per TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).

Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).

## <a name="see-also"></a>Vedere anche

[Elemento EntrySelectedBy (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Definizione di set di oggetti per una vista](./defining-selection-sets.md)

[Creazione di una vista tabella](./creating-a-table-view.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
