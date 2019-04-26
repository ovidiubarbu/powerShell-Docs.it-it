---
title: Lo stato della sessione di Windows PowerShell | Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066975"
---
# <a name="windows-powershell-session-state"></a><span data-ttu-id="10d64-102">Stato della sessione di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="10d64-102">Windows PowerShell Session State</span></span>

<span data-ttu-id="10d64-103">Lo stato della sessione si riferisce alla configurazione corrente di una sessione di Windows PowerShell o un modulo.</span><span class="sxs-lookup"><span data-stu-id="10d64-103">Session state refers to the current configuration of a Windows PowerShell session or module.</span></span> <span data-ttu-id="10d64-104">Una sessione di Windows PowerShell è l'ambiente operativo che viene usato in modo interattivo dall'utente della riga di comando o a livello di codice da un'applicazione host.</span><span class="sxs-lookup"><span data-stu-id="10d64-104">A Windows PowerShell session is the operational environment that is used interactively by the command-line user or programmatically by a host application.</span></span> <span data-ttu-id="10d64-105">Lo stato della sessione per una sessione è detto lo stato sessione globale.</span><span class="sxs-lookup"><span data-stu-id="10d64-105">The session state for a session is referred to as the global session state.</span></span>

<span data-ttu-id="10d64-106">Dalla prospettiva dello sviluppatore, una sessione di Windows PowerShell si intende il tempo tra un'applicazione host all'apertura di uno spazio di esecuzione di Windows PowerShell e quando chiude lo spazio di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="10d64-106">From a developer perspective, a Windows PowerShell session refers to the time between when a host application opens a Windows PowerShell runspace and when it closes the runspace.</span></span> <span data-ttu-id="10d64-107">Preso in esame un altro modo, la sessione è la durata di un'istanza del motore di Windows PowerShell che viene richiamato mentre è presente lo spazio di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="10d64-107">Looked at another way, the session is the lifetime of an instance of the Windows PowerShell engine that is invoked while the runspace exists.</span></span>

## <a name="module-session-state"></a><span data-ttu-id="10d64-108">Stato sessione modulo</span><span class="sxs-lookup"><span data-stu-id="10d64-108">Module Session State</span></span>

<span data-ttu-id="10d64-109">Stato dei moduli della sessione viene creati ogni volta che viene importato il modulo o uno dei relativi moduli annidati nella sessione.</span><span class="sxs-lookup"><span data-stu-id="10d64-109">Module session states are created whenever the module or one of its nested modules is imported into the session.</span></span> <span data-ttu-id="10d64-110">Quando un modulo Esporta un elemento, ad esempio un cmdlet, funzione o script, un riferimento a tale elemento viene aggiunto allo stato sessione globale della sessione.</span><span class="sxs-lookup"><span data-stu-id="10d64-110">When a module exports an element such as a cmdlet, function, or script, a reference to that element is added to the global session state of the session.</span></span> <span data-ttu-id="10d64-111">Tuttavia, quando si esegue l'elemento, viene eseguita nello stato della sessione del modulo.</span><span class="sxs-lookup"><span data-stu-id="10d64-111">However, when the element is run, it is executed within the session state of the module.</span></span>

## <a name="session-state-data"></a><span data-ttu-id="10d64-112">Dati dello stato della sessione</span><span class="sxs-lookup"><span data-stu-id="10d64-112">Session-State Data</span></span>

<span data-ttu-id="10d64-113">I dati dello stato della sessione possono essere pubblico o privato.</span><span class="sxs-lookup"><span data-stu-id="10d64-113">Session state data can be public or private.</span></span> <span data-ttu-id="10d64-114">Dati pubblici sono disponibili per le chiamate dall'esterno dello stato della sessione mentre sono disponibili solo per le chiamate da all'interno dello stato della sessione dati privati.</span><span class="sxs-lookup"><span data-stu-id="10d64-114">Public data is available to calls from outside the session state while private data is available only to calls from within the session state.</span></span> <span data-ttu-id="10d64-115">Ad esempio, un modulo può avere una funzione privata che può essere chiamata solo dal modulo o solo internamente da un elemento pubblico che è stato esportato.</span><span class="sxs-lookup"><span data-stu-id="10d64-115">For example, a module can have a private function that can be called only by the module or only internally by a public element that has been exported.</span></span> <span data-ttu-id="10d64-116">È simile ai membri privati e pubblici di un tipo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="10d64-116">This is similar to the private and public members of a .NET Framework type.</span></span>

