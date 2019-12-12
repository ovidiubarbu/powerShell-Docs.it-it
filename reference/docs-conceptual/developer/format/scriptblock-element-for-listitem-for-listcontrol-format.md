---
title: Elemento ScriptBlock per ListItem per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364810"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>Elemento ScriptBlock per ListItem per ListControl (formato)

Specifica lo script il cui valore viene visualizzato nella riga.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries per l'elemento ListControl (Format) ListEntry per ListEntries per l'elemento ListItem (Format) ListItems per ListEntry per l'elemento ListItem (Format) ListItem per ListItems per l'elemento ListControl (Format) ScriptBlock per ListItem per ListControl (Format)

## <a name="syntax"></a>Sintassi

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ScriptBlock`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ListItem (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definisce la proprietà o lo script il cui valore viene visualizzato in una riga della visualizzazione elenco.|

## <a name="text-value"></a>Valore testo

Specificare lo script il cui valore viene visualizzato nella riga.

## <a name="remarks"></a>Osservazioni

Quando questo elemento viene specificato, non è possibile specificare l'elemento [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) .

Per ulteriori informazioni su come specificare gli script in una visualizzazione elenco, vedere [visualizzazione elenco](./creating-a-list-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come specificare la proprietà di cui viene visualizzato il valore.

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a>Vedere anche

[Elemento PropertyName per ListItem per ListControl (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Elemento ListItem per ListItems per ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
