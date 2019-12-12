---
title: Elemento CustomItem per CustomEntry per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363950"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>Elemento CustomItem per CustomEntry per CustomControl per View (formato)

Definisce quali dati vengono visualizzati dalla visualizzazione controlli personalizzati e come vengono visualizzati. Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries per CustomControl per la vista (Format) CustomEntry elemento per CustomEntries per la visualizzazione (Format) CustomItem elemento per CustomEntry per la visualizzazione (formato)

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
|[Elemento expressiongroup per CustomItem per CustomControl per View (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Definisce i dati visualizzati dal controllo.|
|[Elemento frame per CustomItem per CustomControl per View (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Definisce quali dati vengono visualizzati dalla visualizzazione controlli personalizzati e come vengono visualizzati.|
|[Elemento NewLine per CustomItem per il controllo personalizzato per la visualizzazione (Format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|Elemento facoltativo.<br /><br /> Aggiunge una riga vuota alla visualizzazione del controllo.|
|[Elemento text per CustomItem per CustomControl per View (Format)](./text-element-for-customitem-for-customview-for-view-format.md)|Elemento facoltativo.<br /><br /> Specifica il testo aggiuntivo per i dati visualizzati dal controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntry per CustomEntries per CustomControl per View (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Fornisce una definizione della visualizzazione controlli personalizzata.|

## <a name="remarks"></a>Osservazioni

## <a name="see-also"></a>Vedere anche

[Elemento CustomEntry per CustomEntries per View (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Elemento expressiongroup per CustomItem per CustomControl per View (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[Elemento frame per CustomItem per CustomControl per View (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Elemento NewLine per CustomItem per CustomControl per View (Format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[Elemento text per CustomItem per CustomControl per View (Format)](./text-element-for-customitem-for-customview-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
