---
title: Elemento WideItem per WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862627"
---
# <a name="wideitem-element-for-widecontrol-format"></a>Elemento WideItem per WideControl (formato)

Definisce le proprietà il cui valore viene visualizzato lo script.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) WideItem elemento di configurazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `WideItem` elemento. L'elemento `FormatString` è facoltativo. Tuttavia, è necessario specificare una `PropertyName` o `ScriptBlock` elemento, ma è possibile specificare entrambi.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento FormatString per WideItem per WideControl (formato)](./formatstring-element-for-wideitem-for-widecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica un modello di formato che definisce come viene visualizzato il valore di proprietà o lo script nella visualizzazione.|
|[Elemento PropertyName per WideItem (formato)](./propertyname-element-for-wideitem-for-widecontrol-format.md)|Specifica la proprietà dell'oggetto il cui valore viene visualizzato in visualizzazione estesa.|
|[Elemento ScriptBlock per WideItem (formato)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|Specifica lo script il cui valore viene visualizzato in visualizzazione estesa.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)|Fornisce una definizione della vista wide.|

## <a name="remarks"></a>Osservazioni

Per altre informazioni sui componenti di una visualizzazione più ampia, vedere [visualizzazione estesa](./creating-a-wide-view.md).

## <a name="example"></a>Esempio

L'esempio seguente mostra una `WideEntry` che definisce un singolo elemento `WideItem` elemento. Il `WideItem` elemento definisce le proprietà il cui valore viene visualizzato nella visualizzazione script.

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

Per un esempio completo di una visualizzazione più ampia, vedere [visualizzazione più ampia (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Vedere anche

[Elemento FormatString per WideItem per WideControl (formato)](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[Elemento PropertyName per WideItem (formato)](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[Elemento ScriptBlock per WideItem (formato)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[Elemento WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
