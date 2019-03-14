---
title: Esercitazione StopProc | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a142aeb6-9c11-44a0-b34f-1f9470fa347b
caps.latest.revision: 5
ms.openlocfilehash: 27c8e2c7525aba38e69e50b2b7fd3b18b8e54989
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794400"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="65e7a-102">Esercitazione su StopProc</span><span class="sxs-lookup"><span data-stu-id="65e7a-102">StopProc Tutorial</span></span>

<span data-ttu-id="65e7a-103">In questa sezione fornisce un'esercitazione per la creazione il cmdlet Stop-Process, che è molto simile al [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet forniti da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="65e7a-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="65e7a-104">Questa esercitazione offre frammenti di codice che illustrano come vengono implementati i cmdlet e la descrizione del codice.</span><span class="sxs-lookup"><span data-stu-id="65e7a-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="65e7a-105">Negli argomenti di questa esercitazione</span><span class="sxs-lookup"><span data-stu-id="65e7a-105">Topics in this Tutorial</span></span>

<span data-ttu-id="65e7a-106">Negli argomenti di questa esercitazione sono progettati per essere letti in sequenza, con ogni argomento sulla base di quelle illustrate nell'argomento precedente.</span><span class="sxs-lookup"><span data-stu-id="65e7a-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="65e7a-107">[Creazione di un Cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md) in questa sezione viene descritto come creare un cmdlet che supporta le modifiche di sistema, ad esempio l'arresto di un processo in esecuzione nel computer.</span><span class="sxs-lookup"><span data-stu-id="65e7a-107">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="65e7a-108">[Aggiunta di messaggi dell'utente al Cmdlet Your](./adding-user-messages-to-your-cmdlet.md) in questa sezione viene descritto come aggiungere la possibilità di scrivere i messaggi dell'utente, i messaggi di debug, i messaggi di avviso e informazioni sullo stato al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="65e7a-108">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="65e7a-109">[Aggiunta di alias di espansione di caratteri jolly e consentono di parametri del Cmdlet](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) in questa sezione viene descritto come creare un cmdlet che supporta gli alias dei parametri, Guida e l'espansione di caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="65e7a-109">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="65e7a-110">[Aggiunta di set di parametri ai cmdlet](./adding-parameter-sets-to-a-cmdlet.md) in questa sezione viene descritto come aggiungere set di parametri a un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="65e7a-110">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="65e7a-111">Set di parametri consentono al cmdlet di operare in base alle quali parametri vengono specificati dall'utente.</span><span class="sxs-lookup"><span data-stu-id="65e7a-111">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="65e7a-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="65e7a-112">See Also</span></span>

[<span data-ttu-id="65e7a-113">Creazione di un Cmdlet che modifichi il sistema</span><span class="sxs-lookup"><span data-stu-id="65e7a-113">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="65e7a-114">Aggiunta di messaggi dell'utente al Cmdlet</span><span class="sxs-lookup"><span data-stu-id="65e7a-114">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="65e7a-115">Aggiunta di alias di espansione di caratteri jolly e consentono di parametri del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="65e7a-115">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="65e7a-116">Aggiunta del parametro imposta ai cmdlet</span><span class="sxs-lookup"><span data-stu-id="65e7a-116">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="65e7a-117">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="65e7a-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
