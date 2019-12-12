---
title: Come aggiungere valori restituiti a un argomento della guida del cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: b21811e5a5a819c3d5c4a55fcbe685a84819b71d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367800"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="c7b2e-102">Come aggiungere i tipi di valori restituiti a un argomento della Guida sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="c7b2e-102">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="c7b2e-103">Questa sezione descrive come aggiungere una sezione OUTPUTs a un argomento della guida del cmdlet di® di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c7b2e-103">This section describes how to add an OUTPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="c7b2e-104">Nella sezione output sono elencate le classi .NET di oggetti restituiti dal cmdlet o che passano dalla pipeline.</span><span class="sxs-lookup"><span data-stu-id="c7b2e-104">The OUTPUTS section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="c7b2e-105">Non esiste alcun limite al numero di classi che è possibile aggiungere alla sezione OUTPUTs.</span><span class="sxs-lookup"><span data-stu-id="c7b2e-105">There is no limit to the number of classes that you can add to the OUTPUTS section.</span></span> <span data-ttu-id="c7b2e-106">I tipi restituiti di un cmdlet sono racchiusi in un comando \<: returnValues > nodo, con ogni classe racchiusa in un \<comando: returnValue > elemento.</span><span class="sxs-lookup"><span data-stu-id="c7b2e-106">The return types of a cmdlet are enclosed in a \<command:returnValues> node, with each class enclosed in a \<command:returnValue> element.</span></span>

<span data-ttu-id="c7b2e-107">Se un cmdlet non genera alcun output, utilizzare questa sezione per indicare che non è presente alcun output.</span><span class="sxs-lookup"><span data-stu-id="c7b2e-107">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="c7b2e-108">Ad esempio, al posto del nome della classe, scrivere "None" e fornire una breve spiegazione.</span><span class="sxs-lookup"><span data-stu-id="c7b2e-108">For example, in place of the class name, write "None" and provide a brief explanation.</span></span> <span data-ttu-id="c7b2e-109">Se il cmdlet genera l'output in modo condizionale, usare questo nodo per illustrare le condizioni e descrivere l'output condizionale.</span><span class="sxs-lookup"><span data-stu-id="c7b2e-109">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="c7b2e-110">Lo schema include due elementi \<maml: Description > in ogni comando \<: returnValue > elemento.</span><span class="sxs-lookup"><span data-stu-id="c7b2e-110">The schema includes two \<maml:description> elements in each \<command:returnValue> element.</span></span> <span data-ttu-id="c7b2e-111">Tuttavia, il cmdlet `Get-Help` Visualizza solo il contenuto del comando \<: returnValue >/\<maml: Description > elemento.</span><span class="sxs-lookup"><span data-stu-id="c7b2e-111">However, the `Get-Help` cmdlet displays only the content of the \<command:returnValue>/\<maml:description> element.</span></span>

<span data-ttu-id="c7b2e-112">A partire da Windows PowerShell 3,0, il cmdlet `Get-Help` Visualizza il contenuto dell'elemento > di \<maml: URI.</span><span class="sxs-lookup"><span data-stu-id="c7b2e-112">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="c7b2e-113">Questo elemento consente di indirizzare gli utenti ad argomenti che descrivono la classe .NET.</span><span class="sxs-lookup"><span data-stu-id="c7b2e-113">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="c7b2e-114">Il codice XML seguente mostra il nodo \<maml: returnValues >.</span><span class="sxs-lookup"><span data-stu-id="c7b2e-114">The following XML shows the \<maml:returnValues> node.</span></span>

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> Class Name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
       <maml:para> Brief description <maml:para>

</maml:description>
  </command: returnValue>
</command: returnValues>
```

<span data-ttu-id="c7b2e-115">Nel codice XML seguente viene illustrato un esempio di utilizzo del nodo \<maml: returnValues > per documentare un tipo di output.</span><span class="sxs-lookup"><span data-stu-id="c7b2e-115">The following XML shows an example of using the \<maml:returnValues> node to document an output type.</span></span>

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```



