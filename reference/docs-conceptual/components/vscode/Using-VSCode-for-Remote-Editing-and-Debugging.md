---
title: Uso di Visual Studio Code per la modifica e il debug remoti
description: Uso di Visual Studio Code per la modifica e il debug remoti
ms.date: 06/13/2019
ms.openlocfilehash: 5ce7f575d90ff47fd6b8a0a2b567e972ec3a9fef
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279152"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="d61db-103">Uso di Visual Studio Code per la modifica e il debug remoti</span><span class="sxs-lookup"><span data-stu-id="d61db-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="d61db-104">Gli utenti che hanno familiarità con l'ambiente ISE ricorderanno forse che è possibile eseguire `psedit file.ps1` dalla console integrata per aprire i file, locali o remoti, direttamente nell'ISE.</span><span class="sxs-lookup"><span data-stu-id="d61db-104">For those of you that are familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="d61db-105">Questa funzionalità è disponibile anche nell'estensione di PowerShell per VSCode.</span><span class="sxs-lookup"><span data-stu-id="d61db-105">This feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="d61db-106">Questa guida illustra come eseguire queste operazioni.</span><span class="sxs-lookup"><span data-stu-id="d61db-106">This guide shows you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d61db-107">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="d61db-107">Prerequisites</span></span>

<span data-ttu-id="d61db-108">Questa guida presuppone che si disponga di:</span><span class="sxs-lookup"><span data-stu-id="d61db-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="d61db-109">Una risorsa remota ( ad esempio una macchina virtuale o un contenitore) a cui si ha accesso</span><span class="sxs-lookup"><span data-stu-id="d61db-109">A remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="d61db-110">PowerShell in esecuzione nella risorsa remota e nel computer host</span><span class="sxs-lookup"><span data-stu-id="d61db-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="d61db-111">VSCode e l'estensione di PowerShell per VSCode</span><span class="sxs-lookup"><span data-stu-id="d61db-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="d61db-112">Questa funzionalità funziona in Windows PowerShell e PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="d61db-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="d61db-113">Questa funzionalità funziona anche quando ci si connette a un computer remoto tramite WinRM, PowerShell Direct o SSH.</span><span class="sxs-lookup"><span data-stu-id="d61db-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="d61db-114">Se si desidera usare SSH, ma si usa Windows, considerare la [versione Win32 di SSH](https://github.com/PowerShell/Win32-OpenSSH).</span><span class="sxs-lookup"><span data-stu-id="d61db-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d61db-115">I comandi `Open-EditorFile` e `psedit` funzionano solo nella **console integrata di PowerShell** creata dall'estensione di PowerShell per VSCode.</span><span class="sxs-lookup"><span data-stu-id="d61db-115">The `Open-EditorFile` and `psedit` commands only work in the **PowerShell Integrated Console** created by the PowerShell extension for VSCode.</span></span>

## <a name="usage-examples"></a><span data-ttu-id="d61db-116">Esempi di utilizzo</span><span class="sxs-lookup"><span data-stu-id="d61db-116">Usage examples</span></span>

