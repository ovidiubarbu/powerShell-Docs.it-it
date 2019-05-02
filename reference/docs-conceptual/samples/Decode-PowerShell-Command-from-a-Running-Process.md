---
ms.date: 11/13/2018
keywords: powershell,cmdlet
title: Decodificare un comando PowerShell da un processo in esecuzione
author: randomnote1
ms.openlocfilehash: a0602070a8c5b60ce0bb09e227690f48d970a868
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086239"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a>Decodificare un comando PowerShell da un processo in esecuzione

In alcuni casi, potrebbe essere in esecuzione un processo di PowerShell che usa una grande quantità di risorse.
Questo processo potrebbe essere in esecuzione nel contesto di un processo dell'[Utilità di pianificazione][] o di un processo di [SQL Server Agent][]. In presenza di più processi di PowerShell in esecuzione, può essere difficile sapere quale processo rappresenta il problema. Questo articolo illustra come decodificare un blocco di script eseguito da un processo di PowerShell.

## <a name="create-a-long-running-process"></a>Creare un processo a esecuzione prolungata

Per una dimostrazione di questo scenario, aprire una nuova finestra di PowerShell ed eseguire il codice seguente. Viene eseguito un comando di PowerShell che restituisce un numero al minuto per 10 minuti.

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

## <a name="view-the-process"></a>Visualizzare il processo

Il corpo del comando eseguito da PowerShell viene archiviato nella proprietà **CommandLine** della classe [Win32_Process][]. Se il comando è un [comando codificato][], la proprietà **CommandLine** contiene la stringa "EncodedCommand". È possibile usare queste informazioni per deoffuscare il comando codificato tramite la procedura seguente.

Avviare PowerShell come amministratore. È fondamentale che PowerShell sia in esecuzione come amministratore. In caso contrario non viene restituito alcun risultato per le query sui processi in esecuzione.

Eseguire il comando seguente per ottenere tutti i processi di PowerShell con un comando codificato:

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

Il comando seguente crea un oggetto PowerShell personalizzato che contiene l'ID del processo e il comando codificato.

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

Ora il comando codificato può essere decodificato. Il frammento di codice seguente scorre l'oggetto dei dettagli del comando, decodifica il comando codificato e aggiunge il comando decodificato all'oggetto per un'analisi più approfondita.

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

A questo punto è possibile esaminare il comando decodificato selezionando la proprietà del comando decodificato.

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
[SQL Server Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
[Comando codificato]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
