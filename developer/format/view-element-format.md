---
title: Visualizzare l'elemento (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083723"
---
# <a name="view-element-format"></a>Elemento View (formato)

Definisce una vista contenente uno o più oggetti .NET. Non sono previsti limiti al numero di visualizzazioni che possono essere definite in un file di formattazione.

Elemento di visualizzazione configurazione elemento (formato) elemento ViewDefinitions (formato) (formato)

## <a name="syntax"></a>Sintassi

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `View` elemento. È necessario specificare uno e uno solo gli elementi figlio del controllo e specificare il nome della visualizzazione e gli oggetti che utilizzano la vista. Definisce i controlli personalizzati, come raggruppare gli oggetti e che specifica se la vista è out-of-band sono facoltativi.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento Controls per visualizzazione (formato)](./controls-element-for-view-format.md)|Elemento facoltativo.<br /><br /> Definisce un set di controlli che possono fare riferimento al nome all'interno della visualizzazione.|
|[Elemento CustomControl (formato)](./customcontrol-element-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Definisce un formato di controllo personalizzato per la visualizzazione.|
|[Elemento GroupBy per visualizzazione (formato)](./groupby-element-for-view-format.md)|Elemento facoltativo.<br /><br /> Definisce la modalità di raggruppamento dei membri degli oggetti .NET.|
|[Elemento dell'oggetto ListControl (formato)](./listcontrol-element-format.md)|Elemento facoltativo.<br /><br /> Definisce un formato di elenco per la visualizzazione.|
|[Elemento Name per visualizzazione (formato)](./name-element-for-view-format.md)|Elemento obbligatorio.<br /><br /> Specifica il nome utilizzato per fare riferimento la vista.|
|[Elemento Table (formato)](./tablecontrol-element-format.md)|Elemento facoltativo.<br /><br /> Definisce un formato di tabella per la visualizzazione.|
|[Elemento ViewSelectedBy per visualizzazione (formato)](./viewselectedby-element-format.md)|Elemento obbligatorio.<br /><br /> Definisce gli oggetti .NET che consente di visualizzare.|
|[Elemento WideControl (formato)](./widecontrol-element-format.md)|Elemento facoltativo.<br /><br /> Definisce un'ampia (valore singolo) formato di elenco per la visualizzazione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ViewDefinitions (formato)](./viewdefinitions-element-format.md)|Definisce le viste utilizzate per visualizzare gli oggetti.|

## <a name="remarks"></a>Osservazioni

Per altre informazioni sui componenti di diverse visualizzazioni e i controlli personalizzati, vedere gli argomenti seguenti:

- [Componenti di visualizzazione tabella](./creating-a-table-view.md)

- [Componenti di visualizzazione elenco](./creating-a-list-view.md)

- [Componenti di visualizzazione estesa](./creating-a-wide-view.md)

- [Controlli personalizzati](./creating-custom-controls.md)

## <a name="example"></a>Esempio

Questo esempio viene illustrato un `View` elemento che definisce una visualizzazione tabella per il [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) oggetto.

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>Vedere anche

[Elemento ViewDefinitions (formato)](./viewdefinitions-element-format.md)

[Elemento Name per visualizzazione (formato)](./name-element-for-view-format.md)

[Elemento ViewSelectedBy (formato)](./viewselectedby-element-format.md)

[Elemento Controls per visualizzazione (formato)](./controls-element-for-view-format.md)

[Elemento GroupBy per visualizzazione (formato)](./groupby-element-for-view-format.md)

[Elemento Table (formato)](./tablecontrol-element-format.md)

[Elemento dell'oggetto ListControl (formato)](./listcontrol-element-format.md)

[Elemento WideControl (formato)](./widecontrol-element-format.md)

[Elemento CustomControl (formato)](./customcontrol-element-for-groupby-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
