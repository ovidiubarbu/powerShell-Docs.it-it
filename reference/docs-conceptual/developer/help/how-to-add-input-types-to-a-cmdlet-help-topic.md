---
title: Come aggiungere tipi di input a un argomento della guida del cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361240"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="20eac-102">Come aggiungere i tipi di input a un argomento della Guida sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="20eac-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="20eac-103">Questa sezione descrive come aggiungere una sezione INPUTs a un argomento della Guida di Windows PowerShell® cmdlet.</span><span class="sxs-lookup"><span data-stu-id="20eac-103">This section describes how to add an INPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="20eac-104">La sezione INPUTs elenca le classi .NET di oggetti accettati dal cmdlet come input dalla pipeline, in base al valore o al nome della proprietà.</span><span class="sxs-lookup"><span data-stu-id="20eac-104">The INPUTS section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="20eac-105">Non esiste alcun limite al numero di classi che è possibile aggiungere a una sezione di input.</span><span class="sxs-lookup"><span data-stu-id="20eac-105">There is no limit to the number of classes that you can add to an INPUTS section.</span></span> <span data-ttu-id="20eac-106">I tipi di input sono racchiusi in un nodo \<command: inputTypes >, in cui ogni classe è racchiusa in un elemento \<command: inputType >.</span><span class="sxs-lookup"><span data-stu-id="20eac-106">The input types are enclosed in a \<command:inputTypes> node, with each class enclosed in a  \<command:inputType> element.</span></span>

<span data-ttu-id="20eac-107">Lo schema include due elementi \<maml: Description > in ogni elemento \<command: inputType >.</span><span class="sxs-lookup"><span data-stu-id="20eac-107">The schema includes two \<maml:description> elements in each \<command:inputType> element.</span></span> <span data-ttu-id="20eac-108">Tuttavia, il cmdlet `Get-Help` Visualizza solo il contenuto dell'elemento \<command: inputType >/\<maml: Description >).</span><span class="sxs-lookup"><span data-stu-id="20eac-108">However, the `Get-Help` cmdlet displays only the content of the \<command:inputType>/\<maml:description>) element.</span></span>

<span data-ttu-id="20eac-109">A partire da Windows PowerShell 3,0, il cmdlet `Get-Help` Visualizza il contenuto dell'elemento > \<maml: URI.</span><span class="sxs-lookup"><span data-stu-id="20eac-109">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="20eac-110">Questo elemento consente di indirizzare gli utenti ad argomenti che descrivono la classe .NET.</span><span class="sxs-lookup"><span data-stu-id="20eac-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="20eac-111">Il codice XML seguente mostra il nodo di > \<maml: inputTypes.</span><span class="sxs-lookup"><span data-stu-id="20eac-111">The following XML shows the \<maml:inputTypes> node.</span></span>

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> Class name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Brief description </maml:para>
    </maml:description>
  </command:inputType>
</command:inputTypes>
```

<span data-ttu-id="20eac-112">Nel codice XML seguente viene illustrato un esempio di utilizzo del nodo \<maml: inputTypes > per documentare un tipo di input.</span><span class="sxs-lookup"><span data-stu-id="20eac-112">The following XML shows an example of using the \<maml:inputTypes> node to document an input type.</span></span>

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```