<span data-ttu-id="10d64-117">Dati dello stato della sessione vengono archiviati per l'istanza corrente del motore di esecuzione all'interno del contesto della sessione di Windows PowerShell corrente.</span><span class="sxs-lookup"><span data-stu-id="10d64-117">Session-state data is stored by the current instance of the execution engine within the context of the current Windows PowerShell session.</span></span> <span data-ttu-id="10d64-118">I dati dello stato della sessione prevede i seguenti elementi:</span><span class="sxs-lookup"><span data-stu-id="10d64-118">Session-state data consists of the following items:</span></span>

- <span data-ttu-id="10d64-119">Informazioni sul percorso</span><span class="sxs-lookup"><span data-stu-id="10d64-119">Path information</span></span>

- <span data-ttu-id="10d64-120">Informazioni sull'unità</span><span class="sxs-lookup"><span data-stu-id="10d64-120">Drive information</span></span>

- <span data-ttu-id="10d64-121">Informazioni sul provider di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="10d64-121">Windows PowerShell provider information</span></span>

- <span data-ttu-id="10d64-122">Informazioni sui moduli importati e i riferimenti agli elementi di modulo (ad esempio cmdlet, funzioni e script) che vengono esportati dal modulo.</span><span class="sxs-lookup"><span data-stu-id="10d64-122">Information about the imported modules and references to the module elements (such as cmdlets, functions, and scripts) that are exported by the module.</span></span> <span data-ttu-id="10d64-123">Queste informazioni e questi riferimenti sono per solo lo stato sessione globale.</span><span class="sxs-lookup"><span data-stu-id="10d64-123">This information and these references are for the global session state only.</span></span>

- <span data-ttu-id="10d64-124">Informazioni sulle variabili dello stato della sessione</span><span class="sxs-lookup"><span data-stu-id="10d64-124">Session-state variable information</span></span>

## <a name="accessing-session-state-data-within-cmdlets"></a><span data-ttu-id="10d64-125">L'accesso ai dati dello stato sessione all'interno di cmdlet</span><span class="sxs-lookup"><span data-stu-id="10d64-125">Accessing Session-State Data Within Cmdlets</span></span>

<span data-ttu-id="10d64-126">I cmdlet possono accedere ai dati dello stato della sessione sia indirettamente tramite il [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) proprietà di classe del cmdlet o direttamente tramite il [ System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) classe.</span><span class="sxs-lookup"><span data-stu-id="10d64-126">Cmdlets can access session-state data either indirectly through the [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) property of the cmdlet class or directly through the [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class.</span></span> <span data-ttu-id="10d64-127">Il [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) classe fornisce proprietà che può essere utilizzata per analizzare diversi tipi di dati dello stato della sessione.</span><span class="sxs-lookup"><span data-stu-id="10d64-127">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class provides properties that can be used to investigate different types of session-state data.</span></span>

## <a name="see-also"></a><span data-ttu-id="10d64-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="10d64-128">See Also</span></span>

[<span data-ttu-id="10d64-129">System.Management.Automation.PSCmdlet.Sessionstate</span><span class="sxs-lookup"><span data-stu-id="10d64-129">System.Management.Automation.PSCmdlet.Sessionstate</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[<span data-ttu-id="10d64-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="10d64-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span></span>](/dotnet/api/System.Management.Automation.SessionState)

[<span data-ttu-id="10d64-131">Cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="10d64-131">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="10d64-132">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="10d64-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="10d64-133">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="10d64-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
