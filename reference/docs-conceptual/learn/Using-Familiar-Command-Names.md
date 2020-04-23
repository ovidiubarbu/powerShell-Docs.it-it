---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: Uso di nomi di comandi familiari
ms.openlocfilehash: 30b33bc8739975c1a40e51c04a3ee4e426c199e7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030887"
---
# <a name="using-familiar-command-names"></a><span data-ttu-id="3e568-103">Uso di nomi di comandi familiari</span><span class="sxs-lookup"><span data-stu-id="3e568-103">Using familiar command names</span></span>

<span data-ttu-id="3e568-104">PowerShell supporta l'uso di alias per fare riferimento ai comandi tramite nomi alternativi.</span><span class="sxs-lookup"><span data-stu-id="3e568-104">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="3e568-105">L'uso di alias permette agli utenti che hanno esperienza in altre shell di usare i nomi di comando comuni che conoscono già per operazioni simili in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3e568-105">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="3e568-106">L'uso di alias associa un nuovo nome a un altro comando.</span><span class="sxs-lookup"><span data-stu-id="3e568-106">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="3e568-107">Ad esempio, PowerShell include una funzione interna denominata `Clear-Host` che cancella la finestra di output.</span><span class="sxs-lookup"><span data-stu-id="3e568-107">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="3e568-108">È possibile digitare l'alias `cls` o `clear` al prompt dei comandi.</span><span class="sxs-lookup"><span data-stu-id="3e568-108">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="3e568-109">PowerShell interpreta questi alias ed esegue la funzione `Clear-Host`.</span><span class="sxs-lookup"><span data-stu-id="3e568-109">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="3e568-110">Questa funzionalità semplifica l'apprendimento di PowerShell per gli utenti.</span><span class="sxs-lookup"><span data-stu-id="3e568-110">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="3e568-111">Prima di tutto, la maggior parte degli utenti di **cmd.exe** e UNIX ha a disposizione un vasto repertorio di comandi di cui conosce già il nome.</span><span class="sxs-lookup"><span data-stu-id="3e568-111">First, most **cmd.exe** and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="3e568-112">Gli equivalenti in PowerShell possono non produrre risultati identici.</span><span class="sxs-lookup"><span data-stu-id="3e568-112">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="3e568-113">Tuttavia, i risultati sono sufficientemente simili perché gli utenti possano usarli senza conoscere il nome del comando di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3e568-113">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="3e568-114">La "memoria delle dita" è un'altra importante fonte di frustrazione quando si apprende una nuova shell di comandi.</span><span class="sxs-lookup"><span data-stu-id="3e568-114">"Finger memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="3e568-115">Dopo aver usato **cmd.exe** per anni, si potrebbe digitare in automatico il comando `cls` per cancellare lo schermo.</span><span class="sxs-lookup"><span data-stu-id="3e568-115">If you have used **cmd.exe** for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="3e568-116">Senza l'alias per `Clear-Host`, si riceverebbe un messaggio di errore e potrebbe non essere chiaro che cosa fare per cancellare l'output.</span><span class="sxs-lookup"><span data-stu-id="3e568-116">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

