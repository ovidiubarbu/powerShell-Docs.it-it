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
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="d81d0-102">Come aggiungere collegamenti correlati a un argomento della Guida sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="d81d0-102">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="d81d0-103">Questa sezione descrive come aggiungere riferimenti ad altro contenuto correlato a un argomento della Guida del cmdlet Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="d81d0-103">This section describes how to add references to other content that is related to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="d81d0-104">Poiché questi riferimenti vengono visualizzati in una finestra di comando, non si collega direttamente per il contenuto di riferimento.</span><span class="sxs-lookup"><span data-stu-id="d81d0-104">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="d81d0-105">Negli argomenti della Guida cmdlet inclusi in Windows PowerShell®, questi collegamenti fanno riferimento gli altri cmdlet, contenuto concettuale ("About _") e altri documenti e i file della Guida che non sono correlati a Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="d81d0-105">In the cmdlet Help topics that are included in Windows PowerShell®, these links reference other cmdlets, conceptual content ("about_"), and other documents and Help files that are not related to Windows PowerShell®.</span></span>

<span data-ttu-id="d81d0-106">Il codice XML seguente viene illustrato come aggiungere un nodo RelatedLinks contenente due riferimenti ad argomenti correlati.</span><span class="sxs-lookup"><span data-stu-id="d81d0-106">The following XML shows how to add a RelatedLinks node that contains two references to related topics.</span></span>

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



