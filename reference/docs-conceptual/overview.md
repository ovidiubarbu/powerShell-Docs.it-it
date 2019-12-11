---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: Scripting di PowerShell
ms.openlocfilehash: 281f2e798b3d3fa1c150b079d633cb7e8490dcec
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "62058489"
---
# <a name="powershell"></a><span data-ttu-id="48df2-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="48df2-103">PowerShell</span></span>

<span data-ttu-id="48df2-104">PowerShell è una shell della riga di comando basata su attività e un linguaggio di scripting basato su .NET.</span><span class="sxs-lookup"><span data-stu-id="48df2-104">PowerShell is a task-based command-line shell and scripting language built on .NET.</span></span>
<span data-ttu-id="48df2-105">PowerShell aiuta gli amministratori di sistema e gli utenti esperti ad automatizzare rapidamente attività che gestiscono i sistemi operativi (Linux, macOS e Windows) e i processi.</span><span class="sxs-lookup"><span data-stu-id="48df2-105">PowerShell helps system administrators and power-users rapidly automate tasks that manage operating systems (Linux, macOS, and Windows) and processes.</span></span>

<span data-ttu-id="48df2-106">I comandi di PowerShell permettono di gestire i computer dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="48df2-106">PowerShell commands let you manage computers from the command line.</span></span> <span data-ttu-id="48df2-107">I provider di PowerShell permettono di accedere ad archivi dati, come il Registro di sistema e l'archivio certificati, con la stessa semplicità con cui si accede al file system.</span><span class="sxs-lookup"><span data-stu-id="48df2-107">PowerShell providers let you access data stores, such as the registry and certificate store, as easily as you access the file system.</span></span> <span data-ttu-id="48df2-108">PowerShell include un parser di espressioni avanzato e un linguaggio di scripting completamente sviluppato.</span><span class="sxs-lookup"><span data-stu-id="48df2-108">PowerShell includes a rich expression parser and a fully developed scripting language.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="48df2-109">PowerShell è open source</span><span class="sxs-lookup"><span data-stu-id="48df2-109">PowerShell is open-source</span></span>

