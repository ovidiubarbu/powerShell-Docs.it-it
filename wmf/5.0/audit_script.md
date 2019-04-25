---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 28cd186ab3a08a0da4ff81f5a21514f239770d13
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058081"
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="2fa1b-102">Traccia e registrazione degli script</span><span class="sxs-lookup"><span data-stu-id="2fa1b-102">Script Tracing and Logging</span></span>

<span data-ttu-id="2fa1b-103">Mentre Windows PowerShell ha già l'impostazione di Criteri di gruppo **LogPipelineExecutionDetails** per la registrazione della chiamata dei cmdlet, sono molte le funzionalità del linguaggio di scripting PowerShell che potrebbe essere utile registrare e/o controllare.</span><span class="sxs-lookup"><span data-stu-id="2fa1b-103">While Windows PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell’s scripting language has plenty of features that you might want to log and/or audit.</span></span> <span data-ttu-id="2fa1b-104">La nuova funzionalità di traccia dettagliata degli script consente di monitorare e analizzare nel dettaglio l'uso degli script di Windows PowerShell in un sistema.</span><span class="sxs-lookup"><span data-stu-id="2fa1b-104">The new Detailed Script Tracing feature lets you enable detailed tracking and analysis of Windows PowerShell scripting use on a system.</span></span> <span data-ttu-id="2fa1b-105">Dopo aver abilitato la traccia dettagliata degli script, Windows PowerShell registra tutti i blocchi di script nel registro eventi ETW, **Microsoft-Windows-PowerShell/Operational**.</span><span class="sxs-lookup"><span data-stu-id="2fa1b-105">After you enable detailed script tracing, Windows PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="2fa1b-106">Se un blocco di script crea un altro blocco di script (ad esempio, uno script che chiama il cmdlet Invoke-Expression su una stringa), viene registrato anche il blocco di script risultante.</span><span class="sxs-lookup"><span data-stu-id="2fa1b-106">If a script block creates another script block (for example, a script that calls the Invoke-Expression cmdlet on a string), that resulting script block is logged as well.</span></span>

<span data-ttu-id="2fa1b-107">La registrazione di questi eventi può essere abilitata tramite l'impostazione di Criteri di gruppo **Attiva registrazione blocco script di PowerShell** in Modelli amministrativi -> Componenti di Windows -> Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fa1b-107">Logging of these events can be enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting (in Administrative Templates -> Windows Components -> Windows PowerShell).</span></span>

<span data-ttu-id="2fa1b-108">Gli eventi sono:</span><span class="sxs-lookup"><span data-stu-id="2fa1b-108">The events are:</span></span>

| <span data-ttu-id="2fa1b-109">Canale</span><span class="sxs-lookup"><span data-stu-id="2fa1b-109">Channel</span></span> | <span data-ttu-id="2fa1b-110">Operativo</span><span class="sxs-lookup"><span data-stu-id="2fa1b-110">Operational</span></span>                                 |
|---------|---------------------------------------------|
| <span data-ttu-id="2fa1b-111">Livello</span><span class="sxs-lookup"><span data-stu-id="2fa1b-111">Level</span></span>   | <span data-ttu-id="2fa1b-112">Verbose</span><span class="sxs-lookup"><span data-stu-id="2fa1b-112">Verbose</span></span>                                     |
| <span data-ttu-id="2fa1b-113">Opcode</span><span class="sxs-lookup"><span data-stu-id="2fa1b-113">Opcode</span></span>  | <span data-ttu-id="2fa1b-114">Creazione</span><span class="sxs-lookup"><span data-stu-id="2fa1b-114">Create</span></span>                                      |
| <span data-ttu-id="2fa1b-115">Attività</span><span class="sxs-lookup"><span data-stu-id="2fa1b-115">Task</span></span>    | <span data-ttu-id="2fa1b-116">CommandStart</span><span class="sxs-lookup"><span data-stu-id="2fa1b-116">CommandStart</span></span>                                |
| <span data-ttu-id="2fa1b-117">Parola chiave</span><span class="sxs-lookup"><span data-stu-id="2fa1b-117">Keyword</span></span> | <span data-ttu-id="2fa1b-118">Spazio di esecuzione</span><span class="sxs-lookup"><span data-stu-id="2fa1b-118">Runspace</span></span>                                    |
| <span data-ttu-id="2fa1b-119">ID evento</span><span class="sxs-lookup"><span data-stu-id="2fa1b-119">EventId</span></span> | <span data-ttu-id="2fa1b-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="2fa1b-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>  |
| <span data-ttu-id="2fa1b-121">Messaggio</span><span class="sxs-lookup"><span data-stu-id="2fa1b-121">Message</span></span> | <span data-ttu-id="2fa1b-122">Creazione del testo di Scriptblock (%1 di %2):</span><span class="sxs-lookup"><span data-stu-id="2fa1b-122">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="2fa1b-123">%3</span><span class="sxs-lookup"><span data-stu-id="2fa1b-123">%3</span></span> </br> <span data-ttu-id="2fa1b-124">ID ScriptBlock: %4</span><span class="sxs-lookup"><span data-stu-id="2fa1b-124">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="2fa1b-125">Il testo incorporato nel messaggio è l'estensione del blocco di script compilato.</span><span class="sxs-lookup"><span data-stu-id="2fa1b-125">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="2fa1b-126">L'ID è un GUID mantenuto per tutta la durata del blocco di script.</span><span class="sxs-lookup"><span data-stu-id="2fa1b-126">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="2fa1b-127">Quando si abilita la registrazione dettagliata, la funzionalità scrive indicatori di inizio e di fine:</span><span class="sxs-lookup"><span data-stu-id="2fa1b-127">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="2fa1b-128">Canale</span><span class="sxs-lookup"><span data-stu-id="2fa1b-128">Channel</span></span> | <span data-ttu-id="2fa1b-129">Operativo</span><span class="sxs-lookup"><span data-stu-id="2fa1b-129">Operational</span></span>                                            |
|---------|--------------------------------------------------------|
| <span data-ttu-id="2fa1b-130">Livello</span><span class="sxs-lookup"><span data-stu-id="2fa1b-130">Level</span></span>   | <span data-ttu-id="2fa1b-131">Verbose</span><span class="sxs-lookup"><span data-stu-id="2fa1b-131">Verbose</span></span>                                                |
| <span data-ttu-id="2fa1b-132">Opcode</span><span class="sxs-lookup"><span data-stu-id="2fa1b-132">Opcode</span></span>  | <span data-ttu-id="2fa1b-133">Apri (/ Chiudi)</span><span class="sxs-lookup"><span data-stu-id="2fa1b-133">Open (/ Close)</span></span>                                         |
| <span data-ttu-id="2fa1b-134">Attività</span><span class="sxs-lookup"><span data-stu-id="2fa1b-134">Task</span></span>    | <span data-ttu-id="2fa1b-135">CommandStart (/ CommandStop)</span><span class="sxs-lookup"><span data-stu-id="2fa1b-135">CommandStart (/ CommandStop)</span></span>                           |
| <span data-ttu-id="2fa1b-136">Parola chiave</span><span class="sxs-lookup"><span data-stu-id="2fa1b-136">Keyword</span></span> | <span data-ttu-id="2fa1b-137">Spazio di esecuzione</span><span class="sxs-lookup"><span data-stu-id="2fa1b-137">Runspace</span></span>                                               |
| <span data-ttu-id="2fa1b-138">ID evento</span><span class="sxs-lookup"><span data-stu-id="2fa1b-138">EventId</span></span> | <span data-ttu-id="2fa1b-139">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="2fa1b-139">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="2fa1b-140">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="2fa1b-140">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="2fa1b-141">Message</span><span class="sxs-lookup"><span data-stu-id="2fa1b-141">Message</span></span> | <span data-ttu-id="2fa1b-142">Chiamata ID ScriptBlock avviata (/ completata): %1</span><span class="sxs-lookup"><span data-stu-id="2fa1b-142">Started (/ Completed) invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="2fa1b-143">ID spazio di esecuzione: %2</span><span class="sxs-lookup"><span data-stu-id="2fa1b-143">Runspace ID: %2</span></span> |

