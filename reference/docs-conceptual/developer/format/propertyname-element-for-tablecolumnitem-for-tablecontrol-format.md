---
title: Elemento PropertyName per TableColumnItem per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362250"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a>Elemento PropertyName per TableColumnItem per TableControl (formato)

Specifica la proprietà il cui valore viene visualizzato nella colonna della riga.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) elemento TableColumnItems (Format) elemento TableColumnItem (Format) Elemento PropertyName per TableColumnItem (Format)

## <a name="syntax"></a>Sintassi

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `PropertyName`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableColumnItem (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Definisce la proprietà o lo script il cui valore viene visualizzato nella colonna della riga.|

## <a name="text-value"></a>Valore testo

Consente di specificare il nome della proprietà di cui viene visualizzato il valore.

## <a name="remarks"></a>Osservazioni

Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

Questo esempio illustra un elemento `TableColumnItem` che specifica la proprietà `Status` dell'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Vedere anche

[Creazione di una vista tabella](./creating-a-table-view.md)

[Elemento TableColumnItem (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
