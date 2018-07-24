---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Scripting di PowerShell
ms.openlocfilehash: c6ba3abc2544834e2cbec16a524f79399a1d2599
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094052"
---
# <a name="powershell"></a><span data-ttu-id="0d2a4-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="0d2a4-103">PowerShell</span></span>

<span data-ttu-id="0d2a4-104">PowerShell, basato su .NET Framework, è una shell da riga di comando basata su attività nonché un linguaggio di scripting progettato espressamente per consentire agli amministratori di sistema e agli utenti avanzati di automatizzare rapidamente l'amministrazione di più sistemi operativi (Linux, macOS, Unix e Windows) e i processi correlati alle applicazioni eseguite su tali sistemi operativi.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-104">Built on the .NET Framework, PowerShell is a task-based command-line shell and scripting language; it is designed specifically for system administrators and power-users, to rapidly automate the administration of multiple operating systems (Linux, macOS, Unix, and Windows) and the processes related to the applications that run on those operating systems.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="0d2a4-105">PowerShell è open source</span><span class="sxs-lookup"><span data-stu-id="0d2a4-105">PowerShell is open source</span></span>

<span data-ttu-id="0d2a4-106">Il codice open source di base di PowerShell ora è disponibile su GitHub e aperto ai contributi della community.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-106">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="0d2a4-107">Vedere il [codice open source di PowerShell su GitHub](https://github.com/powershell/powershell).</span><span class="sxs-lookup"><span data-stu-id="0d2a4-107">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="0d2a4-108">Per iniziare, è possibile [ottenere PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span><span class="sxs-lookup"><span data-stu-id="0d2a4-108">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="0d2a4-109">In alternativa, è possibile iniziare da una rapida panoramica di [introduzione](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)</span><span class="sxs-lookup"><span data-stu-id="0d2a4-109">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="0d2a4-110">Obiettivi di progettazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="0d2a4-110">PowerShell design goals</span></span>
<span data-ttu-id="0d2a4-111">PowerShell è progettato per migliorare la riga di comando e l'ambiente di scripting eliminando problemi di lunga data e aggiungendo nuove funzionalità.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-111">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="0d2a4-112">Individuabilità</span><span class="sxs-lookup"><span data-stu-id="0d2a4-112">Discoverability</span></span>
<span data-ttu-id="0d2a4-113">È facile individuare le funzionalità di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-113">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="0d2a4-114">Ad esempio, per trovare un elenco dei cmdlet che consentono di visualizzare e modificare i servizi di Windows, digitare:</span><span class="sxs-lookup"><span data-stu-id="0d2a4-114">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="0d2a4-115">Dopo aver individuato il cmdlet che esegue un'attività, è possibile ottenere altre informazioni con il cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-115">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span>
<span data-ttu-id="0d2a4-116">Per visualizzare la Guida per il cmdlet `Get-Service`, ad esempio, digitare:</span><span class="sxs-lookup"><span data-stu-id="0d2a4-116">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```
<span data-ttu-id="0d2a4-117">La maggior parte dei cmdlet genera oggetti che possono essere modificati e di cui è possibile eseguire il rendering in testo per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-117">Most cmdlets emit objects which can be manipulated and then rendered into text for display.</span></span>
<span data-ttu-id="0d2a4-118">Per una migliore comprensione dell'output del cmdlet, inviarne l'output tramite pipe al cmdlet `Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-118">To fully understand the output of that cmdlet, pipe its output to the `Get-Member` cmdlet.</span></span>
<span data-ttu-id="0d2a4-119">Il comando seguente, ad esempio, visualizza informazioni sui membri dell'oggetto restituito dal cmdlet `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-119">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="0d2a4-120">Coerenza</span><span class="sxs-lookup"><span data-stu-id="0d2a4-120">Consistency</span></span>
<span data-ttu-id="0d2a4-121">La gestione dei sistemi può essere un'impresa complicata e gli strumenti con un'interfaccia coerente sono utili per esercitare un maggiore controllo sulla complessità intrinseca.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-121">Managing systems can be a complex endeavor and tools that have a consistent interface help to control the inherent complexity.</span></span>
<span data-ttu-id="0d2a4-122">Sfortunatamente, gli strumenti da riga di comando o gli oggetti COM gestibili tramite script non sono certo noti per la loro coerenza.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-122">Unfortunately, neither command-line tools nor scriptable COM objects have been known for their consistency.</span></span>

