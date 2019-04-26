---
title: Elemento Alignment per TableColumnHeader per Table (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067009"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a>Elemento Alignment per TableColumnHeader per TableControl (formato)

Definisce la modalità di visualizzazione dati in un'intestazione di colonna.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Table (formato) elemento TableHeaders (formato) elemento TableColumnHeader (formato) allineamento elemento di configurazione per TableColumnHeader (formato)

## <a name="syntax"></a>Sintassi

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `Alignment` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableColumnHeader (formato)](./tablecolumnheader-element-format.md)|Definisce un'etichetta, la larghezza e l'allineamento dei dati per una colonna della tabella.|

## <a name="text-value"></a>Valore di testo

Specificare uno dei valori seguenti. Questi valori non sono tra maiuscole e minuscole.

Se questo elemento non viene specificato, questo Allinea a sinistra i dati visualizzati nella colonna a sinistra è il valore predefinito.

Allinea a destra i dati visualizzati nella colonna a destra.

Centri di centro dati visualizzati nella colonna.

## <a name="remarks"></a>Osservazioni

Per altre informazioni sui componenti di visualizzazione di una tabella, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

Questo esempio viene illustrato un `TableColumnHeader` elemento la cui data è allineato a sinistra.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione tabella](./creating-a-table-view.md)

[Elemento TableColumnHeader (formato)](./tablecolumnheader-element-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
