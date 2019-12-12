---
title: Elemento ListItem per ListItems per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365130"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>Elemento ListItem per ListItems per ListControl (formato)

Definisce la proprietà o lo script il cui valore viene visualizzato in una riga della visualizzazione elenco.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries per ListControl (Format) elemento ListEntry per ListControl (Format) elemento ListItems per ListControl (Format) ListItem per l'elemento ListControl (Format)

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

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ListItem`. È possibile specificare solo una proprietà o uno script.

### <a name="attributes"></a>Attributi

Nessuno

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento FormatString per ListItem per ListControl (Format)](./formatstring-element-for-listitem-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica una stringa di formato che definisce come viene visualizzato il valore della proprietà o dello script.|
|[Elemento ItemSelectionCondition per ListItem per ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve esistere per l'uso di questo elemento elenco.|
|[Elemento label per ListItem per ListControl (Format)](./label-element-for-listitem-for-listcontrol-format.md)|Elemento facoltativo<br /><br /> Specifica l'etichetta visualizzata a sinistra della proprietà o del valore dello script nella riga.|
|[Elemento PropertyName per ListItem per ListControl (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica la proprietà .NET il cui valore viene visualizzato nella riga.|
|[Elemento ScriptBlock per ListItem per ListControl (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script il cui valore viene visualizzato nella riga.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ListItems per il controllo List (Format)](./listitems-element-for-listentry-for-listcontrol-format.md)|Definisce le proprietà e gli script i cui valori vengono visualizzati nella visualizzazione elenco.|

## <a name="remarks"></a>Osservazioni

Per ulteriori informazioni sui componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

## <a name="example"></a>Esempio

In questo esempio vengono illustrati gli elementi XML che definiscono tre righe della visualizzazione elenco. Nelle prime due righe viene visualizzato il valore di una proprietà .NET e nell'ultima riga viene visualizzato un valore generato da uno script.

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

[Elemento ListItems (Format)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Elemento FormatString per ListItem (Format)](./formatstring-element-for-listitem-for-listcontrol-format.md)

[Elemento label per ListItem (Format)](./label-element-for-listitem-for-listcontrol-format.md)

[Elemento PropertyName per ListItem (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Elemento ScriptBlock per ListItem (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Scrittura di un file di formattazione e di tipi di Windows PowerShell](./writing-a-powershell-formatting-file.md)
