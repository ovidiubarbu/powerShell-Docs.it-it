---
title: Elemento PropertyName per ListItem per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362380"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a>Elemento PropertyName per ListItem per ListControl (formato)

Specifica la proprietà .NET il cui valore viene visualizzato nell'elenco.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento ListItem (Format) elemento ListItem (Format) PropertyName elemento per ListItem (formato)

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
|[Elemento ListItem (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definisce la proprietà o lo script il cui valore viene visualizzato nella riga della visualizzazione elenco.|

## <a name="text-value"></a>Valore testo

Consente di specificare il nome della proprietà di cui viene visualizzato il valore.

## <a name="remarks"></a>Osservazioni

Quando questo elemento viene specificato, non è possibile specificare l'elemento [scriptblock](./scriptblock-element-for-listitem-for-listcontrol-format.md) .

Oltre a visualizzare il valore della proprietà, è anche possibile specificare un'etichetta per il valore o una stringa di formato che può essere utilizzata per modificare la visualizzazione del valore. Per ulteriori informazioni su come specificare i dati in una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come specificare l'etichetta e la proprietà di cui viene visualizzato il valore.

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Vedere anche

[Elemento ScriptBlock per ListItem per ListControl (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Elemento ListItem per ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
