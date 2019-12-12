---
title: Elemento TypeName per ViewSelectedBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361440"
---
# <a name="typename-element-for-viewselectedby-format"></a>Elemento TypeName per ViewSelectedBy (formato)

Specifica un oggetto .NET visualizzato dalla visualizzazione.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ViewSelectedBy (Format) elemento TypeName per ViewSelectedBy (Format)

## <a name="syntax"></a>Sintassi

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre dell'elemento `TypeName`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ViewSelectedBy (Format)](./viewselectedby-element-format.md)|Definisce gli oggetti .NET visualizzati dalla visualizzazione.|

## <a name="text-value"></a>Valore testo

Specificare il nome completo del tipo .NET, ad esempio `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Osservazioni

Per ulteriori informazioni sull'utilizzo di questo elemento in visualizzazioni diverse, vedere [creazione di una visualizzazione tabella](./creating-a-table-view.md), [creazione di una visualizzazione elenco](./creating-a-list-view.md), [creazione di un'ampia visualizzazione](./creating-a-wide-view.md)e [componenti visualizzazione personalizzata](./creating-custom-controls.md).

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

[Elemento ViewSelectedBy (Format)](./viewselectedby-element-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
