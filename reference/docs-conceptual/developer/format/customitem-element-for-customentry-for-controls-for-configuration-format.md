---
title: Elemento CustomItem per CustomEntry per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364030"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a>Elemento CustomItem per CustomEntry per Controls per Configuration (formato)

Definisce quali dati vengono visualizzati dal controllo e come vengono visualizzati. Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.

Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento CustomItem per CustomEntry per i controlli per la configurazione

## <a name="syntax"></a>Sintassi

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomItem`. Per ulteriori informazioni, vedere la sezione Osservazioni.

### <a name="attributes"></a>Attributi

Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Elemento expressiongroup per CustomItem per i controlli per la configurazione (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Definisce i dati visualizzati dal controllo.|
|[Elemento frame per CustomItem per i controlli per la configurazione (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Definisce la modalità di visualizzazione dei dati, ad esempio lo spostamento dei dati verso sinistra o verso destra.|
|[Elemento NewLine per CustomItem per i controlli per la configurazione (Format)](./newline-element-for-customitem-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Aggiunge una riga vuota alla visualizzazione del controllo.|
|[Elemento text per CustomItem per i controlli per la configurazione (Format)](./text-element-for-customitem-for-controls-for-configuration-format.md)|Elemento facoltativo.<br /><br /> Aggiunge un testo, ad esempio le parentesi o le parentesi, alla visualizzazione del controllo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Elemento CustomEntry per CustomControl per i controlli per la configurazione (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Fornisce una definizione del controllo.|

## <a name="remarks"></a>Osservazioni

Quando si specificano gli elementi figlio dell'elemento `CustomItem`, tenere presente quanto segue:

- Gli elementi figlio devono essere aggiunti nella sequenza seguente: `ExpressionBinding`, `NewLine`, `Text` e `Frame`.

- Non esiste un limite massimo per il numero di sequenze che è possibile specificare.

- In ogni sequenza non esiste alcun limite massimo per il numero di elementi `ExpressionBinding` che è possibile usare.

## <a name="see-also"></a>Vedere anche

[Elemento expressiongroup per CustomItem per i controlli per la configurazione (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento frame per CustomItem per i controlli per la configurazione (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento NewLine per CustomItem per i controlli per la configurazione (Format)](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento text per CustomItem per i controlli per la configurazione (Format)](./text-element-for-customitem-for-controls-for-configuration-format.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
