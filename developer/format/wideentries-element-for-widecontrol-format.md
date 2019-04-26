---
title: Elemento WideEntries per WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083689"
---
# <a name="wideentries-element-for-widecontrol-format"></a>Elemento WideEntries per WideControl (formato)

Fornisce le definizioni di visualizzazione estesa. La visualizzazione più ampia è necessario specificare una o più definizioni.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) WideEntries elemento di configurazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `WideEntries` elemento. È necessario specificare almeno un elemento figlio.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)|Fornisce una definizione della vista wide.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento WideControl (formato)](./widecontrol-element-format.md)|Definisce un'ampia (valore singolo) formato di elenco per la visualizzazione.|

## <a name="remarks"></a>Osservazioni

Una visualizzazione più ampia è un formato di elenco che viene visualizzato un singolo valore di proprietà o script per ogni oggetto. Per altre informazioni sui componenti di una visualizzazione più ampia, vedere [ampia i componenti di visualizzazione](./creating-a-wide-view.md).

## <a name="example"></a>Esempio

L'esempio seguente mostra una `WideEntries` che definisce un singolo elemento `WideEntry` elemento. Il `WideEntry` elemento contiene un singolo `WideItem` elemento che definisce il valore di proprietà o lo script viene visualizzato nella vista.

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

Per un esempio completo di una visualizzazione più ampia, vedere [visualizzazione più ampia (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione più ampia](./creating-a-wide-view.md)

[Elemento WideControl (formato)](./widecontrol-element-format.md)

[Elemento WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
