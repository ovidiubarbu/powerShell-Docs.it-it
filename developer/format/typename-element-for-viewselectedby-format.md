---
title: Elemento TypeName per ViewSelectedBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857897"
---
# <a name="typename-element-for-viewselectedby-format"></a>Elemento TypeName per ViewSelectedBy (formato)

Specifica un oggetto .NET che viene visualizzato nella visualizzazione.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento ViewSelectedBy (formato) TypeName elemento di configurazione per ViewSelectedBy (formato)

## <a name="syntax"></a>Sintassi

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Le sezioni seguenti descrivono gli attributi, elementi figlio e gli elementi padre del `TypeName` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ViewSelectedBy (formato)](./viewselectedby-element-format.md)|Definisce gli oggetti .NET che vengono visualizzati nella visualizzazione.|

## <a name="text-value"></a>Valore di testo

Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Osservazioni

Per altre informazioni sul modo in cui questo elemento viene usato in diverse visualizzazioni, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md), [creazione di una visualizzazione elenco](./creating-a-list-view.md), [la creazione di una visualizzazione più ampia](./creating-a-wide-view.md), e [ I componenti di visualizzazione personalizzato](./creating-custom-controls.md).

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

[Elemento ViewSelectedBy (formato)](./viewselectedby-element-format.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
