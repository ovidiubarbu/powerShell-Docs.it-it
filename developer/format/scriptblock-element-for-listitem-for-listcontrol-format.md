---
title: Elemento ScriptBlock per ListItem per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064578"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>Elemento ScriptBlock per ListItem per ListControl (formato)

Specifica lo script il cui valore viene visualizzato nella riga.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) ListEntries elemento di configurazione per elemento dell'oggetto ListControl (formato) ListEntry ListEntries per elemento ListItems dell'oggetto ListControl (formato) per ListEntry elemento ListItem ListControl (formato) per ListItems per elemento dell'oggetto ListControl (formato) ScriptBlock ListItem per ListControl (formato)

## <a name="syntax"></a>Sintassi

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ScriptBlock` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ListItem (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definisce proprietà o script il cui valore viene visualizzato in una riga della visualizzazione elenco.|

## <a name="text-value"></a>Valore di testo

Specificare lo script il cui valore viene visualizzato nella riga.

## <a name="remarks"></a>Osservazioni

Quando questo elemento viene specificato, non è possibile specificare il [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento.

Per altre informazioni su come specificare gli script in una visualizzazione elenco, vedere [visualizzazione elenco](./creating-a-list-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come specificare la proprietà il cui valore viene visualizzato.

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a>Vedere anche

[Elemento PropertyName per ListItem per ListControl (formato)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Elemento ListItem per ListItems per ListControl (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
