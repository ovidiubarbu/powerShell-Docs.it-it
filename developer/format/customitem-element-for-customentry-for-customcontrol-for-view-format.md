---
title: Elemento CustomItem per CustomEntry per CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066414"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>Elemento CustomItem per CustomEntry per CustomControl per View (formato)

Definisce i dati visualizzati dalla visualizzazione del controllo personalizzato e modalità di visualizzazione. Questo elemento viene usato quando si definisce una vista di controllo personalizzato.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento CustomControl (formato) CustomEntries elemento di configurazione per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per elemento CustomItem visualizzazione (formato) CustomEntry per visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomItem` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento ExpressionBinding per CustomItem per CustomControl per visualizzazione (formato)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Definisce i dati che vengano visualizzati dal controllo.|
|[Elemento frame per CustomItem per CustomControl per visualizzazione (formato)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Definisce i dati visualizzati dalla visualizzazione del controllo personalizzato e modalità di visualizzazione.|
|[Elemento di una nuova riga per CustomItem per un controllo personalizzato per la visualizzazione (formato)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Aggiunge una riga vuota alla visualizzazione del controllo.|
|[Elemento di testo per CustomItem per CustomControl per visualizzazione (formato)](./text-element-for-customitem-for-customview-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica il testo aggiuntivo per i dati visualizzati dal controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntry per CustomEntries per CustomControl per visualizzazione (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Fornisce una definizione della vista del controllo personalizzato.|

## <a name="remarks"></a>Osservazioni

## <a name="see-also"></a>Vedere anche

[Elemento CustomEntry per CustomEntries per visualizzazione (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Elemento ExpressionBinding per CustomItem per CustomControl per visualizzazione (formato)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[Elemento frame per CustomItem per CustomControl per visualizzazione (formato)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Elemento di una nuova riga per CustomItem per CustomControl per visualizzazione (formato)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[Elemento di testo per CustomItem per CustomControl per visualizzazione (formato)](./text-element-for-customitem-for-customview-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
