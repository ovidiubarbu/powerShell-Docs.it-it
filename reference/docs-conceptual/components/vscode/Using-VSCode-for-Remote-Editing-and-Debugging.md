---
title: Uso di Visual Studio Code per la modifica e il debug remoti
description: Uso di Visual Studio Code per la modifica e il debug remoti
ms.date: 08/06/2018
ms.openlocfilehash: fbc1ee3556e822b4afb2b37111d0688dc89fdab3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086673"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="5cea2-103">Uso di Visual Studio Code per la modifica e il debug remoti</span><span class="sxs-lookup"><span data-stu-id="5cea2-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="5cea2-104">Per coloro hanno familiarità con l'ambiente ISE, si ricorderà che è possibile eseguire `psedit file.ps1` dalla console integrata per aprire i file, locali o remoti, direttamente in ISE.</span><span class="sxs-lookup"><span data-stu-id="5cea2-104">For those of you that were familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="5cea2-105">Questa funzionalità è disponibile anche nell'estensione di PowerShell per VSCode.</span><span class="sxs-lookup"><span data-stu-id="5cea2-105">As it turns out, this feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="5cea2-106">Questa guida illustrerà come eseguire queste operazioni.</span><span class="sxs-lookup"><span data-stu-id="5cea2-106">This guide will show you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5cea2-107">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="5cea2-107">Prerequisites</span></span>

<span data-ttu-id="5cea2-108">Questa guida presuppone che si disponga di quanto segue:</span><span class="sxs-lookup"><span data-stu-id="5cea2-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="5cea2-109">una risorsa remota ( ad esempio, una macchina virtuale, un contenitore) a cui si ha accesso</span><span class="sxs-lookup"><span data-stu-id="5cea2-109">a remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="5cea2-110">PowerShell in esecuzione su di essi e il computer host</span><span class="sxs-lookup"><span data-stu-id="5cea2-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="5cea2-111">VSCode e l'estensione di PowerShell per VSCode</span><span class="sxs-lookup"><span data-stu-id="5cea2-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="5cea2-112">Questa funzionalità funziona in Windows PowerShell e PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="5cea2-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="5cea2-113">Questa funzionalità funziona anche quando ci si connette a un computer remoto tramite Gestione remota Windows, PowerShell Direct o SSH.</span><span class="sxs-lookup"><span data-stu-id="5cea2-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="5cea2-114">Se si desidera usare SSH, ma si usa Windows, verificare la [versione Win32 di SSH](https://github.com/PowerShell/Win32-OpenSSH).</span><span class="sxs-lookup"><span data-stu-id="5cea2-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

## <a name="lets-go"></a><span data-ttu-id="5cea2-115">Partiamo</span><span class="sxs-lookup"><span data-stu-id="5cea2-115">Let's go</span></span>

<span data-ttu-id="5cea2-116">In questa sezione, verranno esaminati la modifica e il debug remoti dal MacBook Pro a una macchina virtuale Ubuntu in esecuzione in Azure.</span><span class="sxs-lookup"><span data-stu-id="5cea2-116">In this section, I'll walk through remote editing and debugging from my MacBook Pro, to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="5cea2-117">Si potrebbe non usare Windows, ma **il processo è identico**.</span><span class="sxs-lookup"><span data-stu-id="5cea2-117">I might not be using Windows, but **the process is identical**.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="5cea2-118">Modifica dei file locali con Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="5cea2-118">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="5cea2-119">Con l'estensione di PowerShell per VSCode avviata e la console integrata di PowerShell aperta, è possibile digitare `Open-EditorFile foo.ps1` o `psedit foo.ps1` per aprire il file locale foo.ps1 si direttamente nell'editor.</span><span class="sxs-lookup"><span data-stu-id="5cea2-119">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Open-EditorFile foo.ps1 funziona localmente](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> <span data-ttu-id="5cea2-121">foo.ps1 deve esistere già.</span><span class="sxs-lookup"><span data-stu-id="5cea2-121">foo.ps1 must already exist.</span></span>

<span data-ttu-id="5cea2-122">Da qui, è possibile:</span><span class="sxs-lookup"><span data-stu-id="5cea2-122">From there, we can:</span></span>

