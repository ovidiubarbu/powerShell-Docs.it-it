---
title: L'etichetta di elemento per GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065411"
---
# <a name="label-element-for-groupby-format"></a>Elemento Label per GroupBy (formato)

Specifica un'etichetta che viene visualizzata quando viene rilevato un nuovo gruppo.

Elemento di GroupBy elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) elemento di visualizzazione (formato) etichetta per GroupBy (formato)

## <a name="syntax"></a>Sintassi

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `Label` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento GroupBy per visualizzazione (formato)](./groupby-element-for-view-format.md)|Definisce come viene visualizzato un nuovo gruppo di oggetti.|

## <a name="text-value"></a>Valore di testo

Specificare il testo che viene visualizzato ogni volta che Windows PowerShell rileva una nuova proprietà o un valore di script.

## <a name="remarks"></a>Osservazioni

Oltre al testo specificato da questo elemento, Windows PowerShell consente di visualizzare il nuovo valore che si avvia il gruppo e aggiunge una riga vuota prima e dopo il gruppo.

## <a name="example"></a>Esempio

Nell'esempio seguente mostra l'etichetta per un nuovo gruppo. Etichetta visualizzata sarà simile al seguente: `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Per un esempio di un file di formattazione completato che include questo elemento, vedere [visualizzazione più ampia (GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Vedere anche

[Elemento GroupBy per visualizzazione (formato)](./groupby-element-for-view-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
