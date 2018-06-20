---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Gestione dei processi con i cmdlet Process
ms.assetid: 5038f612-d149-4698-8bbb-999986959e31
ms.openlocfilehash: d6d7daa810dce2d476566e4d30f03cc95bf730e6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952495"
---
# <a name="managing-processes-with-process-cmdlets"></a><span data-ttu-id="a8b47-103">Gestione dei processi con i cmdlet Process</span><span class="sxs-lookup"><span data-stu-id="a8b47-103">Managing Processes with Process Cmdlets</span></span>

<span data-ttu-id="a8b47-104">È possibile usare i cmdlet Process in Windows PowerShell per gestire i processi locali e remoti in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a8b47-104">You can use the Process cmdlets in Windows PowerShell to manage local and remote processes in Windows PowerShell.</span></span>

## <a name="getting-processes-get-process"></a><span data-ttu-id="a8b47-105">Recupero di processi (Get-Process)</span><span class="sxs-lookup"><span data-stu-id="a8b47-105">Getting Processes (Get-Process)</span></span>

<span data-ttu-id="a8b47-106">Per ottenere i processi in esecuzione nel computer locale, eseguire il comando **Get-Process** senza parametri.</span><span class="sxs-lookup"><span data-stu-id="a8b47-106">To get the processes running on the local computer, run a **Get-Process** with no parameters.</span></span>

<span data-ttu-id="a8b47-107">È possibile recuperare processi specifici specificandone il nome o l'ID.</span><span class="sxs-lookup"><span data-stu-id="a8b47-107">You can get particular processes by specifying their process names or process IDs.</span></span> <span data-ttu-id="a8b47-108">Il comando seguente consente di recuperare il processo Idle:</span><span class="sxs-lookup"><span data-stu-id="a8b47-108">The following command gets the Idle process:</span></span>

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

<span data-ttu-id="a8b47-109">Anche se è normale per i cmdlet non restituire dati in alcune situazioni, quando si specifica un processo mediante il relativo ProcessId **Get-Process** genera un errore se vengono rilevate corrispondenze, poiché l'uso abituale è quello di recuperare un processo in esecuzione noto.</span><span class="sxs-lookup"><span data-stu-id="a8b47-109">Although it is normal for cmdlets to return no data in some situations, when you specify a process by its ProcessId, **Get-Process** generates an error if it finds no matches, because the usual intent is to retrieve a known running process.</span></span> <span data-ttu-id="a8b47-110">Se non è presente alcun processo con tale ID, è probabile che l'ID non sia corretto o che il processo in questione sia già terminato:</span><span class="sxs-lookup"><span data-stu-id="a8b47-110">If there is no process with that Id, it is likely that the Id is incorrect or that the process of interest has already exited:</span></span>

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

<span data-ttu-id="a8b47-111">È possibile usare il parametro Name del cmdlet Get-Process per specificare un sottoinsieme di processi in base al nome di processo.</span><span class="sxs-lookup"><span data-stu-id="a8b47-111">You can use the Name parameter of the Get-Process cmdlet to specify a subset of processes based on the process name.</span></span> <span data-ttu-id="a8b47-112">Il parametro Name può ottenere più nomi in un elenco con valori delimitati da virgole e supporta l'uso dei caratteri jolly, pertanto è possibile digitare modelli di nomi.</span><span class="sxs-lookup"><span data-stu-id="a8b47-112">The Name parameter can take multiple names in a comma-separated list and it supports the use of wildcards, so you can type name patterns.</span></span>

<span data-ttu-id="a8b47-113">Il comando seguente recupera ad esempio i processi i cui nomi iniziano con "ex".</span><span class="sxs-lookup"><span data-stu-id="a8b47-113">For example, the following command gets process whose names begin with "ex."</span></span>

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

<span data-ttu-id="a8b47-114">Poiché la classe .NET System.Diagnostics.Process è alla base dei processi di Windows PowerShell, vengono seguite alcune convenzioni usate da System.Diagnostics.Process.</span><span class="sxs-lookup"><span data-stu-id="a8b47-114">Because the .NET System.Diagnostics.Process class is the foundation for Windows PowerShell processes, it follows some of the conventions used by System.Diagnostics.Process.</span></span> <span data-ttu-id="a8b47-115">Una di queste è che il nome di processo per un eseguibile non include mai l'estensione "exe" alla fine del nome del file eseguibile.</span><span class="sxs-lookup"><span data-stu-id="a8b47-115">One of those conventions is that the process name for an executable never includes the ".exe" at the end of the executable name.</span></span>

