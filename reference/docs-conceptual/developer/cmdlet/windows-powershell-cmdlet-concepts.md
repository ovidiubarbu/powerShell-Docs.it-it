---
title: Concetti relativi ai cmdlet di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b3ef3f4-c626-4679-884f-406a37412b3e
caps.latest.revision: 16
ms.openlocfilehash: 2f84c57da7429462c69b2a020d9f8ac04f8d0f35
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369120"
---
# <a name="windows-powershell-cmdlet-concepts"></a><span data-ttu-id="31985-102">Concetti dei cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="31985-102">Windows PowerShell Cmdlet Concepts</span></span>

<span data-ttu-id="31985-103">In questa sezione viene descritto il funzionamento di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="31985-103">This section describes how cmdlets work.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="31985-104">Contenuto della sezione</span><span class="sxs-lookup"><span data-stu-id="31985-104">In This Section</span></span>

<span data-ttu-id="31985-105">Questa sezione include gli argomenti seguenti.</span><span class="sxs-lookup"><span data-stu-id="31985-105">This section includes the following topics.</span></span>

<span data-ttu-id="31985-106">[Linee guida per lo sviluppo di cmdlet](./cmdlet-development-guidelines.md) In questo argomento vengono fornite linee guida di sviluppo che possono essere utilizzate per produrre cmdlet ben formati.</span><span class="sxs-lookup"><span data-stu-id="31985-106">[Cmdlet Development Guidelines](./cmdlet-development-guidelines.md) This topic provides development guidelines that can be used to produce well-formed cmdlets.</span></span>

<span data-ttu-id="31985-107">[Dichiarazione di classe cmdlet](./cmdlet-class-declaration.md) Questo argomento descrive la dichiarazione della classe di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="31985-107">[Cmdlet Class Declaration](./cmdlet-class-declaration.md) This topic describes cmdlet class declaration.</span></span>

<span data-ttu-id="31985-108">[Verbi approvati per i comandi di Windows PowerShell](./approved-verbs-for-windows-powershell-commands.md) In questo argomento vengono elencati i verbi dei cmdlet predefiniti che è possibile utilizzare quando si dichiara una classe di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="31985-108">[Approved Verbs for Windows PowerShell Commands](./approved-verbs-for-windows-powershell-commands.md) This topic lists the predefined cmdlet verbs that you can use when you declare a cmdlet class.</span></span>

<span data-ttu-id="31985-109">[Metodi di elaborazione dell'input del cmdlet](./cmdlet-input-processing-methods.md) In questo argomento vengono descritti i metodi che consentono a un cmdlet di eseguire operazioni di pre-elaborazione, operazioni di elaborazione degli input e operazioni post-elaborazione.</span><span class="sxs-lookup"><span data-stu-id="31985-109">[Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md) This topic describes the methods that allow a cmdlet to perform preprocessing operations, input processing operations, and post processing operations.</span></span>

<span data-ttu-id="31985-110">[Parametri dei cmdlet](./cmdlet-parameters.md) In questa sezione vengono descritti i diversi tipi di parametri che è possibile aggiungere ai cmdlet di.</span><span class="sxs-lookup"><span data-stu-id="31985-110">[Cmdlet Parameters](./cmdlet-parameters.md) This section describes the different types of parameters that you can add to cmdlets.</span></span>

<span data-ttu-id="31985-111">[Attributi cmdlet](./cmdlet-attributes.md) In questa sezione vengono descritti gli attributi utilizzati per dichiarare .NET Framework classi come cmdlet, per dichiarare i campi come parametri dei cmdlet e per dichiarare regole di convalida dell'input per i parametri.</span><span class="sxs-lookup"><span data-stu-id="31985-111">[Cmdlet Attributes](./cmdlet-attributes.md) This section describes the attributes that are used to declare .NET Framework classes as cmdlets, to declare fields as cmdlet parameters, and to declare input validation rules for parameters.</span></span>

<span data-ttu-id="31985-112">[Alias di cmdlet](./cmdlet-aliases.md) Questo argomento descrive gli alias di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="31985-112">[Cmdlet Aliases](./cmdlet-aliases.md) This topic describes cmdlet aliases.</span></span>

<span data-ttu-id="31985-113">[Output cmdlet](./cmdlet-output.md) In questa sezione viene descritto il tipo di output che i cmdlet possono restituire e come definire e visualizzare gli oggetti restituiti dai cmdlet.</span><span class="sxs-lookup"><span data-stu-id="31985-113">[Cmdlet Output](./cmdlet-output.md) This section describes the type of output that cmdlets can return and how to define and display the objects that are returned by cmdlets.</span></span>

<span data-ttu-id="31985-114">[Registrazione di cmdlet](./modules-and-snap-ins.md) Questa sezione descrive come registrare i cmdlet usando moduli e snap-in.</span><span class="sxs-lookup"><span data-stu-id="31985-114">[Registering Cmdlets](./modules-and-snap-ins.md) This section describes how to register cmdlets by using modules and snap-ins.</span></span>

<span data-ttu-id="31985-115">[Richiesta di conferma](./requesting-confirmation-from-cmdlets.md) In questa sezione viene descritto in che modo i cmdlet richiedono la conferma da un utente prima di apportare una modifica al sistema.</span><span class="sxs-lookup"><span data-stu-id="31985-115">[Requesting Confirmation](./requesting-confirmation-from-cmdlets.md) This section describes how cmdlets request confirmation from a user before they make a change to the system.</span></span>

<span data-ttu-id="31985-116">[Segnalazione errori di Windows PowerShell](./error-reporting-concepts.md) In questa sezione viene descritto in che modo i cmdlet segnalano gli errori di terminazione e gli errori non fatali e viene descritto come interpretare i record degli errori.</span><span class="sxs-lookup"><span data-stu-id="31985-116">[Windows PowerShell Error Reporting](./error-reporting-concepts.md) This section describes how cmdlets report terminating errors and non-terminating errors, and it describes how to interpret error records.</span></span>

<span data-ttu-id="31985-117">[Processi in background](./background-jobs.md) In questo argomento viene descritto come i cmdlet possono eseguire il proprio lavoro nei processi in background che non interferiscono con i comandi in esecuzione nella sessione corrente.</span><span class="sxs-lookup"><span data-stu-id="31985-117">[Background Jobs](./background-jobs.md) This topic describes how cmdlets can perform their work within background jobs that do not interfere with the commands that are executing in the current session.</span></span>

<span data-ttu-id="31985-118">[Richiamo di cmdlet e script all'interno di un cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) In questo argomento viene descritto in che modo i cmdlet possono richiamare altri cmdlet e script all'interno dei metodi di elaborazione dell'input.</span><span class="sxs-lookup"><span data-stu-id="31985-118">[Invoking Cmdlets and Scripts Within a Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) This topic describes how cmdlets can invoke other cmdlets and scripts from within their input processing methods.</span></span>

<span data-ttu-id="31985-119">[Set di cmdlet](./cmdlet-sets.md) In questo argomento viene descritto l'utilizzo delle classi di base per la creazione di set di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="31985-119">[Cmdlet Sets](./cmdlet-sets.md) This topic describes using base classes to create sets of cmdlets.</span></span>

<span data-ttu-id="31985-120">[Stato sessione di Windows PowerShell](./windows-powershell-session-state.md) Questo argomento descrive lo stato della sessione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="31985-120">[Windows PowerShell Session State](./windows-powershell-session-state.md) This topic describes Windows PowerShell session state.</span></span>
