---
title: Elemento SelectionSetName per EntrySelectedBy per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362000"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a>Elemento SelectionSetName per EntrySelectedBy per ListControl (formato)

Specifica un set di oggetti .NET per la voce dell'elenco. Non esiste alcun limite al numero di set di selezione che è possibile specificare per una voce.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento EntrySelectedBy per ListEntry (Format) SelectionSetName elemento per EntrySelectedBy per ListEntry (Format)

## <a name="syntax"></a>Sintassi

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionSetName`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Definisce i tipi .NET che utilizzano questa voce di elenco o la condizione che deve esistere affinché questa voce venga utilizzata.|

## <a name="text-value"></a>Valore di testo

Consente di specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

Per ogni voce di elenco è necessario definire almeno un nome di tipo, un set di selezione o una condizione di selezione.

I set di selezione vengono in genere utilizzati quando si desidera definire un gruppo di oggetti utilizzati in più viste. Ad esempio, potrebbe essere necessario creare una visualizzazione tabella e una visualizzazione elenco per lo stesso set di oggetti. Per ulteriori informazioni sulla definizione di set di selezione, vedere [definizione di set di oggetti per una vista](./defining-selection-sets.md).

Per ulteriori informazioni sui componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come specificare un set di selezione per una voce di una visualizzazione elenco.

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Elemento EntrySelectedBy per ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
