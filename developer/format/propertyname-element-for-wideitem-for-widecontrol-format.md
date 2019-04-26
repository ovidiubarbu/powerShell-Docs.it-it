---
title: Elemento PropertyName per WideItem per WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064646"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a>Elemento PropertyName per WideItem per WideControl (formato)

Specifica la proprietà dell'oggetto il cui valore viene visualizzato in visualizzazione estesa.

Elemento (formato) elemento ViewDefinitions (formato) visualizzazione elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) elemento WideItem (formato) PropertyName elemento di configurazione per WideItem (formato)

## <a name="syntax"></a>Sintassi

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Elementi e attributi

Le sezioni seguenti descrivono gli attributi, elementi figlio ed elemento padre dell'elemento di `PropertyName` elemento.

### <a name="attributes"></a>Attributes

Nessuna.

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento WideItem (formato)](./wideitem-element-for-widecontrol-format.md)|Definisce le proprietà il cui valore viene visualizzato nella vista a livello di script.|

## <a name="text-value"></a>Valore di testo

Specificare il nome della proprietà il cui valore viene visualizzato.

## <a name="remarks"></a>Osservazioni

Per altre informazioni sui componenti di una visualizzazione più ampia, vedere [creazione di una visualizzazione più ampia](./creating-a-wide-view.md).

## <a name="example"></a>Esempio

In questo esempio mostra una visualizzazione più ampia che visualizza il valore della proprietà ProcessName del [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto.

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

[Elemento WideItem (formato)](./wideitem-element-for-widecontrol-format.md)

[Creazione di una visualizzazione più ampia](./creating-a-wide-view.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
