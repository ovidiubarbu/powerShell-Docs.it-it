---
title: Elemento TableColumnItem per TableColumnItems per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 9e6cffc7476ef01124d95ecbf287d9788b0324c9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368230"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>Elemento TableColumnItem per TableColumnItems per TableControl (formato)

Definisce la proprietà o lo script il cui valore viene visualizzato nella colonna della riga.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries per Table ((Format) elemento TableRowEntry per TableRowEntries per Table ((Format) Elemento TableColumnItems per TableControlEntry per l'elemento TableColumnItem di Table ((Format) per TableColumnItems per Table ((Format)

## <a name="syntax"></a>Sintassi

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `TableColumnItem`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento Alignment per TableColumnItem per Table ((Format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Definisce la modalità di visualizzazione dei dati in una colonna della riga.|
|[Elemento FormatString per TableColumnItem per Table ((Format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|Specifica un modello di formato utilizzato per formattare i dati nella colonna della riga.|
|[Elemento PropertyName per TableColumnItem per Table ((Format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica il nome della proprietà di cui viene visualizzato il valore.|
|[Elemento ScriptBlock per TableColumnItem per Table ((Format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script il cui valore viene visualizzato nella colonna di una riga.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableColumnItems per TableControlEntry per Table ((Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Definisce le proprietà o gli script i cui valori vengono visualizzati nella riga.|

## <a name="remarks"></a>Osservazioni

È possibile specificare una proprietà di un oggetto o di uno script in ogni colonna della riga. Se non vengono specificati elementi figlio, l'elemento è un segnaposto e non viene visualizzato alcun dato.

Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

Questo esempio illustra un elemento `TableColumnItem` che Visualizza il valore della proprietà `Status` dell'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Vedere anche

[Creazione di una vista tabella](./creating-a-table-view.md)

[Elemento Alignment per TableColumnItem per Table ((Format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Elemento TableColumnItems (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[Elemento FormatString per TableColumnItem per Table ((Format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Elemento PropertyName per TableColumnItem per Table ((Format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Elemento ScriptBlock per TableColumnItem per Table ((Format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
