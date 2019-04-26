---
title: Elemento TypeName per EntrySelectedBy per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 0f7216d4dcc0380bceb47ea7c15b3d4a7e5ceeb2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084029"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a>Elemento TypeName per EntrySelectedBy per ListControl (formato)

Specifica un tipo .NET che usa questa voce della visualizzazione elenco. Non sono previsti limiti al numero di tipi che possono essere specificati per una voce dell'elenco.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) elemento ListEntries (formato) elemento ListEntry (formato) EntrySelectedBy elemento di configurazione per elemento TypeName ListEntry (formato) per EntrySelectedBy per ListControl (formato)

## <a name="syntax"></a>Sintassi

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `TypeName` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per ListEntry (formato)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Definisce i tipi .NET che usano questa voce di elenco o la condizione che deve essere presente per questa voce da usare.|

## <a name="text-value"></a>Valore di testo

Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Osservazioni

Ogni voce dell'elenco deve avere almeno un nome di tipo, il set di selezione o condizione di selezione definiti.

Per altre informazioni sul modo in cui questo elemento viene usato in una visualizzazione elenco, vedere [visualizzazione elenco](./creating-a-list-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come specificare un insieme di una voce di una visualizzazione elenco di selezione.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Elemento EntrySelectedBy per ListEntry (formato)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[Elemento SelectionSetName per EntrySelectedBy per ListEntry (formato)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
