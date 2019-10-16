---
title: Stato sessione di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: fa207130bbb120750780bb0aa9b32150a32daaa2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369100"
---
# <a name="windows-powershell-session-state"></a><span data-ttu-id="4eb55-102">Stato della sessione di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4eb55-102">Windows PowerShell Session State</span></span>

<span data-ttu-id="4eb55-103">Stato sessione si riferisce alla configurazione corrente di una sessione o di un modulo di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4eb55-103">Session state refers to the current configuration of a Windows PowerShell session or module.</span></span> <span data-ttu-id="4eb55-104">Una sessione di Windows PowerShell è l'ambiente operativo usato in modo interattivo dall'utente dalla riga di comando o a livello di codice da un'applicazione host.</span><span class="sxs-lookup"><span data-stu-id="4eb55-104">A Windows PowerShell session is the operational environment that is used interactively by the command-line user or programmatically by a host application.</span></span> <span data-ttu-id="4eb55-105">Lo stato della sessione per una sessione viene definito stato sessione globale.</span><span class="sxs-lookup"><span data-stu-id="4eb55-105">The session state for a session is referred to as the global session state.</span></span>

<span data-ttu-id="4eb55-106">Dal punto di vista dello sviluppatore, una sessione di Windows PowerShell si riferisce al tempo che intercorre tra l'apertura di un spazio di Windows PowerShell da parte di un'applicazione host e la chiusura del spazio.</span><span class="sxs-lookup"><span data-stu-id="4eb55-106">From a developer perspective, a Windows PowerShell session refers to the time between when a host application opens a Windows PowerShell runspace and when it closes the runspace.</span></span> <span data-ttu-id="4eb55-107">Osservando un altro modo, la sessione è la durata di un'istanza del motore di Windows PowerShell che viene richiamata mentre è presente spazio.</span><span class="sxs-lookup"><span data-stu-id="4eb55-107">Looked at another way, the session is the lifetime of an instance of the Windows PowerShell engine that is invoked while the runspace exists.</span></span>

## <a name="module-session-state"></a><span data-ttu-id="4eb55-108">Stato sessione modulo</span><span class="sxs-lookup"><span data-stu-id="4eb55-108">Module Session State</span></span>

<span data-ttu-id="4eb55-109">Gli Stati della sessione del modulo vengono creati ogni volta che il modulo o uno dei moduli nidificati viene importato nella sessione.</span><span class="sxs-lookup"><span data-stu-id="4eb55-109">Module session states are created whenever the module or one of its nested modules is imported into the session.</span></span> <span data-ttu-id="4eb55-110">Quando un modulo Esporta un elemento, ad esempio un cmdlet, una funzione o uno script, un riferimento a tale elemento viene aggiunto allo stato della sessione globale della sessione.</span><span class="sxs-lookup"><span data-stu-id="4eb55-110">When a module exports an element such as a cmdlet, function, or script, a reference to that element is added to the global session state of the session.</span></span> <span data-ttu-id="4eb55-111">Tuttavia, quando l'elemento viene eseguito, viene eseguito nello stato della sessione del modulo.</span><span class="sxs-lookup"><span data-stu-id="4eb55-111">However, when the element is run, it is executed within the session state of the module.</span></span>

## <a name="session-state-data"></a><span data-ttu-id="4eb55-112">Dati dello stato sessione</span><span class="sxs-lookup"><span data-stu-id="4eb55-112">Session-State Data</span></span>

<span data-ttu-id="4eb55-113">I dati relativi allo stato della sessione possono essere pubblici o privati.</span><span class="sxs-lookup"><span data-stu-id="4eb55-113">Session state data can be public or private.</span></span> <span data-ttu-id="4eb55-114">I dati pubblici sono disponibili per le chiamate dall'esterno dello stato della sessione mentre i dati privati sono disponibili solo per le chiamate dall'interno dello stato della sessione.</span><span class="sxs-lookup"><span data-stu-id="4eb55-114">Public data is available to calls from outside the session state while private data is available only to calls from within the session state.</span></span> <span data-ttu-id="4eb55-115">Un modulo, ad esempio, può avere una funzione privata che può essere chiamata solo dal modulo o solo internamente da un elemento pubblico che è stato esportato.</span><span class="sxs-lookup"><span data-stu-id="4eb55-115">For example, a module can have a private function that can be called only by the module or only internally by a public element that has been exported.</span></span> <span data-ttu-id="4eb55-116">Questa operazione è simile ai membri privati e pubblici di un tipo di .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4eb55-116">This is similar to the private and public members of a .NET Framework type.</span></span>

