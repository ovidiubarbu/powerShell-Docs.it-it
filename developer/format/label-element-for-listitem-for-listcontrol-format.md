---
title: L'etichetta di elemento per elemento ListItem per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065428"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>Elemento Label per ListItem per ListControl (formato)

Specifica l'etichetta che viene visualizzato a sinistra del valore della proprietà o script della riga.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) ListEntries elemento di configurazione per ListControl (formato) ListEntry elemento ListItems dell'oggetto ListControl (formato) per ListEntry per elemento dell'oggetto ListControl ( Elemento ListItem Format) per ListItems per elemento etichetta dell'oggetto ListControl (formato) per ListItem per ListControl (formato)

## <a name="syntax"></a>Sintassi

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Label` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ListItem per ListItems per ListControl (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definisce proprietà o script il cui valore viene visualizzato in una riga della visualizzazione elenco.|

## <a name="text-value"></a>Valore di testo

Specificare l'etichetta per essere visualizzato a sinistra del valore della proprietà o dello script.

## <a name="remarks"></a>Osservazioni

Se non viene specificata un'etichetta, viene visualizzato il nome della proprietà o lo script. Per altre informazioni sull'utilizzo di etichette in una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

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

[Elemento ListItem (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
