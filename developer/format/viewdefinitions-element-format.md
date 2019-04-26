---
title: Elemento ViewDefinitions (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083706"
---
# <a name="viewdefinitions-element-format"></a>Elemento ViewDefinitions (formato)

Definisce le viste consente di visualizzare gli oggetti .NET. Tali viste è possono visualizzare le proprietà e valori di script di un oggetto in un formato di tabella, formato di elenco, formato esteso e personalizzato di controllo del formato.

Elemento di configurazione elemento (formato) ViewDefinitions (formato XML)

## <a name="syntax"></a>Sintassi

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `ViewDefinitions` elemento. Non sono previsti limiti al numero di visualizzazioni che possono essere definite in un file di formattazione e possono essere aggiunti in qualsiasi ordine.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento di visualizzazione (formato)](./view-element-format.md)|Definisce una vista che consente di visualizzare uno o più oggetti .NET.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento di configurazione (formato)](./configuration-element-format.md)|Rappresenta l'elemento di livello superiore di un file di formattazione.|

## <a name="remarks"></a>Osservazioni

Per altre informazioni sui componenti dei diversi tipi di visualizzazioni, vedere gli argomenti seguenti:

- [Creazione di una visualizzazione tabella](./creating-a-table-view.md)

- [Creazione di una visualizzazione elenco](./creating-a-list-view.md)

- [Creazione di una visualizzazione più ampia](./creating-a-wide-view.md)

- [Controlli personalizzati](./creating-custom-controls.md)

## <a name="example"></a>Esempio

Questo esempio viene illustrato un `ViewDefinitions` elemento che contiene gli elementi padre per la visualizzazione di una tabella e una visualizzazione elenco.

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

[Elemento di configurazione (formato)](./configuration-element-format.md)

[Elemento di visualizzazione (formato)](./view-element-format.md)

[Creazione di una visualizzazione tabella](./creating-a-table-view.md)

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Creazione di una visualizzazione più ampia](./creating-a-wide-view.md)

[Controlli personalizzati](./creating-custom-controls.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
