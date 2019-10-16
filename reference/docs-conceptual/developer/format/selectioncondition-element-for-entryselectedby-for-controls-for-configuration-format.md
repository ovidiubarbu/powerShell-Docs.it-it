---
title: Elemento SelectionCondition per EntrySelectedBy per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368450"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a>Elemento SelectionCondition per EntrySelectedBy per Controls per Configuration (formato)

Definisce una condizione che deve esistere per la definizione di un controllo comune da utilizzare. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per i controlli per Configuration (Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (Format) SelectionCondition elemento per EntrySelectedBy per CustomEntry per Configurazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `SelectionCondition`.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento PropertyName per SelectionCondition per i controlli per la configurazione (Format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica una proprietà .NET che attiva la condizione.|
|[Elemento ScriptBlock per SelectionCondition per i controlli per la configurazione (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica lo script che attiva la condizione.|
|[Elemento SelectionSetName per SelectionCondition per i controlli per la configurazione (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica il set di tipi .NET che attiva la condizione.|
|[Elemento TypeName per SelectionCondition per i controlli per la configurazione (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Specifica un tipo .NET che attiva la condizione.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Definisce i tipi .NET che utilizzano questa voce della definizione del controllo comune.|

## <a name="remarks"></a>Osservazioni

Quando si definisce una condizione di selezione, è necessario attenersi alle linee guida seguenti:

- La condizione di selezione deve specificare almeno un nome di proprietà o un blocco di script, ma non è possibile specificarli entrambi.

- La condizione di selezione può specificare un numero qualsiasi di tipi .NET o set di selezione, ma non è possibile specificarli entrambi.

Per ulteriori informazioni sul modo in cui è possibile utilizzare le condizioni di selezione, vedere [definizione delle condizioni per la visualizzazione dei dati](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Vedere anche

[Elemento PropertyName per SelectionCondition per i controlli per la configurazione (Format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elemento ScriptBlock per SelectionCondition per i controlli per la configurazione (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elemento SelectionSetName per SelectionCondition per i controlli per la configurazione (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elemento TypeName per SelectionCondition per i controlli per la configurazione (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elemento EntrySelectedBy per CustomEntry per i controlli per la configurazione (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Scrittura di un file di formattazione e di tipi di Windows PowerShell](./writing-a-powershell-formatting-file.md)
