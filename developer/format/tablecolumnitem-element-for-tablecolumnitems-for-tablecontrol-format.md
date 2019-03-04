---
title: Elemento TableColumnItem per TableColumnItems per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 5d80bdd736ad540f01c5ebc1f3d31dc9bd628ba5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862417"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>Elemento TableColumnItem per TableColumnItems per TableControl (formato)

Definisce le proprietà il cui valore viene visualizzato nella colonna della riga di script.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) TableRowEntries elemento di configurazione per Table (formato) TableRowEntry elemento TableRowEntries per Table (formato) Elemento TableColumnItems per TableControlEntry per Table (formato) TableColumnItem elemento TableColumnItems per Table (formato)

## <a name="syntax"></a>Sintassi

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <SciptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `TableColumnItem` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento Alignment per TableColumnItem per Table (formato)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Definisce la modalità di visualizzazione di dati in una colonna della riga.|
|[Elemento FormatString per TableColumnItem per Table (formato)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|Specifica uno schema di formattazione che consente di formattare i dati della colonna della riga.|
|[Elemento PropertyName per TableColumnItem per Table (formato)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica il nome della proprietà il cui valore viene visualizzato.|
|[Elemento ScriptBlock per TableColumnItem per Table (formato)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script il cui valore viene visualizzato nella colonna di una riga.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableColumnItems per TableControlEntry per Table (formato)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Definisce le proprietà o gli script i cui valori vengono visualizzati nella riga.|

## <a name="remarks"></a>Osservazioni

È possibile specificare una proprietà di un oggetto o uno script in ogni colonna della riga. Se nessun elemento figlio viene specificato, l'elemento è un segnaposto e non vengono visualizzati dati.

Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

Questo esempio viene illustrato un `TableColumnItem` elemento che viene visualizzato il valore della `Status` proprietà del [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto.

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione tabella](./creating-a-table-view.md)

[Elemento Alignment per TableColumnItem per Table (formato)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Elemento TableColumnItems (formato)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[Elemento FormatString per TableColumnItem per Table (formato)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Elemento PropertyName per TableColumnItem per Table (formato)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Elemento ScriptBlock per TableColumnItem per Table (formato)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
