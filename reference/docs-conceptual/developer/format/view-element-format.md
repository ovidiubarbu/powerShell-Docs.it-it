---
title: Elemento View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361460"
---
# <a name="view-element-format"></a>Elemento View (formato)

Definisce una vista che visualizza uno o più oggetti .NET. Non esiste alcun limite al numero di visualizzazioni che è possibile definire in un file di formattazione.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format)

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

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `View`. È necessario specificare uno solo degli elementi figlio del controllo ed è necessario specificare il nome della visualizzazione e gli oggetti che utilizzano la visualizzazione. La definizione di controlli personalizzati, la procedura per raggruppare gli oggetti e la specifica se la vista è fuori banda è facoltativa.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento Controls per View (Format)](./controls-element-for-view-format.md)|Elemento facoltativo.<br /><br /> Definisce un set di controlli a cui è possibile fare riferimento tramite il nome dall'interno della vista.|
|[Elemento CustomControl (Format)](./customcontrol-element-for-groupby-format.md)|Elemento facoltativo.<br /><br /> Definisce un formato di controllo personalizzato per la visualizzazione.|
|[Elemento GroupBy per View (Format)](./groupby-element-for-view-format.md)|Elemento facoltativo.<br /><br /> Definisce la modalità di raggruppamento dei membri degli oggetti .NET.|
|[Elemento ListControl (Format)](./listcontrol-element-format.md)|Elemento facoltativo.<br /><br /> Definisce un formato di elenco per la visualizzazione.|
|[Elemento Name per View (Format)](./name-element-for-view-format.md)|Elemento obbligatorio.<br /><br /> Specifica il nome utilizzato per fare riferimento alla vista.|
|[Elemento Table ((Format)](./tablecontrol-element-format.md)|Elemento facoltativo.<br /><br /> Definisce un formato di tabella per la visualizzazione.|
|[Elemento ViewSelectedBy per View (Format)](./viewselectedby-element-format.md)|Elemento obbligatorio.<br /><br /> Definisce gli oggetti .NET visualizzati da questa visualizzazione.|
|[Elemento WideControl (Format)](./widecontrol-element-format.md)|Elemento facoltativo.<br /><br /> Definisce un formato di elenco Wide (valore singolo) per la visualizzazione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ViewDefinitions (Format)](./viewdefinitions-element-format.md)|Definisce le visualizzazioni utilizzate per visualizzare gli oggetti.|

## <a name="remarks"></a>Osservazioni

Per ulteriori informazioni sui componenti di visualizzazioni e controlli personalizzati diversi, vedere gli argomenti seguenti:

- [Componenti di visualizzazione tabella](./creating-a-table-view.md)

- [Componenti visualizzazione elenco](./creating-a-list-view.md)

- [Componenti di visualizzazione estesa](./creating-a-wide-view.md)

- [Controlli personalizzati](./creating-custom-controls.md)

## <a name="example"></a>Esempio

Questo esempio mostra un elemento `View` che definisce una visualizzazione tabella per l'oggetto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .

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

[Elemento ViewDefinitions (Format)](./viewdefinitions-element-format.md)

[Elemento Name per View (Format)](./name-element-for-view-format.md)

[Elemento ViewSelectedBy (Format)](./viewselectedby-element-format.md)

[Elemento Controls per View (Format)](./controls-element-for-view-format.md)

[Elemento GroupBy per View (Format)](./groupby-element-for-view-format.md)

[Elemento Table ((Format)](./tablecontrol-element-format.md)

[Elemento ListControl (Format)](./listcontrol-element-format.md)

[Elemento WideControl (Format)](./widecontrol-element-format.md)

[Elemento CustomControl (Format)](./customcontrol-element-for-groupby-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
