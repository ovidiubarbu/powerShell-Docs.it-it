---
title: Come aggiungere note a un argomento della guida del cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361270"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Come aggiungere note a un argomento della Guida sui cmdlet

Questa sezione descrive come aggiungere una sezione Note a un argomento della guida del cmdlet di® di Windows PowerShell. La sezione Note viene utilizzata per illustrare i dettagli che non rientrano facilmente nelle altre sezioni strutturate, ad esempio una spiegazione più dettagliata di un parametro. Questo contenuto può includere commenti su come funziona il cmdlet con un provider specifico, un oggetto univoco, ma importante, usi del cmdlet o modi per evitare possibili condizioni di errore.

Non sono previsti limiti per il numero di note che è possibile aggiungere a una sezione Note. Per ogni nota aggiungere una coppia di \<maml: Alert > tag al nodo \<maml: alertt >. Il contenuto di ogni nota viene aggiunto all'interno di un set di tag \<maml: para >. Usare i tag blank \<maml: para > per la spaziatura.

Il codice XML seguente mostra un nodo \<maml: alertt > con due note. Si noti che ogni nota ha un tag facoltativo \<maml: title > (i titoli possono essere usati per raggruppare qualsiasi set di \<maml: Alert > Tags) e che ogni nota ha una riga vuota che segue il contenuto per la spaziatura.

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