<span data-ttu-id="0d2a4-123">La coerenza di PowerShell è una delle sue principali risorse.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-123">The consistency of PowerShell is one of its primary assets.</span></span>
<span data-ttu-id="0d2a4-124">Ad esempio, dopo aver imparato a usare il cmdlet `Sort-Object`, è possibile usare tali conoscenze per ordinare l'output di qualsiasi cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-124">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span>
<span data-ttu-id="0d2a4-125">Non occorre imparare le diverse routine di ordinamento di ogni cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-125">You do not have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="0d2a4-126">Gli sviluppatori di cmdlet, inoltre, non devono progettare funzionalità di ordinamento per i loro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-126">In addition, cmdlet developers do not have to design sorting features for their cmdlets.</span></span>
<span data-ttu-id="0d2a4-127">PowerShell offre loro un framework che fornisce le funzionalità di base e impone la coerenza per molti aspetti dell'interfaccia.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-127">PowerShell gives them a framework that provides the basic features and forces them to be consistent about many aspects of the interface.</span></span>
<span data-ttu-id="0d2a4-128">Il framework elimina alcune delle scelte che sono in genere compito dello sviluppatore, ma, in cambio, semplifica notevolmente lo sviluppo di cmdlet affidabili e facili da usare.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-128">The framework eliminates some of the choices that are typically left to the developer, but, in return, it makes the development of robust and easy-to-use cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="0d2a4-129">Ambienti interattivi e di scripting</span><span class="sxs-lookup"><span data-stu-id="0d2a4-129">Interactive and Scripting Environments</span></span>
<span data-ttu-id="0d2a4-130">PowerShell è un ambiente interattivo e di scripting combinato che offre l'accesso a strumenti da riga di comando e oggetti COM, oltre a consentire l'uso della potente libreria di classi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-130">PowerShell is a combined interactive and scripting environment that gives you access to command-line tools and COM objects, and also enables you to use the power of the .NET Framework Class Library (FCL).</span></span>

<span data-ttu-id="0d2a4-131">Questo ambiente rappresenta un miglioramento del prompt dei comandi Windows, che rende disponibile un ambiente interattivo con più strumenti da riga di comando.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-131">This environment improves upon the Windows Command Prompt, which provides an interactive environment with multiple command-line tools.</span></span>
<span data-ttu-id="0d2a4-132">Si tratta di un miglioramento anche rispetto agli script di Windows Script Host (WSH), che consentono di usare più strumenti da riga di comando e oggetti di automazione COM, ma non offrono un ambiente interattivo.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-132">It also improves upon Windows Script Host (WSH) scripts, which let you use multiple command-line tools and COM automation objects, but do not provide an interactive environment.</span></span>

<span data-ttu-id="0d2a4-133">Combinando l'accesso a tutte queste funzionalità, PowerShell amplia le potenzialità dell'utente interattivo e dell'autore di script, oltre a rendere più gestibile l'amministrazione del sistema.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-133">By combining access to all of these features, PowerShell extends the ability of the interactive user and the script writer, and makes system administration more manageable.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="0d2a4-134">Orientamento agli oggetti</span><span class="sxs-lookup"><span data-stu-id="0d2a4-134">Object Orientation</span></span>
<span data-ttu-id="0d2a4-135">Sebbene le interazioni con PowerShell avvengano tramite la digitazione di comandi testuali, PowerShell è basato su oggetti e non sul testo.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-135">Although you interact with PowerShell by typing commands in text, PowerShell is based on objects, not text.</span></span>
<span data-ttu-id="0d2a4-136">L'output di un comando è un oggetto.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-136">The output of a command is an object.</span></span>
<span data-ttu-id="0d2a4-137">È possibile inviare l'oggetto di output a un altro comando come input.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-137">You can send the output object to another command as its input.</span></span>
<span data-ttu-id="0d2a4-138">Di conseguenza, PowerShell offre un'interfaccia familiare agli utenti esperti di altre shell, introducendo allo stesso tempo un paradigma di riga di comando nuovo e potente.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-138">As a result, PowerShell provides a familiar interface to people experienced with other shells, while introducing a new and powerful command-line paradigm.</span></span>
<span data-ttu-id="0d2a4-139">Estende il concetto di invio dei dati tra i comandi grazie alla possibilità di inviare oggetti invece di testo.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-139">It extends the concept of sending data between commands by enabling you to send objects, rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="0d2a4-140">Facile transizione verso la creazione di script</span><span class="sxs-lookup"><span data-stu-id="0d2a4-140">Easy Transition to Scripting</span></span>
<span data-ttu-id="0d2a4-141">Con PowerShell è facile passare dalla digitazione interattiva di comandi alla creazione ed esecuzione di script.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-141">PowerShell makes it easy to transition from typing commands interactively to creating and running scripts.</span></span>
<span data-ttu-id="0d2a4-142">È possibile digitare i comandi al prompt dei comandi di PowerShell per individuare i comandi che eseguono un'attività.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-142">You can type commands at the PowerShell command prompt to discover the commands that perform a task.</span></span>
<span data-ttu-id="0d2a4-143">Questi comandi possono essere poi salvati in una trascrizione o una cronologia prima di copiarli in un file per l'uso come script.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-143">Then, you can save those commands in a transcript or a history before copying them to a file for use as a script.</span></span>
