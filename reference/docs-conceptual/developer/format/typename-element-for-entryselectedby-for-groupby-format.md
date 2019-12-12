---
title: Elemento TypeName per EntrySelectedBy per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361670"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a>Elemento TypeName per EntrySelectedBy per GroupBy (formato)

Specifica un tipo .NET che usa questa definizione del controllo personalizzato. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per l'elemento EntrySelectedBy di GroupBy (Format) per CustomEntry per l'elemento di GroupBy (Format) TypeName per EntrySelectedBy per GroupBy (Format)

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
|[Elemento EntrySelectedBy per CustomEntry per GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Definisce i tipi .NET che utilizzano questa definizione di controllo o la condizione che deve esistere affinché questa definizione venga utilizzata.|

## <a name="text-value"></a>Valore testo

Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Osservazioni

Per ogni definizione di controllo deve essere definito almeno un nome di tipo, un set di selezione o una condizione di selezione.

Per ulteriori informazioni sui componenti di una visualizzazione controlli personalizzata, vedere [creazione di controlli personalizzati](./creating-custom-controls.md).

## <a name="see-also"></a>Vedere anche

[Creazione di controlli personalizzati](./creating-custom-controls.md)

[Elemento EntrySelectedBy per CustomEntry per GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
