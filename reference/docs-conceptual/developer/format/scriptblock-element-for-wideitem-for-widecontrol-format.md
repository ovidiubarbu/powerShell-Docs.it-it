---
title: Elemento ScriptBlock per WideItem per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362030"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>Elemento ScriptBlock per WideItem per WideControl (formato)

Specifica lo script il cui valore viene visualizzato nella visualizzazione estesa.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) elemento WideItem (Format) elemento ScriptBlock per WideItem (Format)

## <a name="syntax"></a>Sintassi

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ScriptBlock`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento WideItem (Format)](./wideitem-element-for-widecontrol-format.md)|Definisce la proprietà o il blocco di script il cui valore viene visualizzato nella visualizzazione estesa.|

## <a name="text-value"></a>Valore di testo

Specificare lo script di cui viene visualizzato il valore.

## <a name="remarks"></a>Osservazioni

Per ulteriori informazioni sui componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).

## <a name="example"></a>Esempio

Questo esempio mostra un elemento `WideItem` che definisce uno script il cui valore viene visualizzato nella vista.

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>Vedere anche

[Elemento WideItem (Format)](./wideitem-element-for-widecontrol-format.md)

[Creazione di una visualizzazione estesa](./creating-a-wide-view.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
