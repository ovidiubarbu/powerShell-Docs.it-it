---
title: Elemento label per ListItem per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362890"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>Elemento Label per ListItem per ListControl (formato)

Specifica l'etichetta visualizzata a sinistra della proprietà o del valore dello script nella riga.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries per l'elemento ListControl (Format) ListEntry per gli ListItem (Format) ListItem per ListEntry per l'elemento ListControl ( Format) elemento ListItem per ListItems per l'elemento label di ListControl (Format) per ListItem per ListControl (Format)

## <a name="syntax"></a>Sintassi

```xml
<Label>Label for displayed value</Label>
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
|[Elemento ListItem per ListItems per ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definisce la proprietà o lo script il cui valore viene visualizzato in una riga della visualizzazione elenco.|

## <a name="text-value"></a>Valore testo

Consente di specificare l'etichetta da visualizzare a sinistra della proprietà o del valore dello script.

## <a name="remarks"></a>Osservazioni

Se non si specifica un'etichetta, viene visualizzato il nome della proprietà o dello script. Per ulteriori informazioni sull'utilizzo delle etichette in una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come aggiungere un'etichetta a una riga.

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Elemento ListItem (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
