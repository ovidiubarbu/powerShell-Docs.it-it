---
title: Elemento ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362780"
---
# <a name="listcontrol-element-format"></a>Elemento ListControl (formato)

Definisce un formato di elenco per la visualizzazione.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format)

## <a name="syntax"></a>Sintassi

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ListControl`. Questo elemento deve contenere solo un singolo elemento figlio.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento ListEntries (Format)](./listentries-element-for-listcontrol-format.md)|Elemento obbligatorio.<br /><br /> Fornisce le definizioni della visualizzazione elenco.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento View (Format)](./view-element-format.md)|Definisce una vista utilizzata per visualizzare i membri di uno o più oggetti.|

## <a name="remarks"></a>Osservazioni

Per ulteriori informazioni sulla creazione di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

## <a name="example"></a>Esempio

Questo esempio mostra una visualizzazione elenco per l'oggetto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .

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

[Elemento View (Format)](./view-element-format.md)

[Elemento ListEntries (Format)](./listentries-element-for-listcontrol-format.md)

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Scrittura di un file di formattazione e di tipi di Windows PowerShell](./writing-a-powershell-formatting-file.md)
