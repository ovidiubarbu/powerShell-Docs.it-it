---
title: Elemento GroupBy per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859527"
---
# <a name="groupby-element-for-view-format"></a>Elemento GroupBy per View (formato)

Definisce come viene visualizzato un nuovo gruppo di oggetti. Questo elemento viene usato quando si definisce una tabella, elenco, visualizzazione controllo wide o personalizzato.

Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) per la visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi, elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomControl per GroupBy (formato)](./customcontrol-element-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Definisce il controllo personalizzato che consentono di visualizzare i nuovi gruppi.|
|[Elemento CustomControlName per GroupBy (formato)](./customcontrolname-element-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica il nome di un controllo che consente di visualizzare il nuovo gruppo.|
|[Elemento Label per GroupBy (formato)](./label-element-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica un'etichetta che viene visualizzata quando viene rilevato un nuovo gruppo.|
|[Elemento PropertyName per GroupBy (formato)](./propertyname-element-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET inizia un nuovo gruppo ogni volta che cambia il relativo valore.|
|[Elemento ScriptBlock per GroupBy (formato)](./scriptblock-element-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script che avvia un nuovo gruppo ogni volta che cambia il relativo valore.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento di visualizzazione (formato)](./view-element-format.md)|Definisce una vista contenente uno o più oggetti .NET.|

## <a name="remarks"></a>Osservazioni

Quando si definisce come viene visualizzato un nuovo gruppo di oggetti, è necessario specificare la proprietà o script che avvierà il nuovo gruppo; Tuttavia, è possibile specificare entrambi.

## <a name="see-also"></a>Vedere anche

[Elemento CustomControlName per GroupBy (formato)](./customcontrolname-element-for-groupby-format.md)

[Elemento Label per GroupBy (formato)](./label-element-for-groupby-format.md)

[Elemento PropertyName per GroupBy (formato)](./propertyname-element-for-groupby-format.md)

[Elemento ScriptBlock per GroupBy (formato)](./scriptblock-element-for-groupby-format.md)

[Elemento di visualizzazione (formato)](./view-element-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
