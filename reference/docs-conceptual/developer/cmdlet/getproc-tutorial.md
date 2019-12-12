---
title: Esercitazione getproc | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364440"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="f8a92-102">Esercitazione su GetProc</span><span class="sxs-lookup"><span data-stu-id="f8a92-102">GetProc Tutorial</span></span>

<span data-ttu-id="f8a92-103">Questa sezione fornisce un'esercitazione per la creazione di un cmdlet Get-proc molto simile al cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) fornito da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f8a92-103">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="f8a92-104">Questa esercitazione fornisce frammenti di codice che illustrano come vengono implementati i cmdlet e una spiegazione del codice.</span><span class="sxs-lookup"><span data-stu-id="f8a92-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="f8a92-105">Argomenti in questa esercitazione</span><span class="sxs-lookup"><span data-stu-id="f8a92-105">Topics in this Tutorial</span></span>

<span data-ttu-id="f8a92-106">Gli argomenti di questa esercitazione sono progettati per essere letti in sequenza, con ogni argomento che si basa su ciò che è stato discusso nell'argomento precedente.</span><span class="sxs-lookup"><span data-stu-id="f8a92-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="f8a92-107">[Creazione di un cmdlet senza parametri](./creating-a-cmdlet-without-parameters.md) In questa sezione viene descritto come creare un cmdlet che recupera le informazioni dal computer locale senza l'utilizzo di parametri e quindi scrive le informazioni nella pipeline.</span><span class="sxs-lookup"><span data-stu-id="f8a92-107">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="f8a92-108">[Aggiunta di parametri che elaborano l'input della riga di comando](./adding-parameters-that-process-command-line-input.md) Questa sezione descrive come aggiungere un parametro al cmdlet Get-proc in modo che il cmdlet possa elaborare l'input in base a oggetti espliciti passati al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f8a92-108">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="f8a92-109">L'implementazione descritta qui recupera i processi in base al nome e quindi scrive le informazioni nella pipeline.</span><span class="sxs-lookup"><span data-stu-id="f8a92-109">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="f8a92-110">[Aggiunta di parametri che elaborano l'input della pipeline](./adding-parameters-that-process-pipeline-input.md) Questa sezione descrive come aggiungere un parametro al cmdlet Get-proc, in modo che il cmdlet possa elaborare gli oggetti passati tramite la pipeline.</span><span class="sxs-lookup"><span data-stu-id="f8a92-110">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="f8a92-111">Il cmdlet di implementazione descritto di seguito recupera i processi in base agli oggetti passati al cmdlet e quindi scrive le informazioni nella pipeline.</span><span class="sxs-lookup"><span data-stu-id="f8a92-111">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="f8a92-112">[Aggiunta della segnalazione errori non fatale al cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) In questa sezione viene descritto come aggiungere una segnalazione errori non fatale a un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f8a92-112">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="f8a92-113">L'implementazione descritta qui rileva gli errori non fatali che si verificano durante l'elaborazione dell'input e scrive un record di errore nel flusso di errori.</span><span class="sxs-lookup"><span data-stu-id="f8a92-113">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8a92-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f8a92-114">See Also</span></span>

[<span data-ttu-id="f8a92-115">Creazione di un cmdlet senza parametri</span><span class="sxs-lookup"><span data-stu-id="f8a92-115">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="f8a92-116">Aggiunta di parametri che elaborano l'input della riga di comando</span><span class="sxs-lookup"><span data-stu-id="f8a92-116">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="f8a92-117">Aggiunta di parametri che elaborano l'input della pipeline</span><span class="sxs-lookup"><span data-stu-id="f8a92-117">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="f8a92-118">Aggiunta della segnalazione errori non fatale al cmdlet</span><span class="sxs-lookup"><span data-stu-id="f8a92-118">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="f8a92-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f8a92-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
