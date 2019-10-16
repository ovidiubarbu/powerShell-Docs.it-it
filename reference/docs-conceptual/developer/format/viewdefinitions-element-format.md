---
title: Elemento ViewDefinitions (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361420"
---
# <a name="viewdefinitions-element-format"></a>Elemento ViewDefinitions (formato)

Definisce le visualizzazioni utilizzate per visualizzare gli oggetti .NET. Queste visualizzazioni possono visualizzare le proprietà e i valori di script di un oggetto in formato tabella, formato elenco, formato esteso e formato controllo personalizzato.

Elemento Configuration (Format) ViewDefinitions (format XML)

## <a name="syntax"></a>Sintassi

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ViewDefinitions`. Non esiste alcun limite al numero di visualizzazioni che possono essere definite in un file di formattazione e possono essere aggiunte in qualsiasi ordine.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento View (Format)](./view-element-format.md)|Definisce una vista utilizzata per visualizzare uno o più oggetti .NET.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento Configuration (Format)](./configuration-element-format.md)|Rappresenta l'elemento di primo livello di un file di formattazione.|

## <a name="remarks"></a>Osservazioni

Per ulteriori informazioni sui componenti dei diversi tipi di viste, vedere gli argomenti seguenti:

- [Creazione di una vista tabella](./creating-a-table-view.md)

- [Creazione di una visualizzazione elenco](./creating-a-list-view.md)

- [Creazione di una visualizzazione estesa](./creating-a-wide-view.md)

- [Controlli personalizzati](./creating-custom-controls.md)

## <a name="example"></a>Esempio

In questo esempio viene illustrato un elemento `ViewDefinitions` che contiene gli elementi padre per una visualizzazione tabella e una visualizzazione elenco.

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a>Vedere anche

[Elemento Configuration (Format)](./configuration-element-format.md)

[Elemento View (Format)](./view-element-format.md)

[Creazione di una vista tabella](./creating-a-table-view.md)

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Creazione di una visualizzazione estesa](./creating-a-wide-view.md)

[Controlli personalizzati](./creating-custom-controls.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
