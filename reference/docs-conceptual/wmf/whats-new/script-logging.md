---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
title: Traccia e registrazione degli script
ms.openlocfilehash: 6b7e5022cb4c974da5ddb3d670b5808dc9fb7bdc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71147801"
---
# <a name="script-tracing-and-logging"></a>Traccia e registrazione degli script

Mentre PowerShell ha già l'impostazione di Criteri di gruppo **LogPipelineExecutionDetails** per la registrazione della chiamata dei cmdlet, sono molte le funzionalità del linguaggio di scripting PowerShell che potrebbe essere utile registrare e controllare. La nuova funzionalità di traccia dettagliata consente di monitorare e analizzare nel dettaglio l'attività di script di PowerShell in un sistema. Dopo aver abilitato la traccia dettagliata degli script, PowerShell registra tutti i blocchi di script nel registro eventi ETW, **Microsoft-Windows-PowerShell/Operational**. Se un blocco di script crea un altro blocco di script, ad esempio chiamando `Invoke-Expression`, il blocco di script richiamato viene anche registrato.

La registrazione può essere abilitata tramite l'impostazione di Criteri di gruppo **Attiva registrazione blocco script di PowerShell** in **Modelli amministrativi** -> **Componenti di Windows** -> **Windows PowerShell**.

Gli eventi sono:

| Channel |                               Operativo                               |
| ------- | ----------------------------------------------------------------------- |
| Level   | Dettagliato                                                                 |
| Opcode  | Create                                                                  |
| Attività    | CommandStart                                                            |
| Parola chiave | Spazio di esecuzione                                                                |
| EventId | Engine_ScriptBlockCompiled (0x1008 = 4104)                              |
| Message | Creazione del testo di Scriptblock (%1 di %2): </br> %3 </br> ID ScriptBlock: %4 |


Il testo incorporato nel messaggio è l'estensione del blocco di script compilato. L'ID è un GUID mantenuto per tutta la durata del blocco di script.

Quando si abilita la registrazione dettagliata, la funzionalità scrive indicatori di inizio e di fine:

| Channel |                                 Operativo                                |
| ------- | -------------------------------------------------------------------------- |
| Level   | Dettagliato                                                                    |
| Opcode  | Apri/Chiudi                                                               |
| Attività    | CommandStart/CommandStop                                                 |
| Parola chiave | Spazio di esecuzione                                                                   |
| EventId | ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) / </br> ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106) |
| Message | Chiamata ID ScriptBlock avviata/completata: %1 </br> ID spazio di esecuzione: %2 |

L'ID è il GUID che rappresenta il blocco di script (correlabile con l'ID evento 0x1008) e l'ID dello spazio di esecuzione rappresenta lo spazio di esecuzione in cui è stato eseguito il blocco di script.

I segni di percentuale nel messaggio di chiamata rappresentano le proprietà ETW strutturate. Anche se vengono sostituiti con i valori effettivi nel testo del messaggio, un modo più efficiente per accedervi è recuperare il messaggio con il cmdlet Get-WinEvent e quindi usare la matrice **Properties** del messaggio.

Di seguito è riportato un esempio di come questa funzionalità possa essere utile per intercettare un tentativo non autorizzato di crittografare e offuscare uno script:

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)
}

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

L'esecuzione di questo codice genera le voci di log seguenti:

```Output
Compiling Scriptblock text (1 of 1):
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)
    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)

}
ScriptBlock ID: ad8ae740-1f33-42aa-8dfc-1314411877e3

Compiling Scriptblock text (1 of 1):
$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
ScriptBlock ID: ba11c155-d34c-4004-88e3-6502ecb50f52

Compiling Scriptblock text (1 of 1):
Invoke-Expression $decrypted
ScriptBlock ID: 856c01ca-85d7-4989-b47f-e6a09ee4eeb3

Compiling Scriptblock text (1 of 1):
Write-Host 'Pwnd'
ScriptBlock ID: 5e618414-4e77-48e3-8f65-9a863f54b4c8
```

Se la lunghezza del blocco di script supera la capacità di un singolo evento, PowerShell suddivide lo script in più parti. Ecco il codice di esempio per ricomporre uno script dai relativi messaggi di log:

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

Come per tutti i sistemi di registrazione con un buffer limitato per la conservazione, un modo per attaccare questa infrastruttura si basa sull'inondare (flood) il log di eventi spuri per nascondere prove precedenti. Per proteggersi da questo tipo di attacco, assicurarsi di avere configurato qualche forma di raccolta del registro eventi per Inoltro eventi di Windows. Per altre informazioni, vedere [Spotting the Adversary with Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm) (Individuare l'avversario con il monitoraggio del registro eventi di Windows).