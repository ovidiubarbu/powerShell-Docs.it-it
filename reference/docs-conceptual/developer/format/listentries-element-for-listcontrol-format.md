---
title: Elemento ListEntries per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362760"
---
# <a name="listentries-element-for-listcontrol-format"></a>Elemento ListEntries per ListControl (formato)

Fornisce le definizioni della visualizzazione elenco. Nella visualizzazione elenco è necessario specificare una o più definizioni.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format)

## <a name="syntax"></a>Sintassi

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ListEntries`. È necessario specificare almeno un elemento figlio.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento ListEntry (Format)](./listentry-element-for-listcontrol-format.md)|Fornisce una definizione della visualizzazione elenco.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ListControl (Format)](./listcontrol-element-format.md)|Definisce un formato di elenco per la visualizzazione.|

## <a name="remarks"></a>Osservazioni

Per ulteriori informazioni sulle visualizzazioni elenco, vedere [visualizzazione elenco](./creating-a-list-view.md).

## <a name="example"></a>Esempio

Questo esempio Mostra gli elementi XML che definiscono la visualizzazione elenco per l'oggetto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .

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

[Elemento ListControl (Format)](./listcontrol-element-format.md)

[Elemento ListEntry (Format)](./listentry-element-for-listcontrol-format.md)

[Visualizzazione elenco](./creating-a-list-view.md)

[Scrittura di un file di formattazione e di tipi di Windows PowerShell](./writing-a-powershell-formatting-file.md)
