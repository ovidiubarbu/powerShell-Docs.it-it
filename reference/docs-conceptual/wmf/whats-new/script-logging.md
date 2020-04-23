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
# <a name="script-tracing-and-logging"></a><span data-ttu-id="56da5-103">Traccia e registrazione degli script</span><span class="sxs-lookup"><span data-stu-id="56da5-103">Script Tracing and Logging</span></span>

<span data-ttu-id="56da5-104">Mentre PowerShell ha già l'impostazione di Criteri di gruppo **LogPipelineExecutionDetails** per la registrazione della chiamata dei cmdlet, sono molte le funzionalità del linguaggio di scripting PowerShell che potrebbe essere utile registrare e controllare.</span><span class="sxs-lookup"><span data-stu-id="56da5-104">While PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell's scripting language has several features that you might want to log and audit.</span></span> <span data-ttu-id="56da5-105">La nuova funzionalità di traccia dettagliata consente di monitorare e analizzare nel dettaglio l'attività di script di PowerShell in un sistema.</span><span class="sxs-lookup"><span data-stu-id="56da5-105">The new Detailed Script Tracing feature provides detailed tracking and analysis of PowerShell script activity on a system.</span></span> <span data-ttu-id="56da5-106">Dopo aver abilitato la traccia dettagliata degli script, PowerShell registra tutti i blocchi di script nel registro eventi ETW, **Microsoft-Windows-PowerShell/Operational**.</span><span class="sxs-lookup"><span data-stu-id="56da5-106">After enabling detailed script tracing, PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="56da5-107">Se un blocco di script crea un altro blocco di script, ad esempio chiamando `Invoke-Expression`, il blocco di script richiamato viene anche registrato.</span><span class="sxs-lookup"><span data-stu-id="56da5-107">If a script block creates another script block, for example, by calling `Invoke-Expression`, the invoked script block also logged.</span></span>

<span data-ttu-id="56da5-108">La registrazione può essere abilitata tramite l'impostazione di Criteri di gruppo **Attiva registrazione blocco script di PowerShell** in **Modelli amministrativi** -> **Componenti di Windows** -> **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="56da5-108">Logging is enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting in **Administrative Templates** -> **Windows Components** -> **Windows PowerShell**.</span></span>

<span data-ttu-id="56da5-109">Gli eventi sono:</span><span class="sxs-lookup"><span data-stu-id="56da5-109">The events are:</span></span>

| <span data-ttu-id="56da5-110">Channel</span><span class="sxs-lookup"><span data-stu-id="56da5-110">Channel</span></span> |                               <span data-ttu-id="56da5-111">Operativo</span><span class="sxs-lookup"><span data-stu-id="56da5-111">Operational</span></span>                               |
| ------- | ----------------------------------------------------------------------- |
| <span data-ttu-id="56da5-112">Level</span><span class="sxs-lookup"><span data-stu-id="56da5-112">Level</span></span>   | <span data-ttu-id="56da5-113">Dettagliato</span><span class="sxs-lookup"><span data-stu-id="56da5-113">Verbose</span></span>                                                                 |
| <span data-ttu-id="56da5-114">Opcode</span><span class="sxs-lookup"><span data-stu-id="56da5-114">Opcode</span></span>  | <span data-ttu-id="56da5-115">Create</span><span class="sxs-lookup"><span data-stu-id="56da5-115">Create</span></span>                                                                  |
| <span data-ttu-id="56da5-116">Attività</span><span class="sxs-lookup"><span data-stu-id="56da5-116">Task</span></span>    | <span data-ttu-id="56da5-117">CommandStart</span><span class="sxs-lookup"><span data-stu-id="56da5-117">CommandStart</span></span>                                                            |
| <span data-ttu-id="56da5-118">Parola chiave</span><span class="sxs-lookup"><span data-stu-id="56da5-118">Keyword</span></span> | <span data-ttu-id="56da5-119">Spazio di esecuzione</span><span class="sxs-lookup"><span data-stu-id="56da5-119">Runspace</span></span>                                                                |
| <span data-ttu-id="56da5-120">EventId</span><span class="sxs-lookup"><span data-stu-id="56da5-120">EventId</span></span> | <span data-ttu-id="56da5-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="56da5-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>                              |
| <span data-ttu-id="56da5-122">Message</span><span class="sxs-lookup"><span data-stu-id="56da5-122">Message</span></span> | <span data-ttu-id="56da5-123">Creazione del testo di Scriptblock (%1 di %2):</span><span class="sxs-lookup"><span data-stu-id="56da5-123">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="56da5-124">%3</span><span class="sxs-lookup"><span data-stu-id="56da5-124">%3</span></span> </br> <span data-ttu-id="56da5-125">ID ScriptBlock: %4</span><span class="sxs-lookup"><span data-stu-id="56da5-125">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="56da5-126">Il testo incorporato nel messaggio è l'estensione del blocco di script compilato.</span><span class="sxs-lookup"><span data-stu-id="56da5-126">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="56da5-127">L'ID è un GUID mantenuto per tutta la durata del blocco di script.</span><span class="sxs-lookup"><span data-stu-id="56da5-127">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="56da5-128">Quando si abilita la registrazione dettagliata, la funzionalità scrive indicatori di inizio e di fine:</span><span class="sxs-lookup"><span data-stu-id="56da5-128">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="56da5-129">Channel</span><span class="sxs-lookup"><span data-stu-id="56da5-129">Channel</span></span> |                                 <span data-ttu-id="56da5-130">Operativo</span><span class="sxs-lookup"><span data-stu-id="56da5-130">Operational</span></span>                                |
| ------- | -------------------------------------------------------------------------- |
| <span data-ttu-id="56da5-131">Level</span><span class="sxs-lookup"><span data-stu-id="56da5-131">Level</span></span>   | <span data-ttu-id="56da5-132">Dettagliato</span><span class="sxs-lookup"><span data-stu-id="56da5-132">Verbose</span></span>                                                                    |
| <span data-ttu-id="56da5-133">Opcode</span><span class="sxs-lookup"><span data-stu-id="56da5-133">Opcode</span></span>  | <span data-ttu-id="56da5-134">Apri/Chiudi</span><span class="sxs-lookup"><span data-stu-id="56da5-134">Open / Close</span></span>                                                               |
| <span data-ttu-id="56da5-135">Attività</span><span class="sxs-lookup"><span data-stu-id="56da5-135">Task</span></span>    | <span data-ttu-id="56da5-136">CommandStart/CommandStop</span><span class="sxs-lookup"><span data-stu-id="56da5-136">CommandStart / CommandStop</span></span>                                                 |
| <span data-ttu-id="56da5-137">Parola chiave</span><span class="sxs-lookup"><span data-stu-id="56da5-137">Keyword</span></span> | <span data-ttu-id="56da5-138">Spazio di esecuzione</span><span class="sxs-lookup"><span data-stu-id="56da5-138">Runspace</span></span>                                                                   |
| <span data-ttu-id="56da5-139">EventId</span><span class="sxs-lookup"><span data-stu-id="56da5-139">EventId</span></span> | <span data-ttu-id="56da5-140">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="56da5-140">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="56da5-141">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="56da5-141">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="56da5-142">Message</span><span class="sxs-lookup"><span data-stu-id="56da5-142">Message</span></span> | <span data-ttu-id="56da5-143">Chiamata ID ScriptBlock avviata/completata: %1</span><span class="sxs-lookup"><span data-stu-id="56da5-143">Started / Completed invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="56da5-144">ID spazio di esecuzione: %2</span><span class="sxs-lookup"><span data-stu-id="56da5-144">Runspace ID: %2</span></span> |

