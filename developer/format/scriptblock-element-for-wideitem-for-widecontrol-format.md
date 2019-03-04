---
title: Elemento ScriptBlock per WideItem per WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858027"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>Elemento ScriptBlock per WideItem per WideControl (formato)

Specifica lo script il cui valore viene visualizzato in visualizzazione estesa.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) elemento WideItem (formato) ScriptBlock elemento di configurazione per WideItem (formato)

## <a name="syntax"></a>Sintassi

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `ScriptBlock` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento WideItem (formato)](./wideitem-element-for-widecontrol-format.md)|Definisce il blocco di script o proprietà il cui valore viene visualizzato in visualizzazione estesa.|

## <a name="text-value"></a>Valore di testo

Specificare lo script il cui valore viene visualizzato.

## <a name="remarks"></a>Osservazioni

Per altre informazioni sui componenti di una visualizzazione più ampia, vedere [creazione di una visualizzazione più ampia](./creating-a-wide-view.md).

## <a name="example"></a>Esempio

Questo esempio viene illustrato un `WideItem` elemento che definisce uno script il cui valore viene visualizzato nella vista.

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>Vedere anche

[Elemento WideItem (formato)](./wideitem-element-for-widecontrol-format.md)

[Creazione di una visualizzazione più ampia](./creating-a-wide-view.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
