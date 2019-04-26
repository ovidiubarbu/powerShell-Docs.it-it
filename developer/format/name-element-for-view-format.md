---
title: Nome elemento di visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065071"
---
# <a name="name-element-for-view-format"></a>Elemento Name per View (formato)

Specifica il nome utilizzato per identificare la vista.

Configurazione elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento Name (formato)

## <a name="syntax"></a>Sintassi

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Name` elemento. Un solo `Name` l'elemento è consentito per ogni visualizzazione.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento di visualizzazione (formato)](./view-element-format.md)|Definisce una vista che consente di visualizzare i membri di uno o più oggetti .NET.|

## <a name="text-value"></a>Valore di testo

Specificare un nome descrittivo univoco per la visualizzazione. Questo nome può includere un riferimento al tipo della visualizzazione (ad esempio una tabella o una vista elenco), quale oggetto o un set di oggetti di usare la vista, il comando restituisce gli oggetti o una combinazione di questi.

## <a name="remarks"></a>Osservazioni

Per altre informazioni sui diversi tipi di visualizzazioni, vedere gli argomenti seguenti: [Visualizzazione di una tabella](./creating-a-table-view.md), [visualizzazione elenco](./creating-a-list-view.md), [visualizzazione estesa](./creating-a-wide-view.md), e [visualizzazione personalizzata](./creating-custom-controls.md).

## <a name="example"></a>Esempio

L'esempio seguente mostra una `View` elemento che definisce una visualizzazione tabella per il [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) oggetto. Il nome della visualizzazione è "servizio".

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a>Vedere anche

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Creazione di una visualizzazione tabella](./creating-a-table-view.md)

[Creazione di una visualizzazione più ampia](./creating-a-wide-view.md)

[Creazione di controlli personalizzati](./creating-custom-controls.md)

[Elemento di visualizzazione (formato)](./view-element-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
