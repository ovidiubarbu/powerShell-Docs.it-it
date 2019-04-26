---
title: Elemento SelectionSetName per EntrySelectedBy per WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064029"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a>Elemento SelectionSetName per EntrySelectedBy per WideControl (formato)

Specifica un set di oggetti .NET per la definizione. La definizione viene utilizzata ogni volta che viene visualizzato uno di questi oggetti.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento di configurazione per elemento SelectionSetName WideEntry (formato) per EntrySelectedBy per WideEntry (formato)

## <a name="syntax"></a>Sintassi

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `SelectionSetName` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md)|Definisce i tipi .NET che usano questa voce ampia o la condizione che deve essere presente per questa voce da usare.|

## <a name="text-value"></a>Valore di testo

Specificare il nome del set di selezione.

## <a name="remarks"></a>Osservazioni

Ogni definizione deve specificare un nome del tipo, il set di selezione o condizione di selezione.

Set di selezione vengono usati quando si desidera definire un gruppo di oggetti utilizzati in più viste. Ad esempio, è possibile creare una visualizzazione tabella e una visualizzazione elenco per lo stesso set di oggetti. Per altre informazioni sulla definizione di set di selezione, vedere [definizione imposta di oggetti per una visualizzazione](./defining-selection-sets.md).

Per altre informazioni sugli altri componenti di una visualizzazione più ampia, vedere [creazione di una visualizzazione più ampia](./creating-a-wide-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione più ampia](./creating-a-wide-view.md)

[La definizione di set di selezione](./defining-selection-sets.md)

[Elemento EntrySelectedBy per WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