<span data-ttu-id="48df2-110">Il codice open source di base di PowerShell ora è disponibile su GitHub e aperto ai contributi della community.</span><span class="sxs-lookup"><span data-stu-id="48df2-110">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="48df2-111">Vedere il [codice open source di PowerShell su GitHub](https://github.com/powershell/powershell).</span><span class="sxs-lookup"><span data-stu-id="48df2-111">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="48df2-112">Per iniziare, è possibile [ottenere PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span><span class="sxs-lookup"><span data-stu-id="48df2-112">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="48df2-113">In alternativa, è possibile iniziare da una rapida [panoramica introduttiva](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)</span><span class="sxs-lookup"><span data-stu-id="48df2-113">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="48df2-114">Obiettivi di progettazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="48df2-114">PowerShell design goals</span></span>

<span data-ttu-id="48df2-115">PowerShell è progettato per migliorare la riga di comando e l'ambiente di scripting eliminando problemi di lunga data e aggiungendo nuove funzionalità.</span><span class="sxs-lookup"><span data-stu-id="48df2-115">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="48df2-116">Individuabilità</span><span class="sxs-lookup"><span data-stu-id="48df2-116">Discoverability</span></span>

<span data-ttu-id="48df2-117">È facile individuare le funzionalità di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48df2-117">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="48df2-118">Ad esempio, per trovare un elenco dei cmdlet che consentono di visualizzare e modificare i servizi di Windows, digitare:</span><span class="sxs-lookup"><span data-stu-id="48df2-118">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="48df2-119">Dopo aver individuato il cmdlet che esegue un'attività, è possibile ottenere altre informazioni con il cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="48df2-119">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span> <span data-ttu-id="48df2-120">Per visualizzare la Guida per il cmdlet `Get-Service`, ad esempio, digitare:</span><span class="sxs-lookup"><span data-stu-id="48df2-120">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```

<span data-ttu-id="48df2-121">La maggior parte dei cmdlet restituisce oggetti che possono essere modificati e di cui è possibile eseguire il rendering come testo per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="48df2-121">Most cmdlets return objects that can be manipulated and then rendered as text for display.</span></span> <span data-ttu-id="48df2-122">Per una migliore comprensione dell'output di un cmdlet, inviare l'output tramite pipe al cmdlet `Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="48df2-122">To fully understand the output of a cmdlet, pipe the output to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="48df2-123">Il comando seguente, ad esempio, visualizza informazioni sui membri dell'oggetto restituito dal cmdlet `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="48df2-123">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="48df2-124">Coerenza</span><span class="sxs-lookup"><span data-stu-id="48df2-124">Consistency</span></span>

<span data-ttu-id="48df2-125">La gestione dei sistemi può essere un'attività complessa.</span><span class="sxs-lookup"><span data-stu-id="48df2-125">Managing systems can be a complex task.</span></span> <span data-ttu-id="48df2-126">Gli strumenti con un'interfaccia coerente sono utili per assicurare un maggiore controllo sulla complessità intrinseca.</span><span class="sxs-lookup"><span data-stu-id="48df2-126">Tools that have a consistent interface help to control the inherent complexity.</span></span> <span data-ttu-id="48df2-127">Sfortunatamente, gli strumenti da riga di comando o gli oggetti COM (Component Object Model) gestibili tramite script non sono certo noti per la loro coerenza.</span><span class="sxs-lookup"><span data-stu-id="48df2-127">Unfortunately, command-line tools and scriptable Component Object Model (COM) objects aren't known for their consistency.</span></span>

<span data-ttu-id="48df2-128">La coerenza di PowerShell è una delle sue principali risorse.</span><span class="sxs-lookup"><span data-stu-id="48df2-128">The consistency of PowerShell is one of its primary assets.</span></span> <span data-ttu-id="48df2-129">Ad esempio, dopo aver imparato a usare il cmdlet `Sort-Object`, è possibile usare tali conoscenze per ordinare l'output di qualsiasi cmdlet.</span><span class="sxs-lookup"><span data-stu-id="48df2-129">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span> <span data-ttu-id="48df2-130">Non è necessario apprendere le diverse routine di ordinamento di ogni cmdlet.</span><span class="sxs-lookup"><span data-stu-id="48df2-130">You don't have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="48df2-131">Inoltre, gli sviluppatori di cmdlet non devono progettare funzionalità di ordinamento per i propri cmdlet.</span><span class="sxs-lookup"><span data-stu-id="48df2-131">Additionally, cmdlet developers don't have to design sorting features for their cmdlets.</span></span> <span data-ttu-id="48df2-132">PowerShell offre un framework con le funzionalità di base per garantire la coerenza.</span><span class="sxs-lookup"><span data-stu-id="48df2-132">PowerShell provides a framework with the basic features that forces consistency.</span></span> <span data-ttu-id="48df2-133">Il framework elimina alcune possibilità di scelta lasciate allo sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="48df2-133">The framework eliminates some choices that are left to the developer.</span></span> <span data-ttu-id="48df2-134">In cambio, tuttavia, semplifica notevolmente lo sviluppo di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="48df2-134">But, in return, it makes the development of cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="48df2-135">Ambienti interattivi e di scripting</span><span class="sxs-lookup"><span data-stu-id="48df2-135">Interactive and scripting environments</span></span>

<span data-ttu-id="48df2-136">Il prompt dei comandi di Windows offre una shell interattiva con accesso a strumenti da riga di comando e funzionalità di scripting di base.</span><span class="sxs-lookup"><span data-stu-id="48df2-136">The Windows Command Prompt provides an interactive shell with access to command-line tools and basic scripting.</span></span> <span data-ttu-id="48df2-137">Windows Script Host (WSH) include strumenti da riga di comando configurabili tramite script e oggetti di automazione COM, ma non offre una shell interattiva.</span><span class="sxs-lookup"><span data-stu-id="48df2-137">Windows Script Host (WSH) has scriptable command-line tools and COM automation objects, but doesn't provide an interactive shell.</span></span>

<span data-ttu-id="48df2-138">PowerShell integra una shell interattiva e un ambiente di scripting.</span><span class="sxs-lookup"><span data-stu-id="48df2-138">PowerShell combines an interactive shell and a scripting environment.</span></span> <span data-ttu-id="48df2-139">PowerShell può accedere a strumenti da riga di comando, oggetti COM e librerie di classi .NET.</span><span class="sxs-lookup"><span data-stu-id="48df2-139">PowerShell can access command-line tools, COM objects, and .NET class libraries.</span></span> <span data-ttu-id="48df2-140">Questa combinazione di funzionalità estende le capacità dell'utente interattivo, dell'autore di script e dell'amministratore di sistema.</span><span class="sxs-lookup"><span data-stu-id="48df2-140">This combination of features extends the capabilities of the interactive user, the script writer, and the system administrator.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="48df2-141">Orientamento agli oggetti</span><span class="sxs-lookup"><span data-stu-id="48df2-141">Object orientation</span></span>

<span data-ttu-id="48df2-142">PowerShell è basato su oggetti e non sul testo.</span><span class="sxs-lookup"><span data-stu-id="48df2-142">PowerShell is based on object not text.</span></span> <span data-ttu-id="48df2-143">L'output di un comando è un oggetto.</span><span class="sxs-lookup"><span data-stu-id="48df2-143">The output of a command is an object.</span></span> <span data-ttu-id="48df2-144">È possibile inviare l'oggetto di output, tramite la pipeline, a un altro comando come input.</span><span class="sxs-lookup"><span data-stu-id="48df2-144">You can send the output object, through the pipeline, to another command as its input.</span></span>

<span data-ttu-id="48df2-145">Questa pipeline offre un'interfaccia familiare per gli utenti che sanno usare altre shell.</span><span class="sxs-lookup"><span data-stu-id="48df2-145">This pipeline provides a familiar interface for people experienced with other shells.</span></span> <span data-ttu-id="48df2-146">PowerShell estende questo concetto inviando oggetti anziché testo.</span><span class="sxs-lookup"><span data-stu-id="48df2-146">PowerShell extends this concept by sending objects rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="48df2-147">Semplice transizione allo scripting</span><span class="sxs-lookup"><span data-stu-id="48df2-147">Easy transition to scripting</span></span>

<span data-ttu-id="48df2-148">La possibilità di individuare i comandi di PowerShell semplifica il passaggio dalla digitazione interattiva dei comandi alla creazione e all'esecuzione di script.</span><span class="sxs-lookup"><span data-stu-id="48df2-148">PowerShell's command discoverability makes it easy to transition from typing commands interactively to creating and running scripts.</span></span> <span data-ttu-id="48df2-149">Le trascrizioni e la cronologia di PowerShell semplificano la copia di comandi in un file da usare come script.</span><span class="sxs-lookup"><span data-stu-id="48df2-149">PowerShell transcripts and history make it easy to copy commands to a file for use as a script.</span></span>
