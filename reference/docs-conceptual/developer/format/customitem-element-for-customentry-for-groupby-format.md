---
title: Elemento CustomItem per CustomEntry per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363880"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>Elemento CustomItem per CustomEntry per GroupBy (formato)

Definisce quali dati vengono visualizzati dalla visualizzazione controlli personalizzati e come vengono visualizzati. Questo elemento viene utilizzato quando si definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per View (Format) elemento CustomControl per l'elemento GroupBy (Format) CustomEntries per CustomControl per l'elemento GroupBy (Format) CustomItem per CustomEntry per GroupBy (Format)

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

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomItem`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento expressiongroup per CustomItem per GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Definisce i dati visualizzati dal controllo.|
|[Elemento frame per CustomItem per GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Definisce quali dati vengono visualizzati dalla visualizzazione controlli personalizzati e come vengono visualizzati.|
|[Elemento NewLine per CustomItem per GroupBy (Format)](./newline-element-for-customitem-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Aggiunge una riga vuota alla visualizzazione del controllo.|
|[Elemento text per CustomItem per GroupBy (Format)](./text-element-for-customitem-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Specifica il testo aggiuntivo per i dati visualizzati dal controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntry per CustomControl per GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Fornisce una definizione della visualizzazione controlli personalizzata.|

## <a name="remarks"></a>Osservazioni

## <a name="see-also"></a>Vedere anche

[Elemento CustomEntry per CustomControl per GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)

[Elemento expressiongroup per CustomItem per GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Elemento frame per CustomItem per GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)

[Elemento NewLine per CustomItem per GroupBy (Format)](./newline-element-for-customitem-for-groupby-format.md)

[Elemento text per CustomItem per GroupBy (Format)](./text-element-for-customitem-for-groupby-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
