---
title: Elemento CustomControlName per ExpressionName per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368910"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>Elemento CustomControlName per ExpressionBinding per GroupBy (formato)

Specifica il nome di un controllo comune o di un controllo di visualizzazione. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomEntry per CustomControl per GroupBy (Format) elemento CustomItem per CustomEntry per l'elemento di espressione GroupBy (Format) per CustomItem per l'elemento GroupBy (Format) CustomControlName per Expression per GroupBy (Format)

## <a name="syntax"></a>Sintassi

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomControlName`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento expressiongroup per CustomItem per GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Definisce i dati visualizzati dal controllo.|

## <a name="text-value"></a>Valore testo

Specificare il nome del controllo.

## <a name="remarks"></a>Osservazioni

È possibile creare controlli comuni che possono essere utilizzati da tutte le visualizzazioni di un file di formattazione ed è possibile creare controlli di visualizzazione che possono essere utilizzati da una visualizzazione specifica. Gli elementi seguenti specificano i nomi di questi controlli:

- [Elemento Name per il controllo per i controlli per la configurazione (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Elemento Name per il controllo per i controlli per la visualizzazione (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Vedere anche

[Elemento Name per il controllo per i controlli per la configurazione (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Elemento Name per il controllo per i controlli per la visualizzazione (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Elemento expressiongroup per CustomItem per GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
