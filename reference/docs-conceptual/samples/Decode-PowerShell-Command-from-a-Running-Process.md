---
ms.date: 11/13/2018
keywords: powershell,cmdlet
title: Decodificare un comando PowerShell da un processo in esecuzione
author: randomnote1
ms.openlocfilehash: a0602070a8c5b60ce0bb09e227690f48d970a868
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401236"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a><span data-ttu-id="e2c7c-103">Decodificare un comando PowerShell da un processo in esecuzione</span><span class="sxs-lookup"><span data-stu-id="e2c7c-103">Decode a PowerShell command from a running process</span></span>

<span data-ttu-id="e2c7c-104">In alcuni casi, potrebbe essere un processo in esecuzione che sta utilizzando una grande quantità di risorse di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2c7c-104">At times, you may have a PowerShell process running that is taking up a large amount of resources.</span></span>
<span data-ttu-id="e2c7c-105">Questo processo potrebbe essere in esecuzione nel contesto di un [utilità di pianificazione][] processo o un' [SQL Server Agent][] processo.</span><span class="sxs-lookup"><span data-stu-id="e2c7c-105">This process could be running in the context of a [Task Scheduler][] job or a [SQL Server Agent][] job.</span></span> <span data-ttu-id="e2c7c-106">In cui sono presenti più processi di PowerShell in esecuzione, può essere difficile sapere quale processo rappresenta il problema.</span><span class="sxs-lookup"><span data-stu-id="e2c7c-106">Where there are multiple PowerShell processes running, it can be difficult to know which process represents the problem.</span></span> <span data-ttu-id="e2c7c-107">Questo articolo illustra come decodificare un blocco di script che è attualmente in esecuzione un processo di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2c7c-107">This article shows how to decode a script block that a PowerShell process is currently running.</span></span>

## <a name="create-a-long-running-process"></a><span data-ttu-id="e2c7c-108">Creare un processo a esecuzione prolungata</span><span class="sxs-lookup"><span data-stu-id="e2c7c-108">Create a long running process</span></span>

<span data-ttu-id="e2c7c-109">Per illustrare questo scenario, aprire una nuova finestra di PowerShell ed eseguire il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="e2c7c-109">To demonstrate this scenario, open a new PowerShell window and run the following code.</span></span> <span data-ttu-id="e2c7c-110">Esegue un comando di PowerShell che restituisce un numero al minuto per 10 minuti.</span><span class="sxs-lookup"><span data-stu-id="e2c7c-110">It executes a PowerShell command that outputs a number every minute for 10 minutes.</span></span>

```powershell
powershell.exe -Command {
    $i = 1
    while ( $i -le 10 )
    {
        Write-Output -InputObject $i
        Start-Sleep -Seconds 60
        $i++
    }
}
```

## <a name="view-the-process"></a><span data-ttu-id="e2c7c-111">Visualizzare il processo</span><span class="sxs-lookup"><span data-stu-id="e2c7c-111">View the process</span></span>

<span data-ttu-id="e2c7c-112">Il corpo del comando che PowerShell è in esecuzione viene archiviato nel **CommandLine** proprietà delle [Win32_Process][] classe.</span><span class="sxs-lookup"><span data-stu-id="e2c7c-112">The body of the command which PowerShell is executing is stored in the **CommandLine** property of the [Win32_Process][] class.</span></span> <span data-ttu-id="e2c7c-113">Se il comando è un' [codificato comando][], il **CommandLine** proprietà contiene la stringa "EncodedCommand".</span><span class="sxs-lookup"><span data-stu-id="e2c7c-113">If the command is an [encoded command][], the **CommandLine** property contains the string "EncodedCommand".</span></span> <span data-ttu-id="e2c7c-114">Utilizzando queste informazioni, il comando codificato può essere deoffuscato tramite la procedura seguente.</span><span class="sxs-lookup"><span data-stu-id="e2c7c-114">Using this information, the encoded command can be de-obfuscated via the following process.</span></span>

