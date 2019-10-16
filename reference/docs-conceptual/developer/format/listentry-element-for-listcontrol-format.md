---
title: Elemento ListEntry per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362750"
---
# <a name="listentry-element-for-listcontrol-format"></a>Elemento ListEntry per ListControl (formato)

Fornisce una definizione della visualizzazione elenco.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format)

## <a name="syntax"></a>Sintassi

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ListEntry`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Definisce gli oggetti .NET che utilizzano questa definizione di visualizzazione elenco o la condizione che deve esistere affinché questa definizione venga utilizzata.|
|[Elemento ListItems (Format)](./listitems-element-for-listentry-for-listcontrol-format.md)|Elemento obbligatorio.<br /><br /> Definisce le proprietà e gli script i cui valori vengono visualizzati dalla visualizzazione elenco.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ListEntries (Format)](./listentries-element-for-listcontrol-format.md)|Fornisce le definizioni della visualizzazione elenco.|

## <a name="remarks"></a>Osservazioni

Una visualizzazione elenco è un formato di elenco che consente di visualizzare i valori delle proprietà o i valori di script per ogni oggetto. Per ulteriori informazioni sulle visualizzazioni elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

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

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Elemento EntrySelectedBy per ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[Elemento ListEntries (Format)](./listentries-element-for-listcontrol-format.md)

[Elemento ListItems (Format)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Scrittura di un file di formattazione e di tipi di Windows PowerShell](./writing-a-powershell-formatting-file.md)