<span data-ttu-id="a8b47-116">**Get-Process** accetta anche più valori per il parametro Name.</span><span class="sxs-lookup"><span data-stu-id="a8b47-116">**Get-Process** also accepts multiple values for the Name parameter.</span></span>

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="a8b47-117">È possibile usare il parametro ComputerName di Get-Process per ottenere processi nei computer remoti.</span><span class="sxs-lookup"><span data-stu-id="a8b47-117">You can use the ComputerName parameter of Get-Process to get processes on remote computers.</span></span> <span data-ttu-id="a8b47-118">Il comando seguente recupera ad esempio i processi di PowerShell nel computer locale (rappresentato da "localhost") e in due computer remoti.</span><span class="sxs-lookup"><span data-stu-id="a8b47-118">For example, the following command gets the PowerShell processes on the local computer (represented by "localhost") and on two remote computers.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="a8b47-119">I nomi dei computer non sono evidenti in questa visualizzazione, ma sono archiviati nella proprietà MachineName degli oggetti processo restituiti da Get-Process.</span><span class="sxs-lookup"><span data-stu-id="a8b47-119">The computer names are not evident in this display, but they are stored in the MachineName property of the process objects that Get-Process returns.</span></span> <span data-ttu-id="a8b47-120">Il comando seguente usa il cmdlet Format-Table per visualizzare l'ID di processo e le proprietà ProcessName e MachineName (ComputerName) degli oggetti processo.</span><span class="sxs-lookup"><span data-stu-id="a8b47-120">The following command uses the Format-Table cmdlet to display the process ID, ProcessName and MachineName (ComputerName) properties of the process objects.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

<span data-ttu-id="a8b47-121">Questo comando più complesso aggiunge la proprietà MachineName alla visualizzazione standard di Get-Process.</span><span class="sxs-lookup"><span data-stu-id="a8b47-121">This more complex command adds the MachineName property to the standard Get-Process display.</span></span>

