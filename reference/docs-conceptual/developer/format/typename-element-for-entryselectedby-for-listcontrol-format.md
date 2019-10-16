---
title: Elemento TypeName per EntrySelectedBy per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 0f7216d4dcc0380bceb47ea7c15b3d4a7e5ceeb2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361660"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a>Elemento TypeName per EntrySelectedBy per ListControl (formato)

Specifica un tipo .NET che usa questa voce della visualizzazione elenco. Non esiste alcun limite al numero di tipi che è possibile specificare per una voce di elenco.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) EntrySelectedBy elemento per ListEntry (Format) TypeName elemento per EntrySelectedBy per ListControl (formato)

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
|[Elemento EntrySelectedBy per ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Definisce i tipi .NET che utilizzano questa voce di elenco o la condizione che deve esistere affinché questa voce venga utilizzata.|

## <a name="text-value"></a>Valore di testo

Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Osservazioni

Per ogni voce di elenco è necessario definire almeno un nome di tipo, un set di selezione o una condizione di selezione.

Per ulteriori informazioni sull'utilizzo di questo elemento in una visualizzazione elenco, vedere [visualizzazione elenco](./creating-a-list-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come specificare un set di selezione per una voce di una visualizzazione elenco.

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

[Elemento EntrySelectedBy per ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[Elemento SelectionSetName per EntrySelectedBy per ListEntry (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
