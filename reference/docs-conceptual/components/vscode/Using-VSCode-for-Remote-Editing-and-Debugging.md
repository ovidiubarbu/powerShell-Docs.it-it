---
title: Uso di Visual Studio Code per la modifica e il debug remoti
description: Uso di Visual Studio Code per la modifica e il debug remoti
ms.date: 08/06/2018
ms.openlocfilehash: bab1a629a7e9dafd5957cf93025abb18b8a4f326
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655607"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="9ac42-103">Uso di Visual Studio Code per la modifica e il debug remoti</span><span class="sxs-lookup"><span data-stu-id="9ac42-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="9ac42-104">Per coloro che sono stati familiarità con l'ambiente ISE, come si ricorderà che è possibile eseguire `psedit file.ps1` dalla console integrata per aprire i file - locali o remoti: pulsante destro del mouse in ISE.</span><span class="sxs-lookup"><span data-stu-id="9ac42-104">For those of you that were familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="9ac42-105">Ebbene, anche questa funzionalità è disponibile nell'estensione di PowerShell per Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="9ac42-105">As it turns out, this feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="9ac42-106">Questa Guida illustrerà come eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="9ac42-106">This guide will show you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9ac42-107">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="9ac42-107">Prerequisites</span></span>

<span data-ttu-id="9ac42-108">Questa guida si presuppone di avere:</span><span class="sxs-lookup"><span data-stu-id="9ac42-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="9ac42-109">una risorsa remota (es: una macchina virtuale, un contenitore) di avere accesso a</span><span class="sxs-lookup"><span data-stu-id="9ac42-109">a remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="9ac42-110">PowerShell in esecuzione e il computer host</span><span class="sxs-lookup"><span data-stu-id="9ac42-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="9ac42-111">Visual Studio code e l'estensione di PowerShell per Visual Studio code</span><span class="sxs-lookup"><span data-stu-id="9ac42-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="9ac42-112">Questa funzionalità funziona in Windows PowerShell e PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="9ac42-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="9ac42-113">Questa funzionalità funziona anche quando ci si connette a un computer remoto tramite Gestione remota Windows, PowerShell Direct o SSH.</span><span class="sxs-lookup"><span data-stu-id="9ac42-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="9ac42-114">Se si vuole usare SSH, ma si usa Windows, consultare il [versione Win32 di SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span><span class="sxs-lookup"><span data-stu-id="9ac42-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

## <a name="lets-go"></a><span data-ttu-id="9ac42-115">Partiamo</span><span class="sxs-lookup"><span data-stu-id="9ac42-115">Let's go</span></span>

<span data-ttu-id="9ac42-116">In questa sezione, esaminerò remoto di modifica e debug dal mio MacBook Pro, a una VM Ubuntu in esecuzione in Azure.</span><span class="sxs-lookup"><span data-stu-id="9ac42-116">In this section, I'll walk through remote editing and debugging from my MacBook Pro, to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="9ac42-117">Non potrei essere utilizza Windows, ma **il processo è identico**.</span><span class="sxs-lookup"><span data-stu-id="9ac42-117">I might not be using Windows, but **the process is identical**.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="9ac42-118">File locale modifica con Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="9ac42-118">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="9ac42-119">Con l'estensione di PowerShell per avviata Visual Studio code e la Console integrata di PowerShell aperta, è possibile digitare `Open-EditorFile foo.ps1` o `psedit foo.ps1` per aprire il file locale foo.ps1 si direttamente nell'editor.</span><span class="sxs-lookup"><span data-stu-id="9ac42-119">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![EditorFile Open foo.ps1 si lavora in locale](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> <span data-ttu-id="9ac42-121">foo.ps1 si deve esistere già.</span><span class="sxs-lookup"><span data-stu-id="9ac42-121">foo.ps1 must already exist.</span></span>

<span data-ttu-id="9ac42-122">Da qui, è possibile:</span><span class="sxs-lookup"><span data-stu-id="9ac42-122">From there, we can:</span></span>

