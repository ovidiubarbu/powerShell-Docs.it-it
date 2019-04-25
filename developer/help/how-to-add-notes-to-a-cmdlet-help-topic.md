---
title: Come aggiungere note a un argomento della Guida Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083417"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Come aggiungere note a un argomento della Guida sui cmdlet

Questa sezione descrive come aggiungere una sezione Note per un argomento della Guida del cmdlet Windows PowerShell®. La sezione Note viene utilizzata per spiegare i dettagli che non rientrano nelle altre sezioni strutturati, ad esempio una spiegazione più dettagliata di un parametro. Questo contenuto è stato possibile includere commenti su come il cmdlet funziona con un provider specifico, alcuni utilizzi univoci, ma importanti, del cmdlet o modi per evitare possibili condizioni di errore.

Non sono previsti limiti al numero di note che è possibile aggiungere a una sezione Note. Per ogni nota, aggiungere una coppia di \<maml:alert > tag per il \<maml:alertset > nodo. Il contenuto di ogni nota viene aggiunto all'interno di un set di \<maml: para > tag. Utilizzare zero \<maml: para > tag per la spaziatura.

Il codice XML seguente viene illustrato un \<maml:alertset > nodo con due note. Si noti che ogni nota contiene facoltativo \<maml: Title > tag (titoli possono essere usati per raggruppare una serie di \<maml:alert > tag), e che ogni nota disponga di una riga vuota dopo il contenuto per la spaziatura.

```xml
<maml:alertSet>
  <maml:title>title for Note 1</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
  <maml:title>title for Note 2</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
</maml:alertSet>
```



