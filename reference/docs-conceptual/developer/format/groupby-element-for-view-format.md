---
title: Elemento GroupBy per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363630"
---
# <a name="groupby-element-for-view-format"></a>Elemento GroupBy per View (formato)

Definisce la modalità di visualizzazione di un nuovo gruppo di oggetti. Questo elemento viene utilizzato quando si definisce una tabella, un elenco, un'ampia o una visualizzazione controlli personalizzata.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format)

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

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomControl per GroupBy (Format)](./customcontrol-element-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Definisce il controllo personalizzato che Visualizza i nuovi gruppi.|
|[Elemento CustomControlName per GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica il nome di un controllo utilizzato per visualizzare il nuovo gruppo.|
|[Elemento label per GroupBy (Format)](./label-element-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica un'etichetta visualizzata quando viene rilevato un nuovo gruppo.|
|[Elemento PropertyName per GroupBy (Format)](./propertyname-element-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET che avvia un nuovo gruppo ogni volta che cambia il valore.|
|[Elemento ScriptBlock per GroupBy (Format)](./scriptblock-element-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script che avvia un nuovo gruppo ogni volta che cambia il valore.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento View (Format)](./view-element-format.md)|Definisce una vista che visualizza uno o più oggetti .NET.|

## <a name="remarks"></a>Osservazioni

Quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti, è necessario specificare la proprietà o lo script che avvierà il nuovo gruppo. Tuttavia, non è possibile specificare entrambi.

## <a name="see-also"></a>Vedere anche

[Elemento CustomControlName per GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)

[Elemento label per GroupBy (Format)](./label-element-for-groupby-format.md)

[Elemento PropertyName per GroupBy (Format)](./propertyname-element-for-groupby-format.md)

[Elemento ScriptBlock per GroupBy (Format)](./scriptblock-element-for-groupby-format.md)

[Elemento View (Format)](./view-element-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
