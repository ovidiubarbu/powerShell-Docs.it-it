---
title: Elemento ListEntry per ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065224"
---
# <a name="listentry-element-for-listcontrol-format"></a>Elemento ListEntry per ListControl (formato)

Fornisce una definizione della visualizzazione elenco.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) dell'oggetto ListControl elemento (formato) elemento ListEntries (formato) ListEntry elemento di configurazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ListEntry` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per ListEntry (formato)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Definisce gli oggetti .NET che usano questa definizione di visualizzazione elenco o la condizione che deve essere presente per questa definizione da usare.|
|[Elemento ListItems (formato)](./listitems-element-for-listentry-for-listcontrol-format.md)|Elemento obbligatorio.<br /><br /> Definisce le proprietà e gli script i cui valori vengono visualizzati nella visualizzazione elenco.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ListEntries (formato)](./listentries-element-for-listcontrol-format.md)|Fornisce le definizioni della visualizzazione elenco.|

## <a name="remarks"></a>Osservazioni

Una visualizzazione elenco è un formato di elenco che consente di visualizzare valori di proprietà o script per ogni oggetto. Per altre informazioni sulle visualizzazioni di elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

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

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Elemento EntrySelectedBy per ListEntry (formato)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[Elemento ListEntries (formato)](./listentries-element-for-listcontrol-format.md)

[Elemento ListItems (formato)](./listitems-element-for-listentry-for-listcontrol-format.md)

[La scrittura di un metodo di formattazione di Windows PowerShell e i tipi di File](./writing-a-powershell-formatting-file.md)
