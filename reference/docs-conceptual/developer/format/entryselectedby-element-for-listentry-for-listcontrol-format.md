---
title: Elemento EntrySelectedBy per ListEntry per ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363830"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>Elemento EntrySelectedBy per ListEntry per ListControl (formato)

Definisce i tipi .NET che utilizzano questa definizione di visualizzazione elenco o la condizione che deve esistere affinché questa definizione venga utilizzata. Nella maggior parte dei casi è necessaria una sola definizione per una visualizzazione elenco. È tuttavia possibile specificare più definizioni per la visualizzazione elenco se si desidera utilizzare la stessa visualizzazione elenco per visualizzare dati diversi per oggetti diversi.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries per ListControl (Format) elemento ListEntry per ListEntry per l'elemento ListControl (Format) EntrySelectedBy per ListEntry per ListControl (formato)

## <a name="syntax"></a>Sintassi

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `EntrySelectedBy`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento SelectionCondition per EntrySelectedBy per ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Definisce la condizione che deve esistere affinché questa definizione di visualizzazione elenco venga utilizzata.|
|[Elemento SelectionSetName per EntrySelectedBy per ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica un set di tipi .NET che utilizzano questa definizione della vista elenco.|
|[Elemento TypeName per EntrySelectedBy per ListControl (Format)](./typename-element-for-entryselectedby-for-listcontrol-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che usa questa definizione di visualizzazione elenco.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento ListEntry per ListControl (Format)](./listentry-element-for-listcontrol-format.md)|Definisce la modalità di visualizzazione delle righe dell'elenco.|

## <a name="remarks"></a>Osservazioni

È necessario specificare almeno un tipo, un set di selezione o una condizione di selezione per una definizione di visualizzazione elenco. Non esiste un limite massimo per il numero di elementi figlio che è possibile usare.

Le condizioni di selezione vengono usate per definire una condizione che deve esistere per la definizione da usare, ad esempio quando un oggetto ha una proprietà specifica o che un valore di proprietà o uno script specifico restituisce `true`. Per ulteriori informazioni sulle condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

Per ulteriori informazioni sui componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come definire gli oggetti per una visualizzazione elenco utilizzando il relativo nome di tipo .NET.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a>Vedere anche

[Elemento ListEntry per ListControl (Format)](./listentry-element-for-listcontrol-format.md)

[Elemento SelectionCondition per EntrySelectedBy per ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Elemento SelectionSetName per EntrySelectedBy per ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Elemento TypeName per EntrySelectedBy per ListControl (Format)](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[Creazione di una visualizzazione elenco](./creating-a-list-view.md)

[Definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
