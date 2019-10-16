---
title: Elemento WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367990"
---
# <a name="widecontrol-element-format"></a>Elemento WideControl (formato)

Definisce un formato di elenco Wide (valore singolo) per la visualizzazione. Questa vista consente di visualizzare un singolo valore di proprietà o un valore di script per ogni oggetto.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format)

## <a name="syntax"></a>Sintassi

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `WideControl`. Non è possibile specificare contemporaneamente gli elementi `AutoSize` e `ColumnNumber`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento AutoSize per WideControl (Format)](./autosize-element-for-widecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica se le dimensioni della colonna e il numero di colonne vengono regolate in base alle dimensioni dei dati.|
|[Elemento ColumnNumber per WideControl (Format)](./columnnumber-element-for-widecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica il numero di colonne visualizzate nella visualizzazione estesa.|
|[Elemento WideEntries (Format)](./wideentries-element-for-widecontrol-format.md)|Elemento obbligatorio.<br /><br /> Fornisce le definizioni della visualizzazione estesa.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento View (Format)](./view-element-format.md)|Definisce una vista utilizzata per visualizzare uno o più oggetti .NET.|

## <a name="remarks"></a>Osservazioni

Quando si definisce una visualizzazione estesa, è possibile aggiungere l'elemento `AutoSize` o il `ColumnNumber`, ma non è possibile aggiungerne entrambi.

Nella maggior parte dei casi, è necessaria una sola definizione per ogni visualizzazione estesa, ma è possibile avere più definizioni se si vuole usare la stessa visualizzazione per visualizzare oggetti .NET diversi. In questi casi, è possibile specificare una definizione separata per ogni oggetto o set di oggetti.

Per ulteriori informazioni sui componenti di una visualizzazione estesa, vedere [componenti di visualizzazione ampia](./creating-a-wide-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un elemento `WideControl` utilizzato per visualizzare una proprietà dell'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

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

Per un esempio completo di una visualizzazione estesa, vedere [Wide View (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Vedere anche

[Elemento AutoSize per WideControl (Format)](./autosize-element-for-widecontrol-format.md)

[Elemento ColumnNumber per WideControl (Format)](./columnnumber-element-for-widecontrol-format.md)

[Elemento View (Format)](./view-element-format.md)

[Elemento WideEntries (Format)](./wideentries-element-for-widecontrol-format.md)

[Visualizzazione estesa (di base)](./wide-view-basic.md)

[Creazione di una visualizzazione estesa](./creating-a-wide-view.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
