---
title: Elemento ListItems per ListEntry per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858587"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>Elemento ListItems per ListEntry per ListControl (formato)

Definisce le proprietà e gli script i cui valori vengono visualizzati nelle righe della visualizzazione elenco.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) dell'oggetto ListControl elemento (formato) ListEntries elemento di configurazione per elenco controllo (formato) ListEntry elemento per elemento ListItems dell'oggetto ListControl (formato) dell'oggetto ListControl (formato)

## <a name="syntax"></a>Sintassi

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `ListItems` elemento. Non sono previsti limiti al numero di elementi figlio che possono essere specificati. L'ordine degli elementi figlio definisce l'ordine in cui i valori vengono visualizzati nella visualizzazione elenco.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento ListItem per ListControl (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)|Elemento obbligatorio.<br /><br /> Definisce le proprietà dello script il cui valore viene visualizzato nella visualizzazione elenco.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ListEntry per ListControl (formato)](./listentry-element-for-listcontrol-format.md)|Fornisce una definizione della visualizzazione elenco.|

## <a name="remarks"></a>Osservazioni

Per altre informazioni su questo tipo di visualizzazione, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

## <a name="example"></a>Esempio

Questo esempio illustra gli elementi XML che definiscono tre righe della visualizzazione elenco.

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a>Vedere anche

[Elemento ListEntry per ListControl (formato)](./listentry-element-for-listcontrol-format.md)

[Elemento ListItem per ListControl (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
