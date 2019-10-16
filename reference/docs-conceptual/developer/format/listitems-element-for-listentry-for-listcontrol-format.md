---
title: Elemento ListItems per ListEntry per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362740"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>Elemento ListItems per ListEntry per ListControl (formato)

Definisce le proprietà e gli script i cui valori vengono visualizzati nelle righe della visualizzazione elenco.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries per il controllo List (Format) elemento ListEntry per l'elemento ListControl (Format) ListItems per ListControl (Format)

## <a name="syntax"></a>Sintassi

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ListItems`. Non esiste alcun limite al numero di elementi figlio che è possibile specificare. L'ordine degli elementi figlio definisce l'ordine in cui i valori vengono visualizzati nella visualizzazione elenco.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento ListItem per ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Elemento obbligatorio.<br /><br /> Definisce la proprietà o lo script il cui valore viene visualizzato dalla visualizzazione elenco.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ListEntry per ListControl (Format)](./listentry-element-for-listcontrol-format.md)|Fornisce una definizione della visualizzazione elenco.|

## <a name="remarks"></a>Osservazioni

Per ulteriori informazioni su questo tipo di visualizzazione, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

## <a name="example"></a>Esempio

In questo esempio vengono illustrati gli elementi XML che definiscono tre righe della visualizzazione elenco.

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

[Elemento ListEntry per ListControl (Format)](./listentry-element-for-listcontrol-format.md)

[Elemento ListItem per ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
