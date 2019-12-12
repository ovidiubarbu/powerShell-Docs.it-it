---
title: Elemento label per GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365200"
---
# <a name="label-element-for-groupby-format"></a>Elemento Label per GroupBy (formato)

Specifica un'etichetta visualizzata quando viene rilevato un nuovo gruppo.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy per l'elemento label view (Format) per GroupBy (Format)

## <a name="syntax"></a>Sintassi

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Label`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento GroupBy per View (Format)](./groupby-element-for-view-format.md)|Definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.|

## <a name="text-value"></a>Valore testo

Specificare il testo visualizzato ogni volta che Windows PowerShell incontra un nuovo valore di proprietà o script.

## <a name="remarks"></a>Osservazioni

Oltre al testo specificato da questo elemento, Windows PowerShell Visualizza il nuovo valore che avvia il gruppo e aggiunge una riga vuota prima e dopo il gruppo.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrata l'etichetta per un nuovo gruppo. L'etichetta visualizzata avrà un aspetto simile al seguente: `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Per un esempio di un file di formattazione completo che include questo elemento, vedere [visualizzazione estesa (GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Vedere anche

[Elemento GroupBy per View (Format)](./groupby-element-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
