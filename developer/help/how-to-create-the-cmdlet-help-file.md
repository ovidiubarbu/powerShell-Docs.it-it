---
title: Come creare il File della Guida dei Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083247"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="0ba98-102">Come creare il file della Guida sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="0ba98-102">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="0ba98-103">Questa sezione descrive come creare un file XML valido che include contenuto per gli argomenti della Guida di cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0ba98-103">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="0ba98-104">In questa sezione viene illustrato come denominare il file della Guida, come aggiungere le intestazioni appropriate XML e come aggiungere nodi che conterranno le diverse sezioni del contenuto della Guida cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ba98-104">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="0ba98-105">Per una panoramica completa di un file della Guida, aprire un file dll Help.xml che si trova nella directory di installazione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0ba98-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="0ba98-106">Ad esempio, il file Microsoft.PowerShell.Commands.Management.dll Help.xml contiene contenuto per molti dei cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0ba98-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="0ba98-107">Come creare un File della Guida dei Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0ba98-107">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="0ba98-108">Creare un file di testo e salvarlo con codifica UTF8.</span><span class="sxs-lookup"><span data-stu-id="0ba98-108">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="0ba98-109">Il nome del file deve essere nel formato seguente, in modo che Windows PowerShell può rilevare come un file della Guida.</span><span class="sxs-lookup"><span data-stu-id="0ba98-109">The file name must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. <span data-ttu-id="0ba98-110">Aggiungere le intestazioni XML seguente al file di testo.</span><span class="sxs-lookup"><span data-stu-id="0ba98-110">Add the following XML headers to the text file.</span></span> <span data-ttu-id="0ba98-111">Tenere presente che il file verrà convalidato rispetto allo schema del linguaggio di modellazione multi-agente (MAML).</span><span class="sxs-lookup"><span data-stu-id="0ba98-111">Be aware that the file will be validated against the Multi-Agent Modeling Language (MAML) schema.</span></span> <span data-ttu-id="0ba98-112">Attualmente, Windows PowerShell non fornisce alcuno strumento per convalidare il file.</span><span class="sxs-lookup"><span data-stu-id="0ba98-112">Currently, Windows PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. <span data-ttu-id="0ba98-113">Aggiungere un nodo del comando per il file della Guida per ciascun cmdlet nell'assembly.</span><span class="sxs-lookup"><span data-stu-id="0ba98-113">Add a Command node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="0ba98-114">Ogni nodo all'interno del nodo comando mette in relazione a varie sezioni dell'argomento della Guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ba98-114">Each node within the Command node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="0ba98-115">La tabella seguente elenca l'elemento XML per ogni nodo, seguita da una descrizione di ogni nodo.</span><span class="sxs-lookup"><span data-stu-id="0ba98-115">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |<span data-ttu-id="0ba98-116">Node</span><span class="sxs-lookup"><span data-stu-id="0ba98-116">Node</span></span>|<span data-ttu-id="0ba98-117">Description</span><span class="sxs-lookup"><span data-stu-id="0ba98-117">Description</span></span>|
   |----------|-----------------|
   |`<details>`|<span data-ttu-id="0ba98-118">Aggiunge contenuto per le sezioni di nome e il riepilogo dell'argomento della Guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ba98-118">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="0ba98-119">Per altre informazioni, vedere [come aggiungere il nome di Cmdlet e il riepilogo](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="0ba98-119">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:description>`|<span data-ttu-id="0ba98-120">Aggiunge contenuto per la sezione Descrizione dell'argomento della Guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ba98-120">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="0ba98-121">Per altre informazioni, vedere [come aggiungere la descrizione dettagliata per un argomento della Guida Cmdlet](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="0ba98-121">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>|
   |`<command:syntax>`|<span data-ttu-id="0ba98-122">Aggiunge contenuto per la sezione relativa alla sintassi dell'argomento della Guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ba98-122">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="0ba98-123">Per altre informazioni, vedere [come aggiungere la sintassi per un argomento della Guida Cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="0ba98-123">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:parameters>`|<span data-ttu-id="0ba98-124">Aggiunge contenuto per la sezione parametri dell'argomento della Guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ba98-124">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="0ba98-125">Per altre informazioni, vedere [come aggiungere parametri a un argomento della Guida Cmdlet](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="0ba98-125">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>|
   |`<command:inputTypes>`|<span data-ttu-id="0ba98-126">Aggiunge il contenuto della sezione di input dell'argomento della Guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ba98-126">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="0ba98-127">Per altre informazioni, vedere [come aggiungere i tipi di Input a un argomento della Guida Cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="0ba98-127">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:returnValues>`|<span data-ttu-id="0ba98-128">Aggiunge il contenuto della sezione di output dell'argomento della Guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ba98-128">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="0ba98-129">Per altre informazioni, vedere [come aggiungere valori restituiti per un argomento della Guida Cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="0ba98-129">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:alertset>`|<span data-ttu-id="0ba98-130">Aggiunge contenuto alla sezione Note dell'argomento della Guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ba98-130">Adds content to the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="0ba98-131">Per altre informazioni, vedere [come aggiungere note per un argomento della Guida Cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="0ba98-131">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:examples>`|<span data-ttu-id="0ba98-132">Aggiunge il contenuto della sezione di esempi dell'argomento della Guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ba98-132">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="0ba98-133">Per altre informazioni, vedere [come esempi di aggiungere un argomento della Guida per Cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="0ba98-133">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:relatedLinks>`|<span data-ttu-id="0ba98-134">Aggiunge il contenuto della sezione collegamenti correlati dell'argomento della Guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ba98-134">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="0ba98-135">Per altre informazioni, vedere [come aggiungere collegamenti correlati a un argomento della Guida Cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="0ba98-135">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>|

## <a name="example"></a><span data-ttu-id="0ba98-136">Esempio</span><span class="sxs-lookup"><span data-stu-id="0ba98-136">Example</span></span>

 <span data-ttu-id="0ba98-137">Di seguito è riportato un esempio di un nodo del comando che include i nodi per le diverse sezioni dell'argomento della Guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ba98-137">Here is an example of a Command node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0ba98-138">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0ba98-138">See Also</span></span>

 [<span data-ttu-id="0ba98-139">Come aggiungere il nome di Cmdlet e riepilogo</span><span class="sxs-lookup"><span data-stu-id="0ba98-139">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0ba98-140">Come aggiungere la descrizione dettagliata per un argomento della Guida del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0ba98-140">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="0ba98-141">Come aggiungere la sintassi per un argomento della Guida del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0ba98-141">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0ba98-142">Come aggiungere parametri a un argomento della Guida del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0ba98-142">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="0ba98-143">Come aggiungere i tipi di Input a un argomento della Guida del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0ba98-143">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0ba98-144">Come aggiungere i valori restituiti per un argomento della Guida del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0ba98-144">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0ba98-145">Come aggiungere note per un argomento della Guida Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0ba98-145">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0ba98-146">Come aggiungere esempi per un argomento della Guida del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0ba98-146">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0ba98-147">Come aggiungere collegamenti correlati a un argomento della Guida del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0ba98-147">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0ba98-148">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0ba98-148">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)