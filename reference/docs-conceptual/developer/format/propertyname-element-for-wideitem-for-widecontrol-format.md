---
title: Elemento PropertyName per WideItem per WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364940"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a>Elemento PropertyName per WideItem per WideControl (formato)

Specifica la proprietà dell'oggetto il cui valore viene visualizzato nella visualizzazione estesa.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) elemento WideItem (Format) PropertyName per WideItem (Format)

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
|[Elemento WideItem (Format)](./wideitem-element-for-widecontrol-format.md)|Definisce la proprietà o lo script il cui valore viene visualizzato nella visualizzazione estesa.|

## <a name="text-value"></a>Valore testo

Consente di specificare il nome della proprietà di cui viene visualizzato il valore.

## <a name="remarks"></a>Osservazioni

Per ulteriori informazioni sui componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).

## <a name="example"></a>Esempio

Questo esempio mostra una visualizzazione estesa che Visualizza il valore della proprietà ProcessName dell'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a>Vedere anche

[Elemento WideItem (Format)](./wideitem-element-for-widecontrol-format.md)

[Creazione di una visualizzazione estesa](./creating-a-wide-view.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
