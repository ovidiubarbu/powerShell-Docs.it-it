---
title: Esercitazione GetProc | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068097"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="4102a-102">Esercitazione su GetProc</span><span class="sxs-lookup"><span data-stu-id="4102a-102">GetProc Tutorial</span></span>

<span data-ttu-id="4102a-103">In questa sezione fornisce un'esercitazione per la creazione di un cmdlet Get-Process che è molto simile al [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet forniti da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4102a-103">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="4102a-104">Questa esercitazione offre frammenti di codice che illustrano come vengono implementati i cmdlet e la descrizione del codice.</span><span class="sxs-lookup"><span data-stu-id="4102a-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="4102a-105">Negli argomenti di questa esercitazione</span><span class="sxs-lookup"><span data-stu-id="4102a-105">Topics in this Tutorial</span></span>

<span data-ttu-id="4102a-106">Negli argomenti di questa esercitazione sono progettati per essere letti in sequenza, con ogni argomento sulla base di quelle illustrate nell'argomento precedente.</span><span class="sxs-lookup"><span data-stu-id="4102a-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="4102a-107">[Creazione di un Cmdlet senza parametri](./creating-a-cmdlet-without-parameters.md) in questa sezione viene descritto come creare un cmdlet che recupera le informazioni dal computer locale senza l'utilizzo di parametri e quindi scrive le informazioni per la pipeline.</span><span class="sxs-lookup"><span data-stu-id="4102a-107">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="4102a-108">[Aggiunta di parametri di Input della riga di comando tale processo](./adding-parameters-that-process-command-line-input.md) in questa sezione viene descritto come aggiungere un parametro al cmdlet Get-Process in modo che il cmdlet può elaborare l'input in base agli oggetti espliciti passati al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4102a-108">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="4102a-109">L'implementazione descritta qui recupera processi in base al nome e quindi scrive le informazioni per la pipeline.</span><span class="sxs-lookup"><span data-stu-id="4102a-109">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="4102a-110">[Aggiunta di parametri di Input della Pipeline di processo](./adding-parameters-that-process-pipeline-input.md) in questa sezione viene descritto come aggiungere un parametro al cmdlet Get-Process in modo che il cmdlet può elaborare gli oggetti passati a esso tramite la pipeline.</span><span class="sxs-lookup"><span data-stu-id="4102a-110">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="4102a-111">Il cmdlet di implementazione descritto di seguito consente di recuperare i processi in base agli oggetti passati al cmdlet e quindi scrive le informazioni per la pipeline.</span><span class="sxs-lookup"><span data-stu-id="4102a-111">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="4102a-112">[Aggiunta di segnalazione degli errori non fatali al Cmdlet Your](./adding-non-terminating-error-reporting-to-your-cmdlet.md) in questa sezione viene descritto come aggiungere segnalazione a un cmdlet di errori non fatali.</span><span class="sxs-lookup"><span data-stu-id="4102a-112">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="4102a-113">L'implementazione descritta qui rileva errori non fatali che si verificano durante l'elaborazione di input e scrive un record di errore nel flusso di errore.</span><span class="sxs-lookup"><span data-stu-id="4102a-113">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="4102a-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4102a-114">See Also</span></span>

[<span data-ttu-id="4102a-115">Creazione di un Cmdlet senza parametri</span><span class="sxs-lookup"><span data-stu-id="4102a-115">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="4102a-116">Aggiunta di parametri che elaborano gli Input della riga di comando</span><span class="sxs-lookup"><span data-stu-id="4102a-116">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="4102a-117">Aggiunta di parametri di Input della Pipeline di processo</span><span class="sxs-lookup"><span data-stu-id="4102a-117">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="4102a-118">Aggiunta di segnalazione errori non fatali al Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4102a-118">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="4102a-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="4102a-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
