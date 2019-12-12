---
title: Come creare il file della guida del cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361200"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="0b12d-102">Come creare il file della Guida sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="0b12d-102">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="0b12d-103">In questa sezione viene descritto come creare un file XML valido che contiene contenuto per gli argomenti della guida sui cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b12d-103">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="0b12d-104">In questa sezione viene illustrato come assegnare un nome al file della guida, come aggiungere le intestazioni XML appropriate e come aggiungere nodi che conterranno le diverse sezioni del contenuto della guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b12d-104">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="0b12d-105">Per una visualizzazione completa di un file della guida, aprire uno dei file dll-Help. XML che si trovano nella directory di installazione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b12d-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="0b12d-106">Il file Microsoft. PowerShell. Commands. Management. dll-Help. XML, ad esempio, contiene contenuto per diversi cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b12d-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="0b12d-107">Come creare un file della Guida per i cmdlet</span><span class="sxs-lookup"><span data-stu-id="0b12d-107">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="0b12d-108">Creare un file di testo e salvarlo utilizzando la codifica UTF8.</span><span class="sxs-lookup"><span data-stu-id="0b12d-108">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="0b12d-109">Il nome del file deve avere il formato seguente, in modo che Windows PowerShell possa rilevarlo come file della guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b12d-109">The file name must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. <span data-ttu-id="0b12d-110">Aggiungere le intestazioni XML seguenti al file di testo.</span><span class="sxs-lookup"><span data-stu-id="0b12d-110">Add the following XML headers to the text file.</span></span> <span data-ttu-id="0b12d-111">Tenere presente che il file verrà convalidato in base allo schema MAML (multiagent Modeling Language).</span><span class="sxs-lookup"><span data-stu-id="0b12d-111">Be aware that the file will be validated against the Multi-Agent Modeling Language (MAML) schema.</span></span> <span data-ttu-id="0b12d-112">Attualmente, Windows PowerShell non fornisce strumenti per convalidare il file.</span><span class="sxs-lookup"><span data-stu-id="0b12d-112">Currently, Windows PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. <span data-ttu-id="0b12d-113">Aggiungere un nodo del comando al file della guida del cmdlet per ogni cmdlet nell'assembly.</span><span class="sxs-lookup"><span data-stu-id="0b12d-113">Add a Command node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="0b12d-114">Ogni nodo all'interno del nodo Command si riferisce alle diverse sezioni dell'argomento della guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b12d-114">Each node within the Command node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="0b12d-115">La tabella seguente elenca l'elemento XML per ogni nodo, seguito da una descrizione di ogni nodo.</span><span class="sxs-lookup"><span data-stu-id="0b12d-115">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |<span data-ttu-id="0b12d-116">Nodo</span><span class="sxs-lookup"><span data-stu-id="0b12d-116">Node</span></span>|<span data-ttu-id="0b12d-117">Description</span><span class="sxs-lookup"><span data-stu-id="0b12d-117">Description</span></span>|
   |----------|-----------------|
   |`<details>`|<span data-ttu-id="0b12d-118">Aggiunge contenuto per le sezioni nome e riepilogo dell'argomento della guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b12d-118">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="0b12d-119">Per ulteriori informazioni, vedere [come aggiungere il nome del cmdlet e il riepilogo](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="0b12d-119">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:description>`|<span data-ttu-id="0b12d-120">Aggiunge contenuto per la sezione Descrizione dell'argomento della guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b12d-120">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="0b12d-121">Per ulteriori informazioni, vedere [come aggiungere la descrizione dettagliata a un argomento della guida del cmdlet](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="0b12d-121">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>|
   |`<command:syntax>`|<span data-ttu-id="0b12d-122">Aggiunge contenuto per la sezione della sintassi dell'argomento della guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b12d-122">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="0b12d-123">Per ulteriori informazioni, vedere [come aggiungere la sintassi a un argomento della guida del cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="0b12d-123">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:parameters>`|<span data-ttu-id="0b12d-124">Aggiunge contenuto per la sezione PARAMETERS dell'argomento della guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b12d-124">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="0b12d-125">Per ulteriori informazioni, vedere [come aggiungere parametri a un argomento della guida del cmdlet](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="0b12d-125">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>|
   |`<command:inputTypes>`|<span data-ttu-id="0b12d-126">Aggiunge contenuto per la sezione INPUTs dell'argomento della guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b12d-126">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="0b12d-127">Per ulteriori informazioni, vedere [come aggiungere tipi di input a un argomento della guida del cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="0b12d-127">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:returnValues>`|<span data-ttu-id="0b12d-128">Aggiunge contenuto per la sezione OUTPUTs dell'argomento della guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b12d-128">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="0b12d-129">Per ulteriori informazioni, vedere [come aggiungere valori restituiti a un argomento della guida del cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="0b12d-129">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:alertset>`|<span data-ttu-id="0b12d-130">Aggiunge contenuto alla sezione Note dell'argomento della guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b12d-130">Adds content to the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="0b12d-131">Per ulteriori informazioni, vedere [come aggiungere note a un argomento della guida del cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="0b12d-131">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:examples>`|<span data-ttu-id="0b12d-132">Aggiunge contenuto per la sezione degli esempi dell'argomento della guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b12d-132">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="0b12d-133">Per ulteriori informazioni, vedere [come aggiungere esempi a un argomento della guida del cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="0b12d-133">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:relatedLinks>`|<span data-ttu-id="0b12d-134">Aggiunge contenuto per la sezione collegamenti correlati dell'argomento della guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b12d-134">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="0b12d-135">Per ulteriori informazioni, vedere [come aggiungere collegamenti correlati a un argomento della guida del cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="0b12d-135">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>|

## <a name="example"></a><span data-ttu-id="0b12d-136">Esempio</span><span class="sxs-lookup"><span data-stu-id="0b12d-136">Example</span></span>

 <span data-ttu-id="0b12d-137">Di seguito è riportato un esempio di un nodo di comando che include i nodi per le varie sezioni dell'argomento della guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b12d-137">Here is an example of a Command node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a><span data-ttu-id="0b12d-138">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0b12d-138">See Also</span></span>

 [<span data-ttu-id="0b12d-139">Come aggiungere il nome e la sintassi del cmdlet</span><span class="sxs-lookup"><span data-stu-id="0b12d-139">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0b12d-140">Come aggiungere la descrizione dettagliata a un argomento della guida del cmdlet</span><span class="sxs-lookup"><span data-stu-id="0b12d-140">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="0b12d-141">Come aggiungere la sintassi a un argomento della guida del cmdlet</span><span class="sxs-lookup"><span data-stu-id="0b12d-141">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0b12d-142">Come aggiungere parametri a un argomento della guida del cmdlet</span><span class="sxs-lookup"><span data-stu-id="0b12d-142">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="0b12d-143">Come aggiungere tipi di input a un argomento della guida del cmdlet</span><span class="sxs-lookup"><span data-stu-id="0b12d-143">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0b12d-144">Come aggiungere valori restituiti a un argomento della guida del cmdlet</span><span class="sxs-lookup"><span data-stu-id="0b12d-144">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0b12d-145">Come aggiungere note a un argomento della guida del cmdlet</span><span class="sxs-lookup"><span data-stu-id="0b12d-145">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0b12d-146">Come aggiungere esempi a un argomento della guida del cmdlet</span><span class="sxs-lookup"><span data-stu-id="0b12d-146">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0b12d-147">Come aggiungere collegamenti correlati a un argomento della guida del cmdlet</span><span class="sxs-lookup"><span data-stu-id="0b12d-147">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0b12d-148">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0b12d-148">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)