<span data-ttu-id="5cea2-123">aggiungere i punti di interruzione alla barra ![aggiunta di un punto di interruzione alla barra](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span><span class="sxs-lookup"><span data-stu-id="5cea2-123">add breakpoints to the gutter ![adding breakpoint to gutter](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span></span>

<span data-ttu-id="5cea2-124">e premere F5 per eseguire il debug dello script di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5cea2-124">and hit F5 to debug the PowerShell script.</span></span>
<span data-ttu-id="5cea2-125">![Debug dello script locale di PowerShell](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span><span class="sxs-lookup"><span data-stu-id="5cea2-125">![debugging the PowerShell local script](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span></span>

<span data-ttu-id="5cea2-126">Durante il debug, è possibile interagire con la console di debug, verificare le variabili nell'ambito a sinistra e tutti gli altri gli strumenti standard di debug.</span><span class="sxs-lookup"><span data-stu-id="5cea2-126">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="5cea2-127">Modifica dei file remoti con Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="5cea2-127">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="5cea2-128">A questo punto passiamo alla modifica e debug dei file remoti.</span><span class="sxs-lookup"><span data-stu-id="5cea2-128">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="5cea2-129">I passaggi sono quasi gli stessi, occorre solo fare prima di tutto una cosa: avviare la sessione di PowerShell nel server remoto.</span><span class="sxs-lookup"><span data-stu-id="5cea2-129">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="5cea2-130">È disponibile un cmdlet per eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="5cea2-130">There's a cmdlet for to do so.</span></span> <span data-ttu-id="5cea2-131">È denominato `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="5cea2-131">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="5cea2-132">La spiegazione semplificata del cmdlet è:</span><span class="sxs-lookup"><span data-stu-id="5cea2-132">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="5cea2-133">`Enter-PSSession -ComputerName foo` avvia una sessione tramite Gestione remota Windows</span><span class="sxs-lookup"><span data-stu-id="5cea2-133">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="5cea2-134">`Enter-PSSession -ContainerId foo` e `Enter-PSSession -VmId foo` avviano una sessione tramite PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="5cea2-134">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="5cea2-135">`Enter-PSSession -HostName foo` avvia una sessione tramite SSH</span><span class="sxs-lookup"><span data-stu-id="5cea2-135">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="5cea2-136">Per altre informazioni su `Enter-PSSession`, vedere la documentazione [qui](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="5cea2-136">For more info on `Enter-PSSession`, check out the docs [here](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span></span>

<span data-ttu-id="5cea2-137">Per la comunicazione remota verrà usato SSH poiché si sta passando da macOS a una macchina virtuale Ubuntu in Azure.</span><span class="sxs-lookup"><span data-stu-id="5cea2-137">I'll be using SSH for remoting since I'm going from macOS to an Ubuntu VM in Azure.</span></span>

<span data-ttu-id="5cea2-138">In primo luogo, nella console integrata, eseguire Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="5cea2-138">First, in the Integrated Console, let's run our Enter-PSSession.</span></span> <span data-ttu-id="5cea2-139">Si saprà di essere entrati nella sessione perché verrà visualizzato `[something]` a sinistra del prompt dei comandi.</span><span class="sxs-lookup"><span data-stu-id="5cea2-139">You'll know that you're in the session because `[something]` will show up to the left of your prompt.</span></span>

![La chiamata a Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

<span data-ttu-id="5cea2-141">Da qui, è possibile eseguire gli stessi passaggi che si eseguono per modificare uno script locale.</span><span class="sxs-lookup"><span data-stu-id="5cea2-141">From there, we can do the exact steps as if we were editing a local script.</span></span>

1. <span data-ttu-id="5cea2-142">Eseguire `Open-EditorFile test.ps1` o `psedit test.ps1` per aprire il file remoto `test.ps1` ![Open-EditorFile file test.ps1](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span><span class="sxs-lookup"><span data-stu-id="5cea2-142">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file ![Open-EditorFile the test.ps1 file](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span></span>
2. <span data-ttu-id="5cea2-143">Modificare i file/impostare punti di interruzione</span><span class="sxs-lookup"><span data-stu-id="5cea2-143">Edit the file/set breakpoints</span></span> ![modificare i file e impostare punti di interruzione](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. <span data-ttu-id="5cea2-145">Avviare il debug del file remoto (F5)</span><span class="sxs-lookup"><span data-stu-id="5cea2-145">Start debugging (F5) the remote file</span></span>

![debug del file remoto](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

<span data-ttu-id="5cea2-147">Questo è tutto.</span><span class="sxs-lookup"><span data-stu-id="5cea2-147">That's all there's to it!</span></span> <span data-ttu-id="5cea2-148">Ci auguriamo che questa guida abbia contribuito a rispondere a eventuali domande sul debug e la modifica remoti di PowerShell in VSCode.</span><span class="sxs-lookup"><span data-stu-id="5cea2-148">We hope that this guide helped clear up any questions about remote debugging and editing PowerShell in VSCode.</span></span>

<span data-ttu-id="5cea2-149">Se si verificano problemi, è possibile segnalarli [nel repository GitHub](http://github.com/powershell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="5cea2-149">If you have any problems, feel free to open issues [on the GitHub repo](http://github.com/powershell/vscode-powershell).</span></span>
