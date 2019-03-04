---
title: Elemento PropertyName per ListItem per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855737"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a>Elemento PropertyName per ListItem per ListControl (formato)

Specifica la proprietà .NET il cui valore viene visualizzato nell'elenco.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) dell'oggetto ListControl elemento (formato) elemento ListEntries (formato) elemento ListEntry (formato) elemento ListItems (formato) elemento ListItem (formato) PropertyName elemento di configurazione per ListItem (formato)

## <a name="syntax"></a>Sintassi

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `PropertyName` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ListItem (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definisce le proprietà dello script il cui valore viene visualizzato nella riga della visualizzazione elenco.|

## <a name="text-value"></a>Valore di testo

Specificare il nome della proprietà il cui valore viene visualizzato.

## <a name="remarks"></a>Osservazioni

Quando questo elemento viene specificato, non è possibile specificare il [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento.

Oltre a visualizzare il valore della proprietà, è anche possibile specificare un'etichetta per il valore o una stringa di formato che può essere utilizzata per modificare la visualizzazione del valore. Per altre informazioni su come specificare i dati in una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come specificare l'etichetta e la proprietà il cui valore viene visualizzato.

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Vedere anche

[Elemento ScriptBlock per ListItem per ListControl (formato)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Elemento ListItem per ListControl(Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