<span data-ttu-id="56da5-145">L'ID è il GUID che rappresenta il blocco di script (correlabile con l'ID evento 0x1008) e l'ID dello spazio di esecuzione rappresenta lo spazio di esecuzione in cui è stato eseguito il blocco di script.</span><span class="sxs-lookup"><span data-stu-id="56da5-145">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="56da5-146">I segni di percentuale nel messaggio di chiamata rappresentano le proprietà ETW strutturate.</span><span class="sxs-lookup"><span data-stu-id="56da5-146">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="56da5-147">Anche se vengono sostituiti con i valori effettivi nel testo del messaggio, un modo più efficiente per accedervi è recuperare il messaggio con il cmdlet Get-WinEvent e quindi usare la matrice **Properties** del messaggio.</span><span class="sxs-lookup"><span data-stu-id="56da5-147">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="56da5-148">Di seguito è riportato un esempio di come questa funzionalità possa essere utile per intercettare un tentativo non autorizzato di crittografare e offuscare uno script:</span><span class="sxs-lookup"><span data-stu-id="56da5-148">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

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

<span data-ttu-id="56da5-149">L'esecuzione di questo codice genera le voci di log seguenti:</span><span class="sxs-lookup"><span data-stu-id="56da5-149">Running this generates the following log entries:</span></span>

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

Se la lunghezza del blocco di script supera la capacità di un singolo evento, PowerShell suddivide lo script in più parti. <span data-ttu-id="56da5-151">Ecco il codice di esempio per ricomporre uno script dai relativi messaggi di log:</span><span class="sxs-lookup"><span data-stu-id="56da5-151">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="56da5-152">Come per tutti i sistemi di registrazione con un buffer limitato per la conservazione, un modo per attaccare questa infrastruttura si basa sull'inondare (flood) il log di eventi spuri per nascondere prove precedenti.</span><span class="sxs-lookup"><span data-stu-id="56da5-152">As with all logging systems that have a limited retention buffer, one way to attack this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="56da5-153">Per proteggersi da questo tipo di attacco, assicurarsi di avere configurato qualche forma di raccolta del registro eventi per Inoltro eventi di Windows.</span><span class="sxs-lookup"><span data-stu-id="56da5-153">To protect yourself from this attack, ensure that you have some form of event log collection set up Windows Event Forwarding.</span></span> <span data-ttu-id="56da5-154">Per altre informazioni, vedere [Spotting the Adversary with Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm) (Individuare l'avversario con il monitoraggio del registro eventi di Windows).</span><span class="sxs-lookup"><span data-stu-id="56da5-154">For more information, see [Spotting the Adversary with Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span></span>