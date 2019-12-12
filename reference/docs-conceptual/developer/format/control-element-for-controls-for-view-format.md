---
title: Elemento Control per Controls per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363470"
---
# <a name="control-element-for-controls-for-view--format"></a>Elemento Control per Controls per View (formato)

Definisce un controllo che può essere utilizzato dalla visualizzazione e dal nome utilizzato per fare riferimento al controllo.

Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Control`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento Name per Control per View (Format)](./name-element-for-control-for-controls-for-view-format.md)|Elemento obbligatorio.<br /><br /> Specifica il nome del controllo.|
|[Elemento CustomControl per il controllo per i controlli per la visualizzazione (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Elemento obbligatorio.<br /><br /> Definisce il controllo utilizzato da questa visualizzazione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento Controls (Format)](./controls-element-for-view-format.md)|Definisce i controlli di visualizzazione che possono essere utilizzati da una visualizzazione specifica.|

## <a name="remarks"></a>Osservazioni

Questo controllo può essere specificato dagli elementi seguenti:

- [Elemento CustomControlName per Expressiongroup per i controlli per la visualizzazione (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [Elemento CustomControlName per Expression per CustomControl per View (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [Elemento CustomControlName per Expressiongroup per GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [Elemento CustomControlName per GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>Vedere anche

[Elemento CustomControl per il controllo per i controlli per la visualizzazione (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Elemento CustomControlName per Expressiongroup per i controlli per la visualizzazione (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento CustomControlName per Expression per CustomControl per View (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento CustomControlName per Expressiongroup per GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Elemento CustomControlName per Expressiongroup per GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Elemento Controls (Format)](./controls-element-for-view-format.md)

[Elemento Name per il controllo per i controlli per la visualizzazione (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
