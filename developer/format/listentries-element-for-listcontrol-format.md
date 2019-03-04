---
title: Elemento ListEntries per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856787"
---
# <a name="listentries-element-for-listcontrol-format"></a>Elemento ListEntries per ListControl (formato)

Fornisce le definizioni della visualizzazione elenco. La visualizzazione elenco è necessario specificare una o più definizioni.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) dell'oggetto ListControl elemento (formato) ListEntries elemento di configurazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ListEntries` elemento. È necessario specificare almeno un elemento figlio.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento ListEntry (formato)](./listentry-element-for-listcontrol-format.md)|Fornisce una definizione della visualizzazione elenco.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento dell'oggetto ListControl (formato)](./listcontrol-element-format.md)|Definisce un formato di elenco per la visualizzazione.|

## <a name="remarks"></a>Osservazioni

Per altre informazioni sulle visualizzazioni di elenco, vedere [visualizzazione elenco](./creating-a-list-view.md).

## <a name="example"></a>Esempio

Questo esempio illustra gli elementi XML che definiscono la visualizzazione elenco per il [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) oggetto.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>Vedere anche

[Elemento dell'oggetto ListControl (formato)](./listcontrol-element-format.md)

[Elemento ListEntry (formato)](./listentry-element-for-listcontrol-format.md)

[Visualizzazione elenco](./creating-a-list-view.md)

[La scrittura di un metodo di formattazione di Windows PowerShell e i tipi di File](./writing-a-powershell-formatting-file.md)
