---
title: Elemento FormatString per ListItem per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363020"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a>Elemento FormatString per ListItem per ListControl (formato)

Specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries per ListControl (Format) elemento ListEntry per ListControl (Format) elemento ListItems per ListControl (Format) Elemento ListItem per ListControl (Format) elemento FormatString per ListItem per ListControl (Format)

## <a name="syntax"></a>Sintassi

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `FormatString`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ListItem (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definisce la proprietà o lo script il cui valore viene visualizzato in una riga della visualizzazione elenco.|

## <a name="text-value"></a>Valore di testo

Specificare il modello usato per formattare i dati. Ad esempio, è possibile usare questo modello per formattare il valore di qualsiasi proprietà di tipo [System. TimeSpan](/dotnet/api/System.TimeSpan): {0: mmm} {0: dd} {0: HH}: {0: mm}.

## <a name="remarks"></a>Osservazioni

Le stringhe di formato possono essere utilizzate durante la creazione di visualizzazioni di tabella, visualizzazioni di elenchi, visualizzazioni estese o visualizzazioni personalizzate. Per ulteriori informazioni sulla formattazione di un valore visualizzato in una visualizzazione, vedere [formattazione dei dati visualizzati](./formatting-displayed-data.md).

Per ulteriori informazioni sull'utilizzo di stringhe di formato nelle visualizzazioni elenco, vedere Creazione di una [visualizzazione elenco](./creating-a-list-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come definire una stringa di formattazione per il valore della proprietà `StartTime`.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Elemento ListItem (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Scrittura di un file di formattazione e di tipi di Windows PowerShell](./writing-a-powershell-formatting-file.md)