```
PS> Get-Process powershell -ComputerName localhost, Server01, Server02 |
    Format-Table -Property Handles,
        @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}},
        @{Label="PM(K)";Expression={[int]($_.PM/1024)}},
        @{Label="WS(K)";Expression={[int]($_.WS/1024)}},
        @{Label="VM(M)";Expression={[int]($_.VM/1MB)}},
        @{Label="CPU(s)";Expression={if ($_.CPU -ne $() {$_.CPU.ToString("N")}}},
        Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a><span data-ttu-id="a8b47-122">Arresto dei processi (Stop-Process)</span><span class="sxs-lookup"><span data-stu-id="a8b47-122">Stopping Processes (Stop-Process)</span></span>

<span data-ttu-id="a8b47-123">Windows PowerShell offre la massima flessibilità per elencare i processi, ma cosa succede con l'arresto di un processo?</span><span class="sxs-lookup"><span data-stu-id="a8b47-123">Windows PowerShell gives you flexibility for listing processes, but what about stopping a process?</span></span>

<span data-ttu-id="a8b47-124">Il cmdlet **Stop-Process** accetta un nome o un ID per specificare un processo da arrestare.</span><span class="sxs-lookup"><span data-stu-id="a8b47-124">The **Stop-Process** cmdlet takes a Name or Id to specify a process you want to stop.</span></span> <span data-ttu-id="a8b47-125">La possibilità di arrestare i processi dipende dalle autorizzazioni di cui si dispone.</span><span class="sxs-lookup"><span data-stu-id="a8b47-125">Your ability to stop processes depends on your permissions.</span></span> <span data-ttu-id="a8b47-126">Alcuni processi non possono essere arrestati.</span><span class="sxs-lookup"><span data-stu-id="a8b47-126">Some processes cannot be stopped.</span></span> <span data-ttu-id="a8b47-127">Se ad esempio si prova ad arrestare il processo inattivo, viene visualizzato un errore:</span><span class="sxs-lookup"><span data-stu-id="a8b47-127">For example, if you try to stop the idle process, you get an error:</span></span>

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

<span data-ttu-id="a8b47-128">È anche possibile forzare la richiesta di conferma con il parametro **Confirm**.</span><span class="sxs-lookup"><span data-stu-id="a8b47-128">You can also force prompting with the **Confirm** parameter.</span></span> <span data-ttu-id="a8b47-129">Questo parametro è particolarmente utile se si usa un carattere jolly quando si specifica il nome del processo, poiché si potrebbero trovare accidentalmente corrispondenze con alcuni processi che non si vuole arrestare:</span><span class="sxs-lookup"><span data-stu-id="a8b47-129">This parameter is particularly useful if you use a wildcard when specifying the process name, because you may accidentally match some processes you do not want to stop:</span></span>

```
PS> Stop-Process -Name t*,e* -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "explorer (408)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "taskmgr (4072)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
```

<span data-ttu-id="a8b47-130">La manipolazione di un processo complesso è possibile con alcuni cmdlet per i filtri degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="a8b47-130">Complex process manipulation is possible by using some of the object filtering cmdlets.</span></span> <span data-ttu-id="a8b47-131">Dal momento che un oggetto Process ha una proprietà Responding che restituisce true se non risponde, è possibile arrestare tutte le applicazioni che non rispondono con il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="a8b47-131">Because a Process object has a Responding property that is true when it is no longer responding, you can stop all nonresponsive applications with the following command:</span></span>

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

<span data-ttu-id="a8b47-132">Lo stesso approccio è applicabile anche ad altre situazioni.</span><span class="sxs-lookup"><span data-stu-id="a8b47-132">You can use the same approach in other situations.</span></span> <span data-ttu-id="a8b47-133">Si supponga ad esempio che un'applicazione dell'area di notifica secondaria venga eseguita automaticamente quando gli utenti avviano un'altra applicazione.</span><span class="sxs-lookup"><span data-stu-id="a8b47-133">For example, suppose a secondary notification area application automatically runs when users start another application.</span></span> <span data-ttu-id="a8b47-134">È possibile che non funzioni correttamente nelle sessioni di Servizi Terminal, ma si vuole comunque mantenerla nelle sessioni in esecuzione nella console del computer fisico.</span><span class="sxs-lookup"><span data-stu-id="a8b47-134">You may find that this does not work correctly in Terminal Services sessions, but you still want to keep it in sessions that run on the physical computer console.</span></span> <span data-ttu-id="a8b47-135">Le sessioni connesse al desktop del computer fisico hanno sempre un ID di sessione uguale a 0, pertanto è possibile arrestare tutte le istanze del processo che si trovano in altre sessioni usando **Where-Object** e il processo, **SessionId**:</span><span class="sxs-lookup"><span data-stu-id="a8b47-135">Sessions connected to the physical computer desktop always have a session ID of 0, so you can stop all instances of the process that are in other sessions by using **Where-Object** and the process, **SessionId**:</span></span>

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

<span data-ttu-id="a8b47-136">Il cmdlet Stop-Process non dispone di un parametro ComputerName.</span><span class="sxs-lookup"><span data-stu-id="a8b47-136">The Stop-Process cmdlet does not have a ComputerName parameter.</span></span> <span data-ttu-id="a8b47-137">Per eseguire un comando Stop-Process in un computer remoto, pertanto è necessario usare il cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="a8b47-137">Therefore, to run a stop process command on a remote computer, you need to use the Invoke-Command cmdlet.</span></span> <span data-ttu-id="a8b47-138">Per arrestare ad esempio arrestare il processo PowerShell nel computer remoto Server01, digitare:</span><span class="sxs-lookup"><span data-stu-id="a8b47-138">For example, to stop the PowerShell process on the Server01 remote computer, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a><span data-ttu-id="a8b47-139">Arresto di tutte le altre sessioni di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a8b47-139">Stopping All Other Windows PowerShell Sessions</span></span>

<span data-ttu-id="a8b47-140">In alcuni casi può essere utile interrompere tutte le sessioni di Windows PowerShell in esecuzione, fatta eccezione per quella corrente.</span><span class="sxs-lookup"><span data-stu-id="a8b47-140">It may occasionally be useful to be able to stop all running Windows PowerShell sessions other than the current session.</span></span> <span data-ttu-id="a8b47-141">Se una sessione usa troppe risorse o non è accessibile (perché in esecuzione in modalità remota o in un'altra sessione desktop), potrebbe risultare impossibile arrestarla direttamente.</span><span class="sxs-lookup"><span data-stu-id="a8b47-141">If a session is using too many resources or is inaccessible (it may be running remotely or in another desktop session), you may not be able to directly stop it.</span></span> <span data-ttu-id="a8b47-142">Se si prova ad arrestare tutte le sessioni in esecuzione, invece, la sessione corrente può essere arrestata.</span><span class="sxs-lookup"><span data-stu-id="a8b47-142">If you try to stop all running sessions, however, the current session may be terminated instead.</span></span>

<span data-ttu-id="a8b47-143">Ogni sessione di Windows PowerShell ha un identificatore di processo (PID) per la variabile di ambiente che contiene l'ID del processo di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a8b47-143">Each Windows PowerShell session has an environment variable PID that contains the Id of the Windows PowerShell process.</span></span> <span data-ttu-id="a8b47-144">È possibile controllare la variabile $PID sulla base dell'ID di ogni sessione e terminare solo le sessioni di Windows PowerShell che hanno un ID diverso. Il seguente comando della pipeline esegue questa operazione e restituisce l'elenco delle sessioni terminate (grazie all'uso del parametro **PassThru**):</span><span class="sxs-lookup"><span data-stu-id="a8b47-144">You can check the $PID against the Id of each session and terminate only Windows PowerShell sessions that have a different Id. The following pipeline command does this and returns the list of terminated sessions (because of the use of the **PassThru** parameter):</span></span>

```
PS> Get-Process -Name powershell | Where-Object -FilterScript {$_.Id -ne $PID} | Stop-Process -PassThru

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    334       9    23348      29136   143     1.03    388 powershell
    304       9    23152      29040   143     1.03    632 powershell
    302       9    20916      26804   143     1.03   1116 powershell
    335       9    25656      31412   143     1.09   3452 powershell
    303       9    23156      29044   143     1.05   3608 powershell
    287       9    21044      26928   143     1.02   3672 powershell
