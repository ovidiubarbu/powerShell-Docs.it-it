---
title: Elemento CustomItem per CustomEntry per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862937"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a>Elemento CustomItem per CustomEntry per Controls per Configuration (formato)

Definisce i dati che vengano visualizzati dal controllo e la modalità di visualizzazione. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli di configurazione (formato) CustomControl elemento per il controllo per elemento di configurazione (formato) CustomEntries per CustomControl per Configuration ( Elemento CustomEntry Format) per CustomControl per i controlli per elemento di configurazione (formato) CustomItem per CustomEntry per i controlli per la configurazione

## <a name="syntax"></a>Sintassi

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomItem` elemento. Per altre informazioni, vedere la sezione Osservazioni.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento ExpressionBinding per CustomItem per i controlli per la configurazione (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Definisce i dati che vengano visualizzati dal controllo.|
|[Elemento frame per CustomItem per i controlli per la configurazione (formato)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Definisce come verranno visualizzati i dati, ad esempio lo spostamento di dati a sinistra o destra.|
|[Elemento di una nuova riga per CustomItem per i controlli per la configurazione (formato)](./newline-element-for-customitem-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Aggiunge una riga vuota alla visualizzazione del controllo.|
|[Elemento di testo per CustomItem per i controlli per la configurazione (formato)](./text-element-for-customitem-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Aggiunge testo, ad esempio parentesi o parentesi quadre, alla visualizzazione del controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntry per CustomControl per i controlli per la configurazione (formato)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Fornisce una definizione del controllo.|

## <a name="remarks"></a>Osservazioni

Quando si specificano gli elementi figlio del `CustomItem` elemento, tenere presente quanto segue:

- Gli elementi figlio devono essere aggiunti nella sequenza seguente: `ExpressionBinding`, `NewLine`, `Text`, e `Frame`.

- Non è definito alcun limite massimo al numero di sequenze che è possibile specificare.

- In ogni sequenza, non è definito alcun limite massimo al numero di `ExpressionBinding` gli elementi che è possibile usare.

## <a name="see-also"></a>Vedere anche

[Elemento ExpressionBinding per CustomItem per i controlli per la configurazione (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento frame per CustomItem per i controlli per la configurazione (formato)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento di una nuova riga per CustomItem per i controlli per la configurazione (formato)](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento di testo per CustomItem per i controlli per la configurazione (formato)](./text-element-for-customitem-for-controls-for-configuration-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
