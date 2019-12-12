---
title: Elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364070"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a>Elemento CustomEntry per CustomControl per Controls per Configuration (formato)

Fornisce una definizione del controllo comune. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format)

## <a name="syntax"></a>Sintassi

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomEntry`. È necessario specificare gli elementi visualizzati dalla definizione.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Definisce i tipi .NET che usano la definizione del controllo comune o la condizione che deve esistere affinché questo controllo venga usato.|
|[Elemento CustomItem per CustomEntry per i controlli per la configurazione](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Elemento obbligatorio.<br /><br /> Definisce quali dati vengono visualizzati dal controllo e come vengono visualizzati.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntries per CustomControl per Configuration (Format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|Fornisce le definizioni del controllo comune.|

## <a name="remarks"></a>Osservazioni

Nella maggior parte dei casi, è necessaria una sola definizione per ogni controllo personalizzato comune, ma è possibile avere più definizioni se si vuole usare lo stesso controllo per visualizzare oggetti .NET diversi. In questi casi, è possibile specificare una definizione separata per ogni oggetto o set di oggetti.

## <a name="see-also"></a>Vedere anche

[Elemento CustomEntries per CustomControl per Configuration (Format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[Elemento CustomItem per CustomEntry per i controlli per la configurazione](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
