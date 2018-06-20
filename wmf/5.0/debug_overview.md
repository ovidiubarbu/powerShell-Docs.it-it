---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 9ead27fd5d4f146e9062488c1c8cc22a073b922e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187103"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="199e2-102">Miglioramenti per il debug degli script di PowerShell</span><span class="sxs-lookup"><span data-stu-id="199e2-102">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="199e2-103">In PowerShell 5.0 sono stati introdotti numerosi miglioramenti per ottimizzare l'esperienza di debug.</span><span class="sxs-lookup"><span data-stu-id="199e2-103">A number of improvements were made in PowerShell 5.0 to enhance the debugging experience:</span></span>

## <a name="break-all"></a><span data-ttu-id="199e2-104">Interrompi tutto</span><span class="sxs-lookup"><span data-stu-id="199e2-104">Break All</span></span>

<span data-ttu-id="199e2-105">La console di PowerShell e Windows PowerShell ISE ora consentono di interrompere il debugger per gli script in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="199e2-105">The PowerShell console and Windows PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="199e2-106">Questa funzionalità è disponibile sia per le sessioni locali che remote.</span><span class="sxs-lookup"><span data-stu-id="199e2-106">This works in both local and remote sessions.</span></span>

<span data-ttu-id="199e2-107">Nella console premere **CTRL+INTERR**.</span><span class="sxs-lookup"><span data-stu-id="199e2-107">In the console, press **Ctrl+Break**.</span></span>

<span data-ttu-id="199e2-108">In ISE premere **CTRL+B** oppure usare il comando di menu **Debug -> Interrompi tutto**.</span><span class="sxs-lookup"><span data-stu-id="199e2-108">In ISE, press **Ctrl+B**, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a><span data-ttu-id="199e2-109">Debug remoto e modifica dei file remota in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="199e2-109">Remote debugging and remote file editing in Windows PowerShell ISE</span></span>

<span data-ttu-id="199e2-110">Windows PowerShell ISE consente ora di aprire e modificare i file in una sessione remota eseguendo il comando PSEdit.</span><span class="sxs-lookup"><span data-stu-id="199e2-110">Windows PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="199e2-111">Ad esempio, è possibile aprire un file per la modifica dalla riga di comando in una sessione remota nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="199e2-111">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="199e2-112">Inoltre, è ora possibile modificare e salvare le modifiche in un file remoto che viene aperto automaticamente in Windows PowerShell ISE quando si raggiunge un punto di interruzione.</span><span class="sxs-lookup"><span data-stu-id="199e2-112">In addition, you can now edit and save changes in a remote file that is automatically opened in Windows PowerShell ISE when you hit a breakpoint.</span></span>
<span data-ttu-id="199e2-113">È ora possibile eseguire il debug di un file di script in esecuzione in un computer remoto, modificare il file per correggere un errore ed eseguire nuovamente lo script modificato.</span><span class="sxs-lookup"><span data-stu-id="199e2-113">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="199e2-114">Debug avanzato degli script</span><span class="sxs-lookup"><span data-stu-id="199e2-114">Advanced Script Debugging</span></span>

<span data-ttu-id="199e2-115">Sono disponibili nuove funzionalità di debug avanzate che consentono di collegare qualsiasi processo del computer locale che ha caricato Windows PowerShell e di eseguire il debug di spazi di esecuzione arbitrari in tale processo.</span><span class="sxs-lookup"><span data-stu-id="199e2-115">There are new, advanced debugging features that let you attach to any local computer process that has loaded Windows PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="199e2-116">Debug di spazi di esecuzione</span><span class="sxs-lookup"><span data-stu-id="199e2-116">Runspace Debugging</span></span>

<span data-ttu-id="199e2-117">Sono stati aggiunti nuovi cmdlet che consentono di elencare gli spazi di esecuzione correnti in un processo e collegare il debugger della console di Windows PowerShell o di ISE a tale spazio di esecuzione per il debug degli script:</span><span class="sxs-lookup"><span data-stu-id="199e2-117">New cmdlets have been added that let you list current runspaces in a process, and attach the Windows PowerShell console or ISE debugger to that runspace for script debugging:</span></span>

-   <span data-ttu-id="199e2-118">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="199e2-118">Get-Runspace</span></span>
-   <span data-ttu-id="199e2-119">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="199e2-119">Debug-Runspace</span></span>
-   <span data-ttu-id="199e2-120">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="199e2-120">Enable-RunspaceDebug</span></span>
-   <span data-ttu-id="199e2-121">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="199e2-121">Disable-RunspaceDebug</span></span>
-   <span data-ttu-id="199e2-122">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="199e2-122">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="199e2-123">Collegarsi a un processo che ospita PowerShell</span><span class="sxs-lookup"><span data-stu-id="199e2-123">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="199e2-124">È ora possibile collegarsi a qualsiasi processo di computer con Windows PowerShell caricato.</span><span class="sxs-lookup"><span data-stu-id="199e2-124">You can now attach to any computer process that has Windows PowerShell loaded.</span></span> <span data-ttu-id="199e2-125">A tale scopo, si avvia una sessione interattiva con il processo, in modo analogo a come si avvia una sessione remota interattiva eseguendo il cmdlet Enter-PSSession:</span><span class="sxs-lookup"><span data-stu-id="199e2-125">You do this by entering into an interactive session with the process, similarly to how you enter into an interactive remote session by running the Enter-PSSession cmdlet:</span></span>

-   <span data-ttu-id="199e2-126">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="199e2-126">Enter-PSHostProcess</span></span>
-   <span data-ttu-id="199e2-127">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="199e2-127">Exit-PSHostProcess</span></span>
