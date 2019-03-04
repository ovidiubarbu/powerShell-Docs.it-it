---
title: Concetti di Cmdlet di PowerShell di Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b3ef3f4-c626-4679-884f-406a37412b3e
caps.latest.revision: 16
ms.openlocfilehash: 2f84c57da7429462c69b2a020d9f8ac04f8d0f35
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855787"
---
# <a name="windows-powershell-cmdlet-concepts"></a><span data-ttu-id="b95ac-102">Concetti dei cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b95ac-102">Windows PowerShell Cmdlet Concepts</span></span>

<span data-ttu-id="b95ac-103">In questa sezione viene descritto il funzionano di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b95ac-103">This section describes how cmdlets work.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b95ac-104">Contenuto della sezione</span><span class="sxs-lookup"><span data-stu-id="b95ac-104">In This Section</span></span>

<span data-ttu-id="b95ac-105">Questa sezione include gli argomenti seguenti.</span><span class="sxs-lookup"><span data-stu-id="b95ac-105">This section includes the following topics.</span></span>

<span data-ttu-id="b95ac-106">[Linee guida sullo sviluppo di cmdlet](./cmdlet-development-guidelines.md) in questo argomento vengono fornite linee guida di sviluppo che possono essere utilizzate per produrre i cmdlet in formato corretto.</span><span class="sxs-lookup"><span data-stu-id="b95ac-106">[Cmdlet Development Guidelines](./cmdlet-development-guidelines.md) This topic provides development guidelines that can be used to produce well-formed cmdlets.</span></span>

<span data-ttu-id="b95ac-107">[Dichiarazione di classe cmdlet](./cmdlet-class-declaration.md) in questo argomento descrive la dichiarazione di classe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b95ac-107">[Cmdlet Class Declaration](./cmdlet-class-declaration.md) This topic describes cmdlet class declaration.</span></span>

<span data-ttu-id="b95ac-108">[Approvato verbi per Windows PowerShell i comandi](./approved-verbs-for-windows-powershell-commands.md) in questo argomento elenca i verbi di cmdlet predefiniti che è possibile usare quando si dichiara una classe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b95ac-108">[Approved Verbs for Windows PowerShell Commands](./approved-verbs-for-windows-powershell-commands.md) This topic lists the predefined cmdlet verbs that you can use when you declare a cmdlet class.</span></span>

<span data-ttu-id="b95ac-109">[I metodi di elaborazione Input cmdlet](./cmdlet-input-processing-methods.md) in questo argomento vengono descritti i metodi che consentono un cmdlet per eseguire operazioni di pre-elaborazione, le operazioni di elaborazione di input e registra le operazioni di elaborazione.</span><span class="sxs-lookup"><span data-stu-id="b95ac-109">[Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md) This topic describes the methods that allow a cmdlet to perform preprocessing operations, input processing operations, and post processing operations.</span></span>

<span data-ttu-id="b95ac-110">[Parametri del cmdlet](./cmdlet-parameters.md) in questa sezione vengono descritti i diversi tipi di parametri che è possibile aggiungere ai cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b95ac-110">[Cmdlet Parameters](./cmdlet-parameters.md) This section describes the different types of parameters that you can add to cmdlets.</span></span>

<span data-ttu-id="b95ac-111">[Gli attributi di cmdlet](./cmdlet-attributes.md) in questa sezione vengono descritti gli attributi che vengono usati per dichiarare le classi di .NET Framework come cmdlet, dichiarare i campi come parametri del cmdlet di dichiarare le regole di convalida dell'input per i parametri.</span><span class="sxs-lookup"><span data-stu-id="b95ac-111">[Cmdlet Attributes](./cmdlet-attributes.md) This section describes the attributes that are used to declare .NET Framework classes as cmdlets, to declare fields as cmdlet parameters, and to declare input validation rules for parameters.</span></span>

<span data-ttu-id="b95ac-112">[Alias di cmdlet](./cmdlet-aliases.md) in questo argomento descrive gli alias di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b95ac-112">[Cmdlet Aliases](./cmdlet-aliases.md) This topic describes cmdlet aliases.</span></span>

<span data-ttu-id="b95ac-113">[Output del cmdlet](./cmdlet-output.md) in questa sezione descrive il tipo di output che possono restituire i cmdlet e su come definire e visualizzare gli oggetti restituiti dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b95ac-113">[Cmdlet Output](./cmdlet-output.md) This section describes the type of output that cmdlets can return and how to define and display the objects that are returned by cmdlets.</span></span>

<span data-ttu-id="b95ac-114">[La registrazione di cmdlet](./modules-and-snap-ins.md) in questa sezione viene descritto come registrare i cmdlet di utilizzando moduli e snap-in.</span><span class="sxs-lookup"><span data-stu-id="b95ac-114">[Registering Cmdlets](./modules-and-snap-ins.md) This section describes how to register cmdlets by using modules and snap-ins.</span></span>

<span data-ttu-id="b95ac-115">[Richiesta di conferma](./requesting-confirmation-from-cmdlets.md) in questa sezione descrive come i cmdlet di richiedono conferma da un utente prima di apportare una modifica al sistema.</span><span class="sxs-lookup"><span data-stu-id="b95ac-115">[Requesting Confirmation](./requesting-confirmation-from-cmdlets.md) This section describes how cmdlets request confirmation from a user before they make a change to the system.</span></span>

<span data-ttu-id="b95ac-116">[Segnalazione errori Windows PowerShell](./error-reporting-concepts.md) in questa sezione descrive come i cmdlet di segnalano gli errori irreversibili e gli errori non fatali e descrive come interpretare i record di errore.</span><span class="sxs-lookup"><span data-stu-id="b95ac-116">[Windows PowerShell Error Reporting](./error-reporting-concepts.md) This section describes how cmdlets report terminating errors and non-terminating errors, and it describes how to interpret error records.</span></span>

<span data-ttu-id="b95ac-117">[I processi in background](./background-jobs.md) in questo argomento viene descritto come i cmdlet possono eseguire le proprie attività all'interno dei processi in background che non interferiscono con i comandi che sono in esecuzione nella sessione corrente.</span><span class="sxs-lookup"><span data-stu-id="b95ac-117">[Background Jobs](./background-jobs.md) This topic describes how cmdlets can perform their work within background jobs that do not interfere with the commands that are executing in the current session.</span></span>

<span data-ttu-id="b95ac-118">[Richiamare i cmdlet e gli script all'interno di un Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) in questo argomento viene descritto come i cmdlet possono richiamare altri cmdlet e script all'interno i metodi di elaborazione dell'input.</span><span class="sxs-lookup"><span data-stu-id="b95ac-118">[Invoking Cmdlets and Scripts Within a Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) This topic describes how cmdlets can invoke other cmdlets and scripts from within their input processing methods.</span></span>

<span data-ttu-id="b95ac-119">[Cmdlet imposta](./cmdlet-sets.md) in questo argomento viene descritto l'utilizzo di classi di base per creare set di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b95ac-119">[Cmdlet Sets](./cmdlet-sets.md) This topic describes using base classes to create sets of cmdlets.</span></span>

<span data-ttu-id="b95ac-120">[Lo stato della sessione di Windows PowerShell](./windows-powershell-session-state.md) in questo argomento descrive lo stato della sessione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b95ac-120">[Windows PowerShell Session State](./windows-powershell-session-state.md) This topic describes Windows PowerShell session state.</span></span>
