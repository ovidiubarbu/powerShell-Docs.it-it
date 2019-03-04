---
title: Elemento ListItem per ListItems per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855157"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>Elemento ListItem per ListItems per ListControl (formato)

Definisce proprietà o script il cui valore viene visualizzato in una riga della visualizzazione elenco.

Configurazione (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento dell'oggetto ListControl (formato) ListEntries elemento dell'elemento dell'oggetto ListControl (formato) ListEntry elemento per elemento ListItems dell'oggetto ListControl (formato) dell'oggetto ListControl (formato) ListItem per elemento dell'oggetto ListControl (formato)

## <a name="syntax"></a>Sintassi

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `ListItem` elemento. Può essere specificato solo una proprietà o dello script.

### <a name="attributes"></a>Attributes

Nessuno

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento FormatString per ListItem per ListControl (formato)](./formatstring-element-for-listitem-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica una stringa di formato che definisce come viene visualizzato il valore della proprietà o dello script.|
|[Elemento ItemSelectionCondition per ListItem per ListControl (formato)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve essere presente per questo elemento di elenco da utilizzare.|
|[Elemento Label per ListItem per ListControl (formato)](./label-element-for-listitem-for-listcontrol-format.md)|Elemento facoltativo<br /><br /> Specifica l'etichetta che viene visualizzato a sinistra del valore della proprietà o script della riga.|
|[Elemento PropertyName per ListItem per ListControl (formato)](./propertyname-element-for-listitem-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET il cui valore viene visualizzato nella riga.|
|[Elemento ScriptBlock per ListItem per ListControl (formato)](./scriptblock-element-for-listitem-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script il cui valore viene visualizzato nella riga.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ListItems per il controllo elenco (Format)](./listitems-element-for-listentry-for-listcontrol-format.md)|Definisce le proprietà e gli script i cui valori vengono visualizzati nella visualizzazione elenco.|

## <a name="remarks"></a>Osservazioni

Per altre informazioni sui componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

## <a name="example"></a>Esempio

Questo esempio illustra gli elementi XML che definiscono tre righe della visualizzazione elenco. Le prime due righe visualizzare il valore della proprietà .NET e l'ultima riga visualizza un valore generato da uno script.

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a>Vedere anche

[Elemento ListItems (formato)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Elemento FormatString per ListItem (formato)](./formatstring-element-for-listitem-for-listcontrol-format.md)

[Elemento Label per ListItem (formato)](./label-element-for-listitem-for-listcontrol-format.md)

[Elemento PropertyName per ListItem (formato)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Elemento ScriptBlock per ListItem (formato)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[La scrittura di un metodo di formattazione di Windows PowerShell e i tipi di File](./writing-a-powershell-formatting-file.md)
