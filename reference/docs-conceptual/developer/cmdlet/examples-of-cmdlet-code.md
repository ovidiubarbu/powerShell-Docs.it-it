---
title: Esempi di codice cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 936728d64f30a08fb9e2fa9ccef103683594aa3e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364500"
---
# <a name="examples-of-cmdlet-code"></a><span data-ttu-id="f02dc-102">Esempi di codice dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="f02dc-102">Examples of Cmdlet Code</span></span>

<span data-ttu-id="f02dc-103">Questa sezione contiene esempi di codice cmdlet che è possibile usare per iniziare a scrivere cmdlet personalizzati.</span><span class="sxs-lookup"><span data-stu-id="f02dc-103">This section contains examples of cmdlet code that you can use to start writing your own cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f02dc-104">Per istruzioni dettagliate per la scrittura di cmdlet, vedere [esercitazioni per la scrittura di cmdlet](./tutorials-for-writing-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="f02dc-104">If you want step-by-step instructions for writing cmdlets, see [Tutorials for Writing Cmdlets](./tutorials-for-writing-cmdlets.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="f02dc-105">Contenuto della sezione</span><span class="sxs-lookup"><span data-stu-id="f02dc-105">In This Section</span></span>

<span data-ttu-id="f02dc-106">[Come scrivere un semplice cmdlet](./how-to-write-a-simple-cmdlet.md) In questo esempio viene illustrata la struttura di base del codice del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f02dc-106">[How to Write a Simple Cmdlet](./how-to-write-a-simple-cmdlet.md) This example shows the basic structure of cmdlet code.</span></span>

<span data-ttu-id="f02dc-107">[Come dichiarare i parametri dei cmdlet](./how-to-declare-cmdlet-parameters.md) Questo esempio illustra come dichiarare i diversi tipi di parametri.</span><span class="sxs-lookup"><span data-stu-id="f02dc-107">[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md) This example shows how to declare the different types of parameters.</span></span>

<span data-ttu-id="f02dc-108">[Come dichiarare i set di parametri](./how-to-declare-parameter-sets.md) In questo esempio viene illustrato come dichiarare set di parametri che possono modificare l'azione eseguita da un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f02dc-108">[How to Declare Parameter Sets](./how-to-declare-parameter-sets.md) This example shows how to declare sets of parameters that can change the action a cmdlet performs.</span></span>

<span data-ttu-id="f02dc-109">[Come convalidare l'input del parametro](./how-to-validate-parameter-input.md) In questi esempi viene illustrato come convalidare l'input dei parametri.</span><span class="sxs-lookup"><span data-stu-id="f02dc-109">[How to Validate Parameter Input](./how-to-validate-parameter-input.md) These examples show how to validate parameter input.</span></span>

<span data-ttu-id="f02dc-110">[Come dichiarare i parametri dinamici](./how-to-declare-dynamic-parameters.md) Questo esempio illustra come dichiarare un parametro aggiunto in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="f02dc-110">[How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md) This example shows how to declare a parameter that is added at runtime.</span></span>

<span data-ttu-id="f02dc-111">[Come richiamare gli script all'interno di un cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) In questo esempio viene illustrato come richiamare uno script fornito a un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f02dc-111">[How to Invoke Scripts Within a Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) This example shows how to invoke a script that is supplied to a cmdlet.</span></span>

<span data-ttu-id="f02dc-112">[Come eseguire l'override dei metodi di elaborazione dell'input](./how-to-override-input-processing-methods.md) In questi esempi viene illustrata la struttura di base utilizzata per eseguire l'override dei metodi BeginProcessing, ProcessRecord e EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="f02dc-112">[How To Override Input Processing Methods](./how-to-override-input-processing-methods.md) These examples show the basic structure used to override the BeginProcessing, ProcessRecord, and EndProcessing methods.</span></span>

<span data-ttu-id="f02dc-113">[Come supportare le chiamate ShouldProcess](./how-to-request-confirmations.md) Questo esempio illustra il modo in cui i metodi [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) devono essere chiamati dall'interno di un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f02dc-113">[How to Support ShouldProcess Calls](./how-to-request-confirmations.md) This example shows how the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods should be called from within a cmdlet.</span></span>

<span data-ttu-id="f02dc-114">[Come supportare le transazioni](./how-to-support-transactions.md) In questo esempio viene illustrato come indicare che il cmdlet supporta le transazioni e come implementare l'azione eseguita quando il cmdlet viene utilizzato all'interno di una transazione.</span><span class="sxs-lookup"><span data-stu-id="f02dc-114">[How to Support Transactions](./how-to-support-transactions.md) This example shows how to indicate that the cmdlet supports transactions and how to implement the action that is taken when the cmdlet is used within a transaction.</span></span>

<span data-ttu-id="f02dc-115">[Come supportare i processi](./how-to-support-jobs.md) Questo esempio illustra come supportare i processi quando si scrivono i cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f02dc-115">[How to Support Jobs](./how-to-support-jobs.md) This example shows how to support jobs when you write cmdlets.</span></span>

<span data-ttu-id="f02dc-116">[Come richiamare un cmdlet all'interno di un cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) In questo esempio viene illustrato come richiamare un cmdlet da un altro cmdlet, che consente di aggiungere la funzionalità del cmdlet richiamato al cmdlet che si sta sviluppando.</span><span class="sxs-lookup"><span data-stu-id="f02dc-116">[How to Invoke a Cmdlet From Within a Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span>

## <a name="see-also"></a><span data-ttu-id="f02dc-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f02dc-117">See Also</span></span>

[<span data-ttu-id="f02dc-118">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f02dc-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