<span data-ttu-id="3e568-117">L'elenco seguente mostra alcuni dei comandi di UNIX e **cmd.exe** comuni che è possibile usare in PowerShell:</span><span class="sxs-lookup"><span data-stu-id="3e568-117">The following list shows a few of the common **cmd.exe** and Unix commands that you can use in PowerShell:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="3e568-118">cat</span><span class="sxs-lookup"><span data-stu-id="3e568-118">cat</span></span>|<span data-ttu-id="3e568-119">dir</span><span class="sxs-lookup"><span data-stu-id="3e568-119">dir</span></span>|<span data-ttu-id="3e568-120">montare</span><span class="sxs-lookup"><span data-stu-id="3e568-120">mount</span></span>|<span data-ttu-id="3e568-121">rm</span><span class="sxs-lookup"><span data-stu-id="3e568-121">rm</span></span>|
|<span data-ttu-id="3e568-122">cd</span><span class="sxs-lookup"><span data-stu-id="3e568-122">cd</span></span>|<span data-ttu-id="3e568-123">echo (eco)</span><span class="sxs-lookup"><span data-stu-id="3e568-123">echo</span></span>|<span data-ttu-id="3e568-124">spostamento</span><span class="sxs-lookup"><span data-stu-id="3e568-124">move</span></span>|<span data-ttu-id="3e568-125">rmdir</span><span class="sxs-lookup"><span data-stu-id="3e568-125">rmdir</span></span>|
|<span data-ttu-id="3e568-126">chdir</span><span class="sxs-lookup"><span data-stu-id="3e568-126">chdir</span></span>|<span data-ttu-id="3e568-127">erase</span><span class="sxs-lookup"><span data-stu-id="3e568-127">erase</span></span>|<span data-ttu-id="3e568-128">popd</span><span class="sxs-lookup"><span data-stu-id="3e568-128">popd</span></span>|<span data-ttu-id="3e568-129">sleep</span><span class="sxs-lookup"><span data-stu-id="3e568-129">sleep</span></span>|
|<span data-ttu-id="3e568-130">deselezionare</span><span class="sxs-lookup"><span data-stu-id="3e568-130">clear</span></span>|<span data-ttu-id="3e568-131">h</span><span class="sxs-lookup"><span data-stu-id="3e568-131">h</span></span>|<span data-ttu-id="3e568-132">ps</span><span class="sxs-lookup"><span data-stu-id="3e568-132">ps</span></span>|<span data-ttu-id="3e568-133">sort</span><span class="sxs-lookup"><span data-stu-id="3e568-133">sort</span></span>|
|<span data-ttu-id="3e568-134">cls</span><span class="sxs-lookup"><span data-stu-id="3e568-134">cls</span></span>|<span data-ttu-id="3e568-135">history</span><span class="sxs-lookup"><span data-stu-id="3e568-135">history</span></span>|<span data-ttu-id="3e568-136">pushd</span><span class="sxs-lookup"><span data-stu-id="3e568-136">pushd</span></span>|<span data-ttu-id="3e568-137">tee</span><span class="sxs-lookup"><span data-stu-id="3e568-137">tee</span></span>|
|<span data-ttu-id="3e568-138">copy</span><span class="sxs-lookup"><span data-stu-id="3e568-138">copy</span></span>|<span data-ttu-id="3e568-139">kill</span><span class="sxs-lookup"><span data-stu-id="3e568-139">kill</span></span>|<span data-ttu-id="3e568-140">pwd</span><span class="sxs-lookup"><span data-stu-id="3e568-140">pwd</span></span>|<span data-ttu-id="3e568-141">type</span><span class="sxs-lookup"><span data-stu-id="3e568-141">type</span></span>|
|<span data-ttu-id="3e568-142">del</span><span class="sxs-lookup"><span data-stu-id="3e568-142">del</span></span>|<span data-ttu-id="3e568-143">lp</span><span class="sxs-lookup"><span data-stu-id="3e568-143">lp</span></span>|<span data-ttu-id="3e568-144">r</span><span class="sxs-lookup"><span data-stu-id="3e568-144">r</span></span>|<span data-ttu-id="3e568-145">scrivere</span><span class="sxs-lookup"><span data-stu-id="3e568-145">write</span></span>|
|<span data-ttu-id="3e568-146">diff</span><span class="sxs-lookup"><span data-stu-id="3e568-146">diff</span></span>|<span data-ttu-id="3e568-147">ls</span><span class="sxs-lookup"><span data-stu-id="3e568-147">ls</span></span>|<span data-ttu-id="3e568-148">ren</span><span class="sxs-lookup"><span data-stu-id="3e568-148">ren</span></span>||

<span data-ttu-id="3e568-149">Il cmdlet `Get-Alias` mostra il vero nome del comando di PowerShell nativo associato a un alias.</span><span class="sxs-lookup"><span data-stu-id="3e568-149">The `Get-Alias` cmdlet shows you the real name of the native PowerShell command associated with an alias.</span></span>

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a><span data-ttu-id="3e568-150">Interpretazione di alias standard</span><span class="sxs-lookup"><span data-stu-id="3e568-150">Interpreting standard aliases</span></span>

<span data-ttu-id="3e568-151">Gli alias descritti nella sezione precedente sono stati progettati per la compatibilità dei nomi con altre shell di comandi.</span><span class="sxs-lookup"><span data-stu-id="3e568-151">The aliases we described previously were designed for name-compatibility with other command shells.</span></span>
<span data-ttu-id="3e568-152">La maggior parte degli alias integrati in PowerShell è progettata per garantire la brevità.</span><span class="sxs-lookup"><span data-stu-id="3e568-152">Most aliases built into PowerShell are designed for brevity.</span></span> <span data-ttu-id="3e568-153">Nomi più brevi sono più facili da digitare, ma sono difficili da leggere se non si sa a cosa si riferiscono.</span><span class="sxs-lookup"><span data-stu-id="3e568-153">Shorter names are easier to type, but are difficult to read if you don't know what they refer to.</span></span>

<span data-ttu-id="3e568-154">Gli alias di PowerShell stabiliscono un compromesso tra chiarezza e brevità.</span><span class="sxs-lookup"><span data-stu-id="3e568-154">PowerShell aliases try to compromise between clarity and brevity.</span></span> <span data-ttu-id="3e568-155">PowerShell usa un set standard di alias per sostantivi e verbi comuni.</span><span class="sxs-lookup"><span data-stu-id="3e568-155">PowerShell uses a standard set of aliases for common nouns and verbs.</span></span>

<span data-ttu-id="3e568-156">Esempi di abbreviazioni:</span><span class="sxs-lookup"><span data-stu-id="3e568-156">Example abbreviations:</span></span>

