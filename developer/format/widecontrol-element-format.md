---
title: Elemento WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859827"
---
# <a name="widecontrol-element-format"></a>Elemento WideControl (formato)

Definisce un'ampia (valore singolo) formato di elenco per la visualizzazione. Questa vista sono riportati un singolo valore di proprietà o valore di uno script per ogni oggetto.

Configurazione (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) WideControl elemento (formato)

## <a name="syntax"></a>Sintassi

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `WideControl` elemento. Non è possibile specificare il `AutoSize` e `ColumnNumber` elementi nello stesso momento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[AutoSize (elemento) per WideControl (formato)](./autosize-element-for-widecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica se la dimensione della colonna e il numero di colonne vengono adattate in base alla dimensione dei dati.|
|[Elemento ColumnNumber per WideControl (formato)](./columnnumber-element-for-widecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di colonne visualizzate in visualizzazione estesa.|
|[Elemento WideEntries (formato)](./wideentries-element-for-widecontrol-format.md)|Elemento obbligatorio.<br /><br /> Fornisce le definizioni di visualizzazione estesa.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento di visualizzazione (formato)](./view-element-format.md)|Definisce una vista che consente di visualizzare uno o più oggetti .NET.|

## <a name="remarks"></a>Osservazioni

Quando si definisce una visualizzazione più ampia, è possibile aggiungere il `AutoSize` elemento o `ColumnNumber` ma non è possibile aggiungere.

Nella maggior parte dei casi, è necessaria per ogni visualizzazione estesa una sola definizione, ma è possibile avere più definizioni, se si desidera utilizzare la stessa vista per visualizzare diversi oggetti .NET. In questi casi, è possibile fornire una definizione separata per ogni oggetto o un set di oggetti.

Per altre informazioni sui componenti di una visualizzazione più ampia, vedere [ampia i componenti di visualizzazione](./creating-a-wide-view.md).

## <a name="example"></a>Esempio

L'esempio seguente mostra una `WideControl` elemento utilizzato per visualizzare una proprietà del [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto.

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

Per un esempio completo di una visualizzazione più ampia, vedere [visualizzazione più ampia (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Vedere anche

[AutoSize (elemento) per WideControl (formato)](./autosize-element-for-widecontrol-format.md)

[Elemento ColumnNumber per WideControl (formato)](./columnnumber-element-for-widecontrol-format.md)

[Elemento di visualizzazione (formato)](./view-element-format.md)

[Elemento WideEntries (formato)](./wideentries-element-for-widecontrol-format.md)

[Visualizzazione più ampia (Basic)](./wide-view-basic.md)

[Creazione di una visualizzazione più ampia](./creating-a-wide-view.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