<span data-ttu-id="4eb55-117">I dati relativi allo stato sessione vengono archiviati dall'istanza corrente del motore di esecuzione all'interno del contesto della sessione corrente di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4eb55-117">Session-state data is stored by the current instance of the execution engine within the context of the current Windows PowerShell session.</span></span> <span data-ttu-id="4eb55-118">I dati relativi allo stato sessione sono costituiti dagli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="4eb55-118">Session-state data consists of the following items:</span></span>

- <span data-ttu-id="4eb55-119">Informazioni sul percorso</span><span class="sxs-lookup"><span data-stu-id="4eb55-119">Path information</span></span>

- <span data-ttu-id="4eb55-120">Informazioni sull'unità</span><span class="sxs-lookup"><span data-stu-id="4eb55-120">Drive information</span></span>

- <span data-ttu-id="4eb55-121">Informazioni sul provider di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4eb55-121">Windows PowerShell provider information</span></span>

- <span data-ttu-id="4eb55-122">Informazioni sui moduli importati e i riferimenti agli elementi del modulo (ad esempio cmdlet, funzioni e script) esportati dal modulo.</span><span class="sxs-lookup"><span data-stu-id="4eb55-122">Information about the imported modules and references to the module elements (such as cmdlets, functions, and scripts) that are exported by the module.</span></span> <span data-ttu-id="4eb55-123">Queste informazioni e questi riferimenti sono solo per lo stato della sessione globale.</span><span class="sxs-lookup"><span data-stu-id="4eb55-123">This information and these references are for the global session state only.</span></span>

- <span data-ttu-id="4eb55-124">Informazioni sulle variabili dello stato sessione</span><span class="sxs-lookup"><span data-stu-id="4eb55-124">Session-state variable information</span></span>

## <a name="accessing-session-state-data-within-cmdlets"></a><span data-ttu-id="4eb55-125">Accesso ai dati dello stato sessione nei cmdlet</span><span class="sxs-lookup"><span data-stu-id="4eb55-125">Accessing Session-State Data Within Cmdlets</span></span>

<span data-ttu-id="4eb55-126">I cmdlet possono accedere ai dati dello stato sessione indirettamente tramite la proprietà [System. Management. Automation. PSCmdlet. SessionState \*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) della classe cmdlet o direttamente tramite la classe [System. Management. Automation. SessionState](/dotnet/api/System.Management.Automation.SessionState) .</span><span class="sxs-lookup"><span data-stu-id="4eb55-126">Cmdlets can access session-state data either indirectly through the [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) property of the cmdlet class or directly through the [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class.</span></span> <span data-ttu-id="4eb55-127">La classe [System. Management. Automation. SessionState](/dotnet/api/System.Management.Automation.SessionState) fornisce proprietà che possono essere usate per analizzare diversi tipi di dati relativi allo stato sessione.</span><span class="sxs-lookup"><span data-stu-id="4eb55-127">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class provides properties that can be used to investigate different types of session-state data.</span></span>

## <a name="see-also"></a><span data-ttu-id="4eb55-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4eb55-128">See Also</span></span>

[<span data-ttu-id="4eb55-129">System. Management. Automation. PSCmdlet. SessionState</span><span class="sxs-lookup"><span data-stu-id="4eb55-129">System.Management.Automation.PSCmdlet.Sessionstate</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[<span data-ttu-id="4eb55-130">System. Management. Automation. SessionState? DisplayProperty = FullName</span><span class="sxs-lookup"><span data-stu-id="4eb55-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span></span>](/dotnet/api/System.Management.Automation.SessionState)

[<span data-ttu-id="4eb55-131">Cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4eb55-131">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="4eb55-132">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4eb55-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="4eb55-133">SDK della shell di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4eb55-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
