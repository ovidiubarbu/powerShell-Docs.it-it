---
title: Elemento ViewSelectedBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863187"
---
# <a name="viewselectedby-element-format"></a>Elemento ViewSelectedBy (formato)

Definisce gli oggetti .NET che vengono visualizzati nella visualizzazione. Ogni visualizzazione è necessario specificare almeno un oggetto .NET.

Elemento ViewDefinitions (formato) visualizzazione elemento (formato) ViewSelectedBy elemento (formato)

## <a name="syntax"></a>Sintassi

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `ViewSelectedBy` elemento. Questo elemento deve contenere almeno un `TypeName` o `SelectionSetName` elemento figlio. Non sono previsti limiti al numero di elementi figlio che possono essere specificati né il relativo ordine significativo.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento TypeName per ViewSelectedBy (formato)](./typename-element-for-viewselectedby-format.md)|Elemento facoltativo.<br /><br /> Specifica un oggetto .NET che viene visualizzato nella visualizzazione.|
|[Elemento SelectionSetName per ViewSelectedBy (formato)](./selectionsetname-element-for-viewselectedby-format.md)|Elemento facoltativo.<br /><br /> Specifica un set di oggetti .NET che vengono visualizzati nella visualizzazione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento di visualizzazione (formato)](./view-element-format.md)|Definisce una vista contenente uno o più oggetti .NET.|

## <a name="remarks"></a>Osservazioni

Per altre informazioni sul modo in cui questo elemento viene usato in diverse visualizzazioni, vedere [i componenti di visualizzazione tabella](./creating-a-table-view.md), [i componenti di visualizzazione elenco](./creating-a-list-view.md), [componenti di visualizzazione Wide](./creating-a-wide-view.md)e [Componenti di controllo personalizzato](./creating-custom-controls.md).

Il `SelectionSetName` elemento viene usato quando il file di formattazione definisce un set di oggetti visualizzati da più viste. Per altre informazioni su come i set di selezione vengono definiti e fa riferimento, vedere [definizione imposta di oggetti](./defining-selection-sets.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come specificare il [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) oggetto per una visualizzazione elenco. Lo stesso schema viene utilizzato per le visualizzazioni di tabella, ampia e personalizzati.

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

[Creazione di una visualizzazione tabella](./creating-a-table-view.md)

[Creazione di una visualizzazione più ampia](./creating-a-wide-view.md)

[Creazione di controlli personalizzati](./creating-custom-controls.md)

[La definizione di set di selezione](./defining-selection-sets.md)

[Elemento SelectionSetName per ViewSelectedBy (formato)](./selectionsetname-element-for-viewselectedby-format.md)

[Elemento TypeName (formato)](./typename-element-for-viewselectedby-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
