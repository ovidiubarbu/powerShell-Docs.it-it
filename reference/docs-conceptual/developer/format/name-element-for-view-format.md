---
title: Elemento Name per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362640"
---
# <a name="name-element-for-view-format"></a>Elemento Name per View (formato)

Specifica il nome utilizzato per identificare la visualizzazione.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) elemento Name (Format)

## <a name="syntax"></a>Sintassi

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Name`. Per ogni visualizzazione è consentito un solo elemento `Name`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento View (Format)](./view-element-format.md)|Definisce una vista utilizzata per visualizzare i membri di uno o più oggetti .NET.|

## <a name="text-value"></a>Valore di testo

Specificare un nome descrittivo univoco per la visualizzazione. Questo nome può includere un riferimento al tipo di visualizzazione, ad esempio una vista tabella o una visualizzazione elenco, che l'oggetto o il set di oggetti utilizza la vista, il comando che restituisce gli oggetti o una combinazione di questi.

## <a name="remarks"></a>Osservazioni

Per ulteriori informazioni sui diversi tipi di viste, vedere gli argomenti seguenti: [vista tabella](./creating-a-table-view.md), [visualizzazione elenco](./creating-a-list-view.md), [visualizzazione estesa](./creating-a-wide-view.md)e [visualizzazione personalizzata](./creating-custom-controls.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un elemento `View` che definisce una vista tabella per l'oggetto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) . Il nome della vista è "Service".

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Creazione di una vista tabella](./creating-a-table-view.md)

[Creazione di una visualizzazione estesa](./creating-a-wide-view.md)

[Creazione di controlli personalizzati](./creating-custom-controls.md)

[Elemento View (Format)](./view-element-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
