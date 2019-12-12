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
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="26361-102">Come aggiungere note a un argomento della Guida sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="26361-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="26361-103">Questa sezione descrive come aggiungere una sezione Note a un argomento della guida del cmdlet di® di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="26361-103">This section describes how to add a Notes section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="26361-104">La sezione Note viene utilizzata per illustrare i dettagli che non rientrano facilmente nelle altre sezioni strutturate, ad esempio una spiegazione più dettagliata di un parametro.</span><span class="sxs-lookup"><span data-stu-id="26361-104">The Notes section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="26361-105">Questo contenuto può includere commenti su come funziona il cmdlet con un provider specifico, un oggetto univoco, ma importante, usi del cmdlet o modi per evitare possibili condizioni di errore.</span><span class="sxs-lookup"><span data-stu-id="26361-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="26361-106">Non sono previsti limiti per il numero di note che è possibile aggiungere a una sezione Note.</span><span class="sxs-lookup"><span data-stu-id="26361-106">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="26361-107">Per ogni nota aggiungere una coppia di \<maml: Alert > tag al nodo \<maml: alertt >.</span><span class="sxs-lookup"><span data-stu-id="26361-107">For each note, add a pair of \<maml:alert> tags to the \<maml:alertset> node.</span></span> <span data-ttu-id="26361-108">Il contenuto di ogni nota viene aggiunto all'interno di un set di tag \<maml: para >.</span><span class="sxs-lookup"><span data-stu-id="26361-108">The content of each note is added within a set of \<maml:para> tags.</span></span> <span data-ttu-id="26361-109">Usare i tag blank \<maml: para > per la spaziatura.</span><span class="sxs-lookup"><span data-stu-id="26361-109">Use blank \<maml:para> tags for spacing.</span></span>

<span data-ttu-id="26361-110">Il codice XML seguente mostra un nodo \<maml: alertt > con due note.</span><span class="sxs-lookup"><span data-stu-id="26361-110">The following XML shows an \<maml:alertset> node with two notes.</span></span> <span data-ttu-id="26361-111">Si noti che ogni nota ha un tag facoltativo \<maml: title > (i titoli possono essere usati per raggruppare qualsiasi set di \<maml: Alert > Tags) e che ogni nota ha una riga vuota che segue il contenuto per la spaziatura.</span><span class="sxs-lookup"><span data-stu-id="26361-111">Notice that each note has an optional \<maml:title> tag (titles can be used to group any set of \<maml:alert> tags), and that each note has a blank line following the content for spacing.</span></span>

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



