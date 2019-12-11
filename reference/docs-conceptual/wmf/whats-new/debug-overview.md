---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
title: Miglioramenti per il debug degli script di PowerShell
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71147811"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="b9f33-103">Miglioramenti per il debug degli script di PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9f33-103">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="b9f33-104">PowerShell 5.0 include diversi miglioramenti che ottimizzano l'esperienza di debug.</span><span class="sxs-lookup"><span data-stu-id="b9f33-104">PowerShell 5.0 includes several improvements that enhance the debugging experience.</span></span>

## <a name="break-all"></a><span data-ttu-id="b9f33-105">Interrompi tutto</span><span class="sxs-lookup"><span data-stu-id="b9f33-105">Break All</span></span>

<span data-ttu-id="b9f33-106">La console di PowerShell e PowerShell ISE ora consentono di interrompere il debugger per gli script in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="b9f33-106">The PowerShell console and PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="b9f33-107">Questa funzionalità è disponibile sia per le sessioni locali che remote.</span><span class="sxs-lookup"><span data-stu-id="b9f33-107">This works in both local and remote sessions.</span></span>

<span data-ttu-id="b9f33-108">Nella console premere <kbd>CTRL</kbd>+<kbd>INTERR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b9f33-108">In the console, press <kbd>Ctrl</kbd>+<kbd>Break</kbd>.</span></span>

<span data-ttu-id="b9f33-109">In ISE premere <kbd>CTRL</kbd>+<kbd>B</kbd> oppure usare il comando di menu **Debug -> Interrompi tutto**.</span><span class="sxs-lookup"><span data-stu-id="b9f33-109">In ISE, press <kbd>Ctrl</kbd>+<kbd>B</kbd>, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a><span data-ttu-id="b9f33-110">Debug remoto e modifica dei file remota in PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="b9f33-110">Remote debugging and remote file editing in PowerShell ISE</span></span>

<span data-ttu-id="b9f33-111">PowerShell ISE consente ora di aprire e modificare i file in una sessione remota eseguendo il comando PSEdit.</span><span class="sxs-lookup"><span data-stu-id="b9f33-111">PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="b9f33-112">Ad esempio, è possibile aprire un file per la modifica dalla riga di comando in una sessione remota nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="b9f33-112">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="b9f33-113">Inoltre, è ora possibile modificare e salvare le modifiche in un file remoto che viene aperto automaticamente in PowerShell ISE quando si raggiunge un punto di interruzione.</span><span class="sxs-lookup"><span data-stu-id="b9f33-113">In addition, you can now edit and save changes in a remote file that is automatically opened in PowerShell ISE when you hit a breakpoint.</span></span> <span data-ttu-id="b9f33-114">È ora possibile eseguire il debug di un file di script in esecuzione in un computer remoto, modificare il file per correggere un errore ed eseguire nuovamente lo script modificato.</span><span class="sxs-lookup"><span data-stu-id="b9f33-114">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="b9f33-115">Debug avanzato degli script</span><span class="sxs-lookup"><span data-stu-id="b9f33-115">Advanced Script Debugging</span></span>

<span data-ttu-id="b9f33-116">Sono disponibili nuove funzionalità di debug avanzate che consentono di collegare qualsiasi processo del computer locale che ha caricato PowerShell e di eseguire il debug di spazi di esecuzione arbitrari in tale processo.</span><span class="sxs-lookup"><span data-stu-id="b9f33-116">There are new, advanced debugging features that let you attach to any local computer process that has loaded PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="b9f33-117">Debug di spazi di esecuzione</span><span class="sxs-lookup"><span data-stu-id="b9f33-117">Runspace Debugging</span></span>

<span data-ttu-id="b9f33-118">Sono stati aggiunti nuovi cmdlet che consentono di elencare gli spazi di esecuzione correnti in un processo e collegare il debugger della console di PowerShell o di PowerShell ISE a tale spazio di esecuzione per il debug degli script:</span><span class="sxs-lookup"><span data-stu-id="b9f33-118">New cmdlets have been added that let you list current runspaces in a process, and attach the PowerShell console or PowerShell ISE debugger to that runspace for script debugging:</span></span>

- <span data-ttu-id="b9f33-119">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="b9f33-119">Get-Runspace</span></span>
- <span data-ttu-id="b9f33-120">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="b9f33-120">Debug-Runspace</span></span>
- <span data-ttu-id="b9f33-121">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="b9f33-121">Enable-RunspaceDebug</span></span>
- <span data-ttu-id="b9f33-122">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="b9f33-122">Disable-RunspaceDebug</span></span>
- <span data-ttu-id="b9f33-123">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="b9f33-123">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="b9f33-124">Collegarsi a un processo che ospita PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9f33-124">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="b9f33-125">È ora possibile collegarsi a qualsiasi processo di computer con PowerShell caricato.</span><span class="sxs-lookup"><span data-stu-id="b9f33-125">You can now attach to any computer process that has PowerShell loaded.</span></span> <span data-ttu-id="b9f33-126">Per eseguire questa operazione, avviare una sessione interattiva con il processo host.</span><span class="sxs-lookup"><span data-stu-id="b9f33-126">You do this by entering into an interactive session with the host process.</span></span> <span data-ttu-id="b9f33-127">Per altre informazioni, vedere:</span><span class="sxs-lookup"><span data-stu-id="b9f33-127">For more information, see:</span></span>

- [<span data-ttu-id="b9f33-128">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="b9f33-128">Enter-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [<span data-ttu-id="b9f33-129">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="b9f33-129">Exit-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
