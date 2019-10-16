---
title: Elemento CustomItem per CustomEntry per i controlli per la visualizzazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363940"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>Elemento CustomItem per CustomEntry per Controls per View (formato)

Definisce quali dati vengono visualizzati dal controllo e come vengono visualizzati. Questo elemento viene utilizzato per la definizione di controlli che possono essere utilizzati da una visualizzazione.

Elemento di configurazione (Format) elemento ViewDefinitions (Format) elemento di visualizzazione (Format) controlli elemento (Format) elemento di controllo per i controlli per la visualizzazione (formato) elemento CustomControl per il controllo per i controlli per la visualizzazione (formato) elemento CustomEntries per CustomControl per la visualizzazione (formato) elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (formato) CustomItem elemento per CustomEntry per i controlli per la visualizzazione (formato)

## <a name="syntax"></a>Sintassi

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomItem`. Per ulteriori informazioni, vedere la sezione Osservazioni.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento expressiongroup per CustomItem per i controlli per la visualizzazione (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Definisce i dati visualizzati dal controllo.|
|[Elemento frame per CustomItem per i controlli per la visualizzazione (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra.|
|[Elemento NewLine per CustomItem per i controlli per la visualizzazione (Format)](./newline-element-for-customitem-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Aggiunge una riga vuota alla visualizzazione del controllo.|
|[Elemento text per CustomItem per i controlli per la visualizzazione (Format)](./text-element-for-customitem-for-controls-for-view-format.md)|Elemento facoltativo.<br /><br /> Aggiunge un testo, ad esempio le parentesi o le parentesi, alla visualizzazione del controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntry per CustomEntries per i controlli per la visualizzazione (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Fornisce una definizione del controllo.|

## <a name="remarks"></a>Osservazioni

Quando si specificano gli elementi figlio dell'elemento `CustomItem`, tenere presente quanto segue:

- Gli elementi figlio devono essere aggiunti nella sequenza seguente: `ExpressionBinding`, `NewLine`, `Text` e `Frame`.

- Non esiste un limite massimo per il numero di sequenze che è possibile specificare.

- In ogni sequenza non esiste alcun limite massimo per il numero di elementi `ExpressionBinding` che è possibile usare.

## <a name="see-also"></a>Vedere anche

[Elemento expressiongroup per CustomItem per i controlli per la visualizzazione (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Elemento frame per CustomItem per i controlli per la visualizzazione (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Elemento NewLine per CustomItem per i controlli per la visualizzazione (Format)](./newline-element-for-customitem-for-controls-for-view-format.md)

[Elemento text per CustomItem per i controlli per la visualizzazione (Format)](./text-element-for-customitem-for-controls-for-view-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
