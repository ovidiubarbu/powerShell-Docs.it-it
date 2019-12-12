---
title: Elemento TypeName per SelectionCondition per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361480"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a>Elemento TypeName per SelectionCondition per GroupBy (formato)

Specifica un tipo .NET che attiva la condizione. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per l'elemento EntrySelectedBy di GroupBy (Format) per CustomEntry per l'elemento SelectionCondition di GroupBy (Format) per EntrySelectedBy per la SelectionCondition per l'elemento TypeName (Format) TypeName per per GroupBy (Format)

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
|[Elemento SelectionCondition per EntrySelectedBy per GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Definisce una condizione che deve esistere per la definizione del controllo da utilizzare.|

## <a name="text-value"></a>Valore testo

Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Osservazioni

Quando si specifica questo elemento, non è possibile specificare l'elemento `SelectionSetName`. Per ulteriori informazioni sulla definizione delle condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[Elemento SelectionCondition per EntrySelectedBy per GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
