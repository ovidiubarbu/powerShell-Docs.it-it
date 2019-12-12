---
title: Elemento Alignment per TableColumnHeader per Table ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364380"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a>Elemento Alignment per TableColumnHeader per TableControl (formato)

Definisce la modalità di visualizzazione dei dati in un'intestazione di colonna.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Table ((Format) elemento TableHeaders (Format) elemento TableColumnHeader (Format) elemento Alignment per TableColumnHeader (Format)

## <a name="syntax"></a>Sintassi

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Alignment`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento TableColumnHeader (Format)](./tablecolumnheader-element-format.md)|Definisce un'etichetta, la larghezza e l'allineamento dei dati per una colonna della tabella.|

## <a name="text-value"></a>Valore testo

Specificare uno dei valori seguenti. Questi valori non fanno distinzione tra maiuscole e minuscole.

Left allinea i dati visualizzati nella colonna a sinistra. si tratta del valore predefinito se questo elemento non è specificato.

Allinea a destra i dati visualizzati nella colonna a destra.

Allinea al centro i dati visualizzati nella colonna.

## <a name="remarks"></a>Osservazioni

Per ulteriori informazioni sui componenti di una vista tabella, vedere [creazione di una vista tabella](./creating-a-table-view.md).

## <a name="example"></a>Esempio

Questo esempio mostra un `TableColumnHeader` elemento i cui dati sono allineati a sinistra.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Vedere anche

[Creazione di una vista tabella](./creating-a-table-view.md)

[Elemento TableColumnHeader (Format)](./tablecolumnheader-element-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