<span data-ttu-id="2fa1b-144">L'ID è il GUID che rappresenta il blocco di script (correlabile con l'ID evento 0x1008) e l'ID dello spazio di esecuzione rappresenta lo spazio di esecuzione in cui è stato eseguito il blocco di script.</span><span class="sxs-lookup"><span data-stu-id="2fa1b-144">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="2fa1b-145">I segni di percentuale nel messaggio di chiamata rappresentano le proprietà ETW strutturate.</span><span class="sxs-lookup"><span data-stu-id="2fa1b-145">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="2fa1b-146">Anche se vengono sostituiti con i valori effettivi nel testo del messaggio, un modo più efficiente per accedervi è recuperare il messaggio con il cmdlet Get-WinEvent e quindi usare la matrice **Properties** del messaggio.</span><span class="sxs-lookup"><span data-stu-id="2fa1b-146">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="2fa1b-147">Di seguito è riportato un esempio di come questa funzionalità possa essere utile per intercettare un tentativo non autorizzato di crittografare e offuscare uno script:</span><span class="sxs-lookup"><span data-stu-id="2fa1b-147">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR “encryption”
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

<span data-ttu-id="2fa1b-148">L'esecuzione di questo codice genera le voci di log seguenti:</span><span class="sxs-lookup"><span data-stu-id="2fa1b-148">Running this generates the following log entries:</span></span>

```
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

Se la lunghezza del blocco di script supera la capacità di ETW per un singolo evento, Windows PowerShell suddivide lo script in più parti. <span data-ttu-id="2fa1b-150">Ecco il codice di esempio per ricomporre uno script dai relativi messaggi di log:</span><span class="sxs-lookup"><span data-stu-id="2fa1b-150">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="2fa1b-151">Come per tutti i sistemi di registrazione con un buffer limitato per la conservazione (ad esempio, i log ETW), un attacco contro questa infrastruttura si basa sull'inondare (flood) il log di eventi spuri per nascondere prove precedenti.</span><span class="sxs-lookup"><span data-stu-id="2fa1b-151">As with all logging systems that have a limited retention buffer (i.e. ETW logs), one attack against this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="2fa1b-152">Per proteggersi da questo tipo di attacco, assicurarsi di aver configurato una qualche forma di raccolta del registro eventi (ad esempio, l'inoltro degli eventi di Windows o il [monitoraggio del registro eventi di Windows per individuare i nemici](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)) per spostare i registri eventi in una posizione al di fuori del computer non appena possibile.</span><span class="sxs-lookup"><span data-stu-id="2fa1b-152">To protect yourself from this attack, ensure that you have some form of event log collection set up (i.e., Windows Event Forwarding, [Spotting the Adversary with Windows Event Log Monitoring](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)) to move event logs off of the computer as soon as possible.</span></span>
