---
title: Elemento TypeName per EntrySelectedBy per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361630"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a>Elemento TypeName per EntrySelectedBy per TableControl (formato)

Specifica un tipo .NET che usa questa voce della visualizzazione tabella. Non esiste alcun limite al numero di tipi che è possibile specificare per una voce di tabella.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) elemento EntrySelectedBy (Format) elemento TypeName per EntrySelectedBy per TableRowEntry (Format)

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
|[Elemento EntrySelectedBy (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Definisce i tipi .NET che utilizzano questa voce o la condizione che deve esistere affinché questa voce venga utilizzata.|

## <a name="text-value"></a>Valore testo

Specificare il nome del tipo .NET.

## <a name="remarks"></a>Osservazioni

Per ogni voce di elenco è necessario definire almeno un nome di tipo, un set di selezione o una condizione di selezione.

Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una vista tabella](./creating-a-table-view.md)

[Elemento EntrySelectedBy (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
