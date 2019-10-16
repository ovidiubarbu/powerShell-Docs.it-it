---
title: Elemento TypeName per EntrySelectedBy per CustomEntry per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368070"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a>Elemento TypeName per EntrySelectedBy per CustomEntry per View (formato)

Specifica un tipo .NET che usa questa definizione della visualizzazione del controllo personalizzato. Non esiste alcun limite al numero di tipi che è possibile specificare per una definizione.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per l'elemento View (Format) CustomEntry per CustomEntries per View (Format) EntrySelectedBy Elemento per CustomEntry per la visualizzazione (formato) elemento TypeName per EntrySelectedBy per CustomEntry per View (Format)

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
|[Elemento EntrySelectedBy per CustomEntry per View (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Definisce i tipi .NET che utilizzano questa definizione della vista di controllo personalizzata o la condizione che deve esistere affinché questa definizione venga utilizzata.|

## <a name="text-value"></a>Valore di testo

Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Osservazioni

Ogni definizione di visualizzazione controlli personalizzata deve avere almeno un nome di tipo, un set di selezione o una condizione di selezione definita.

Per ulteriori informazioni sui componenti di una visualizzazione controlli personalizzata, vedere [creazione di controlli personalizzati](./creating-custom-controls.md).

## <a name="see-also"></a>Vedere anche

[Creazione di controlli personalizzati](./creating-custom-controls.md)

[Elemento EntrySelectedBy per CustomEntry per View (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
