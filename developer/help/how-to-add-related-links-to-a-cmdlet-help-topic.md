---
title: Come aggiungere collegamenti correlati a un argomento della Guida Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: aa46cbc5bfcfdfec9fcf9d2581ff641baa532860
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855397"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>Come aggiungere collegamenti correlati a un argomento della Guida sui cmdlet

Questa sezione descrive come aggiungere riferimenti ad altro contenuto correlato a un argomento della Guida del cmdlet Windows PowerShell®. Poiché questi riferimenti vengono visualizzati in una finestra di comando, non si collega direttamente per il contenuto di riferimento.

Negli argomenti della Guida cmdlet inclusi in Windows PowerShell®, questi collegamenti fanno riferimento gli altri cmdlet, contenuto concettuale ("About _") e altri documenti e i file della Guida che non sono correlati a Windows PowerShell®.

Il codice XML seguente viene illustrato come aggiungere un nodo RelatedLinks contenente due riferimenti ad argomenti correlati.

```xml
<maml:relatedLinks>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
</ maml:relatedLinks >
```



