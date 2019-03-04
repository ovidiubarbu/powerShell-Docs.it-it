---
title: Elemento dell'oggetto ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857457"
---
# <a name="listcontrol-element-format"></a>Elemento ListControl (formato)

Definisce un formato di elenco per la visualizzazione.

Configurazione (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) dell'oggetto ListControl elemento (formato)

## <a name="syntax"></a>Sintassi

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ListControl` elemento. Questo elemento deve contenere solo un singolo elemento figlio.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento ListEntries (formato)](./listentries-element-for-listcontrol-format.md)|Elemento obbligatorio.<br /><br /> Fornisce le definizioni della visualizzazione elenco.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento di visualizzazione (formato)](./view-element-format.md)|Definisce una vista che consente di visualizzare i membri di uno o più oggetti.|

## <a name="remarks"></a>Osservazioni

Per altre informazioni sulla creazione di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

## <a name="example"></a>Esempio

Questo esempio mostra una visualizzazione elenco per il [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) oggetto.

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>Vedere anche

[Elemento di visualizzazione (formato)](./view-element-format.md)

[Elemento ListEntries (formato)](./listentries-element-for-listcontrol-format.md)

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[La scrittura di un metodo di formattazione di Windows PowerShell e i tipi di File](./writing-a-powershell-formatting-file.md)
