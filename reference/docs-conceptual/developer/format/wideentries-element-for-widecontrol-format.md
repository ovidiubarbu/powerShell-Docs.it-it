---
title: Elemento WideEntries per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361430"
---
# <a name="wideentries-element-for-widecontrol-format"></a>Elemento WideEntries per WideControl (formato)

Fornisce le definizioni della visualizzazione estesa. La visualizzazione estesa deve specificare una o più definizioni.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format)

## <a name="syntax"></a>Sintassi

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `WideEntries`. È necessario specificare almeno un elemento figlio.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)|Fornisce una definizione dell'ampia visualizzazione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento WideControl (Format)](./widecontrol-element-format.md)|Definisce un formato di elenco Wide (valore singolo) per la visualizzazione.|

## <a name="remarks"></a>Osservazioni

Una visualizzazione estesa è un formato di elenco che consente di visualizzare un singolo valore di proprietà o un valore di script per ogni oggetto. Per ulteriori informazioni sui componenti di una visualizzazione estesa, vedere [componenti di visualizzazione ampia](./creating-a-wide-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un elemento `WideEntries` che definisce un singolo elemento di `WideEntry`. L'elemento `WideEntry` contiene un singolo elemento `WideItem` che definisce la proprietà o il valore dello script visualizzato nella visualizzazione.

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

Per un esempio completo di una visualizzazione estesa, vedere [Wide View (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione estesa](./creating-a-wide-view.md)

[Elemento WideControl (Format)](./widecontrol-element-format.md)

[Elemento WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
