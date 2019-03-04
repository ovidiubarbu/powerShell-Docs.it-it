---
title: Elemento CustomItem per CustomEntry per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856927"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>Elemento CustomItem per CustomEntry per GroupBy (formato)

Definisce i dati visualizzati dalla visualizzazione del controllo personalizzato e modalità di visualizzazione. Questo elemento viene usato quando si definisce come viene visualizzato un nuovo gruppo di oggetti.

Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per visualizzazione (formato) CustomControl elemento per elemento CustomEntries GroupBy (formato) per CustomControl per elemento CustomItem GroupBy (formato) CustomEntry per GroupBy (formato)

## <a name="syntax"></a>Sintassi

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomItem` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento ExpressionBinding per CustomItem per GroupBy (formato)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Definisce i dati che vengano visualizzati dal controllo.|
|[Elemento frame per CustomItem per GroupBy (formato)](./frame-element-for-customitem-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Definisce i dati visualizzati dalla visualizzazione del controllo personalizzato e modalità di visualizzazione.|
|[Elemento di una nuova riga per CustomItem per GroupBy (formato)](./newline-element-for-customitem-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Aggiunge una riga vuota alla visualizzazione del controllo.|
|[Elemento di testo per CustomItem per GroupBy (formato)](./text-element-for-customitem-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica il testo aggiuntivo per i dati visualizzati dal controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntry per CustomControl per GroupBy (formato)](./customentry-element-for-customcontrol-for-groupby-format.md)|Fornisce una definizione della vista del controllo personalizzato.|

## <a name="remarks"></a>Osservazioni

## <a name="see-also"></a>Vedere anche

[Elemento CustomEntry per CustomControl per GroupBy (formato)](./customentry-element-for-customcontrol-for-groupby-format.md)

[Elemento ExpressionBinding per CustomItem per GroupBy (formato)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Elemento frame per CustomItem per GroupBy (formato)](./frame-element-for-customitem-for-groupby-format.md)

[Elemento di una nuova riga per CustomItem per GroupBy (formato)](./newline-element-for-customitem-for-groupby-format.md)

[Elemento di testo per CustomItem per GroupBy (formato)](./text-element-for-customitem-for-groupby-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