<span data-ttu-id="9ac42-123">aggiungere i punti di interruzione alla barra di navigazione ![aggiunta punto di interruzione per barra](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span><span class="sxs-lookup"><span data-stu-id="9ac42-123">add breakpoints to the gutter ![adding breakpoint to gutter](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span></span>

<span data-ttu-id="9ac42-124">e premere F5 per eseguire il debug di script di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9ac42-124">and hit F5 to debug the PowerShell script.</span></span>
<span data-ttu-id="9ac42-125">![debug dello script di PowerShell locale](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span><span class="sxs-lookup"><span data-stu-id="9ac42-125">![debugging the PowerShell local script](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span></span>

<span data-ttu-id="9ac42-126">Durante il debug, è possibile interagire con la console di debug, vedere le variabili nell'ambito a sinistra e tutti gli altri standard gli strumenti di debug.</span><span class="sxs-lookup"><span data-stu-id="9ac42-126">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="9ac42-127">File remoto modifica con Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="9ac42-127">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="9ac42-128">A questo punto è possibile passare in file remoti di modifica e debug.</span><span class="sxs-lookup"><span data-stu-id="9ac42-128">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="9ac42-129">I passaggi sono quasi lo stesso, solo una cosa da fare prima di tutto: immettere la sessione di PowerShell nel server remoto.</span><span class="sxs-lookup"><span data-stu-id="9ac42-129">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="9ac42-130">È disponibile un cmdlet per eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="9ac42-130">There's a cmdlet for to do so.</span></span> <span data-ttu-id="9ac42-131">Viene chiamato `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="9ac42-131">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="9ac42-132">La spiegazione ridotta verso il basso del cmdlet è:</span><span class="sxs-lookup"><span data-stu-id="9ac42-132">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="9ac42-133">`Enter-PSSession -ComputerName foo` Avvia una sessione tramite WinRM</span><span class="sxs-lookup"><span data-stu-id="9ac42-133">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="9ac42-134">`Enter-PSSession -ContainerId foo` e `Enter-PSSession -VmId foo` avviare una sessione tramite PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="9ac42-134">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="9ac42-135">`Enter-PSSession -HostName foo` Avvia una sessione tramite SSH</span><span class="sxs-lookup"><span data-stu-id="9ac42-135">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="9ac42-136">Per altre informazioni sul `Enter-PSSession`, vedere la documentazione [qui](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="9ac42-136">For more info on `Enter-PSSession`, check out the docs [here](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span></span>

<span data-ttu-id="9ac42-137">Userà SSH per la comunicazione remota poiché voglio da macOS una VM Ubuntu in Azure.</span><span class="sxs-lookup"><span data-stu-id="9ac42-137">I'll be using SSH for remoting since I'm going from macOS to an Ubuntu VM in Azure.</span></span>

<span data-ttu-id="9ac42-138">In primo luogo, nella Console integrata, eseguiamo il Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="9ac42-138">First, in the Integrated Console, let's run our Enter-PSSession.</span></span> <span data-ttu-id="9ac42-139">Si saprà che sia aperta la sessione perché `[something]` verrà visualizzato a sinistra della finestra del prompt dei comandi.</span><span class="sxs-lookup"><span data-stu-id="9ac42-139">You'll know that you're in the session because `[something]` will show up to the left of your prompt.</span></span>

![La chiamata a Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

<span data-ttu-id="9ac42-141">Da qui, possiamo eseguire la procedura esatta come se si stava modificando uno script locale.</span><span class="sxs-lookup"><span data-stu-id="9ac42-141">From there, we can do the exact steps as if we were editing a local script.</span></span>

1. <span data-ttu-id="9ac42-142">Eseguire `Open-EditorFile test.ps1` oppure `psedit test.ps1` per aprire il computer remoto `test.ps1` file ![Open-EditorFile file test.ps1](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span><span class="sxs-lookup"><span data-stu-id="9ac42-142">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file ![Open-EditorFile the test.ps1 file](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span></span>
2. <span data-ttu-id="9ac42-143">Modificare i file o impostare punti di interruzione</span><span class="sxs-lookup"><span data-stu-id="9ac42-143">Edit the file/set breakpoints</span></span> ![modificare e impostare i punti di interruzione](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. <span data-ttu-id="9ac42-145">Avviare il debug (F5) il file remoto</span><span class="sxs-lookup"><span data-stu-id="9ac42-145">Start debugging (F5) the remote file</span></span>

![debug di file remoto](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

<span data-ttu-id="9ac42-147">Questo è tutto qui!</span><span class="sxs-lookup"><span data-stu-id="9ac42-147">That's all there's to it!</span></span> <span data-ttu-id="9ac42-148">Ci auguriamo che questa guida ha contribuito a deselezionare le eventuali domande sul debug remoto e la modifica di PowerShell in Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="9ac42-148">We hope that this guide helped clear up any questions about remote debugging and editing PowerShell in VSCode.</span></span>

<span data-ttu-id="9ac42-149">Se si verificano problemi, è possibile segnalare problemi [nel repository GitHub](http://github.com/powershell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="9ac42-149">If you have any problems, feel free to open issues [on the GitHub repo](http://github.com/powershell/vscode-powershell).</span></span>