```

## <a name="starting-debugging-and-waiting-for-processes"></a><span data-ttu-id="a8b47-145">Avvio, debug e attesa di processi</span><span class="sxs-lookup"><span data-stu-id="a8b47-145">Starting, Debugging, and Waiting for Processes</span></span>

<span data-ttu-id="a8b47-146">Windows PowerShell include anche cmdlet per avviare (o riavviare) un processo, eseguirne il debug e attenderne il completamento prima di eseguire un comando.</span><span class="sxs-lookup"><span data-stu-id="a8b47-146">Windows PowerShell also comes with cmdlets to start (or restart), debug a process, and wait for a process to complete before running a command.</span></span> <span data-ttu-id="a8b47-147">Per informazioni su questi cmdlet, vedere l'argomento della Guida corrispondente per ciascun cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a8b47-147">For information about these cmdlets, see the cmdlet help topic for each cmdlet.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8b47-148">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a8b47-148">See Also</span></span>

- <span data-ttu-id="a8b47-149">[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)</span><span class="sxs-lookup"><span data-stu-id="a8b47-149">[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)</span></span>
- <span data-ttu-id="a8b47-150">[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)</span><span class="sxs-lookup"><span data-stu-id="a8b47-150">[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)</span></span>
- [<span data-ttu-id="a8b47-151">Start-Process</span><span class="sxs-lookup"><span data-stu-id="a8b47-151">Start-Process</span></span>](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [<span data-ttu-id="a8b47-152">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="a8b47-152">Wait-Process</span></span>](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [<span data-ttu-id="a8b47-153">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="a8b47-153">Debug-Process</span></span>](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [<span data-ttu-id="a8b47-154">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="a8b47-154">Invoke-Command</span></span>](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)