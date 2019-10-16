---
title: Elemento ScriptBlock per SelectionCondition per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368620"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a>Elemento ScriptBlock per SelectionCondition per Controls per Configuration (formato)

Specifica lo script che attiva la condizione. Quando questo script viene valutato `true`, la condizione viene soddisfatta e viene usata la definizione. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (Format) SelectionCondition elemento per EntrySelectedBy per i controlli per la configurazione (Format) Elemento ScriptBlock per SelectionCondition per i controlli per la configurazione (Format)

## <a name="syntax"></a>Sintassi

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
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
|[Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Definisce una condizione che deve esistere per la definizione del controllo comune da utilizzare.|

## <a name="text-value"></a>Valore di testo

Specificare lo script che viene valutato.

## <a name="remarks"></a>Osservazioni

Per valutare la condizione di selezione, è necessario specificare almeno uno script o un nome di proprietà, ma non è possibile specificarli entrambi. Per ulteriori informazioni sul modo in cui è possibile utilizzare le condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
