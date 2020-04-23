---
title: Novità di PowerShell 7.0
description: Nuove funzionalità e modifiche rilasciate in PowerShell 7.0
ms.date: 03/04/2020
ms.openlocfilehash: 84631d9fa169c8d1b4cd4dd23eb3d7c1bca120bb
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "80263136"
---
# <a name="whats-new-in-powershell-70"></a><span data-ttu-id="dcd7c-103">Novità di PowerShell 7.0</span><span class="sxs-lookup"><span data-stu-id="dcd7c-103">What's New in PowerShell 7.0</span></span>

<span data-ttu-id="dcd7c-104">PowerShell 7.0 è una edizione open source multipiattaforma di PowerShell (Windows, macOS e Linux) creata per la gestione di ambienti eterogenei e del cloud ibrido.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-104">PowerShell 7.0 is an open-source, cross-platform (Windows, macOS, and Linux) edition of PowerShell, built to manage heterogeneous environments and hybrid cloud.</span></span>

<span data-ttu-id="dcd7c-105">In questa versione sono state introdotte alcune nuove funzionalità, tra cui:</span><span class="sxs-lookup"><span data-stu-id="dcd7c-105">In this release, we're introducing a number of new features, including:</span></span>

- <span data-ttu-id="dcd7c-106">Parallelizzazione della pipeline con `ForEach-Object -Parallel`</span><span class="sxs-lookup"><span data-stu-id="dcd7c-106">Pipeline parallelization with `ForEach-Object -Parallel`</span></span>
- <span data-ttu-id="dcd7c-107">Nuovi operatori:</span><span class="sxs-lookup"><span data-stu-id="dcd7c-107">New operators:</span></span>
  - <span data-ttu-id="dcd7c-108">Operatore ternario: `a ? b : c`</span><span class="sxs-lookup"><span data-stu-id="dcd7c-108">Ternary operator: `a ? b : c`</span></span>
  - <span data-ttu-id="dcd7c-109">Operatori di concatenamento delle pipeline: `||` e `&&`</span><span class="sxs-lookup"><span data-stu-id="dcd7c-109">Pipeline chain operators: `||` and `&&`</span></span>
  - <span data-ttu-id="dcd7c-110">Operatori condizionali Null: `??` e `??=`</span><span class="sxs-lookup"><span data-stu-id="dcd7c-110">Null conditional operators: `??` and `??=`</span></span>
- <span data-ttu-id="dcd7c-111">Visualizzazione degli errori semplificata e dinamica e cmdlet `Get-Error` per semplificare l'analisi degli errori</span><span class="sxs-lookup"><span data-stu-id="dcd7c-111">A simplified and dynamic error view and `Get-Error` cmdlet for easier investigation of errors</span></span>
- <span data-ttu-id="dcd7c-112">Livello di compatibilità che consente agli utenti di importare i moduli in una sessione implicita di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dcd7c-112">A compatibility layer that enables users to import modules in an implicit Windows PowerShell session</span></span>
- <span data-ttu-id="dcd7c-113">Notifiche automatiche di nuove versioni</span><span class="sxs-lookup"><span data-stu-id="dcd7c-113">Automatic new version notifications</span></span>
- <span data-ttu-id="dcd7c-114">La possibilità di richiamare le risorse DSC direttamente da PowerShell 7 (sperimentale)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-114">The ability to invoke DSC resources directly from PowerShell 7 (experimental)</span></span>

<span data-ttu-id="dcd7c-115">Per visualizzare un elenco completo delle funzionalità e delle correzioni, vedere i [log delle modifiche](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md).</span><span class="sxs-lookup"><span data-stu-id="dcd7c-115">To see a full list of features and fixes, see the [changelogs](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md).</span></span>

## <a name="where-can-i-install-powershell"></a><span data-ttu-id="dcd7c-116">Dove è possibile installare PowerShell?</span><span class="sxs-lookup"><span data-stu-id="dcd7c-116">Where can I install PowerShell?</span></span>

<span data-ttu-id="dcd7c-117">PowerShell 7 supporta attualmente i sistemi operativi x64 seguenti:</span><span class="sxs-lookup"><span data-stu-id="dcd7c-117">PowerShell 7 currently supports the following operating systems on x64, including:</span></span>

- <span data-ttu-id="dcd7c-118">Windows 8.1 e 10</span><span class="sxs-lookup"><span data-stu-id="dcd7c-118">Windows 8.1, and 10</span></span>
- <span data-ttu-id="dcd7c-119">Windows Server 2012, 2012 R2, 2016 e 2019</span><span class="sxs-lookup"><span data-stu-id="dcd7c-119">Windows Server 2012, 2012 R2, 2016, and 2019</span></span>
- <span data-ttu-id="dcd7c-120">macOS 10.13+</span><span class="sxs-lookup"><span data-stu-id="dcd7c-120">macOS 10.13+</span></span>
- <span data-ttu-id="dcd7c-121">Red Hat Enterprise Linux (RHEL)/CentOS 7</span><span class="sxs-lookup"><span data-stu-id="dcd7c-121">Red Hat Enterprise Linux (RHEL) / CentOS 7</span></span>
- <span data-ttu-id="dcd7c-122">Fedora 30+</span><span class="sxs-lookup"><span data-stu-id="dcd7c-122">Fedora 30+</span></span>
- <span data-ttu-id="dcd7c-123">Debian 9</span><span class="sxs-lookup"><span data-stu-id="dcd7c-123">Debian 9</span></span>
- <span data-ttu-id="dcd7c-124">Ubuntu LTS 16.04+</span><span class="sxs-lookup"><span data-stu-id="dcd7c-124">Ubuntu LTS 16.04+</span></span>
- <span data-ttu-id="dcd7c-125">Alpine Linux 3.8+</span><span class="sxs-lookup"><span data-stu-id="dcd7c-125">Alpine Linux 3.8+</span></span>

<span data-ttu-id="dcd7c-126">PowerShell 7.0 supporta anche le versioni ARM32 e ARM64 Debian e Ubuntu e la versione ARM64 Alpine Linux.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-126">Additionally, PowerShell 7.0 supports ARM32 and ARM64 flavors of Debian, Ubuntu, and ARM64 Alpine Linux.</span></span>

