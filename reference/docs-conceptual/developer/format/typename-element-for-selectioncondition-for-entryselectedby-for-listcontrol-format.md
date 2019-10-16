---
title: Elemento TypeName per SelectionCondition per EntrySelectedBy per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361560"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>Elemento TypeName per SelectionCondition per EntrySelectedBy per ListControl (formato)

Specifica un tipo .NET che attiva la condizione. Quando questo tipo è presente, viene usata la voce dell'elenco.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries per ListControl (Format) elemento ListEntry per ListEntries per l'elemento ListControl (Format) EntrySelectedBy per ListEntry per ListControl (Format) elemento SelectionCondition per EntrySelectedBy per il parametro ListControl (Format) TypeName per SelectionCondition per EntrySelectedBy per ListControl (Format)

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
|[Elemento SelectionCondition per EntrySelectedBy per ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Definisce la condizione che deve esistere affinché questa voce di elenco venga utilizzata.|

## <a name="text-value"></a>Valore di testo

Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Osservazioni

La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi. Per ulteriori informazioni sull'utilizzo delle condizioni di selezione, vedere [definizione di condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

Per ulteriori informazioni su altri componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Elemento SelectionCondition per EntrySelectedBy per ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
