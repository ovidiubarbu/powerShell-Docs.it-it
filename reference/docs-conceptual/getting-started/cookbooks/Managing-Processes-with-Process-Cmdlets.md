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
# <a name="managing-processes-with-process-cmdlets"></a>Gestione dei processi con i cmdlet Process

È possibile usare i cmdlet Process in Windows PowerShell per gestire i processi locali e remoti in Windows PowerShell.

## <a name="getting-processes-get-process"></a>Recupero di processi (Get-Process)

Per ottenere i processi in esecuzione nel computer locale, eseguire il comando **Get-Process** senza parametri.

È possibile recuperare processi specifici specificandone il nome o l'ID. Il comando seguente consente di recuperare il processo Idle:

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

Anche se è normale per i cmdlet non restituire dati in alcune situazioni, quando si specifica un processo mediante il relativo ProcessId **Get-Process** genera un errore se vengono rilevate corrispondenze, poiché l'uso abituale è quello di recuperare un processo in esecuzione noto. Se non è presente alcun processo con tale ID, è probabile che l'ID non sia corretto o che il processo in questione sia già terminato:

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

È possibile usare il parametro Name del cmdlet Get-Process per specificare un sottoinsieme di processi in base al nome di processo. Il parametro Name può ottenere più nomi in un elenco con valori delimitati da virgole e supporta l'uso dei caratteri jolly, pertanto è possibile digitare modelli di nomi.

Il comando seguente recupera ad esempio i processi i cui nomi iniziano con "ex".

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

Poiché la classe .NET System.Diagnostics.Process è alla base dei processi di Windows PowerShell, vengono seguite alcune convenzioni usate da System.Diagnostics.Process. Una di queste è che il nome di processo per un eseguibile non include mai l'estensione "exe" alla fine del nome del file eseguibile.

**Get-Process** accetta anche più valori per il parametro Name.

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

È possibile usare il parametro ComputerName di Get-Process per ottenere processi nei computer remoti. Il comando seguente recupera ad esempio i processi di PowerShell nel computer locale (rappresentato da "localhost") e in due computer remoti.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

I nomi dei computer non sono evidenti in questa visualizzazione, ma sono archiviati nella proprietà MachineName degli oggetti processo restituiti da Get-Process. Il comando seguente usa il cmdlet Format-Table per visualizzare l'ID di processo e le proprietà ProcessName e MachineName (ComputerName) degli oggetti processo.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

Questo comando più complesso aggiunge la proprietà MachineName alla visualizzazione standard di Get-Process.

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

## <a name="stopping-processes-stop-process"></a>Arresto dei processi (Stop-Process)

Windows PowerShell offre la massima flessibilità per elencare i processi, ma cosa succede con l'arresto di un processo?

Il cmdlet **Stop-Process** accetta un nome o un ID per specificare un processo da arrestare. La possibilità di arrestare i processi dipende dalle autorizzazioni di cui si dispone. Alcuni processi non possono essere arrestati. Se ad esempio si prova ad arrestare il processo inattivo, viene visualizzato un errore:

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

È anche possibile forzare la richiesta di conferma con il parametro **Confirm**. Questo parametro è particolarmente utile se si usa un carattere jolly quando si specifica il nome del processo, poiché si potrebbero trovare accidentalmente corrispondenze con alcuni processi che non si vuole arrestare:

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

La manipolazione di un processo complesso è possibile con alcuni cmdlet per i filtri degli oggetti. Dal momento che un oggetto Process ha una proprietà Responding che restituisce true se non risponde, è possibile arrestare tutte le applicazioni che non rispondono con il comando seguente:

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

Lo stesso approccio è applicabile anche ad altre situazioni. Si supponga ad esempio che un'applicazione dell'area di notifica secondaria venga eseguita automaticamente quando gli utenti avviano un'altra applicazione. È possibile che non funzioni correttamente nelle sessioni di Servizi Terminal, ma si vuole comunque mantenerla nelle sessioni in esecuzione nella console del computer fisico. Le sessioni connesse al desktop del computer fisico hanno sempre un ID di sessione uguale a 0, pertanto è possibile arrestare tutte le istanze del processo che si trovano in altre sessioni usando **Where-Object** e il processo, **SessionId**:

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

Il cmdlet Stop-Process non dispone di un parametro ComputerName. Per eseguire un comando Stop-Process in un computer remoto, pertanto è necessario usare il cmdlet Invoke-Command. Per arrestare ad esempio arrestare il processo PowerShell nel computer remoto Server01, digitare:

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a>Arresto di tutte le altre sessioni di Windows PowerShell

In alcuni casi può essere utile interrompere tutte le sessioni di Windows PowerShell in esecuzione, fatta eccezione per quella corrente. Se una sessione usa troppe risorse o non è accessibile (perché in esecuzione in modalità remota o in un'altra sessione desktop), potrebbe risultare impossibile arrestarla direttamente. Se si prova ad arrestare tutte le sessioni in esecuzione, invece, la sessione corrente può essere arrestata.

Ogni sessione di Windows PowerShell ha un identificatore di processo (PID) per la variabile di ambiente che contiene l'ID del processo di Windows PowerShell. È possibile controllare la variabile $PID sulla base dell'ID di ogni sessione e terminare solo le sessioni di Windows PowerShell che hanno un ID diverso. Il seguente comando della pipeline esegue questa operazione e restituisce l'elenco delle sessioni terminate (grazie all'uso del parametro **PassThru**):

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

## <a name="starting-debugging-and-waiting-for-processes"></a>Avvio, debug e attesa di processi

Windows PowerShell include anche cmdlet per avviare (o riavviare) un processo, eseguirne il debug e attenderne il completamento prima di eseguire un comando. Per informazioni su questi cmdlet, vedere l'argomento della Guida corrispondente per ciascun cmdlet.

## <a name="see-also"></a>Vedere anche

- [Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)
- [Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)
- [Start-Process](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [Wait-Process](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [Debug-Process](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)