<span data-ttu-id="dcd7c-127">Vedere le istruzioni di installazione per il sistema operativo preferito [Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7), [macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) o [Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="dcd7c-127">Check the installation instructions for your preferred operating system [Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7), [macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7), or [Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7).</span></span>

<span data-ttu-id="dcd7c-128">Sebbene non siano supportati ufficialmente, la community ha offerto anche pacchetti per [Arch](https://aur.archlinux.org/packages/powershell/) e Kali Linux.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-128">While not officially supported, the community has also provided packages for [Arch](https://aur.archlinux.org/packages/powershell/) and Kali Linux.</span></span>

> [!NOTE]
> <span data-ttu-id="dcd7c-129">Debian 10 e CentOS 8 attualmente non supportano la comunicazione remota WinRM.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-129">Debian 10 and CentOS 8 currently do not support WinRM remoting.</span></span> <span data-ttu-id="dcd7c-130">Per informazioni dettagliate sulla configurazione della comunicazione remota basata su SSH, vedere [Comunicazione remota di PowerShell su SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="dcd7c-130">For details on setting up SSH-based remoting, see [PowerShell Remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7).</span></span>

<span data-ttu-id="dcd7c-131">Per informazioni aggiornate sui sistemi operativi supportati e il ciclo di vita del supporto, vedere [Ciclo di vita del supporto di PowerShell](/powershell/scripting/powershell-support-lifecycle?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="dcd7c-131">For more up-to-date information about supported operating systems and support lifecycle, see the [PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle?view=powershell-7).</span></span>

## <a name="running-powershell-7"></a><span data-ttu-id="dcd7c-132">Esecuzione di PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="dcd7c-132">Running PowerShell 7</span></span>

<span data-ttu-id="dcd7c-133">PowerShell 7 viene installato in una nuova directory ed eseguito side-by-side con Windows PowerShell 5.1.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-133">PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="dcd7c-134">Per PowerShell Core 6.x, PowerShell 7 è un aggiornamento sul posto che rimuove PowerShell Core 6.x.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-134">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>

- <span data-ttu-id="dcd7c-135">PowerShell 7 è installato in `%programfiles%\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="dcd7c-135">PowerShell 7 is installed to `%programfiles%\PowerShell\7`</span></span>
- <span data-ttu-id="dcd7c-136">La cartella `%programfiles%\PowerShell\7` viene aggiunta a `$env:PATH`</span><span class="sxs-lookup"><span data-stu-id="dcd7c-136">The `%programfiles%\PowerShell\7` folder is added to `$env:PATH`</span></span>

<span data-ttu-id="dcd7c-137">I pacchetti di installazione di PowerShell 7 aggiornano le versioni precedenti di PowerShell Core 6.x:</span><span class="sxs-lookup"><span data-stu-id="dcd7c-137">The PowerShell 7 installer packages upgrade previous versions of PowerShell Core 6.x:</span></span>

- <span data-ttu-id="dcd7c-138">PowerShell Core 6.x in Windows: `%programfiles%\PowerShell\6` è sostituito da `%programfiles%\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="dcd7c-138">PowerShell Core 6.x on Windows: `%programfiles%\PowerShell\6` is replaced by `%programfiles%\PowerShell\7`</span></span>
- <span data-ttu-id="dcd7c-139">Linux: `/opt/microsoft/powershell/6` è sostituito da `/opt/microsoft/powershell/7`</span><span class="sxs-lookup"><span data-stu-id="dcd7c-139">Linux: `/opt/microsoft/powershell/6` is replaced by `/opt/microsoft/powershell/7`</span></span>
- <span data-ttu-id="dcd7c-140">macOS: `/usr/local/microsoft/powershell/6` è sostituito da `/usr/local/microsoft/powershell/7`</span><span class="sxs-lookup"><span data-stu-id="dcd7c-140">macOS: `/usr/local/microsoft/powershell/6` is replaced by `/usr/local/microsoft/powershell/7`</span></span>

> [!NOTE]
> <span data-ttu-id="dcd7c-141">In Windows PowerShell l'eseguibile per l'avvio di PowerShell è denominato `powershell.exe`.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-141">In Windows PowerShell, the executable to launch PowerShell is named `powershell.exe`.</span></span> <span data-ttu-id="dcd7c-142">Nella versione 6 e nelle versioni successive l'eseguibile è modificato per supportare l'esecuzione side-by-side.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-142">In version 6 and above, the executable is changed to support side-by-side execution.</span></span> <span data-ttu-id="dcd7c-143">Il nuovo eseguibile per l'avvio di PowerShell 7 è `pwsh.exe`.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-143">The new executable to launch PowerShell 7 is `pwsh.exe`.</span></span> <span data-ttu-id="dcd7c-144">Le build di anteprima vengono mantenute come `pwsh-preview` anziché `pwsh` nella directory di anteprima della versione 7.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-144">Preview builds will remain in-place as `pwsh-preview` instead of `pwsh` under the 7-preview directory.</span></span>

## <a name="improved-backwards-compatibility-with-windows-powershell"></a><span data-ttu-id="dcd7c-145">Compatibilità migliorata con le versioni precedenti di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dcd7c-145">Improved backwards compatibility with Windows PowerShell</span></span>

<span data-ttu-id="dcd7c-146">PowerShell 7.0 comporta il passaggio verso .NET Core 3.1 offrendo una maggiore compatibilità con le versioni precedenti dei moduli di Windows PowerShell esistenti.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-146">PowerShell 7.0 marks a move a to .NET Core 3.1, enabling significantly more backwards compatibility with existing Windows PowerShell modules.</span></span> <span data-ttu-id="dcd7c-147">Sono inclusi molti moduli in Windows che richiedono funzionalità GUI come `Out-GridView` e `Show-Command`, nonché molti moduli di gestione dei ruoli forniti con Windows.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-147">This includes many modules on Windows that require GUI functionality like `Out-GridView` and `Show-Command`, as well as many role management modules that ship as part of Windows.</span></span>

<span data-ttu-id="dcd7c-148">Per Windows, viene aggiunto un nuovo parametro opzionale **UseWindowsPowerShell** a `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-148">For Windows, a new switch parameter **UseWindowsPowerShell** is added to `Import-Module`.</span></span> <span data-ttu-id="dcd7c-149">Questa opzione crea un modulo proxy in PowerShell 7 che usa un processo di Windows PowerShell locale per eseguire in modo implicito tutti i cmdlet contenuti nel modulo.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-149">This switch creates a proxy module in PowerShell 7 that uses a local Windows PowerShell process to implicitly run any cmdlets contained in that module.</span></span> <span data-ttu-id="dcd7c-150">Per altre informazioni, vedere [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="dcd7c-150">For more information on [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7).</span></span>

<span data-ttu-id="dcd7c-151">Per altre informazioni sui moduli Microsoft che funzionano con PowerShell 7.0, vedere [Tabella di compatibilità dei moduli](https://aka.ms/PSModuleCompat).</span><span class="sxs-lookup"><span data-stu-id="dcd7c-151">For more information on which Microsoft modules work with PowerShell 7.0, see the [Module Compatibility Table](https://aka.ms/PSModuleCompat).</span></span>

## <a name="parallel-execution-added-to-foreach-object"></a><span data-ttu-id="dcd7c-152">Esecuzione parallela aggiunta a ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="dcd7c-152">Parallel execution added to ForEach-Object</span></span>

<span data-ttu-id="dcd7c-153">Il cmdlet `ForEach-Object`, che esegue l'iterazione degli elementi di una raccolta, include ora il parallelismo integrato con il nuovo parametro **Parallel**.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-153">The `ForEach-Object` cmdlet, which iterates items in a collection, now has built-in parallelism with the new **Parallel** parameter.</span></span>

<span data-ttu-id="dcd7c-154">Per impostazione predefinita, i blocchi di script paralleli usano la directory di lavoro corrente del chiamante che ha avviato le attività parallele.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-154">By default, parallel script blocks use the current working directory of the caller that started the parallel tasks.</span></span>

<span data-ttu-id="dcd7c-155">Questo esempio recupera 50.000 voci di log da 5 registri di sistema in un computer Windows locale:</span><span class="sxs-lookup"><span data-stu-id="dcd7c-155">This example retrieves 50,000 log entries from 5 system logs on a local Windows machine:</span></span>

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count

50000
```

<span data-ttu-id="dcd7c-156">Il parametro **Parallel** specifica il blocco di script eseguito in parallelo per ogni nome di registro di input.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-156">The **Parallel** parameter specifies the script block that is run in parallel for each input log name.</span></span>

<span data-ttu-id="dcd7c-157">Il nuovo parametro **ThrottleLimit** limita il numero di blocchi di script in esecuzione in parallelo in un determinato momento.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-157">The new **ThrottleLimit** parameter limits the number of script blocks running in parallel at a given time.</span></span> <span data-ttu-id="dcd7c-158">Il valore predefinito è 5.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-158">The default is 5.</span></span>

<span data-ttu-id="dcd7c-159">Usare la variabile `$_` per rappresentare l'oggetto di input corrente nel blocco di script.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-159">Use the `$_` variable to represent the current input object in the script block.</span></span> <span data-ttu-id="dcd7c-160">Usare l'ambito `$using:` per passare riferimenti a variabili al blocco di script in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-160">Use the `$using:` scope to pass variable references to the running script block.</span></span>

<span data-ttu-id="dcd7c-161">Per altre informazioni, vedere [ForEach-Object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="dcd7c-161">For more information about [ForEach-Object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7).</span></span>

## <a name="ternary-operator"></a><span data-ttu-id="dcd7c-162">Operatore ternario</span><span class="sxs-lookup"><span data-stu-id="dcd7c-162">Ternary operator</span></span>

<span data-ttu-id="dcd7c-163">PowerShell 7.0 introduce un operatore ternario che si comporta come un'istruzione `if-else` semplificata.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-163">PowerShell 7.0 introduces a ternary operator which behaves like a simplified `if-else` statement.</span></span>
<span data-ttu-id="dcd7c-164">L'operatore ternario di PowerShell è strettamente modellato dalla sintassi dell'operatore ternario C#:</span><span class="sxs-lookup"><span data-stu-id="dcd7c-164">PowerShell's ternary operator is closely modeled from the C# ternary operator syntax:</span></span>

```
<condition> ? <if-true> : <if-false>
```

<span data-ttu-id="dcd7c-165">L'espressione condition viene sempre valutata e il risultato viene convertito in un **valore booleano** per determinare il ramo valutato successivo:</span><span class="sxs-lookup"><span data-stu-id="dcd7c-165">The condition-expression is always evaluated and its result converted to a **Boolean** to determine which branch is evaluated next:</span></span>

- <span data-ttu-id="dcd7c-166">L'espressione `<if-true>` viene eseguita se l'espressione `<condition>` è true</span><span class="sxs-lookup"><span data-stu-id="dcd7c-166">The `<if-true>` expression is executed if the `<condition>` expression is true</span></span>
- <span data-ttu-id="dcd7c-167">L'espressione `<if-false>` viene eseguita se l'espressione `<condition>` è false</span><span class="sxs-lookup"><span data-stu-id="dcd7c-167">The `<if-false>` expression is executed if the `<condition>` expression is false</span></span>

<span data-ttu-id="dcd7c-168">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="dcd7c-168">For example:</span></span>

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

<span data-ttu-id="dcd7c-169">In questo esempio, se il percorso esiste, viene visualizzato **Path exists** (Percorso esistente).</span><span class="sxs-lookup"><span data-stu-id="dcd7c-169">In this example, if the path exists, then **Path exists** is displayed.</span></span> <span data-ttu-id="dcd7c-170">Se il percorso non esiste, viene visualizzato **Path not found** (Percorso non trovato).</span><span class="sxs-lookup"><span data-stu-id="dcd7c-170">If the path does not exist, then **Path not found** is displayed.</span></span>

<span data-ttu-id="dcd7c-171">Per altre informazioni, vedere [Informazioni su If](/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="dcd7c-171">For more information [About If](/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7).</span></span>

## <a name="pipeline-chain-operators"></a><span data-ttu-id="dcd7c-172">Operatori di concatenamento delle pipeline</span><span class="sxs-lookup"><span data-stu-id="dcd7c-172">Pipeline chain operators</span></span>

<span data-ttu-id="dcd7c-173">PowerShell 7 implementa gli operatori `&&` e `||` per concatenare le pipeline in modo condizionale.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-173">PowerShell 7 implements the `&&` and `||` operators to conditionally chain pipelines.</span></span> <span data-ttu-id="dcd7c-174">In PowerShell questi operatori sono chiamati "operatori di concatenamento delle pipeline" e sono simili agli elenchi AND e OR in shell come **Bash** e **Zsh** e ai simboli di elaborazione condizionale nella shell dei comandi di Windows (**cmd. exe**).</span><span class="sxs-lookup"><span data-stu-id="dcd7c-174">These operators are known in PowerShell as "pipeline chain operators", and are similar to AND and OR lists in shells like **Bash** and **Zsh**, as well as conditional processing symbols in the Windows Command Shell (**cmd.exe**).</span></span>

<span data-ttu-id="dcd7c-175">L'operatore `&&` esegue la pipeline di destra se la pipeline di sinistra ha avuto esito positivo.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-175">The `&&` operator executes the right-hand pipeline, if the left-hand pipeline succeeded.</span></span> <span data-ttu-id="dcd7c-176">Viceversa, l'operatore `||` esegue la pipeline di destra se la pipeline di sinistra ha avuto esito negativo.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-176">Conversely, the `||` operator executes the right-hand pipeline if the left-hand pipeline failed.</span></span>

> [!NOTE]
> <span data-ttu-id="dcd7c-177">Questi operatori usano le variabili `$?` e `$LASTEXITCODE` per determinare se una pipeline ha avuto esito negativo.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-177">These operators use the `$?` and `$LASTEXITCODE` variables to determine if a pipeline failed.</span></span> <span data-ttu-id="dcd7c-178">Ciò consente di usarli con comandi nativi e non solo con cmdlet o funzioni.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-178">This allows you to use them with native commands and not just with cmdlets or functions.</span></span>

<span data-ttu-id="dcd7c-179">Di seguito, il primo comando ha esito positivo e viene eseguito il secondo comando:</span><span class="sxs-lookup"><span data-stu-id="dcd7c-179">Here, the first command succeeds and the second command is executed:</span></span>

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

<span data-ttu-id="dcd7c-180">Di seguito, il primo comando ha esito negativo e non viene eseguito il secondo comando:</span><span class="sxs-lookup"><span data-stu-id="dcd7c-180">Here, the first command fails, the second is not executed:</span></span>

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

<span data-ttu-id="dcd7c-181">Di seguito, il primo comando ha esito positivo e non viene eseguito il secondo comando:</span><span class="sxs-lookup"><span data-stu-id="dcd7c-181">Here, the first command succeeds, the second command is not executed:</span></span>

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

<span data-ttu-id="dcd7c-182">Di seguito, il primo comando ha esito negativo e viene eseguito il secondo comando:</span><span class="sxs-lookup"><span data-stu-id="dcd7c-182">Here, the first command fails, so the second command is executed:</span></span>

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error 'Bad'
Second
```

<span data-ttu-id="dcd7c-183">Per altre informazioni, vedere [Informazioni sugli operatori di concatenamento delle pipeline](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="dcd7c-183">For more information [About Pipeline Chain Operators](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7).</span></span>

## <a name="null-coalescing-assignment-and-conditional-operators"></a><span data-ttu-id="dcd7c-184">Operatori di coalescenza, di assegnazione e condizionali di valori Null</span><span class="sxs-lookup"><span data-stu-id="dcd7c-184">Null-coalescing, assignment, and conditional operators</span></span>

<span data-ttu-id="dcd7c-185">PowerShell 7 include l'operatore di coalescenza di valori Null `??`, l'operatore di assegnazione condizionale di valori Null `??=` e gli operatori di accesso membri condizionali di valori Null `?.` e `?[]`.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-185">PowerShell 7 includes Null coalescing operator `??`, Null conditional assignment `??=`, and Null conditional member access operators `?.` and `?[]`.</span></span>

### <a name="null-coalescing-operator-"></a><span data-ttu-id="dcd7c-186">Operatore di coalescenza di valori Null ??</span><span class="sxs-lookup"><span data-stu-id="dcd7c-186">Null-coalescing Operator ??</span></span>

<span data-ttu-id="dcd7c-187">L'operatore di coalescenza di valori Null `??` restituisce il valore dell'operando di sinistra se non è Null.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-187">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't null.</span></span>
<span data-ttu-id="dcd7c-188">In caso contrario, valuta l'operando di destra e ne restituisce il risultato.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-188">Otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="dcd7c-189">L'operatore `??` non valuta l'operando di destra se l'operando di sinistra restituisce un valore non Null.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-189">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ?? 100
100
```

<span data-ttu-id="dcd7c-190">Nell'esempio seguente l'operando di destra non verrà valutato:</span><span class="sxs-lookup"><span data-stu-id="dcd7c-190">In the following example, the right-hand operand won't be evaluated:</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-assignment-operator-"></a><span data-ttu-id="dcd7c-191">Operatore di assegnazione condizionale di valori Null ??=</span><span class="sxs-lookup"><span data-stu-id="dcd7c-191">Null conditional assignment operator ??=</span></span>

<span data-ttu-id="dcd7c-192">L'operatore di assegnazione condizionale di valori Null `??=` assegna il valore dell'operando di destra all'operando di sinistra solo se l'operando di sinistra restituisce un valore Null.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-192">The null conditional assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to null.</span></span> <span data-ttu-id="dcd7c-193">L'operatore `??=` non valuta l'operando di destra se l'operando di sinistra restituisce un valore non Null.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-193">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ??= 100
$x
100
```

<span data-ttu-id="dcd7c-194">Nell'esempio seguente l'operando di destra non verrà valutato:</span><span class="sxs-lookup"><span data-stu-id="dcd7c-194">In the following example, the right-hand operand won't be evaluated:</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-member-access-operators--and--experimental"></a><span data-ttu-id="dcd7c-195">Operatori di accesso membri condizionali di valori Null ?.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-195">Null conditional member access operators ?.</span></span> <span data-ttu-id="dcd7c-196">e ?[] (sperimentale)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-196">and ?[] (Experimental)</span></span>

> [!NOTE]
> <span data-ttu-id="dcd7c-197">Questa funzionalità sperimentale è denominata **PSNullConditionalOperators**.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-197">This is an experimental feature named **PSNullConditionalOperators**.</span></span> <span data-ttu-id="dcd7c-198">Per altre informazioni, vedere [Funzionalità sperimentali](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="dcd7c-198">Learn more [About Experimental Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).</span></span>

<span data-ttu-id="dcd7c-199">Un operatore condizionale di valori Null consente l'accesso ai membri, `?.`, o l'accesso agli elementi, `?[]`, al relativo operando solo se l'operando restituisce un valore non Null. In caso contrario, restituisce un valore Null.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-199">A null conditional operator permits member access, `?.`, or element access, `?[]`, to its operand only if that operand evaluates to non-null; otherwise, it returns null.</span></span>

> [!NOTE]
> <span data-ttu-id="dcd7c-200">Poiché in PowerShell `?` può essere incluso nel nome della variabile, è necessario specificare formalmente il nome della variabile per usare questi operatori.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-200">Since PowerShell allows `?` to be part of the variable name, formal specification of the variable name is required for using these operators.</span></span> <span data-ttu-id="dcd7c-201">Pertanto, è necessario usare `{}` per i nomi delle variabili, ad esempio `${a}`, o quando `?` è incluso nel nome della variabile `${a?}`.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-201">So it is required to use `{}` around the variable names like `${a}` or when `?` is part of the variable name `${a?}`.</span></span>

<span data-ttu-id="dcd7c-202">Nell'esempio seguente viene restituito il valore della proprietà membro **Status**:</span><span class="sxs-lookup"><span data-stu-id="dcd7c-202">In the following example, the value of the member property **Status** is returned:</span></span>

```powershell
$Service = Get-Service -Name 'bits'
${Service}?.status
Stopped
```

<span data-ttu-id="dcd7c-203">L'esempio seguente restituirà un valore Null senza tentare di accedere al nome del membro **Status**:</span><span class="sxs-lookup"><span data-stu-id="dcd7c-203">The following example will return null, without trying to access the member name **Status**:</span></span>

```powershell
$service = $Null
${Service}?.status
```

<span data-ttu-id="dcd7c-204">Analogamente, se si usa `?[]`, verrà restituito il valore dell'elemento:</span><span class="sxs-lookup"><span data-stu-id="dcd7c-204">Similarly, using `?[]`, the value of the element will be returned:</span></span>

```powershell
$a = 1..10
${a}?[0]
1
```

<span data-ttu-id="dcd7c-205">Quando l'operando è Null, non viene eseguito l'accesso all'elemento e viene restituito un valore Null:</span><span class="sxs-lookup"><span data-stu-id="dcd7c-205">And when the operand is null, the element isn't accessed and null is returned:</span></span>

```powershell
$a = $null
${a}?[0]
```

<span data-ttu-id="dcd7c-206">Per altre informazioni, vedere [Informazioni sugli operatori](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="dcd7c-206">For more information [About_Operators](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7).</span></span>

## <a name="new-view-conciseview-and-cmdlet-get-error"></a><span data-ttu-id="dcd7c-207">Nuova visualizzazione ConciseView e nuovo cmdlet Get-Error</span><span class="sxs-lookup"><span data-stu-id="dcd7c-207">New view ConciseView and cmdlet Get-Error</span></span>

<span data-ttu-id="dcd7c-208">La visualizzazione dei messaggi di errore è stata migliorata per aumentare la leggibilità degli errori interattivi e di script con una nuova visualizzazione predefinita **ConciseView**.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-208">The display of error messages has been improved to enhance the readability of interactive and script errors with a new default view **ConciseView**.</span></span> <span data-ttu-id="dcd7c-209">Le visualizzazioni possono essere selezionate dall'utente tramite la variabile di preferenza `$ErrorView`.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-209">The views are user-selectable through the preference variable `$ErrorView`.</span></span>

<span data-ttu-id="dcd7c-210">In **ConciseView**, se un errore non è dovuto a un errore di script o parser, viene visualizzato un messaggio di errore a riga singola:</span><span class="sxs-lookup"><span data-stu-id="dcd7c-210">With **ConciseView**, if an error is not from a script or parser error, then it's a single line error message:</span></span>

```powershell
Get-Childitem -Path c:\NotReal
```

```Output
Get-ChildItem: Cannot find path 'C:\NotReal' because it does not exist
```

<span data-ttu-id="dcd7c-211">Se l'errore si verifica durante l'esecuzione dello script o si tratta di un errore di analisi, PowerShell restituisce un messaggio di errore su più righe che contiene l'errore, un puntatore e un messaggio di errore che indicano la posizione dell'errore.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-211">If the error occurs during script execution or is a parsing error, PowerShell returns a multiline error message that contains the error, a pointer and error message showing where the error is in that line.</span></span> <span data-ttu-id="dcd7c-212">Se il terminale non supporta le sequenze di escape dei colori ANSI (VT100), i colori non vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-212">If the terminal doesn't support ANSI color escape sequences (VT100), then colors are not displayed.</span></span>

![Visualizzazione degli errori da uno script](./media/What-s-New-in-PowerShell-70/myscript-error.png)

<span data-ttu-id="dcd7c-214">La visualizzazione predefinita in PowerShell 7 è **ConciseView**.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-214">The default view in PowerShell 7 is **ConciseView**.</span></span> <span data-ttu-id="dcd7c-215">La visualizzazione predefinita precedente era **NormalView** ed era selezionabile dall'utente impostando la variabile di preferenza `$ErrorView`.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-215">The previous default view was **NormalView** and is user selectable by setting the preference variable `$ErrorView`.</span></span>

```powershell
$ErrorView = 'NormalView' # Sets the error view to NormalView
$ErrorView = 'ConciseView' # Sets the error view to ConciseView
```

> [!NOTE]
> <span data-ttu-id="dcd7c-216">Una nuova proprietà **ErrorAccentColor** è stata aggiunta a `$Host.PrivateData` per supportare la modifica del colore principale del messaggio di errore.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-216">A new property **ErrorAccentColor** is added to `$Host.PrivateData` to support changing the accent color of the error message.</span></span>

<span data-ttu-id="dcd7c-217">Un nuovo cmdlet `Get-Error` offre una visualizzazione dettagliata completa dell'errore quando si desidera.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-217">A new cmdlet `Get-Error` provides complete detailed view of the fully qualified error when desired.</span></span>
<span data-ttu-id="dcd7c-218">Per impostazione predefinita, il cmdlet visualizza i dettagli completi, incluse le eccezioni interne, dell'ultimo errore che si è verificato.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-218">By default the cmdlet displays the full details, including inner exceptions, of the last error that occurred.</span></span>

![Visualizzazione da Get-Error](./media/What-s-New-in-PowerShell-70/myscript-geterror.png)

<span data-ttu-id="dcd7c-220">Il cmdlet `Get-Error` supporta l'input dalla pipeline tramite la variabile incorporata `$Error`.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-220">The `Get-Error` cmdlet supports input from the pipeline using the built-in variable `$Error`.</span></span>
<span data-ttu-id="dcd7c-221">`Get-Error` visualizza tutti gli errori delle pipeline.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-221">`Get-Error` displays all piped errors.</span></span>

```powershell
$Error | Get-Error
```

<span data-ttu-id="dcd7c-222">Il cmdlet `Get-Error` supporta il parametro **Newest** e consente di specificare il numero di errori della sessione corrente che si vuole visualizzare.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-222">The `Get-Error` cmdlet supports the **Newest** parameter, allowing you to specify how many errors from the current session you wish displayed.</span></span>

```powershell
Get-Error -Newest 3 # Displays the lst three errors that occurred in the session
```

<span data-ttu-id="dcd7c-223">Per altre informazioni, vedere [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="dcd7c-223">For more information about [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7).</span></span>

## <a name="new-version-notification"></a><span data-ttu-id="dcd7c-224">Notifica di nuove versioni</span><span class="sxs-lookup"><span data-stu-id="dcd7c-224">New version notification</span></span>

<span data-ttu-id="dcd7c-225">PowerShell 7 usa le notifiche di aggiornamento per avvisare gli utenti dell'esistenza di aggiornamenti per PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-225">PowerShell 7 uses update notifications to alert users to the existence of updates to PowerShell.</span></span>
<span data-ttu-id="dcd7c-226">Una volta al giorno, PowerShell esegue una query su un servizio online per determinare se è disponibile una versione più recente.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-226">Once per day, PowerShell queries an online service to determine if a newer version is available.</span></span>

> [!NOTE]
> <span data-ttu-id="dcd7c-227">Il controllo degli aggiornamenti si verifica durante la prima sessione in un determinato periodo di 24 ore.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-227">The update check happens during the first session in a given 24-hour period.</span></span> <span data-ttu-id="dcd7c-228">Per motivi di prestazioni, il controllo degli aggiornamenti inizia 3 secondi dopo l'inizio della sessione.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-228">For performance reasons, the update check starts 3 seconds after the session begins.</span></span> <span data-ttu-id="dcd7c-229">La notifica viene visualizzata solo all'avvio delle sessioni successive.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-229">The notification is shown only on the start of subsequent sessions.</span></span>

<span data-ttu-id="dcd7c-230">Per impostazione predefinita, PowerShell esegue una sottoscrizione a uno dei due diversi canali di notifica, a seconda della versione/ramo.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-230">By default, PowerShell subscribes to one of two different notification channels depending on its version/branch.</span></span> <span data-ttu-id="dcd7c-231">Le versioni supportate disponibili a livello generale (GA) di PowerShell restituiscono solo le notifiche per le versioni GA aggiornate.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-231">Supported, Generally Available (GA) versions of PowerShell only return notifications for updated GA releases.</span></span> <span data-ttu-id="dcd7c-232">La versione di anteprima e la versione finale candidata (RC) inviano notifiche sugli aggiornamenti alle versioni di anteprima, RC e GA.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-232">Preview and Release Candidate (RC) releases notify of updates to preview, RC, and GA releases.</span></span>

<span data-ttu-id="dcd7c-233">Il comportamento delle notifiche di aggiornamento può essere modificato usando la variabile di ambiente `$Env:POWERSHELL_UPDATECHECK`.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-233">The update notification behavior can be changed using the `$Env:POWERSHELL_UPDATECHECK` environment variable.</span></span> <span data-ttu-id="dcd7c-234">Sono supportati i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="dcd7c-234">The following values are supported:</span></span>

- <span data-ttu-id="dcd7c-235">**Default** corrisponde a non definire `$Env:POWERSHELL_UPDATECHECK`</span><span class="sxs-lookup"><span data-stu-id="dcd7c-235">**Default** is the same as not defining `$Env:POWERSHELL_UPDATECHECK`</span></span>
  - <span data-ttu-id="dcd7c-236">Le versioni disponibili a livello generale (GA) inviano notifiche degli aggiornamenti alle versioni GA</span><span class="sxs-lookup"><span data-stu-id="dcd7c-236">GA releases notify of updates to GA releases</span></span>
  - <span data-ttu-id="dcd7c-237">Le versioni di anteprima/RC inviano notifiche degli aggiornamenti alle versioni GA e di anteprima</span><span class="sxs-lookup"><span data-stu-id="dcd7c-237">Preview/RC releases notify of updates to GA and preview releases</span></span>
- <span data-ttu-id="dcd7c-238">**Off** disattiva la funzione di notifica degli aggiornamenti</span><span class="sxs-lookup"><span data-stu-id="dcd7c-238">**Off** turns off the update notification feature</span></span>
- <span data-ttu-id="dcd7c-239">**LTS** notifica solo gli aggiornamenti alle versioni GA LTS (Long Term Servicing)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-239">**LTS** only notifies of updates to long-term-servicing (LTS) GA releases</span></span>

> [!NOTE]
> <span data-ttu-id="dcd7c-240">La variabile di ambiente `$Env:POWERSHELL_UPDATECHECK` non esiste fino a quando non viene impostata per la prima volta.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-240">The environment variable `$Env:POWERSHELL_UPDATECHECK` does not exist until it is set for the first time.</span></span>

<span data-ttu-id="dcd7c-241">Per impostare la notifica delle versioni solo per le versioni `LTS`:</span><span class="sxs-lookup"><span data-stu-id="dcd7c-241">To set the version notification for `LTS` releases only:</span></span>

```powershell
$Env:POWERSHELL_UPDATECHECK = 'LTS'
```

<span data-ttu-id="dcd7c-242">Per impostare la notifica delle versioni per il comportamento `Default`:</span><span class="sxs-lookup"><span data-stu-id="dcd7c-242">To set the version notification to the `Default` behavior:</span></span>

```powershell
$Env:POWERSHELL_UPDATECHECK = 'Default'
```

<span data-ttu-id="dcd7c-243">Per altre informazioni, vedere [Informazioni sulle notifiche degli aggiornamenti](/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="dcd7c-243">For more information [About Update Notifications](/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7).</span></span>

## <a name="new-dsc-resource-support-with-invoke-dscresource-experimental"></a><span data-ttu-id="dcd7c-244">Nuovo supporto delle risorse DSC con Invoke-DSCResource (sperimentale)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-244">New DSC Resource support with Invoke-DSCResource (Experimental)</span></span>

> [!NOTE]
> <span data-ttu-id="dcd7c-245">Questa funzionalità sperimentale è denominata **PSDesiredStateConfiguration.InvokeDscResource**.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-245">This is an experimental feature named **PSDesiredStateConfiguration.InvokeDscResource**.</span></span> <span data-ttu-id="dcd7c-246">Per altre informazioni, vedere [Funzionalità sperimentali](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="dcd7c-246">Learn more [About Experimental Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).</span></span>

<span data-ttu-id="dcd7c-247">Il cmdlet `Invoke-DscResource` esegue un metodo di una risorsa DSC (Desired State Configuration) specificata di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-247">The `Invoke-DscResource` cmdlet runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

<span data-ttu-id="dcd7c-248">Questo cmdlet richiama direttamente una risorsa DSC senza creare un documento di configurazione.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-248">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span> <span data-ttu-id="dcd7c-249">Usando questo cmdlet, i prodotti di gestione della configurazione possono gestire Windows o Linux usando le risorse DSC.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-249">Using this cmdlet, configuration management products can manage Windows or Linux by using DSC resources.</span></span> <span data-ttu-id="dcd7c-250">Questo cmdlet abilita anche il debug delle risorse quando il motore DSC è in esecuzione con il debug abilitato.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-250">This cmdlet also enables debugging of resources when the DSC engine is running with debugging enabled.</span></span>

<span data-ttu-id="dcd7c-251">Questo comando richiama il metodo **Set** di una risorsa denominata Log e specifica una proprietà **Message**.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-251">This command invokes the **Set** method of a resource named Log and specifies a **Message** property.</span></span>

```powershell
Invoke-DscResource -Name Log -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Message = 'Hello World'
}
```

<span data-ttu-id="dcd7c-252">Per altre informazioni, vedere [Invoke-DSCResource](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="dcd7c-252">For more information about [Invoke-DSCResource](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7).</span></span>

## <a name="breaking-changes-and-improvements"></a><span data-ttu-id="dcd7c-253">Modifiche e miglioramenti di rilievo</span><span class="sxs-lookup"><span data-stu-id="dcd7c-253">Breaking Changes and Improvements</span></span>

### <a name="breaking-changes"></a><span data-ttu-id="dcd7c-254">Modifiche di rilievo</span><span class="sxs-lookup"><span data-stu-id="dcd7c-254">Breaking Changes</span></span>

- <span data-ttu-id="dcd7c-255">Supporto delle notifiche degli aggiornamenti per LTS e i canali predefiniti (#11132)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-255">Make update notification support LTS and default channels (#11132)</span></span>
- <span data-ttu-id="dcd7c-256">Aggiornamento di Test-Connection per un funzionamento più simile a quello in Windows PowerShell (#10697) (grazie @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-256">Update Test-Connection to work more like the one in Windows PowerShell (#10697) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="dcd7c-257">Mantenimento di $?</span><span class="sxs-lookup"><span data-stu-id="dcd7c-257">Preserve $?</span></span> <span data-ttu-id="dcd7c-258">per ParenExpression, SubExpression e ArrayExpression (#11040)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-258">for ParenExpression, SubExpression and ArrayExpression (#11040)</span></span>
- <span data-ttu-id="dcd7c-259">Impostazione della directory di lavoro sulla directory corrente in Start-Job (#10920) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-259">Set working directory to current directory in Start-Job (#10920) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-260">$PSCulture riflette in modo coerente le modifiche delle impostazioni cultura della sessione (#10138) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-260">Make $PSCulture consistently reflect in-session culture changes (#10138) (Thanks @iSazonov!)</span></span>

### <a name="engine-updates-and-fixes"></a><span data-ttu-id="dcd7c-261">Aggiornamenti e correzioni del motore</span><span class="sxs-lookup"><span data-stu-id="dcd7c-261">Engine Updates and Fixes</span></span>

- <span data-ttu-id="dcd7c-262">Miglioramenti nelle API dei punti di interruzione per gli scenari remoti (#11312)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-262">Improvements in breakpoint APIs for remote scenarios (#11312)</span></span>
- <span data-ttu-id="dcd7c-263">Correzione della perdita della definizione di classe PowerShell in un altro spazio di esecuzione (#11273)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-263">Fix PowerShell class definition leaking into another Runspace (#11273)</span></span>
- <span data-ttu-id="dcd7c-264">Correzione di una regressione nella formattazione causata dalla primitiva FirstOrDefault aggiunta in 7.0.0-Preview1 (#11258)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-264">Fix a regression in formatting caused by the FirstOrDefault primitive added in 7.0.0-Preview1 (#11258)</span></span>
- <span data-ttu-id="dcd7c-265">Moduli Microsoft aggiuntivi per tenere traccia dei dati di telemetria di PS7 (#10751)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-265">Additional Microsoft Modules to track in PS7 Telemetry (#10751)</span></span>
- <span data-ttu-id="dcd7c-266">Conversione delle funzionalità approvate in funzionalità non sperimentali (#11303)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-266">Make approved features non-experimental (#11303)</span></span>
- <span data-ttu-id="dcd7c-267">Aggiornamento di ConciseView per l'uso di TargetObject, se applicabile (#11075)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-267">Update ConciseView to use TargetObject if applicable (#11075)</span></span>
- <span data-ttu-id="dcd7c-268">Correzione di NullReferenceException nei metodi pubblici CompletionCompleters (#11274)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-268">Fix NullReferenceException in CompletionCompleters public methods (#11274)</span></span>
- <span data-ttu-id="dcd7c-269">Correzione del controllo dello stato del thread apartment nelle piattaforme non Windows (#11301)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-269">Fix apartment thread state check on non-Windows platforms (#11301)</span></span>
- <span data-ttu-id="dcd7c-270">Aggiornamento dell'impostazione PSModulePath per concatenare le variabili di ambiente del processo e del computer (#11276)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-270">Update setting PSModulePath to concatenate the process and machine environment variables (#11276)</span></span>
- <span data-ttu-id="dcd7c-271">Aggiornamento di .NET Core alla versione 3.1.0 (#11260)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-271">Bump .NET Core to 3.1.0 (#11260)</span></span>
- <span data-ttu-id="dcd7c-272">Correzione del rilevamento di $PSHOME che precede $env:PATH (#11141)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-272">Fix detection of $PSHOME in front of $env:PATH (#11141)</span></span>
- <span data-ttu-id="dcd7c-273">Possibilità di pwsh di ereditare $env:PSModulePath e abilitare powershell.exe per un avvio corretto (#11057)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-273">Allow pwsh to inherit $env:PSModulePath and enable powershell.exe to start correctly (#11057)</span></span>
- <span data-ttu-id="dcd7c-274">Passaggio a .NET Core 3.1 Preview 1 (#10798)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-274">Move to .NET Core 3.1 preview 1 (#10798)</span></span>
- <span data-ttu-id="dcd7c-275">Refactoring dei controlli dei tag di rianalisi nel provider del file system (#10431) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-275">Refactor reparse tag checks in file system provider (#10431) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-276">Sostituzione di CR e nuova riga con un carattere 0x23CE nella registrazione degli script (#10616)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-276">Replace CR and new line with a 0x23CE character in script logging (#10616)</span></span>
- <span data-ttu-id="dcd7c-277">Correzione della perdita di una risorsa tramite l'annullamento della registrazione del gestore dell'evento da AppDomain.CurrentDomain.ProcessExit (#10626)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-277">Fix a resource leak by unregistering the event handler from AppDomain.CurrentDomain.ProcessExit (#10626)</span></span>
- <span data-ttu-id="dcd7c-278">Aggiunta del supporto in ActionPreference.Break per interrompere l'esecuzione nel debugger quando vengono generati messaggi di debug, errore, informazioni, stato, Verbose o di avviso (#8205) (grazie @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-278">Add support to ActionPreference.Break to break into debugger when Debug, Error, Information, Progress, Verbose or Warning messages are generated (#8205) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="dcd7c-279">Abilitazione dell'avvio di componenti aggiuntivi del pannello di controllo all'interno di PowerShell Core senza specificare l'estensione CPL.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-279">Enable starting control panel add-ins within PowerShell Core without specifying .CPL extension.</span></span> <span data-ttu-id="dcd7c-280">(#9828)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-280">(#9828)</span></span>
- <span data-ttu-id="dcd7c-281">Supporto di numeri negativi nell'operatore -split (#8960) (ringraziamenti @ece-jacob-scott!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-281">Support negative numbers in -split operator (#8960) (Thanks @ece-jacob-scott!)</span></span>

### <a name="general-cmdlet-updates-and-fixes"></a><span data-ttu-id="dcd7c-282">Aggiornamenti e correzioni generali dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="dcd7c-282">General Cmdlet Updates and Fixes</span></span>

- <span data-ttu-id="dcd7c-283">Correzione del problema in Raspbian per l'impostazione della data delle modifiche dei file nella funzionalità sperimentale UnixStat (#11313)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-283">Fix for issue on Raspbian for setting date of file changes in UnixStat Experimental Feature (#11313)</span></span>
- <span data-ttu-id="dcd7c-284">Aggiunta di -AsPlainText a ConvertFrom-SecureString (#11142)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-284">Add -AsPlainText to ConvertFrom-SecureString (#11142)</span></span>
- <span data-ttu-id="dcd7c-285">Aggiunta del controllo della versione WindowsPS per WinCompat (#11148)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-285">Added WindowsPS version check for WinCompat (#11148)</span></span>
- <span data-ttu-id="dcd7c-286">Correzione della segnalazione degli errori in alcuni scenari WinCompat (#11259)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-286">Fix error-reporting in some WinCompat scenarios (#11259)</span></span>
- <span data-ttu-id="dcd7c-287">Aggiunta del sistema di risoluzione binario nativo (#11032) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-287">Add native binary resolver (#11032) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-288">Aggiornamento del calcolo della larghezza del carattere per rispettare correttamente i caratteri CJK (#11262)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-288">Update calculation of char width to respect CJK chars correctly (#11262)</span></span>
- <span data-ttu-id="dcd7c-289">Aggiunta di Unblock-File per macOS (#11137)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-289">Add Unblock-File for macOS (#11137)</span></span>
- <span data-ttu-id="dcd7c-290">Correzione della regressione in Get-PSCallStack (#11210) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-290">Fix regression in Get-PSCallStack (#11210) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-291">Rimozione del caricamento automatico del modulo ScheduledJob quando si usano i cmdlet Job (#11194)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-291">Remove autoloading of the ScheduledJob module when using Job cmdlets (#11194)</span></span>
- <span data-ttu-id="dcd7c-292">Aggiunta di OutputType al cmdlet Get-Error e mantenimento dei TypeName originali (#10856)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-292">Add OutputType to Get-Error cmdlet and preserve original typenames (#10856)</span></span>
- <span data-ttu-id="dcd7c-293">Correzione di un riferimento Null nella proprietà SupportsVirtualTerminal (#11105)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-293">Fix null reference in SupportsVirtualTerminal property (#11105)</span></span>
- <span data-ttu-id="dcd7c-294">Aggiunta di un controllo del limite in Get-WinEvent (#10648) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-294">Add limit check in Get-WinEvent (#10648) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-295">Correzione del runtime del comando in modo che StopUpstreamCommandsException non venga popolato in -ErrorVariable (#10840)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-295">Fix command runtime so StopUpstreamCommandsException doesn't get populated in -ErrorVariable (#10840)</span></span>
- <span data-ttu-id="dcd7c-296">Impostazione della codifica di output su [Console]::OutputEncoding per i comandi nativi (#10824)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-296">Set the output encoding to [Console]::OutputEncoding for native commands (#10824)</span></span>
- <span data-ttu-id="dcd7c-297">Supporto di blocchi di codice a più righe negli esempi (#10776) (grazie @Greg-Smulko!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-297">Support multi-line code blocks in examples (#10776) (Thanks @Greg-Smulko!)</span></span>
- <span data-ttu-id="dcd7c-298">Aggiunta del parametro Culture al cmdlet Select-String (#10943) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-298">Add Culture parameter to Select-String cmdlet (#10943) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-299">Correzione del percorso della directory di lavoro Start-Job con barra rovesciata finale (#11041)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-299">Fix Start-Job working directory path with trailing backslash (#11041)</span></span>
- <span data-ttu-id="dcd7c-300">ConvertFrom-Json: Annullamento del wrapping delle raccolte per impostazione predefinita (#10861) (grazie @danstur!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-300">ConvertFrom-Json: Unwrap collections by default (#10861) (Thanks @danstur!)</span></span>
- <span data-ttu-id="dcd7c-301">Uso di una tabella hash con distinzione tra maiuscole e minuscole per il cmdlet Group-Object con le opzioni -CaseSensitive e -AsHashtable (#11030) (grazie @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-301">Use case-sensitive Hashtable for Group-Object cmdlet with -CaseSensitive and -AsHashtable switches (#11030) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="dcd7c-302">Gestione dell'eccezione se l'enumerazione dei file ha esito negativo quando si ricompila il percorso per avere la combinazione di maiuscole e minuscole corretta (#11014)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-302">Handle exception if enumerating files fails when rebuilding path to have correct casing (#11014)</span></span>
- <span data-ttu-id="dcd7c-303">Correzione di ConciseView per visualizzare Activity anziché myCommand (#11007)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-303">Fix ConciseView to show Activity instead of myCommand (#11007)</span></span>
- <span data-ttu-id="dcd7c-304">Possibilità per i cmdlet Web di ignorare gli stati degli errori HTTP (#10466) (grazie @vdamewood!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-304">Allow web cmdlets to ignore HTTP error statuses (#10466) (Thanks @vdamewood!)</span></span>
- <span data-ttu-id="dcd7c-305">Correzione del piping di più CommandInfo in Get-Command (#10929)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-305">Fix piping of more than one CommandInfo to Get-Command (#10929)</span></span>
- <span data-ttu-id="dcd7c-306">Aggiunta del cmdlet Get-Counter per Windows (#10933)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-306">Add back Get-Counter cmdlet for Windows (#10933)</span></span>
- <span data-ttu-id="dcd7c-307">Conversione del treat ConvertTo-Json [AutomationNull]::Value e [NullString]::Value in $null (#10957)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-307">Make ConvertTo-Json treat [AutomationNull]::Value and [NullString]::Value as $null (#10957)</span></span>
- <span data-ttu-id="dcd7c-308">Rimozione delle parentesi quadre dall'indirizzo IPv6 per la comunicazione remota SSH (#10968)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-308">Remove brackets from ipv6 address for SSH remoting (#10968)</span></span>
- <span data-ttu-id="dcd7c-309">Correzione dell'arresto anomalo se il comando inviato a pwsh è solo uno spazio vuoto (#10977)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-309">Fix crash if command sent to pwsh is just whitespace (#10977)</span></span>
- <span data-ttu-id="dcd7c-310">Aggiunta di Get-Clipboard e Set-Clipboard multipiattaforma (#10340)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-310">Added cross-platform Get-Clipboard and Set-Clipboard (#10340)</span></span>
- <span data-ttu-id="dcd7c-311">Correzione dell'impostazione del percorso originale dell'oggetto filesystem in modo che non abbia una barra finale aggiuntiva (#10959)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-311">Fix setting original path of filesystem object to not have extra trailing slash (#10959)</span></span>
- <span data-ttu-id="dcd7c-312">Supporto di $Null per ConvertTo-Json (#10947)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-312">Support $null for ConvertTo-Json (#10947)</span></span>
- <span data-ttu-id="dcd7c-313">Aggiunta del comando Out-Printer in Windows (#10906)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-313">Add back Out-Printer command on Windows (#10906)</span></span>
- <span data-ttu-id="dcd7c-314">Correzione di Start-Job -WorkingDirectory con spazio vuoto (#10951)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-314">Fix Start-Job -WorkingDirectory with whitespace (#10951)</span></span>
- <span data-ttu-id="dcd7c-315">Restituzione del valore predefinito quando si recupera un valore Null per un'impostazione in PSConfiguration.cs (#10963) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-315">Return default value when getting null for a setting in PSConfiguration.cs (#10963) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-316">Gestione dell'eccezione I/O come non fatale (#10950)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-316">Handle IO exception as non-terminating (#10950)</span></span>
- <span data-ttu-id="dcd7c-317">Aggiunta dell'assembly GraphicalHost per abilitare Out-GridView, Show-Command e Get-Help -ShowWindow (#10899)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-317">Add GraphicalHost assembly to enable Out-GridView, Show-Command, and Get-Help -ShowWindow (#10899)</span></span>
- <span data-ttu-id="dcd7c-318">Recupero di ComputerName tramite pipeline in Get-HotFix (#10852) (grazie @kvprasoon!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-318">Take ComputerName via pipeline in Get-HotFix (#10852) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="dcd7c-319">Correzione del completamento tramite TAB per i parametri in modo che mostri i parametri comuni come disponibili (#10850)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-319">Fix tab completion for parameters so that it shows common parameters as available (#10850)</span></span>
- <span data-ttu-id="dcd7c-320">Correzione di GetCorrectCasedPath() per controllare innanzitutto se vengono restituite voci di file di sistema prima di chiamare First() (#10930)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-320">Fix GetCorrectCasedPath() to first check if any system file entries is returned before calling First() (#10930)</span></span>
- <span data-ttu-id="dcd7c-321">Impostazione della directory di lavoro sulla directory corrente in Start-Job (#10920) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-321">Set working directory to current directory in Start-Job (#10920) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-322">Modifica di TabExpansion2 in modo che non richieda -CursorColumn e venga trattata come $InputScript.Length (#10849)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-322">Change TabExpansion2 to not require -CursorColumn and treat as $InputScript.Length (#10849)</span></span>
- <span data-ttu-id="dcd7c-323">Gestione del caso in cui Host non può restituire righe o colonne della schermata (#10938)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-323">Handle case where Host may not return Rows or Columns of screen (#10938)</span></span>
- <span data-ttu-id="dcd7c-324">Correzione dell'uso dei colori principali per gli host che non li supportano (#10937)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-324">Fix use of accent colors for hosts that don't support them (#10937)</span></span>
- <span data-ttu-id="dcd7c-325">Aggiunta del comando Update-List (#10922)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-325">Add back Update-List command (#10922)</span></span>
- <span data-ttu-id="dcd7c-326">Aggiornamento dell'ID FWLink per Clear-RecycleBin (#10925)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-326">Update FWLink Id for Clear-RecycleBin (#10925)</span></span>
- <span data-ttu-id="dcd7c-327">Durante il completamento tramite TAB, ignorare il file se non è in grado di leggere gli attributi del file (#10910)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-327">During tab completion, skip file if can't read file attributes (#10910)</span></span>
- <span data-ttu-id="dcd7c-328">Aggiunta di Clear-RecycleBin per Windows (#10909)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-328">Add back Clear-RecycleBin for Windows (#10909)</span></span>
- <span data-ttu-id="dcd7c-329">Aggiunta di `$env:__SuppressAnsiEscapeSequences` per controllare se è presente una sequenza di escape VT nell'output (#10814)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-329">Add `$env:__SuppressAnsiEscapeSequences` to control whether to have VT escape sequence in output (#10814)</span></span>
- <span data-ttu-id="dcd7c-330">Aggiunta del parametro -NoEmphasize per colorare l'output di Select-String (#8963) (grazie @derek-xia!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-330">Add -NoEmphasize parameter to colorize Select-String output (#8963) (Thanks @derek-xia!)</span></span>
- <span data-ttu-id="dcd7c-331">Aggiunta del cmdlet Get-HotFix (#10740)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-331">Add back Get-HotFix cmdlet (#10740)</span></span>
- <span data-ttu-id="dcd7c-332">Add-Type utilizzabile nelle applicazioni che ospitano PowerShell (#10587)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-332">Make Add-Type usable in applications that host PowerShell (#10587)</span></span>
- <span data-ttu-id="dcd7c-333">Uso di un ordine di valutazione più efficace in LanguagePrimitives.IsNullLike() (#10781) (grazie @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-333">Use more effective evaluation order in LanguagePrimitives.IsNullLike() (#10781) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="dcd7c-334">Miglioramento della gestione di input e flussi di input della pipeline della raccolta in Format-Hex (#8674) (grazie @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-334">Improve handling of mixed-collection piped input and piped streams of input in Format-Hex (#8674) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="dcd7c-335">Uso della conversione del tipo nelle tabelle hash SSHConnection quando il valore non corrisponde al tipo previsto (#10720) (grazie @SeeminglyScience!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-335">Use type conversion in SSHConnection hashtables when value doesn't match expected type (#10720) (Thanks @SeeminglyScience!)</span></span>
- <span data-ttu-id="dcd7c-336">Correzione del comportamento di Get-Content -ReadCount 0 quando viene impostato -TotalCount (#10749) (grazie @eugenesmlv!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-336">Fix Get-Content -ReadCount 0 behavior when -TotalCount is set (#10749) (Thanks @eugenesmlv!)</span></span>
- <span data-ttu-id="dcd7c-337">Ridefinizione del messaggio di errore di accesso negato in Get-WinEvent (#10639) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-337">Reword access denied error message in Get-WinEvent (#10639) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-338">Abilitazione del completamento tramite tasto TAB per l'assegnazione di variabili vincolata da enumerazione o tipo (#10646)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-338">Enable tab completion for variable assignment that is enum or type constrained (#10646)</span></span>
- <span data-ttu-id="dcd7c-339">Rimozione della proprietà remota SourceLength inutilizzata che causa problemi di formattazione (#10765)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-339">Remove unused SourceLength remoting property causing formatting issues (#10765)</span></span>
- <span data-ttu-id="dcd7c-340">Aggiunta del parametro -Delimiter a ConvertFrom-StringData (#10665) (grazie @steviecoaster!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-340">Add -Delimiter parameter to ConvertFrom-StringData (#10665) (Thanks @steviecoaster!)</span></span>
- <span data-ttu-id="dcd7c-341">Aggiunta del parametro posizionale per ScriptBlock quando si usa Invoke-Command con SSH (#10721) (grazie @machgo!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-341">Add positional parameter for ScriptBlock when using Invoke-Command with SSH (#10721) (Thanks @machgo!)</span></span>
- <span data-ttu-id="dcd7c-342">Visualizzazione delle informazioni di contesto della riga se sono presenti più righe ma nessun nome di script per ConciseView (#10746)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-342">Show line context information if multiple lines but no script name for ConciseView (#10746)</span></span>
- <span data-ttu-id="dcd7c-343">Aggiunta del supporto per i percorsi \\wsl$\ al provider del file system (#10674)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-343">Add support for \\wsl$\ paths to file system provider (#10674)</span></span>
- <span data-ttu-id="dcd7c-344">Aggiunta del testo del token mancante per TokenKind.QuestionMark nel parser (#10706)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-344">Add the missing token text for TokenKind.QuestionMark in parser (#10706)</span></span>
- <span data-ttu-id="dcd7c-345">Impostazione della directory di lavoro corrente di ogni script in esecuzione ForEach-Object -Parallel sullo stesso percorso dello script chiamante.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-345">Set current working directory of each ForEach-Object -Parallel running script to the same location as the calling script.</span></span> <span data-ttu-id="dcd7c-346">(#10672)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-346">(#10672)</span></span>
- <span data-ttu-id="dcd7c-347">Sostituzione di api-ms-win-core-file-l1-2-2.dll con Kernell32.dll per le API FindFirstStreamW e FindNextStreamW (#10680) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-347">Replace api-ms-win-core-file-l1-2-2.dll with Kernell32.dll for FindFirstStreamW and FindNextStreamW APIs (#10680) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-348">Perfezionamento dello script di formattazione della Guida per maggiore supporto di StrictMode (#10563)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-348">Tweak help formatting script to be more StrictMode tolerant (#10563)</span></span>
- <span data-ttu-id="dcd7c-349">Aggiunta del parametro -SecurityDescriptorSDDL a New-Service (#10483) (grazie @kvprasoon!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-349">Add -SecurityDescriptorSDDL parameter to New-Service (#10483) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="dcd7c-350">Rimozione dell'output informativo, consolidamento dell'utilizzo dei ping in Test-Connection (#10478) (grazie @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-350">Remove informational output, consolidate ping usage in Test-Connection (#10478) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="dcd7c-351">Lettura dei punti di analisi speciali senza eseguire l'accesso (#10662) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-351">Read special reparse points without accessing them (#10662) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-352">Indirizzamento dell'output Clear-Host al terminale (#10681) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-352">Direct Clear-Host output to terminal (#10681) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-353">Aggiunta di una nuova riga per il raggruppamento con Format-Table e -Property (#10653)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-353">Add back newline for grouping with Format-Table and -Property (#10653)</span></span>
- <span data-ttu-id="dcd7c-354">Rimozione di [ValidateNotNullOrEmpty] da -InputObject in Get-Random per consentire una stringa vuota (#10644)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-354">Remove [ValidateNotNullOrEmpty] from -InputObject on Get-Random to allow empty string (#10644)</span></span>
- <span data-ttu-id="dcd7c-355">Impostazione dell'algoritmo della distanza delle stringhe del sistema dei suggerimenti senza distinzione tra maiuscole e minuscole (#10549) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-355">Make suggestion system string distance algorithm case-insensitive (#10549) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-356">Correzione dell'eccezione di riferimento Null nell'elaborazione dell'input ForEach-Object -Parallel (#10577)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-356">Fix null reference exception in ForEach-Object -Parallel input processing (#10577)</span></span>
- <span data-ttu-id="dcd7c-357">Aggiunta delle definizioni dei criteri di gruppo di PowerShell Core (#10468)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-357">Add PowerShell Core group policy definitions (#10468)</span></span>
- <span data-ttu-id="dcd7c-358">Aggiornamento dell'host della console per il supporto delle sequenza di controllo VT XTPUSHSGR/XTPOPSGR usante negli scenari di composizione.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-358">Update console host to support XTPUSHSGR/XTPOPSGR VT control sequences that are used in composability scenarios.</span></span> <span data-ttu-id="dcd7c-359">(#10208)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-359">(#10208)</span></span>
- <span data-ttu-id="dcd7c-360">Aggiunta del parametro WorkingDirectory a Start-Job (#10324) (grazie @davinci26!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-360">Add WorkingDirectory parameter to Start-Job (#10324) (Thanks @davinci26!)</span></span>
- <span data-ttu-id="dcd7c-361">Rimozione del gestore dell'evento che ha causato la replica erronea delle modifiche del punto di interruzione nel debugger dello spazio di esecuzione dell'host (#10503) (grazie @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-361">Remove the event handler that was causing breakpoint changes to be erroneously replicated to the host runspace debugger (#10503) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="dcd7c-362">Sostituzione di api-ms-win-core-job-12-1-0.dll con Kernell32.dll nell'API P/Invoke Microsoft.PowerShell.Commands.NativeMethods (#10417) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-362">Replace api-ms-win-core-job-12-1-0.dll with Kernell32.dll in Microsoft.PowerShell.Commands.NativeMethods P/Invoke API(#10417) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-363">Correzione dell'output errato per New-Service nell'assegnazione di variabili e -OutVariable (#10444) (grazie @kvprasoon!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-363">Fix wrong output for New-Service in variable assignment and -OutVariable (#10444) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="dcd7c-364">Risoluzione dei problemi degli strumenti globali per il codice di uscita, i parametri della riga di comando e il percorso con spazi (#10461)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-364">Fix global tool issues around exit code, command line parameters and path with spaces (#10461)</span></span>
- <span data-ttu-id="dcd7c-365">Correzione della ricorsione in OneDrive - modifica di FindFirstFileEx() per l'uso del tipo SafeFindHandle (#10405)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-365">Fix recursion into OneDrive - change FindFirstFileEx() to use SafeFindHandle type (#10405)</span></span>
- <span data-ttu-id="dcd7c-366">Possibilità di ignorare il caricamento automatico di PSReadLine in Windows se il lettore NVDA è attivo (#10385)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-366">Skip auto-loading PSReadLine on Windows if the NVDA screen reader is active (#10385)</span></span>
- <span data-ttu-id="dcd7c-367">Aggiornamento delle versioni del modulo built-with-PowerShell alla versione 7.0.0.0 (#10356)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-367">Increase built-with-PowerShell module versions to 7.0.0.0 (#10356)</span></span>
- <span data-ttu-id="dcd7c-368">Aggiunta della generazione di un errore in Add-Type se esiste già un tipo con lo stesso nome (#9609) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-368">Add throwing an error in Add-Type if a type with the same name already exists (#9609) (Thanks @iSazonov!)</span></span>

### <a name="performance"></a><span data-ttu-id="dcd7c-369">Prestazioni</span><span class="sxs-lookup"><span data-stu-id="dcd7c-369">Performance</span></span>

- <span data-ttu-id="dcd7c-370">Mancato utilizzo della chiusura in Parser.SaveError (#11006)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-370">Avoid using closure in Parser.SaveError (#11006)</span></span>
- <span data-ttu-id="dcd7c-371">Miglioramento della memorizzazione nella cache durante la creazione di nuove istanze Regex (#10657) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-371">Improve the caching when creating new Regex instances (#10657) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-372">Miglioramento dell'elaborazione dei dati del tipo predefinito di PowerShell da types.ps1xml, typesV3.ps1xml e GetEvent.types.ps1xml (#10898)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-372">Improve processing of the PowerShell built-in type data from types.ps1xml, typesV3.ps1xml and GetEvent.types.ps1xml (#10898)</span></span>
- <span data-ttu-id="dcd7c-373">Aggiornamento di PSConfiguration.ReadValueFromFile per renderlo più veloce e più efficiente per la memoria (#10839)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-373">Update PSConfiguration.ReadValueFromFile to make it faster and more memory efficient (#10839)</span></span>
- <span data-ttu-id="dcd7c-374">Aggiunta di miglioramenti delle prestazioni secondari per l'inizializzazione dello spazio di esecuzione (#10569) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-374">Add minor performance improvements for runspace initialization (#10569) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-375">ForEach-Object più veloce per gli scenari di uso comune (#10454) e correzione del problema di prestazioni di ForEach-Object -Parallel con molti spazi di esecuzione (#10455)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-375">Make ForEach-Object faster for its commonly used scenarios (#10454) and fix ForEach-Object -Parallel performance problem with many runspaces (#10455)</span></span>

### <a name="code-cleanup"></a><span data-ttu-id="dcd7c-376">Pulizia del codice</span><span class="sxs-lookup"><span data-stu-id="dcd7c-376">Code Cleanup</span></span>

- <span data-ttu-id="dcd7c-377">Modifica del testo di commenti ed elementi per soddisfare gli standard Microsoft (#11304)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-377">Change comment and element text to meet Microsoft standards (#11304)</span></span>
- <span data-ttu-id="dcd7c-378">Pulizia dei problemi di stile in Compiler.cs (#10368) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-378">Cleanup style issues in Compiler.cs (#10368) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-379">Rimozione del convertitore di tipi non usati per CommaDelimitedStringCollection (#11000) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-379">Remove the unused type converter for CommaDelimitedStringCollection (#11000) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-380">Pulizia dello stile in InitialSessionState.cs (#10865) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-380">Cleanup style in InitialSessionState.cs (#10865) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-381">Pulizia del codice per la classe PSSession (#11001)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-381">Code clean up for PSSession class (#11001)</span></span>
- <span data-ttu-id="dcd7c-382">Rimozione della funzionalità 'run Update-Help from Get-Help when Get-Help runs for the first time' non funzionante (#10974)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-382">Remove the not-working 'run Update-Help from Get-Help when Get-Help runs for the first time' feature (#10974)</span></span>
- <span data-ttu-id="dcd7c-383">Risoluzione dei problemi di stile (#10998) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-383">Fix style issues (#10998) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-384">Pulizia: uso dell'alias di tipo predefinito (#10882) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-384">Cleanup: use the built-in type alias (#10882) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-385">Rimozione della chiave di impostazione non usata ConsolePrompting e rimozione della creazione di stringhe non necessarie quando si esegue una query sull'impostazione ExecutionPolicy (#10985)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-385">Remove the unused setting key ConsolePrompting and avoid unnecessary string creation when querying ExecutionPolicy setting (#10985)</span></span>
- <span data-ttu-id="dcd7c-386">Disabilitazione del controllo delle notifiche degli aggiornamenti per le build giornaliere (#10903) (grazie @bergmeister!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-386">Disable update notification check for daily builds (#10903) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="dcd7c-387">Reintegro dell'API di debug persa in #10338 (#10808)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-387">Reinstate debugging API lost in #10338 (#10808)</span></span>
- <span data-ttu-id="dcd7c-388">Rimozione del riferimento a WorkflowJobSourceAdapter non più usato (#10326) (grazie @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-388">Remove WorkflowJobSourceAdapter reference that is no longer used (#10326) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="dcd7c-389">Pulizia delle interfacce COM nel codice delle jump list tramite la correzione degli attributi PreserveSig (#9899) (grazie @weltkante!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-389">Cleanup COM interfaces in jump list code by fixing PreserveSig attributes (#9899) (Thanks @weltkante!)</span></span>
- <span data-ttu-id="dcd7c-390">Aggiunta di un commento che descrive perché -ia non è l'alias per il parametro comune -InformationAction (#10703) (grazie @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-390">Add a comment describing why -ia is not the alias for -InformationAction common parameter (#10703) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="dcd7c-391">Ridenominazione di InvokeCommandCmdlet.cs in InvokeExpressionCommand.cs (#10659) (grazie @kilasuit!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-391">Rename InvokeCommandCmdlet.cs to InvokeExpressionCommand.cs (#10659) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="dcd7c-392">Aggiunta di pulizie del codice secondarie correlate alle notifiche degli aggiornamenti (#10698)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-392">Add minor code cleanups related to update notifications (#10698)</span></span>
- <span data-ttu-id="dcd7c-393">Rimozione della logica del flusso di lavoro deprecato dagli script di installazione remota (#10320) (grazie @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-393">Remove deprecated workflow logic from the remoting setup scripts (#10320) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="dcd7c-394">Aggiornamento del formato della Guida per l'uso appropriato delle maiuscole e minuscole (#10678) (grazie @tnieto88!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-394">Update help format to use proper case (#10678) (Thanks @tnieto88!)</span></span>
- <span data-ttu-id="dcd7c-395">Pulizia dei problemi di stile di CodeFactor che si verificano nei commit dell'ultimo mese (#10591) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-395">Clean up CodeFactor style issues coming in commits for the last month (#10591) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-396">Correzione dell'errore di ortografia nella descrizione della funzionalità sperimentale PSTernaryOperator (#10586) (grazie @bergmeister!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-396">Fix typo in description of PSTernaryOperator experimental feature (#10586) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="dcd7c-397">Conversione del valore di enumerazione ActionPreference.Suspend in uno stato riservato non supportato e rimozione della restrizione sull'uso di ActionPreference.Ignore nelle variabili di preferenza (#10317) (grazie @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-397">Convert ActionPreference.Suspend enumeration value into a non-supported, reserved state, and remove restriction on using ActionPreference.Ignore in preference variables (#10317) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="dcd7c-398">Sostituzione di ArrayList con List<T> per ottenere un codice più leggibile e affidabile senza modificare la funzionalità (#10333) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-398">Replace ArrayList with List<T> to get more readable and reliable code without changing functionality (#10333) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-399">Correzioni allo stile del codice in TestConnectionCommand (#10439) (grazie @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-399">Make code style fixes to TestConnectionCommand (#10439) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="dcd7c-400">Pulizia di AutomationEngine e rimozione della chiamata al metodo SetSessionStateDrive aggiuntiva (#10416) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-400">Cleanup AutomationEngine and remove extra SetSessionStateDrive method call (#10416) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-401">Ridenominazione di ParameterSetName predefinito in Delimiter per ConvertTo-Csv e ConvertFrom-Csv (#10425)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-401">Rename default ParameterSetName back to Delimiter for ConvertTo-Csv and ConvertFrom-Csv (#10425)</span></span>

### <a name="tools"></a><span data-ttu-id="dcd7c-402">Strumenti</span><span class="sxs-lookup"><span data-stu-id="dcd7c-402">Tools</span></span>

- <span data-ttu-id="dcd7c-403">Aggiunta dell'impostazione predefinita per la proprietà SDKToUse in modo che venga compilata in VS (#11085)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-403">Add default setting for the SDKToUse property so that it builds in VS (#11085)</span></span>
- <span data-ttu-id="dcd7c-404">Install-Powershell.ps1: Aggiunta del parametro per l'uso dell'installazione MSI (#10921) (grazie @MJECloud!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-404">Install-Powershell.ps1: Add parameter to use MSI installation (#10921) (Thanks @MJECloud!)</span></span>
- <span data-ttu-id="dcd7c-405">Aggiunta di esempi di base per install-powershell.ps1 (#10914) (grazie @kilasuit!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-405">Add basic examples for install-powershell.ps1 (#10914) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="dcd7c-406">Install-PowerShellRemoting.ps1 gestisce la stringa vuota nel parametro PowerShellHome (#10526) (grazie @Orca88!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-406">Make Install-PowerShellRemoting.ps1 handle empty string in PowerShellHome parameter (#10526) (Thanks @Orca88!)</span></span>
- <span data-ttu-id="dcd7c-407">Passaggio da /etc/lsb-release a /etc/os-release in install-powershell.sh (#10773) (grazie @Himura2la!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-407">Switch from /etc/lsb-release to /etc/os-release in install-powershell.sh (#10773) (Thanks @Himura2la!)</span></span>
- <span data-ttu-id="dcd7c-408">Controllo di pwsh.exe e pwsh nella versione giornaliera in Windows (#10738) (grazie @centreboard!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-408">Check pwsh.exe and pwsh in daily version on Windows (#10738) (Thanks @centreboard!)</span></span>
- <span data-ttu-id="dcd7c-409">Rimozione del tocco non necessario in installpsh-osx.sh (#10752)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-409">Remove unneeded tap in installpsh-osx.sh (#10752)</span></span>
- <span data-ttu-id="dcd7c-410">Aggiornamento di install-powershell.ps1 per verificare la presenza di una build giornaliera già installata (#10489)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-410">Update install-powershell.ps1 to check for already installed daily build (#10489)</span></span>

### <a name="tests"></a><span data-ttu-id="dcd7c-411">Test</span><span class="sxs-lookup"><span data-stu-id="dcd7c-411">Tests</span></span>

- <span data-ttu-id="dcd7c-412">Test DSC non affidabili in sospeso (#11131)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-412">Make unreliable DSC test pending (#11131)</span></span>
- <span data-ttu-id="dcd7c-413">Correzione del test stringdata per convalidare correttamente le chiavi di tabelle hash (#10810)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-413">Fix stringdata test to correctly validate keys of hashtables (#10810)</span></span>
- <span data-ttu-id="dcd7c-414">Scaricamento di moduli di test (#11061) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-414">Unload test modules (#11061) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-415">Aumento dell'intervallo di tempo tra i tentativi degli URL di test (#11015)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-415">Increase time between retries of testing URL (#11015)</span></span>
- <span data-ttu-id="dcd7c-416">Aggiornamento dei test per una descrizione accurata delle azioni di test.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-416">Update tests to accurately describe test actions.</span></span> <span data-ttu-id="dcd7c-417">(#10928) (grazie @romero126!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-417">(#10928) (Thanks @romero126!)</span></span>
- <span data-ttu-id="dcd7c-418">Possibilità di ignorare temporaneamente il test inattendibile TestAppDomainProcessExitEvenHandlerNotLeaking (#10827)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-418">Temporary skip the flaky test TestAppDomainProcessExitEvenHandlerNotLeaking (#10827)</span></span>
- <span data-ttu-id="dcd7c-419">Stabilità del test di perdita del gestore dell'evento (#10790)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-419">Make the event handler leaking test stable (#10790)</span></span>
- <span data-ttu-id="dcd7c-420">Sincronizzazione delle iniziali maiuscole in CI YAML (#10767) (grazie @RDIL!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-420">Sync capitalization in CI YAML (#10767) (Thanks @RDIL!)</span></span>
- <span data-ttu-id="dcd7c-421">Aggiunta del test per la correzione della perdita del gestore dell'evento (#10768)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-421">Add test for the event handler leaking fix (#10768)</span></span>
- <span data-ttu-id="dcd7c-422">Aggiunta del test Get-ChildItem (#10507) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-422">Add Get-ChildItem test (#10507) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-423">Sostituzione del linguaggio ambiguo per i test da opzione a parametro per maggior accuratezza (#10666) (grazie @romero126!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-423">Replace ambiguous language for tests from switch to parameter for accuracy (#10666) (Thanks @romero126!)</span></span>
- <span data-ttu-id="dcd7c-424">Aggiunta del controllo sperimentale ai test ForEach-Object -Parallel (#10354) (grazie @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-424">Add experimental check to ForEach-Object -Parallel tests (#10354) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="dcd7c-425">Aggiornamento dei test per la convalida Alpine (#10428)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-425">Update tests for Alpine validation (#10428)</span></span>

### <a name="build-and-package-improvements"></a><span data-ttu-id="dcd7c-426">Miglioramenti di build e pacchetti</span><span class="sxs-lookup"><span data-stu-id="dcd7c-426">Build and Package Improvements</span></span>

- <span data-ttu-id="dcd7c-427">Correzione della firma dei pacchetti NuGet per la build Coordinated Package (#11316)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-427">Fix Nuget package signing for Coordinated Package build (#11316)</span></span>
- <span data-ttu-id="dcd7c-428">Aggiornamento delle dipendenze da PowerShell Gallery e NuGet (#11323)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-428">Update dependencies from PowerShell Gallery and NuGet (#11323)</span></span>
- <span data-ttu-id="dcd7c-429">Aggiornamento di Microsoft.ApplicationInsights dalla versione 2.11.0 alla versione 2.12.0 (#11305)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-429">Bump Microsoft.ApplicationInsights from 2.11.0 to 2.12.0 (#11305)</span></span>
- <span data-ttu-id="dcd7c-430">Aggiornamento di Microsoft.CodeAnalysis.CSharp dalla versione 3.3.1 alla versione 3.4.0 (#11265)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-430">Bump Microsoft.CodeAnalysis.CSharp from 3.3.1 to 3.4.0 (#11265)</span></span>
- <span data-ttu-id="dcd7c-431">Aggiornamento dei pacchetti per Debian 10 e 11 (#11236)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-431">Updates packages for Debian 10 and 11 (#11236)</span></span>
- <span data-ttu-id="dcd7c-432">Abilitazione delle funzionalità sperimentali solo prima della versione RC (#11162)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-432">Only enable experimental features prior to RC (#11162)</span></span>
- <span data-ttu-id="dcd7c-433">Aggiornamento della versione minima di macOS (#11163)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-433">Update macOS minimum version (#11163)</span></span>
- <span data-ttu-id="dcd7c-434">Aggiornamento di NJsonSchema dalla versione 10.0.27 alla versione 10.0.28 (#11170)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-434">Bump NJsonSchema from 10.0.27 to 10.0.28 (#11170)</span></span>
- <span data-ttu-id="dcd7c-435">Aggiornamento dei collegamenti in README.md e metadata.json per la versione Preview.5 (#10854)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-435">Updating links in README.md and metadata.json for Preview.5 (#10854)</span></span>
- <span data-ttu-id="dcd7c-436">Selezione dei file per i test di conformità di proprietà di PowerShell (#10837)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-436">Select the files for compliance tests which are owned by PowerShell (#10837)</span></span>
- <span data-ttu-id="dcd7c-437">Compilazione del pacchetto msix di win7x86.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-437">Allow win7x86 msix package to build.</span></span> <span data-ttu-id="dcd7c-438">(Interno 10515)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-438">(Internal 10515)</span></span>
- <span data-ttu-id="dcd7c-439">Passaggio di versioni semantiche alla funzione NormalizeVersion (#11087)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-439">Allow semantic versions to be passed to NormalizeVersion function (#11087)</span></span>
- <span data-ttu-id="dcd7c-440">Aggiornamento del framework .NET Core alla versione 3.1-Preview.3 (#11079)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-440">Bump .NET core framework to 3.1-preview.3 (#11079)</span></span>
- <span data-ttu-id="dcd7c-441">Aggiornamento di PSReadLine dalla versione 2.0.0-beta5 alla versione 2.0.0-beta6 in /src/Modules (#11078)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-441">Bump PSReadLine from 2.0.0-beta5 to 2.0.0-beta6 in /src/Modules (#11078)</span></span>
- <span data-ttu-id="dcd7c-442">Aggiornamento di Newtonsoft.Json dalla versione 12.0.2 alla versione 12.0.3 (#11037) (#11038)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-442">Bump Newtonsoft.Json from 12.0.2 to 12.0.3 (#11037) (#11038)</span></span>
- <span data-ttu-id="dcd7c-443">Aggiunta dei pacchetti Debian 10, 11 e CentOS 8 (#11028)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-443">Add Debian 10, 11 and CentOS 8 packages (#11028)</span></span>
- <span data-ttu-id="dcd7c-444">Caricamento del file JSON Build-Info con il campo ReleaseDate (#10986)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-444">Upload Build-Info Json file with the ReleaseDate field (#10986)</span></span>
- <span data-ttu-id="dcd7c-445">Aggiornamento del framework .NET Core alla versione 3.1-Preview.2 (#10993)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-445">Bump .NET core framework to 3.1-preview.2 (#10993)</span></span>
- <span data-ttu-id="dcd7c-446">Abilitazione della compilazione del pacchetto MSIX x86 (#10934)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-446">Enable build of x86 MSIX package (#10934)</span></span>
- <span data-ttu-id="dcd7c-447">Aggiornamento dell'URL dello script di installazione DotNet SDK in build.psm1 (#10927)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-447">Update the dotnet SDK install script URL in build.psm1 (#10927)</span></span>
- <span data-ttu-id="dcd7c-448">Aggiornamento di Markdig.Signed dalla versione 0.17.1 alla versione 0.18.0 (#10887)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-448">Bump Markdig.Signed from 0.17.1 to 0.18.0 (#10887)</span></span>
- <span data-ttu-id="dcd7c-449">Aggiornamento di ThreadJob dalla versione 2.0.1 alla versione 2.0.2 (#10886)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-449">Bump ThreadJob from 2.0.1 to 2.0.2 (#10886)</span></span>
- <span data-ttu-id="dcd7c-450">Aggiornamento del manifesto AppX e del modulo di creazione pacchetti per soddisfare i requisiti di MS Store (#10878)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-450">Update AppX Manifest and Packaging module to conform to MS Store requirements (#10878)</span></span>
- <span data-ttu-id="dcd7c-451">Aggiornamento del riferimento al pacchetto per PowerShell SDK nella versione Preview.5 (Interno 10295)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-451">Update package reference for PowerShell SDK to preview.5 (Internal 10295)</span></span>
- <span data-ttu-id="dcd7c-452">Aggiornamento di ThirdPartyNotices.txt (#10834)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-452">Update ThirdPartyNotices.txt (#10834)</span></span>
- <span data-ttu-id="dcd7c-453">Aggiornamento di Microsoft.PowerShell.Native alla versione 7.0.0-Preview.3 (#10826)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-453">Bump Microsoft.PowerShell.Native to 7.0.0-preview.3 (#10826)</span></span>
- <span data-ttu-id="dcd7c-454">Aggiornamento di Microsoft.ApplicationInsights dalla versione 2.10.0 alla versione 2.11.0 (#10608)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-454">Bump Microsoft.ApplicationInsights from 2.10.0 to 2.11.0 (#10608)</span></span>
- <span data-ttu-id="dcd7c-455">Aggiornamento di NJsonSchema dalla versione 10.0.24 alla versione 10.0.27 (#10756)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-455">Bump NJsonSchema from 10.0.24 to 10.0.27 (#10756)</span></span>
- <span data-ttu-id="dcd7c-456">Aggiunta del supporto MacPorts al sistema di compilazione (#10736) (grazie @Lucius-Q-User!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-456">Add MacPorts support to the build system (#10736) (Thanks @Lucius-Q-User!)</span></span>
- <span data-ttu-id="dcd7c-457">Aggiornamento di PackageManagement dalla versione 1.4.4 alla versione 1.4.5 (#10728)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-457">Bump PackageManagement from 1.4.4 to 1.4.5 (#10728)</span></span>
- <span data-ttu-id="dcd7c-458">Aggiornamento di NJsonSchema dalla versione 10.0.23 alla versione 10.0.24 (#10635)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-458">Bump NJsonSchema from 10.0.23 to 10.0.24 (#10635)</span></span>
- <span data-ttu-id="dcd7c-459">Aggiunta della variabile di ambiente per distinguere i dati di telemetria client/server in MSI (#10612)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-459">Add environment variable to differentiate client/server telemetry in MSI (#10612)</span></span>
- <span data-ttu-id="dcd7c-460">Aggiornamento di PSDesiredStateConfiguration dalla versione 2.0.3 alla versione 2.0.4 (#10603)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-460">Bump PSDesiredStateConfiguration from 2.0.3 to 2.0.4 (#10603)</span></span>
- <span data-ttu-id="dcd7c-461">Aggiornamento di Microsoft.CodeAnalysis.CSharp dalla versione 3.2.1 alla versione 3.3.1 (#10607)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-461">Bump Microsoft.CodeAnalysis.CSharp from 3.2.1 to 3.3.1 (#10607)</span></span>
- <span data-ttu-id="dcd7c-462">Aggiornamento a .Net Core 3.0 RTM (#10604) (grazie @bergmeister!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-462">Update to .Net Core 3.0 RTM (#10604) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="dcd7c-463">Aggiornamento della creazione pacchetti MSIX per la versione per soddisfare i requisiti di Windows Store (#10588)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-463">Update MSIX packaging so the version to Windows Store requirements (#10588)</span></span>
- <span data-ttu-id="dcd7c-464">Aggiornamento di PowerShellGet dalla versione 2.2 alla versione 2.2.1 (#10382)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-464">Bump PowerShellGet version from 2.2 to 2.2.1 (#10382)</span></span>
- <span data-ttu-id="dcd7c-465">Aggiornamento di PackageManagement dalla versione 1.4.3 alla versione 1.4.4 (#10383)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-465">Bump PackageManagement version from 1.4.3 to 1.4.4 (#10383)</span></span>
- <span data-ttu-id="dcd7c-466">Aggiornamento di README.md e metadata.json per la versione 7.0.0-Preview.4 (Interno 10011)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-466">Update README.md and metadata.json for 7.0.0-preview.4 (Internal 10011)</span></span>
- <span data-ttu-id="dcd7c-467">Aggiornamento di .Net Core 3.0 dalla versione Preview 9 alla versione RC1 (#10552) (grazie @bergmeister!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-467">Upgrade .Net Core 3.0 version from Preview 9 to RC1 (#10552) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="dcd7c-468">Correzione della generazione dell'elenco ExperimentalFeature (Interno 9996)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-468">Fix ExperimentalFeature list generation (Internal 9996)</span></span>
- <span data-ttu-id="dcd7c-469">Aggiornamento di PSReadLine dalla versione 2.0.0-beta4 alla versione 2.0.0-beta5 (#10536)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-469">Bump PSReadLine version from 2.0.0-beta4 to 2.0.0-beta5 (#10536)</span></span>
- <span data-ttu-id="dcd7c-470">Correzione dello script di compilazione della versione per l'impostazione del tag di versione</span><span class="sxs-lookup"><span data-stu-id="dcd7c-470">Fix release build script to set release tag</span></span>
- <span data-ttu-id="dcd7c-471">Aggiornamento della versione di Microsoft.PowerShell.Native alla versione 7.0.0-Preview.2 (#10519)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-471">Update version of Microsoft.PowerShell.Native to 7.0.0-preview.2 (#10519)</span></span>
- <span data-ttu-id="dcd7c-472">Aggiornamento a Netcoreapp3.0 preview9 (#10484) (grazie @bergmeister!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-472">Upgrade to Netcoreapp3.0 preview9 (#10484) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="dcd7c-473">Verifica che la build coordinata giornaliera venga considerata come build giornaliera (#10464)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-473">Make sure the daily coordinated build, knows it is a daily build (#10464)</span></span>
- <span data-ttu-id="dcd7c-474">Aggiornamento della build del pacchetto combinato per il rilascio di build giornaliere (#10449)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-474">Update the combined package build to release the daily builds (#10449)</span></span>
- <span data-ttu-id="dcd7c-475">Rimozione del riferimento ad appveyor (#10445) (grazie @RDIL!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-475">Remove appveyor reference (#10445) (Thanks @RDIL!)</span></span>
- <span data-ttu-id="dcd7c-476">Aggiornamento di NJsonSchema dalla versione 10.0.22 alla versione 10.0.23 (#10421)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-476">Bump NJsonSchema version from 10.0.22 to 10.0.23 (#10421)</span></span>
- <span data-ttu-id="dcd7c-477">Rimozione dell'eliminazione della cartella della build linux-x64 perché richiesta da alcune dipendenze per Alpine (#10407)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-477">Remove the deletion of linux-x64 build folder because some dependencies for Alpine need it (#10407)</span></span>

### <a name="documentation-and-help-content"></a><span data-ttu-id="dcd7c-478">Documentazione e contenuto della Guida</span><span class="sxs-lookup"><span data-stu-id="dcd7c-478">Documentation and Help Content</span></span>

- <span data-ttu-id="dcd7c-479">Refactoring dei log delle modifiche in un unico log per ogni versione (#11165)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-479">Refactor change logs into one log per release (#11165)</span></span>
- <span data-ttu-id="dcd7c-480">Correzione dei FWLink per i documenti della Guida in linea di PowerShell 7 (#11071)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-480">Fix FWLinks for PowerShell 7 online help documents (#11071)</span></span>
- <span data-ttu-id="dcd7c-481">Aggiornamento di CONTRIBUTING.md (#11096) (grazie @mklement0!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-481">Update CONTRIBUTING.md (#11096) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="dcd7c-482">Correzione dei collegamenti della documentazione di installazione in README.md (#11083)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-482">Fix installation doc links in README.md (#11083)</span></span>
- <span data-ttu-id="dcd7c-483">Aggiunta di esempi allo script install-powershell.ps1 (#11024) (grazie @kilasuit!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-483">Adds examples to install-powershell.ps1 script (#11024) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="dcd7c-484">Correzione dell'enfasi Select-String e Import-DscResource in CHANGELOG.md (#10890)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-484">Fix to Select-String emphasis and Import-DscResource in CHANGELOG.md (#10890)</span></span>
- <span data-ttu-id="dcd7c-485">Rimozione del collegamento non aggiornato da powershell-beginners-guide.md (#10926)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-485">Remove the stale link from powershell-beginners-guide.md (#10926)</span></span>
- <span data-ttu-id="dcd7c-486">Unione dei log delle modifiche stabili e di manutenzione (#10527)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-486">Merge stable and servicing change logs (#10527)</span></span>
- <span data-ttu-id="dcd7c-487">Aggiornamento della versione di .NET usata nelle documentazioni delle build (#10775) (grazie @Greg-Smulko!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-487">Update used .NET version in build docs (#10775) (Thanks @Greg-Smulko!)</span></span>
- <span data-ttu-id="dcd7c-488">Sostituzione dei collegamenti di MSDN a docs.microsoft.com in powershell-beginners-guide.md (#10778) (grazie @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-488">Replace links from MSDN to docs.microsoft.com in powershell-beginners-guide.md (#10778) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="dcd7c-489">Correzione del collegamento di panoramica DSC interrotto (#10702)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-489">Fix broken DSC overview link (#10702)</span></span>
- <span data-ttu-id="dcd7c-490">Aggiornamento di Support_Question.md per il collegamento a Stack Overflow come risorsa di community diversa (#10638) (grazie @mklement0!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-490">Update Support_Question.md to link to Stack Overflow as another community resource (#10638) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="dcd7c-491">Aggiunta dell'architettura del processore al modello di richiesta di distribuzione (#10661)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-491">Add processor architecture to distribution request template (#10661)</span></span>
- <span data-ttu-id="dcd7c-492">Aggiunta di un nuovo libro MoL di PowerShell alla documentazione di PowerShell per l'apprendimento (#10602)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-492">Add new PowerShell MoL book to learning PowerShell docs (#10602)</span></span>
- <span data-ttu-id="dcd7c-493">Aggiornamento di README.md e dei metadati per le versioni v6.1.6 e v6.2.3 (#10523)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-493">Update README.md and metadata for v6.1.6 and v6.2.3 releases (#10523)</span></span>
- <span data-ttu-id="dcd7c-494">Correzione di un errore di ortografia in README.md (#10465) (grazie @vedhasp!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-494">Fix a typo in README.md (#10465) (Thanks @vedhasp!)</span></span>
- <span data-ttu-id="dcd7c-495">Aggiunta di un riferimento al modulo PSKoans alla documentazione delle risorse didattiche (#10369) (grazie @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-495">Add a reference to PSKoans module to Learning Resources documentation (#10369) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="dcd7c-496">Aggiornamento di README.md e metadata.json per 7.0.0-Preview. 3 (#10393)</span><span class="sxs-lookup"><span data-stu-id="dcd7c-496">Update README.md and metadata.json for 7.0.0-preview.3 (#10393)</span></span>