| <span data-ttu-id="3e568-157">Sostantivo o verbo</span><span class="sxs-lookup"><span data-stu-id="3e568-157">Noun or Verb</span></span> | <span data-ttu-id="3e568-158">Abbreviazione</span><span class="sxs-lookup"><span data-stu-id="3e568-158">Abbreviation</span></span> |
|--------------|--------------|
| <span data-ttu-id="3e568-159">Recupero</span><span class="sxs-lookup"><span data-stu-id="3e568-159">Get</span></span>          | <span data-ttu-id="3e568-160">g</span><span class="sxs-lookup"><span data-stu-id="3e568-160">g</span></span>            |
| <span data-ttu-id="3e568-161">Configurazione</span><span class="sxs-lookup"><span data-stu-id="3e568-161">Set</span></span>          | <span data-ttu-id="3e568-162">s</span><span class="sxs-lookup"><span data-stu-id="3e568-162">s</span></span>            |
| <span data-ttu-id="3e568-163">Elemento</span><span class="sxs-lookup"><span data-stu-id="3e568-163">Item</span></span>         | <span data-ttu-id="3e568-164">i</span><span class="sxs-lookup"><span data-stu-id="3e568-164">i</span></span>            |
| <span data-ttu-id="3e568-165">Location</span><span class="sxs-lookup"><span data-stu-id="3e568-165">Location</span></span>     | <span data-ttu-id="3e568-166">l</span><span class="sxs-lookup"><span data-stu-id="3e568-166">l</span></span>            |
| <span data-ttu-id="3e568-167">Comando</span><span class="sxs-lookup"><span data-stu-id="3e568-167">Command</span></span>      | <span data-ttu-id="3e568-168">cm</span><span class="sxs-lookup"><span data-stu-id="3e568-168">cm</span></span>           |
| <span data-ttu-id="3e568-169">Alias</span><span class="sxs-lookup"><span data-stu-id="3e568-169">Alias</span></span>        | <span data-ttu-id="3e568-170">al</span><span class="sxs-lookup"><span data-stu-id="3e568-170">al</span></span>           |

<span data-ttu-id="3e568-171">Questi alias sono comprensibili quando si conoscono i nomi abbreviati.</span><span class="sxs-lookup"><span data-stu-id="3e568-171">These aliases are understandable when you know the shorthand names.</span></span>

| <span data-ttu-id="3e568-172">Nome del cmdlet</span><span class="sxs-lookup"><span data-stu-id="3e568-172">Cmdlet name</span></span>    | <span data-ttu-id="3e568-173">Alias</span><span class="sxs-lookup"><span data-stu-id="3e568-173">Alias</span></span> |
|----------------|-------|
| `Get-Item`     | <span data-ttu-id="3e568-174">gi</span><span class="sxs-lookup"><span data-stu-id="3e568-174">gi</span></span>    |
| `Set-Item`     | <span data-ttu-id="3e568-175">si</span><span class="sxs-lookup"><span data-stu-id="3e568-175">si</span></span>    |
| `Get-Location` | <span data-ttu-id="3e568-176">gl</span><span class="sxs-lookup"><span data-stu-id="3e568-176">gl</span></span>    |
| `Set-Location` | <span data-ttu-id="3e568-177">sl</span><span class="sxs-lookup"><span data-stu-id="3e568-177">sl</span></span>    |
| `Get-Command`  | <span data-ttu-id="3e568-178">gcm</span><span class="sxs-lookup"><span data-stu-id="3e568-178">gcm</span></span>   |
| `Get-Alias`    | <span data-ttu-id="3e568-179">gal</span><span class="sxs-lookup"><span data-stu-id="3e568-179">gal</span></span>   |

<span data-ttu-id="3e568-180">Dopo aver acquisito familiarità con gli alias di PowerShell, è facile indovinare che l'alias **sal** si riferisce a `Set-Alias`.</span><span class="sxs-lookup"><span data-stu-id="3e568-180">Once you're familiar with PowerShell aliasing, it's easy to guess that the **sal** alias refers to `Set-Alias`.</span></span>

## <a name="creating-new-aliases"></a><span data-ttu-id="3e568-181">Creazione di nuovi alias</span><span class="sxs-lookup"><span data-stu-id="3e568-181">Creating new aliases</span></span>

<span data-ttu-id="3e568-182">È possibile creare alias personalizzati usando il cmdlet `Set-Alias`.</span><span class="sxs-lookup"><span data-stu-id="3e568-182">You can create your own aliases using the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="3e568-183">Ad esempio, le istruzioni seguenti creano gli alias dei cmdlet standard descritti in precedenza:</span><span class="sxs-lookup"><span data-stu-id="3e568-183">For example, the following statements create the standard cmdlet aliases previously discussed:</span></span>

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

<span data-ttu-id="3e568-184">Internamente PowerShell usa comandi simili durante l'avvio, ma questi alias non sono modificabili.</span><span class="sxs-lookup"><span data-stu-id="3e568-184">Internally, PowerShell uses similar commands during startup, but these aliases are not changeable.</span></span>
<span data-ttu-id="3e568-185">Se si prova a eseguire uno di questi comandi, si otterrà un errore che indica che l'alias non può essere modificato.</span><span class="sxs-lookup"><span data-stu-id="3e568-185">If you try to execute one of these commands, you get an error explaining that the alias can't be modified.</span></span> <span data-ttu-id="3e568-186">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="3e568-186">For example:</span></span>

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```
