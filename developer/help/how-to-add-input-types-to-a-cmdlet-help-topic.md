---
title: Come aggiungere i tipi di Input a un argomento della Guida Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083434"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="1c2c7-102">Come aggiungere i tipi di input a un argomento della Guida sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="1c2c7-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="1c2c7-103">Questa sezione descrive come aggiungere una sezione input a un argomento della Guida del cmdlet Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="1c2c7-103">This section describes how to add an INPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="1c2c7-104">La sezione input sono elencate le classi .NET di oggetti che il cmdlet accetta come input dalla pipeline, in base al valore o al nome di proprietà.</span><span class="sxs-lookup"><span data-stu-id="1c2c7-104">The INPUTS section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="1c2c7-105">Non sono previsti limiti al numero di classi che è possibile aggiungere a una sezione input.</span><span class="sxs-lookup"><span data-stu-id="1c2c7-105">There is no limit to the number of classes that you can add to an INPUTS section.</span></span> <span data-ttu-id="1c2c7-106">I tipi di input sono racchiusi in un \<comando: inputTypes > nodo, con ogni classe racchiuso tra parentesi un \<comando: inputType > elemento.</span><span class="sxs-lookup"><span data-stu-id="1c2c7-106">The input types are enclosed in a \<command:inputTypes> node, with each class enclosed in a  \<command:inputType> element.</span></span>

<span data-ttu-id="1c2c7-107">Lo schema include due \<maml:description > elementi in ogni \<comando: inputType > elemento.</span><span class="sxs-lookup"><span data-stu-id="1c2c7-107">The schema includes two \<maml:description> elements in each \<command:inputType> element.</span></span> <span data-ttu-id="1c2c7-108">Tuttavia, il `Get-Help` cmdlet visualizza soltanto il contenuto del \<inputType: comando > /\<maml:description >) elemento.</span><span class="sxs-lookup"><span data-stu-id="1c2c7-108">However, the `Get-Help` cmdlet displays only the content of the \<command:inputType>/\<maml:description>) element.</span></span>

<span data-ttu-id="1c2c7-109">A partire da Windows PowerShell 3.0, il `Get-Help` cmdlet consente di visualizzare il contenuto del \<navigationlink > elemento.</span><span class="sxs-lookup"><span data-stu-id="1c2c7-109">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="1c2c7-110">Questo elemento consente di indirizzare gli utenti ad argomenti che descrivono la classe .NET.</span><span class="sxs-lookup"><span data-stu-id="1c2c7-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="1c2c7-111">Il codice XML seguente viene illustrato il \<maml:inputTypes > nodo.</span><span class="sxs-lookup"><span data-stu-id="1c2c7-111">The following XML shows the \<maml:inputTypes> node.</span></span>

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

<span data-ttu-id="1c2c7-112">Il codice XML seguente viene illustrato un esempio dell'uso di \<maml:inputTypes > nodo per documentare un tipo di input.</span><span class="sxs-lookup"><span data-stu-id="1c2c7-112">The following XML shows an example of using the \<maml:inputTypes> node to document an input type.</span></span>

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