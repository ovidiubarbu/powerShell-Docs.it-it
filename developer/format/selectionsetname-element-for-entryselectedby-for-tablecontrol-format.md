---
title: Elemento SelectionSetName per EntrySelectedBy per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063922"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a>Elemento SelectionSetName per EntrySelectedBy per TableControl (formato)

Specifica che un set di .NET tipi l'uso di questa voce della visualizzazione della tabella. Non sono previsti limiti al numero di set di selezione che è possibile specificare per una voce.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) elemento EntrySelectedBy (formato) SelectionSetName elemento di configurazione per EntrySelectedBy per TableRowEntry (formato)

## <a name="syntax"></a>Sintassi

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi, elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy (formato)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Definisce i tipi .NET che usano questa voce o la condizione che deve essere presente per questa voce da usare.|

## <a name="text-value"></a>Valore di testo

Specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

Set di selezione vengono usati quando si desidera definire un gruppo di oggetti utilizzati in più viste. Ad esempio, è possibile creare una visualizzazione tabella e una visualizzazione elenco per lo stesso set di oggetti. Per altre informazioni sulla definizione di set di selezione, vedere [definizione di set di oggetti per una visualizzazione](./defining-selection-sets.md).

Se si specifica una selezione impostato per una voce, è possibile specificare un nome di tipo. Per altre informazioni su come specificare un tipo .NET, vedere [elemento TypeName per EntrySelectedBy per TableRowEntry (formato)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).

Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).

## <a name="see-also"></a>Vedere anche

[Elemento EntrySelectedBy (formato)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[La definizione di set di oggetti per una visualizzazione](./defining-selection-sets.md)

[Creazione di una visualizzazione tabella](./creating-a-table-view.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
