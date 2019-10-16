---
title: Esercitazione su StopProc | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a142aeb6-9c11-44a0-b34f-1f9470fa347b
caps.latest.revision: 5
ms.openlocfilehash: 27c8e2c7525aba38e69e50b2b7fd3b18b8e54989
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369410"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="26123-102">Esercitazione su StopProc</span><span class="sxs-lookup"><span data-stu-id="26123-102">StopProc Tutorial</span></span>

<span data-ttu-id="26123-103">Questa sezione fornisce un'esercitazione per la creazione del cmdlet Stop-proc, che è molto simile al cmdlet [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) fornito da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="26123-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="26123-104">Questa esercitazione fornisce frammenti di codice che illustrano come vengono implementati i cmdlet e una spiegazione del codice.</span><span class="sxs-lookup"><span data-stu-id="26123-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="26123-105">Argomenti in questa esercitazione</span><span class="sxs-lookup"><span data-stu-id="26123-105">Topics in this Tutorial</span></span>

<span data-ttu-id="26123-106">Gli argomenti di questa esercitazione sono progettati per essere letti in sequenza, con ogni argomento che si basa su ciò che è stato discusso nell'argomento precedente.</span><span class="sxs-lookup"><span data-stu-id="26123-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="26123-107">[Creazione di un cmdlet che modifica il sistema](./creating-a-cmdlet-that-modifies-the-system.md) In questa sezione viene descritto come creare un cmdlet che supporta le modifiche di sistema, ad esempio l'arresto di un processo in esecuzione nel computer.</span><span class="sxs-lookup"><span data-stu-id="26123-107">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="26123-108">[Aggiunta di messaggi utente al cmdlet](./adding-user-messages-to-your-cmdlet.md) In questa sezione viene descritto come aggiungere la possibilità di scrivere messaggi utente, eseguire il debug di messaggi, messaggi di avviso e informazioni sullo stato del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="26123-108">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="26123-109">[Aggiunta di alias, espansione con caratteri jolly e guida ai parametri dei cmdlet](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) In questa sezione viene descritto come creare un cmdlet che supporta gli alias di parametro, la guida e l'espansione con caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="26123-109">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="26123-110">[Aggiunta di set di parametri ai cmdlet](./adding-parameter-sets-to-a-cmdlet.md) In questa sezione viene descritto come aggiungere set di parametri a un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="26123-110">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="26123-111">I set di parametri consentono al cmdlet di funzionare in modo diverso in base ai parametri specificati dall'utente.</span><span class="sxs-lookup"><span data-stu-id="26123-111">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="26123-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="26123-112">See Also</span></span>

[<span data-ttu-id="26123-113">Creazione di un cmdlet che modifica il sistema</span><span class="sxs-lookup"><span data-stu-id="26123-113">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="26123-114">Aggiunta di messaggi utente al cmdlet</span><span class="sxs-lookup"><span data-stu-id="26123-114">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="26123-115">Aggiunta di alias, espansione con caratteri jolly e guida ai parametri dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="26123-115">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="26123-116">Aggiunta di set di parametri ai cmdlet</span><span class="sxs-lookup"><span data-stu-id="26123-116">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="26123-117">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="26123-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
