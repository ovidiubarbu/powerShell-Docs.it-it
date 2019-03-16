---
title: Esempi di codice per Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 936728d64f30a08fb9e2fa9ccef103683594aa3e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056261"
---
# <a name="examples-of-cmdlet-code"></a><span data-ttu-id="80e90-102">Esempi di codice dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="80e90-102">Examples of Cmdlet Code</span></span>

<span data-ttu-id="80e90-103">In questa sezione contiene esempi di codice del cmdlet che è possibile utilizzare per iniziare a scrivere cmdlet personalizzati.</span><span class="sxs-lookup"><span data-stu-id="80e90-103">This section contains examples of cmdlet code that you can use to start writing your own cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="80e90-104">Per istruzioni dettagliate per la scrittura di cmdlet, vedere [esercitazioni per la scrittura di cmdlet](./tutorials-for-writing-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="80e90-104">If you want step-by-step instructions for writing cmdlets, see [Tutorials for Writing Cmdlets](./tutorials-for-writing-cmdlets.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="80e90-105">Contenuto della sezione</span><span class="sxs-lookup"><span data-stu-id="80e90-105">In This Section</span></span>

<span data-ttu-id="80e90-106">[Come scrivere un semplice Cmdlet](./how-to-write-a-simple-cmdlet.md) questo esempio illustra la struttura di base di codice del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80e90-106">[How to Write a Simple Cmdlet](./how-to-write-a-simple-cmdlet.md) This example shows the basic structure of cmdlet code.</span></span>

<span data-ttu-id="80e90-107">[Come dichiarare i parametri del Cmdlet](./how-to-declare-cmdlet-parameters.md) in questo esempio viene illustrato come dichiarare i diversi tipi di parametri.</span><span class="sxs-lookup"><span data-stu-id="80e90-107">[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md) This example shows how to declare the different types of parameters.</span></span>

<span data-ttu-id="80e90-108">[Come dichiarare set di parametri](./how-to-declare-parameter-sets.md) in questo esempio viene illustrato come dichiarare set di parametri che è possono modificare l'azione esegue un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80e90-108">[How to Declare Parameter Sets](./how-to-declare-parameter-sets.md) This example shows how to declare sets of parameters that can change the action a cmdlet performs.</span></span>

<span data-ttu-id="80e90-109">[Convalida Input parametro come](./how-to-validate-parameter-input.md) questi esempi illustrano come eseguire la convalida di input del parametro.</span><span class="sxs-lookup"><span data-stu-id="80e90-109">[How to Validate Parameter Input](./how-to-validate-parameter-input.md) These examples show how to validate parameter input.</span></span>

<span data-ttu-id="80e90-110">[Come dichiarare i parametri dinamici](./how-to-declare-dynamic-parameters.md) in questo esempio viene illustrato come dichiarare un parametro che viene aggiunto in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="80e90-110">[How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md) This example shows how to declare a parameter that is added at runtime.</span></span>

<span data-ttu-id="80e90-111">[Come richiamare gli script all'interno di un Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) in questo esempio viene illustrato come richiamare uno script che viene fornito a un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80e90-111">[How to Invoke Scripts Within a Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) This example shows how to invoke a script that is supplied to a cmdlet.</span></span>

<span data-ttu-id="80e90-112">[Come eseguire l'Override di metodi di elaborazione di Input](./how-to-override-input-processing-methods.md) questi esempi illustrano la struttura di base usata per eseguire l'override di metodi BeginProcessing, ProcessRecord ed EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="80e90-112">[How To Override Input Processing Methods](./how-to-override-input-processing-methods.md) These examples show the basic structure used to override the BeginProcessing, ProcessRecord, and EndProcessing methods.</span></span>

<span data-ttu-id="80e90-113">[Come supporto per le chiamate ShouldProcess](./how-to-request-confirmations.md) in questo esempio viene illustrato come il [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodi devono essere chiamati da all'interno di un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80e90-113">[How to Support ShouldProcess Calls](./how-to-request-confirmations.md) This example shows how the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods should be called from within a cmdlet.</span></span>

<span data-ttu-id="80e90-114">[Modalità di supporto delle transazioni](./how-to-support-transactions.md) in questo esempio viene illustrato come indicare che il cmdlet supporta le transazioni e come implementare l'azione da eseguita quando il cmdlet viene usato all'interno di una transazione.</span><span class="sxs-lookup"><span data-stu-id="80e90-114">[How to Support Transactions](./how-to-support-transactions.md) This example shows how to indicate that the cmdlet supports transactions and how to implement the action that is taken when the cmdlet is used within a transaction.</span></span>

<span data-ttu-id="80e90-115">[Come supportare processi](./how-to-support-jobs.md) in questo esempio viene illustrato come supportare i processi quando si scrivono i cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80e90-115">[How to Support Jobs](./how-to-support-jobs.md) This example shows how to support jobs when you write cmdlets.</span></span>

<span data-ttu-id="80e90-116">[Come richiamare un Cmdlet da all'interno di un Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) in questo esempio viene illustrato come richiamare un cmdlet all'interno di un altro cmdlet, che consente di aggiungere la funzionalità del cmdlet richiamato al cmdlet si sta sviluppando.</span><span class="sxs-lookup"><span data-stu-id="80e90-116">[How to Invoke a Cmdlet From Within a Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span>

## <a name="see-also"></a><span data-ttu-id="80e90-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="80e90-117">See Also</span></span>

[<span data-ttu-id="80e90-118">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="80e90-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
