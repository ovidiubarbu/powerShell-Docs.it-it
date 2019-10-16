---
title: Elemento WideItem per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361400"
---
# <a name="wideitem-element-for-widecontrol-format"></a>Elemento WideItem per WideControl (formato)

Definisce la proprietà o lo script di cui viene visualizzato il valore.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) elemento WideItem (Format)

## <a name="syntax"></a>Sintassi

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `WideItem`. L'elemento `FormatString` è facoltativo. Tuttavia, è necessario specificare un elemento `PropertyName` o `ScriptBlock`, ma non è possibile specificare entrambi.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento FormatString per WideItem per WideControl (Format)](./formatstring-element-for-wideitem-for-widecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica un modello di formato che definisce come viene visualizzato il valore della proprietà o dello script nella visualizzazione.|
|[Elemento PropertyName per WideItem (Format)](./propertyname-element-for-wideitem-for-widecontrol-format.md)|Specifica la proprietà dell'oggetto il cui valore viene visualizzato nella visualizzazione estesa.|
|[Elemento ScriptBlock per WideItem (Format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|Specifica lo script il cui valore viene visualizzato nella visualizzazione estesa.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)|Fornisce una definizione dell'ampia visualizzazione.|

## <a name="remarks"></a>Osservazioni

Per ulteriori informazioni sui componenti di una visualizzazione estesa, vedere [visualizzazione estesa](./creating-a-wide-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un elemento `WideEntry` che definisce un singolo elemento `WideItem`. L'elemento `WideItem` definisce la proprietà o lo script il cui valore viene visualizzato nella visualizzazione.

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

Per un esempio completo di una visualizzazione estesa, vedere [Wide View (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Vedere anche

[Elemento FormatString per WideItem per WideControl (Format)](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[Elemento PropertyName per WideItem (Format)](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[Elemento ScriptBlock per WideItem (Format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[Elemento WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