<span data-ttu-id="d61db-117">Questi esempi illustrano le operazioni di modifica e debug remoti da un MacBook Pro a una macchina virtuale Ubuntu in esecuzione in Azure.</span><span class="sxs-lookup"><span data-stu-id="d61db-117">These examples show remote editing and debugging from a MacBook Pro to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="d61db-118">Il processo è identico in Windows.</span><span class="sxs-lookup"><span data-stu-id="d61db-118">The process is identical on Windows.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="d61db-119">Modifica dei file locali con Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="d61db-119">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="d61db-120">Con l'estensione di PowerShell per VSCode avviata e la console integrata di PowerShell aperta, è possibile digitare `Open-EditorFile foo.ps1` o `psedit foo.ps1` per aprire il file locale foo.ps1 direttamente nell'editor.</span><span class="sxs-lookup"><span data-stu-id="d61db-120">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Open-EditorFile foo.ps1 funziona localmente](media/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> <span data-ttu-id="d61db-122">Il file `foo.ps1` deve essere già presente.</span><span class="sxs-lookup"><span data-stu-id="d61db-122">The file `foo.ps1` must already exist.</span></span>

<span data-ttu-id="d61db-123">Da qui, è possibile:</span><span class="sxs-lookup"><span data-stu-id="d61db-123">From there, we can:</span></span>

- <span data-ttu-id="d61db-124">Aggiungere punti di interruzione alla barra di navigazione</span><span class="sxs-lookup"><span data-stu-id="d61db-124">Add breakpoints to the gutter</span></span>

  ![aggiunta di punti di interruzione alla barra di navigazione](media/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- <span data-ttu-id="d61db-126">Premere F5 per eseguire il debug dello script di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d61db-126">Hit F5 to debug the PowerShell script.</span></span>

  ![debug dello script locale di PowerShell](media/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

<span data-ttu-id="d61db-128">Durante il debug, è possibile interagire con la console di debug, verificare le variabili nell'ambito a sinistra e tutti gli altri gli strumenti standard di debug.</span><span class="sxs-lookup"><span data-stu-id="d61db-128">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="d61db-129">Modifica dei file remoti con Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="d61db-129">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="d61db-130">È ora possibile passare alla modifica e al debug dei file remoti.</span><span class="sxs-lookup"><span data-stu-id="d61db-130">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="d61db-131">I passaggi sono quasi gli stessi, occorre solo fare prima di tutto una cosa: avviare la sessione di PowerShell nel server remoto.</span><span class="sxs-lookup"><span data-stu-id="d61db-131">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="d61db-132">È disponibile un cmdlet per eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="d61db-132">There's a cmdlet for to do so.</span></span> <span data-ttu-id="d61db-133">È denominato `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="d61db-133">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="d61db-134">La spiegazione semplificata del cmdlet è:</span><span class="sxs-lookup"><span data-stu-id="d61db-134">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="d61db-135">`Enter-PSSession -ComputerName foo` avvia una sessione tramite Gestione remota Windows</span><span class="sxs-lookup"><span data-stu-id="d61db-135">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="d61db-136">`Enter-PSSession -ContainerId foo` e `Enter-PSSession -VmId foo` avviano una sessione tramite PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="d61db-136">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="d61db-137">`Enter-PSSession -HostName foo` avvia una sessione tramite SSH</span><span class="sxs-lookup"><span data-stu-id="d61db-137">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="d61db-138">Per altre informazioni, vedere la documentazione di [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="d61db-138">For more information, see the documentation for [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span></span>

<span data-ttu-id="d61db-139">Poiché si sta passando da macOS a una macchina virtuale Ubuntu in Azure, per la comunicazione remota si userà SSH.</span><span class="sxs-lookup"><span data-stu-id="d61db-139">Since we are going from macOS to an Ubuntu VM in Azure, we are using SSH for remoting.</span></span>

<span data-ttu-id="d61db-140">Nella console integrata eseguire prima di tutto `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="d61db-140">First, in the Integrated Console, run `Enter-PSSession`.</span></span> <span data-ttu-id="d61db-141">Quando `[<hostname>]` viene visualizzato a sinistra del prompt, si è connessi alla sessione remota.</span><span class="sxs-lookup"><span data-stu-id="d61db-141">You're connected to the remote session when `[<hostname>]` shows up to the left of your prompt.</span></span>

![La chiamata a Enter-PSSession](media/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

<span data-ttu-id="d61db-143">Ora è possibile eseguire gli stessi passaggi che si eseguono per modificare uno script locale.</span><span class="sxs-lookup"><span data-stu-id="d61db-143">Now, we can do the same steps as if we are editing a local script.</span></span>

1. <span data-ttu-id="d61db-144">Eseguire `Open-EditorFile test.ps1` o `psedit test.ps1` per aprire il file remoto `test.ps1`</span><span class="sxs-lookup"><span data-stu-id="d61db-144">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file</span></span>

  ![Eseguire Open-EditorFile sul file test.ps1](media/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. <span data-ttu-id="d61db-146">Modificare i file/impostare punti di interruzione</span><span class="sxs-lookup"><span data-stu-id="d61db-146">Edit the file/set breakpoints</span></span>

   ![modificare i file e impostare punti di interruzione](media/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. <span data-ttu-id="d61db-148">Avviare il debug del file remoto (F5)</span><span class="sxs-lookup"><span data-stu-id="d61db-148">Start debugging (F5) the remote file</span></span>

   ![debug del file remoto](media/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

<span data-ttu-id="d61db-150">Se si verificano problemi, è possibile segnalarli [nel repository GitHub](https://github.com/powershell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="d61db-150">If you have any problems, you can open issues in the [GitHub repo](https://github.com/powershell/vscode-powershell).</span></span>
