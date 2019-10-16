---
title: Elemento CustomControlName per Expression per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364110"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a>Elemento CustomControlName per ExpressionBinding per CustomControl per View (formato)

Specifica il nome di un controllo comune o di un controllo di visualizzazione. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl per View (Format) elemento CustomEntries per CustomControl per la visualizzazione (Format) CustomEntry elemento per CustomEntries per View (Format) CustomItem Elemento per CustomEntry per l'elemento Expressiongroup per la visualizzazione (Format) per CustomItem (Format) CustomControlName per l'associazione di espressioni per CustomItem (Format)

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
|[Elemento expressiongroup per CustomItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Definisce i dati visualizzati dal controllo.|

## <a name="text-value"></a>Valore di testo

Specificare il nome del controllo.

## <a name="remarks"></a>Osservazioni

È possibile creare controlli comuni che possono essere utilizzati da tutte le visualizzazioni di un file di formattazione ed è possibile creare controlli di visualizzazione che possono essere utilizzati da una visualizzazione specifica. I nomi di questi controlli sono specificati dagli elementi seguenti.

- [Elemento Name per il controllo per i controlli per la configurazione (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Elemento Name per il controllo per i controlli per la visualizzazione (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Vedere anche

[Elemento Name per il controllo per i controlli per la configurazione (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Elemento Name per il controllo per i controlli per la visualizzazione (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Elemento expressiongroup per CustomItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
