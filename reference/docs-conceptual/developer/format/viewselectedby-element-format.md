---
title: Elemento ViewSelectedBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367970"
---
# <a name="viewselectedby-element-format"></a>Elemento ViewSelectedBy (formato)

Definisce gli oggetti .NET visualizzati dalla visualizzazione. Ogni visualizzazione deve specificare almeno un oggetto .NET.

Elemento ViewDefinitions (Format) elemento View (Format) elemento ViewSelectedBy (Format)

## <a name="syntax"></a>Sintassi

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ViewSelectedBy`. Questo elemento deve contenere almeno un elemento figlio `TypeName` o `SelectionSetName`. Non esiste alcun limite al numero di elementi figlio che è possibile specificare, né l'ordine è significativo.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento TypeName per ViewSelectedBy (Format)](./typename-element-for-viewselectedby-format.md)|Elemento facoltativo.<br /><br /> Specifica un oggetto .NET visualizzato dalla visualizzazione.|
|[Elemento SelectionSetName per ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md)|Elemento facoltativo.<br /><br /> Specifica un set di oggetti .NET visualizzati dalla visualizzazione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento View (Format)](./view-element-format.md)|Definisce una vista che visualizza uno o più oggetti .NET.|

## <a name="remarks"></a>Osservazioni

Per ulteriori informazioni sull'utilizzo di questo elemento in visualizzazioni diverse, vedere [componenti di visualizzazione tabella](./creating-a-table-view.md), [componenti di visualizzazione elenco](./creating-a-list-view.md), [componenti di visualizzazione ampia](./creating-a-wide-view.md)e [componenti di controllo personalizzati](./creating-custom-controls.md).

L'elemento `SelectionSetName` viene utilizzato quando il file di formattazione definisce un set di oggetti visualizzati da più visualizzazioni. Per ulteriori informazioni su come definire e fare riferimento ai set di selezione, vedere [definizione di set di oggetti](./defining-selection-sets.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come specificare l'oggetto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) per una visualizzazione elenco. Lo stesso schema viene utilizzato per le visualizzazioni tabella, Wide e Custom.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Creazione di una vista tabella](./creating-a-table-view.md)

[Creazione di una visualizzazione estesa](./creating-a-wide-view.md)

[Creazione di controlli personalizzati](./creating-custom-controls.md)

[Definizione di set di selezione](./defining-selection-sets.md)

[Elemento SelectionSetName per ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md)

[Elemento TypeName (Format)](./typename-element-for-viewselectedby-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