<span data-ttu-id="e2c7c-115">Avviare PowerShell come amministratore.</span><span class="sxs-lookup"><span data-stu-id="e2c7c-115">Start PowerShell as Administrator.</span></span> <span data-ttu-id="e2c7c-116">È fondamentale che PowerShell sia in esecuzione come amministratore, in caso contrario, viene restituito alcun risultato quando si eseguono i processi in esecuzione di query.</span><span class="sxs-lookup"><span data-stu-id="e2c7c-116">It is vital that PowerShell is running as administrator, otherwise no results are returned when querying the running processes.</span></span>

<span data-ttu-id="e2c7c-117">Eseguire il comando seguente per ottenere tutti i processi di PowerShell con un comando codificato:</span><span class="sxs-lookup"><span data-stu-id="e2c7c-117">Execute the following command to get all of the PowerShell processes that have an encoded command:</span></span>

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

<span data-ttu-id="e2c7c-118">Il comando seguente crea un oggetto PowerShell personalizzato che contiene l'ID del processo e il comando codificato.</span><span class="sxs-lookup"><span data-stu-id="e2c7c-118">The following command creates a custom PowerShell object that contains the process ID and the encoded command.</span></span>

```powershell
$commandDetails = $powerShellProcesses | Select-Object -Property ProcessId,
@{
    name       = 'EncodedCommand'
    expression = {
        if ( $_.CommandLine -match 'encodedCommand (.*) -inputFormat' )
        {
            return $matches[1]
        }
    }
}
```

<span data-ttu-id="e2c7c-119">Ora il comando codificato può essere decodificato.</span><span class="sxs-lookup"><span data-stu-id="e2c7c-119">Now the encoded command can be decoded.</span></span> <span data-ttu-id="e2c7c-120">Il frammento di codice seguente scorre l'oggetto di dettagli del comando, decodifica il comando con codificato e aggiunge il comando decodificato all'oggetto per un'analisi più approfondita.</span><span class="sxs-lookup"><span data-stu-id="e2c7c-120">The following snippet iterates over the command details object, decodes the encoded command, and adds the decoded command back to the object for further investigation.</span></span>

```powershell
$commandDetails | ForEach-Object -Process {
    # Get the current process
    $currentProcess = $_

    # Convert the Base 64 string to a Byte Array
    $commandBytes = [System.Convert]::FromBase64String($currentProcess.EncodedCommand)

    # Convert the Byte Array to a string
    $decodedCommand = [System.Text.Encoding]::Unicode.GetString($commandBytes)

    # Add the decoded command back to the object
    $commandDetails |
        Where-Object -FilterScript { $_.ProcessId -eq $_.ProcessId } |
        Add-Member -MemberType NoteProperty -Name DecodedCommand -Value $decodedCommand
}
$commandDetails[0]
```

<span data-ttu-id="e2c7c-121">A questo punto è possibile esaminare il comando decodificato selezionando la proprietà command decodificato.</span><span class="sxs-lookup"><span data-stu-id="e2c7c-121">The decoded command can now be reviewed by selecting the decoded command property.</span></span>

```output
ProcessId      : 8752
EncodedCommand : IAAKAAoACgAgAAoAIAAgACAAIAAkAGkAIAA9ACAAMQAgAAoACgAKACAACgAgACAAIAAgAHcAaABpAGwAZQAgACgAIAAkAGkAIAAtAG
                 wAZQAgADEAMAAgACkAIAAKAAoACgAgAAoAIAAgACAAIAB7ACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABXAHIAaQB0AGUALQBP
                 AHUAdABwAHUAdAAgAC0ASQBuAHAAdQB0AE8AYgBqAGUAYwB0ACAAJABpACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABTAHQAYQ
                 ByAHQALQBTAGwAZQBlAHAAIAAtAFMAZQBjAG8AbgBkAHMAIAA2ADAAIAAKAAoACgAgAAoAIAAgACAAIAAgACAAIAAgACQAaQArACsA
                 IAAKAAoACgAgAAoAIAAgACAAIAB9ACAACgAKAAoAIAAKAA==
DecodedCommand :
                     $i = 1

                     while ( $i -le 10 )

                     {

                         Write-Output -InputObject $i

                         Start-Sleep -Seconds 60

                         $i++

                     }
```

[Utilità di pianificazione]: /windows/desktop/TaskSchd/task-scheduler-start-page
[Task Scheduler]: /windows/desktop/TaskSchd/task-scheduler-start-page
[SQL Server Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
[codificato comando]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
[encoded command]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
