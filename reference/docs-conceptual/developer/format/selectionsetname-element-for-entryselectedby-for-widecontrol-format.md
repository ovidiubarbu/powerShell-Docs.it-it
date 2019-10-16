---
title: Elemento SelectionSetName per EntrySelectedBy per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361980"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a>Elemento SelectionSetName per EntrySelectedBy per WideControl (formato)

Specifica un set di oggetti .NET per la definizione. La definizione viene utilizzata ogni volta che viene visualizzato uno di questi oggetti.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) elemento EntrySelectedBy per WideEntry (Format) SelectionSetName elemento per EntrySelectedBy per WideEntry (Format)

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
|[Elemento EntrySelectedBy per WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Definisce i tipi .NET che utilizzano questa voce estesa o la condizione che deve esistere affinché questa voce venga utilizzata.|

## <a name="text-value"></a>Valore di testo

Consente di specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

Ogni definizione deve specificare un nome di tipo, un set di selezione o una condizione di selezione.

I set di selezione vengono in genere utilizzati quando si desidera definire un gruppo di oggetti utilizzati in più viste. Ad esempio, potrebbe essere necessario creare una visualizzazione tabella e una visualizzazione elenco per lo stesso set di oggetti. Per ulteriori informazioni sulla definizione di set di selezione, vedere [definizione di set di oggetti per una vista](./defining-selection-sets.md).

Per ulteriori informazioni su altri componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione estesa](./creating-a-wide-view.md)

[Definizione di set di selezione](./defining-selection-sets.md)

[Elemento EntrySelectedBy per WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
