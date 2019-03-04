---
title: Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855607"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>Elemento CustomItem per CustomEntry per Controls per View (formato)

Definisce i dati che vengano visualizzati dal controllo e la modalità di visualizzazione. Questo elemento viene usato quando si definiscono i controlli che possono essere usati da una vista.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) i controlli elemento (formato) controllo elemento di configurazione per i controlli elemento di visualizzazione (formato) CustomControl per il controllo per i controlli elemento di visualizzazione (formato) CustomEntries per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per i controlli elemento di visualizzazione (formato) CustomItem per CustomEntry per i controlli per la visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomItem` elemento. Per altre informazioni, vedere la sezione Osservazioni.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Definisce i dati che vengano visualizzati dal controllo.|
|[Elemento frame per CustomItem per i controlli per la visualizzazione (formato)](./frame-element-for-customitem-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra.|
|[Elemento di una nuova riga per CustomItem per i controlli per la visualizzazione (formato)](./newline-element-for-customitem-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Aggiunge una riga vuota alla visualizzazione del controllo.|
|[Elemento di testo per CustomItem per i controlli per la visualizzazione (formato)](./text-element-for-customitem-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Aggiunge testo, ad esempio parentesi o parentesi quadre, alla visualizzazione del controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Fornisce una definizione del controllo.|

## <a name="remarks"></a>Osservazioni

Quando si specificano gli elementi figlio del `CustomItem` elemento, tenere presente quanto segue:

- Gli elementi figlio devono essere aggiunti nella sequenza seguente: `ExpressionBinding`, `NewLine`, `Text`, e `Frame`.

- Non è definito alcun limite massimo al numero di sequenze che è possibile specificare.

- In ogni sequenza, non è definito alcun limite massimo al numero di `ExpressionBinding` gli elementi che è possibile usare.

## <a name="see-also"></a>Vedere anche

[Elemento ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Elemento frame per CustomItem per i controlli per la visualizzazione (formato)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Elemento di una nuova riga per CustomItem per i controlli per la visualizzazione (formato)](./newline-element-for-customitem-for-controls-for-view-format.md)

[Elemento di testo per CustomItem per i controlli per la visualizzazione (formato)](./text-element-for-customitem-for-controls-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
