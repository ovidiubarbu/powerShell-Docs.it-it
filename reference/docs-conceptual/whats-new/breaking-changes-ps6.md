---
ms.date: 02/03/2020
keywords: powershell,core
title: Modifiche di rilievo in PowerShell Core 6.0
ms.openlocfilehash: 47ed14cceed86e4dd04a8e0079af00f6a98988ea
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "76995454"
---
# <a name="breaking-changes-for-powershell-6x"></a><span data-ttu-id="d3577-103">Modifiche di rilievo in PowerShell Core 6.x</span><span class="sxs-lookup"><span data-stu-id="d3577-103">Breaking Changes for PowerShell 6.x</span></span>

## <a name="features-no-longer-available-in-powershell-core"></a><span data-ttu-id="d3577-104">Funzionalità non più disponibili in PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="d3577-104">Features no longer available in PowerShell Core</span></span>

### <a name="modules-not-shipped-for-powershell-6x"></a><span data-ttu-id="d3577-105">Moduli non inclusi in PowerShell 6.x</span><span class="sxs-lookup"><span data-stu-id="d3577-105">Modules not shipped for PowerShell 6.x</span></span>

<span data-ttu-id="d3577-106">Per diversi motivi di compatibilità, i moduli seguenti non sono inclusi in PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="d3577-106">For various compatibility reasons, the following modules are not included in PowerShell 6.</span></span>

- <span data-ttu-id="d3577-107">ISE</span><span class="sxs-lookup"><span data-stu-id="d3577-107">ISE</span></span>
- <span data-ttu-id="d3577-108">Microsoft.PowerShell.LocalAccounts</span><span class="sxs-lookup"><span data-stu-id="d3577-108">Microsoft.PowerShell.LocalAccounts</span></span>
- <span data-ttu-id="d3577-109">Microsoft.PowerShell.ODataUtils</span><span class="sxs-lookup"><span data-stu-id="d3577-109">Microsoft.PowerShell.ODataUtils</span></span>
- <span data-ttu-id="d3577-110">Microsoft.PowerShell.Operation.Validation</span><span class="sxs-lookup"><span data-stu-id="d3577-110">Microsoft.PowerShell.Operation.Validation</span></span>
- <span data-ttu-id="d3577-111">PSScheduledJob</span><span class="sxs-lookup"><span data-stu-id="d3577-111">PSScheduledJob</span></span>
- <span data-ttu-id="d3577-112">PSWorkflow</span><span class="sxs-lookup"><span data-stu-id="d3577-112">PSWorkflow</span></span>
- <span data-ttu-id="d3577-113">PSWorkflowUtility</span><span class="sxs-lookup"><span data-stu-id="d3577-113">PSWorkflowUtility</span></span>

### <a name="powershell-workflow"></a><span data-ttu-id="d3577-114">Flusso di lavoro PowerShell</span><span class="sxs-lookup"><span data-stu-id="d3577-114">PowerShell Workflow</span></span>

<span data-ttu-id="d3577-115">[Flusso di lavoro PowerShell][workflow] è una funzionalità di Windows PowerShell basata su [Windows Workflow Foundation (WF)][workflow-foundation] che consente di creare runbook affidabili per le attività di lunga durata o parallelizzate.</span><span class="sxs-lookup"><span data-stu-id="d3577-115">[PowerShell Workflow][workflow] is a feature in Windows PowerShell that builds on top of [Windows Workflow Foundation (WF)][workflow-foundation] that enables the creation of robust runbooks for long-running or parallelized tasks.</span></span>

<span data-ttu-id="d3577-116">Dal momento che Windows Workflow Foundation non è supportato in .NET Core, il flusso di lavoro di PowerShell non è supportato in PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="d3577-116">Due to the lack of support for Windows Workflow Foundation in .NET Core, we are not supporting PowerShell Workflow in PowerShell Core.</span></span>

<span data-ttu-id="d3577-117">In futuro, è prevista l'abilitazione di parallelismo/concorrenza nativi nel linguaggio di PowerShell senza la necessità di Flusso di lavoro PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d3577-117">In the future, we would like to enable native parallelism/concurrency in the PowerShell language without the need for PowerShell Workflow.</span></span>

<span data-ttu-id="d3577-118">Se è necessario usare i checkpoint per riprendere uno script dopo il riavvio del sistema operativo, è consigliabile usare il componente Utilità di pianificazione per eseguire uno script all'avvio del sistema operativo, ma lo script deve mantenere il proprio stato, ad esempio con il salvataggio permanente in un file.</span><span class="sxs-lookup"><span data-stu-id="d3577-118">If there is a need to use checkpoints to resume a script after the OS restarts, we recommend using Task Scheduler to run a script on OS startup, but the script would need to maintain its own state (like persisting it to a file).</span></span>

[workflow]: /powershell/scripting/components/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a><span data-ttu-id="d3577-119">Snap-in personalizzati</span><span class="sxs-lookup"><span data-stu-id="d3577-119">Custom snap-ins</span></span>

<span data-ttu-id="d3577-120">Gli [snap-in PowerShell][snapin] sono predecessori dei moduli PowerShell che non sono stati adottati diffusamente nella community di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d3577-120">[PowerShell snap-ins][snapin] are a predecessor to PowerShell modules that do not have widespread adoption in the PowerShell community.</span></span>

<span data-ttu-id="d3577-121">A causa della complessità di supportare gli snap-in e dello scarso utilizzo nella community, gli snap-in personalizzati non sono più supportati in PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="d3577-121">Due to the complexity of supporting snap-ins and their lack of usage in the community, we no longer support custom snap-ins in PowerShell Core.</span></span>

<span data-ttu-id="d3577-122">Attualmente, ciò causa problemi per i moduli `ActiveDirectory` e `DnsClient` in Windows e Windows Server.</span><span class="sxs-lookup"><span data-stu-id="d3577-122">Today, this breaks the `ActiveDirectory` and `DnsClient` modules in Windows and Windows Server.</span></span>

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a><span data-ttu-id="d3577-123">Cmdlet WMI v1</span><span class="sxs-lookup"><span data-stu-id="d3577-123">WMI v1 cmdlets</span></span>

<span data-ttu-id="d3577-124">A causa della complessità del supporto di due set di moduli basati su WMI, i cmdlet WMI v1 sono stati rimossi da PowerShell Core:</span><span class="sxs-lookup"><span data-stu-id="d3577-124">Due to the complexity of supporting two sets of WMI-based modules, we removed the WMI v1 cmdlets from PowerShell Core:</span></span>

- `Register-WmiEvent`
- `Set-WmiInstance`
- `Invoke-WmiMethod`
- `Get-WmiObject`
- `Remove-WmiObject`

<span data-ttu-id="d3577-125">In alternativa, viene consigliato l'uso dei cmdlet CIM (noti anche come WMI versione 2) che offrono le stesse funzionalità con alcune novità e una sintassi riprogettata:</span><span class="sxs-lookup"><span data-stu-id="d3577-125">Instead, we recommend that you the use the CIM (aka WMI v2) cmdlets which provide the same functionality with new functionality and a redesigned syntax:</span></span>

- `Get-CimAssociatedInstance`
- `Get-CimClass`
- `Get-CimInstance`
- `Get-CimSession`
- `Invoke-CimMethod`
- `New-CimInstance`
- `New-CimSession`
- `New-CimSessionOption`
- `Register-CimIndicationEvent`
- `Remove-CimInstance`
- `Remove-CimSession`
- `Set-CimInstance`

### <a name="microsoftpowershelllocalaccounts"></a><span data-ttu-id="d3577-126">Microsoft.PowerShell.LocalAccounts</span><span class="sxs-lookup"><span data-stu-id="d3577-126">Microsoft.PowerShell.LocalAccounts</span></span>

<span data-ttu-id="d3577-127">A causa dell'uso di API non supportate, `Microsoft.PowerShell.LocalAccounts` è stato rimosso da PowerShell Core finché non viene trovata una soluzione migliore.</span><span class="sxs-lookup"><span data-stu-id="d3577-127">Due to the use of unsupported APIs, `Microsoft.PowerShell.LocalAccounts` has been removed from PowerShell Core until a better solution is found.</span></span>

### <a name="new-webserviceproxy-cmdlet-removed"></a><span data-ttu-id="d3577-128">Cmdlet `New-WebServiceProxy` rimosso</span><span class="sxs-lookup"><span data-stu-id="d3577-128">`New-WebServiceProxy` cmdlet removed</span></span>

<span data-ttu-id="d3577-129">.NET Core non supporta Windows Communication Framework, che offre servizi per l'uso del protocollo SOAP.</span><span class="sxs-lookup"><span data-stu-id="d3577-129">.NET Core does not support the Windows Communication Framework, which provide services for using the SOAP protocol.</span></span> <span data-ttu-id="d3577-130">Questo cmdlet è stato rimosso perché richiede SOAP.</span><span class="sxs-lookup"><span data-stu-id="d3577-130">This cmdlet was removed because it requires SOAP.</span></span>

### <a name="-transaction-cmdlets-removed"></a><span data-ttu-id="d3577-131">Cmdlet `*-Transaction` rimossi</span><span class="sxs-lookup"><span data-stu-id="d3577-131">`*-Transaction` cmdlets removed</span></span>

<span data-ttu-id="d3577-132">Questi cmdlet hanno un utilizzo molto limitato.</span><span class="sxs-lookup"><span data-stu-id="d3577-132">These cmdlets had very limited usage.</span></span> <span data-ttu-id="d3577-133">È stata presa la decisione di interromperne il supporto.</span><span class="sxs-lookup"><span data-stu-id="d3577-133">The decision was made to discontinue support for them.</span></span>

- `Complete-Transaction`
- `Get-Transaction`
- `Start-Transaction`
- `Undo-Transaction`
- `Use-Transaction`

### <a name="security-cmdlets-not-available-on-non-windows-platforms"></a><span data-ttu-id="d3577-134">Cmdlet di sicurezza non disponibili nelle piattaforme non Windows</span><span class="sxs-lookup"><span data-stu-id="d3577-134">Security cmdlets not available on non-Windows platforms</span></span>

- `Get-Acl`
- `Set-Acl`
- `Get-AuthenticodeSignature`
- `Set-AuthenticodeSignature`
- `Get-CmsMessage`
- `Protect-CmsMessage`
- `Unprotect-CmsMessage`
- `New-FileCatalog`
- `Test-FileCatalog`

### <a name="-computerand-other-windows-specific-cmdlets"></a><span data-ttu-id="d3577-135">Cmdlet `*-Computer` e altri cmdlet specifici di Windows</span><span class="sxs-lookup"><span data-stu-id="d3577-135">`*-Computer`and other Windows-specific cmdlets</span></span>

<span data-ttu-id="d3577-136">A causa dell'uso di API non supportate, i cmdlet seguenti sono stati rimossi da PowerShell Core finché non viene trovata una soluzione migliore.</span><span class="sxs-lookup"><span data-stu-id="d3577-136">Due to the use of unsupported APIs, the following cmdlets have been removed from PowerShell Core until a better solution is found.</span></span>

- `Get-Clipboard`
- `Set-Clipboard`
- `Add-Computer`
- `Checkpoint-Computer`
- `Remove-Computer`
- `Restore-Computer`
- `Reset-ComputerMachinePassword`
- `Disable-ComputerRestore`
- `Enable-ComputerRestore`
- `Get-ComputerRestorePoint`
- `Test-ComputerSecureChannel`
- `Get-ControlPanelItem`
- `Show-ControlPanelItem`
- `Get-HotFix`
- `Clear-RecycleBin`
- `Update-List`
- `Out-Printer`
- `ConvertFrom-String`
- `Convert-String`

### <a name="-counter-cmdlets"></a><span data-ttu-id="d3577-137">Cmdlet di `*-Counter`</span><span class="sxs-lookup"><span data-stu-id="d3577-137">`*-Counter` cmdlets</span></span>

<span data-ttu-id="d3577-138">A causa dell'uso di API non supportate, `*-Counter` è stato rimosso da PowerShell Core finché non viene trovata una soluzione migliore.</span><span class="sxs-lookup"><span data-stu-id="d3577-138">Due to the use of unsupported APIs, the `*-Counter` has been removed from PowerShell Core until a better solution is found.</span></span>

### <a name="-eventlog-cmdlets"></a><span data-ttu-id="d3577-139">Cmdlet di `*-EventLog`</span><span class="sxs-lookup"><span data-stu-id="d3577-139">`*-EventLog` cmdlets</span></span>

<span data-ttu-id="d3577-140">A causa dell'uso di API non supportate, `*-EventLog` è stato rimosso da PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="d3577-140">Due to the use of unsupported APIs, the `*-EventLog` has been removed from PowerShell Core.</span></span> <span data-ttu-id="d3577-141">fino a quando non viene trovata una soluzione migliore.</span><span class="sxs-lookup"><span data-stu-id="d3577-141">until a better solution is found.</span></span> <span data-ttu-id="d3577-142">`Get-WinEvent` e `Create-WinEvent` sono disponibili per ottenere e creare gli eventi in Windows.</span><span class="sxs-lookup"><span data-stu-id="d3577-142">`Get-WinEvent` and `Create-WinEvent` are available to get and create events on Windows.</span></span>

### <a name="cmdlets-that-use-wpf-removed"></a><span data-ttu-id="d3577-143">Cmdlet che usano WPF rimossi</span><span class="sxs-lookup"><span data-stu-id="d3577-143">Cmdlets that use WPF removed</span></span>

<span data-ttu-id="d3577-144">Windows Presentation Framework non è supportato in CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d3577-144">The Windows Presentation Framework is not supported on CoreCLR.</span></span> <span data-ttu-id="d3577-145">Sono interessati i seguenti cmdlet:</span><span class="sxs-lookup"><span data-stu-id="d3577-145">The following cmdlets are affected:</span></span>

- `Show-Command`
- `Out-GridView`
- <span data-ttu-id="d3577-146">Il parametro **showwindow** di `Get-Help`</span><span class="sxs-lookup"><span data-stu-id="d3577-146">The **showwindow** parameter of `Get-Help`</span></span>

### <a name="some-dsc-cmdlets-removed"></a><span data-ttu-id="d3577-147">Alcuni cmdlet DSC sono stati rimossi</span><span class="sxs-lookup"><span data-stu-id="d3577-147">Some DSC cmdlets removed</span></span>

- `Get-DscConfiguration`
- `Publish-DscConfiguration`
- `Restore-DscConfiguration`
- `Start-DscConfiguration`
- `Stop-DscConfiguration`
- `Test-DscConfiguration`
- `Update-DscConfiguration`
- `Remove-DscConfigurationDocument`
- `Get-DscConfigurationStatus`
- `Disable-DscDebug`
- `Enable-DscDebug`
- `Get-DscLocalConfigurationManager`
- `Set-DscLocalConfigurationManager`
- `Invoke-DscResource`

## <a name="enginelanguage-changes"></a><span data-ttu-id="d3577-148">Modifiche del motore/linguaggio</span><span class="sxs-lookup"><span data-stu-id="d3577-148">Engine/language changes</span></span>

### <a name="rename-powershellexe-to-pwshexe-5101"></a><span data-ttu-id="d3577-149">Rinominare `powershell.exe` in `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)</span><span class="sxs-lookup"><span data-stu-id="d3577-149">Rename `powershell.exe` to `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)</span></span>

<span data-ttu-id="d3577-150">Per offrire agli utenti un modo deterministico per chiamare PowerShell Core in Windows (in contrapposizione a Windows PowerShell), il file binario di PowerShell Core è stato modificato in `pwsh.exe` in Windows e in `pwsh` nelle piattaforme non Windows.</span><span class="sxs-lookup"><span data-stu-id="d3577-150">In order to give users a deterministic way to call PowerShell Core on Windows (as opposed to Windows PowerShell), the PowerShell Core binary was changed to `pwsh.exe` on Windows and `pwsh` on non-Windows platforms.</span></span>

<span data-ttu-id="d3577-151">Il nome abbreviato è anche coerente con la denominazione delle shell in piattaforme non Windows.</span><span class="sxs-lookup"><span data-stu-id="d3577-151">The shortened name is also consistent with naming of shells on non-Windows platforms.</span></span>

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193"></a><span data-ttu-id="d3577-152">Non inserire interruzioni di riga nell'output (ad eccezione delle tabelle) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)</span><span class="sxs-lookup"><span data-stu-id="d3577-152">Don't insert line breaks to output (except for tables) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)</span></span>

<span data-ttu-id="d3577-153">In precedenza, l'output veniva allineato alla larghezza della console e venivano aggiunte interruzioni di riga alla fine in base alla larghezza della console. L'output non veniva però riformattato come previsto in caso di ridimensionamento del terminale.</span><span class="sxs-lookup"><span data-stu-id="d3577-153">Previously, output was aligned to the width of the console and line breaks were added at the end width of the console, meaning the output didn't get reformatted as expected if the terminal was resized.</span></span> <span data-ttu-id="d3577-154">Questa modifica non è stata applicata alle tabelle, perché le interruzioni di riga sono necessarie per mantenere allineate le colonne.</span><span class="sxs-lookup"><span data-stu-id="d3577-154">This change was not applied to tables, as the line breaks are necessary to keep the columns aligned.</span></span>

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432"></a><span data-ttu-id="d3577-155">Ignorare il controllo degli elementi Null per le raccolte con elementi di tipo valore [#5432](https://github.com/PowerShell/PowerShell/issues/5432)</span><span class="sxs-lookup"><span data-stu-id="d3577-155">Skip null-element check for collections with a value-type element type [#5432](https://github.com/PowerShell/PowerShell/issues/5432)</span></span>

<span data-ttu-id="d3577-156">Per il parametro `Mandatory` e gli attributi `ValidateNotNull` e `ValidateNotNullOrEmpty`, ignorare il controllo degli elementi Null se il tipo di elemento della raccolta è un tipo valore.</span><span class="sxs-lookup"><span data-stu-id="d3577-156">For the `Mandatory` parameter and `ValidateNotNull` and `ValidateNotNullOrEmpty` attributes, skip the null-element check if the collection's element type is value type.</span></span>

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369"></a><span data-ttu-id="d3577-157">Modificare `$OutputEncoding` per usare la codifica `UTF-8 NoBOM` invece di ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)</span><span class="sxs-lookup"><span data-stu-id="d3577-157">Change `$OutputEncoding` to use `UTF-8 NoBOM` encoding rather than ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)</span></span>

<span data-ttu-id="d3577-158">La codifica precedente, ASCII (7 bit), comporterebbe la modifica non corretta dell'output in alcuni casi.</span><span class="sxs-lookup"><span data-stu-id="d3577-158">The previous encoding, ASCII (7-bit), would result in incorrect alteration of the output in some cases.</span></span> <span data-ttu-id="d3577-159">Questa modifica è finalizzata a rendere `UTF-8 NoBOM` la codifica predefinita, in modo da mantenere l'output in formato Unicode con una codifica supportata dalla maggior parte degli strumenti e dei sistemi operativi.</span><span class="sxs-lookup"><span data-stu-id="d3577-159">This change is to make `UTF-8 NoBOM` default, which preserves Unicode output with an encoding supported by most tools and operating systems.</span></span>

### <a name="remove-allscope-from-most-default-aliases-5268"></a><span data-ttu-id="d3577-160">Rimuovere `AllScope` dalla maggior parte degli alias predefiniti [#5268](https://github.com/PowerShell/PowerShell/issues/5268)</span><span class="sxs-lookup"><span data-stu-id="d3577-160">Remove `AllScope` from most default aliases [#5268](https://github.com/PowerShell/PowerShell/issues/5268)</span></span>

<span data-ttu-id="d3577-161">Per velocizzare la creazione dell'ambito, `AllScope` è stato rimosso dalla maggior parte degli alias predefiniti.</span><span class="sxs-lookup"><span data-stu-id="d3577-161">To speed up scope creation, `AllScope` was removed from most default aliases.</span></span> <span data-ttu-id="d3577-162">`AllScope` è stato lasciato per alcuni alias usati di frequente in cui la ricerca era più veloce.</span><span class="sxs-lookup"><span data-stu-id="d3577-162">`AllScope` was left for a few frequently used aliases where the lookup was faster.</span></span>

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113"></a><span data-ttu-id="d3577-163">`-Verbose` e `-Debug` non eseguono più l'override di `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)</span><span class="sxs-lookup"><span data-stu-id="d3577-163">`-Verbose` and `-Debug` no longer overrides `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)</span></span>

<span data-ttu-id="d3577-164">In precedenza, specificando `-Verbose` o `-Debug` veniva eseguito l'override del comportamento di `$ErrorActionPreference`.</span><span class="sxs-lookup"><span data-stu-id="d3577-164">Previously, if `-Verbose` or `-Debug` were specified, it overrode the behavior of `$ErrorActionPreference`.</span></span> <span data-ttu-id="d3577-165">Con questa modifica, `-Verbose` e `-Debug` non influiscono più sul comportamento di `$ErrorActionPreference`.</span><span class="sxs-lookup"><span data-stu-id="d3577-165">With this change, `-Verbose` and `-Debug` no longer affect the behavior of `$ErrorActionPreference`.</span></span>

## <a name="cmdlet-changes"></a><span data-ttu-id="d3577-166">Modifiche dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="d3577-166">Cmdlet changes</span></span>

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320"></a><span data-ttu-id="d3577-167">Invoke-RestMethod non restituisce informazioni utili quando non vengono restituiti dati.</span><span class="sxs-lookup"><span data-stu-id="d3577-167">Invoke-RestMethod doesn't return useful info when no data is returned.</span></span> [<span data-ttu-id="d3577-168">#5320</span><span class="sxs-lookup"><span data-stu-id="d3577-168">#5320</span></span>](https://github.com/PowerShell/PowerShell/issues/5320)

<span data-ttu-id="d3577-169">Quando un'API restituisce solo `null`, Invoke-RestMethod serializza questo valore come stringa `"null"` anziché come `$null`.</span><span class="sxs-lookup"><span data-stu-id="d3577-169">When an API returns just `null`, Invoke-RestMethod was serializing this as the string `"null"` instead of `$null`.</span></span> <span data-ttu-id="d3577-170">Questa modifica consente di correggere la logica in `Invoke-RestMethod` per serializzare correttamente un singolo valore letterale valido JSON `null` come `$null`.</span><span class="sxs-lookup"><span data-stu-id="d3577-170">This change fixes the logic in `Invoke-RestMethod` to properly serialize a valid single value JSON `null` literal as `$null`.</span></span>

### <a name="remove--protocol-from--computer-cmdlets-5277"></a><span data-ttu-id="d3577-171">Rimozione di `-Protocol` dai cmdlet `*-Computer`[#5277](https://github.com/PowerShell/PowerShell/issues/5277)</span><span class="sxs-lookup"><span data-stu-id="d3577-171">Remove `-Protocol` from `*-Computer` cmdlets [#5277](https://github.com/PowerShell/PowerShell/issues/5277)</span></span>

<span data-ttu-id="d3577-172">A causa di problemi con la comunicazione remota RPC in CoreFX (in particolare nelle piattaforme non Windows) e per garantire un'esperienza coerente di comunicazione remota in PowerShell, il parametro `-Protocol` è stato rimosso dai cmdlet `\*-Computer`.</span><span class="sxs-lookup"><span data-stu-id="d3577-172">Due to issues with RPC remoting in CoreFX (particularly on non-Windows platforms) and ensuring a consistent remoting experience in PowerShell, the `-Protocol` parameter was removed from the `\*-Computer` cmdlets.</span></span> <span data-ttu-id="d3577-173">DCOM non è più supportato per la comunicazione remota.</span><span class="sxs-lookup"><span data-stu-id="d3577-173">DCOM is no longer supported for remoting.</span></span> <span data-ttu-id="d3577-174">I cmdlet seguenti supportano solo la comunicazione remota WS-Management:</span><span class="sxs-lookup"><span data-stu-id="d3577-174">The following cmdlets only support WSMAN remoting:</span></span>

- <span data-ttu-id="d3577-175">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="d3577-175">Rename-Computer</span></span>
- <span data-ttu-id="d3577-176">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="d3577-176">Restart-Computer</span></span>
- <span data-ttu-id="d3577-177">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="d3577-177">Stop-Computer</span></span>

### <a name="remove--computername-from--service-cmdlets-5090"></a><span data-ttu-id="d3577-178">Rimuovere `-ComputerName` dai cmdlet `*-Service`[#5090](https://github.com/PowerShell/PowerShell/issues/5094)</span><span class="sxs-lookup"><span data-stu-id="d3577-178">Remove `-ComputerName` from `*-Service` cmdlets [#5090](https://github.com/PowerShell/PowerShell/issues/5094)</span></span>

<span data-ttu-id="d3577-179">Per favorire l'uso coerente di PSRP, il parametro `-ComputerName` è stato rimosso dai cmdlet `*-Service`.</span><span class="sxs-lookup"><span data-stu-id="d3577-179">In order to encourage the consistent use of PSRP, the `-ComputerName` parameter was removed from `*-Service` cmdlets.</span></span>

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197"></a><span data-ttu-id="d3577-180">Correggere `Get-Item -LiteralPath a*b` se `a*b` non esiste per restituire un errore [#5197](https://github.com/PowerShell/PowerShell/issues/5197)</span><span class="sxs-lookup"><span data-stu-id="d3577-180">Fix `Get-Item -LiteralPath a*b` if `a*b` doesn't actually exist to return error [#5197](https://github.com/PowerShell/PowerShell/issues/5197)</span></span>

<span data-ttu-id="d3577-181">In precedenza, `-LiteralPath` con un carattere jolly specificato veniva considerato uguale a `-Path` e se il carattere jolly non trovava alcun file, il cmdlet veniva chiuso senza messaggi.</span><span class="sxs-lookup"><span data-stu-id="d3577-181">Previously, `-LiteralPath` given a wildcard would treat it the same as `-Path` and if the wildcard found no files, it would silently exit.</span></span> <span data-ttu-id="d3577-182">Il comportamento corretto prevede che `-LiteralPath` sia un valore letterale in modo che generi un errore se il file non esiste.</span><span class="sxs-lookup"><span data-stu-id="d3577-182">Correct behavior should be that `-LiteralPath` is literal so if the file doesn't exist, it should error.</span></span> <span data-ttu-id="d3577-183">La modifica consiste nel considerare i caratteri jolly usati con `-Literal` come valore letterale.</span><span class="sxs-lookup"><span data-stu-id="d3577-183">Change is to treat wildcards used with `-Literal` as literal.</span></span>

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134"></a><span data-ttu-id="d3577-184">`Import-Csv` deve applicare `PSTypeNames` al momento dell'importazione quando nel CSV sono presenti informazioni sui tipi [#5134](https://github.com/PowerShell/PowerShell/issues/5134)</span><span class="sxs-lookup"><span data-stu-id="d3577-184">`Import-Csv` should apply `PSTypeNames` upon import when type information is present in the CSV [#5134](https://github.com/PowerShell/PowerShell/issues/5134)</span></span>

<span data-ttu-id="d3577-185">In precedenza, gli oggetti esportati usando `Export-CSV` con `TypeInformation` e importati con `ConvertFrom-Csv` non mantenevano le informazioni sui tipi.</span><span class="sxs-lookup"><span data-stu-id="d3577-185">Previously, objects exported using `Export-CSV` with `TypeInformation` imported with `ConvertFrom-Csv` were not retaining the type information.</span></span> <span data-ttu-id="d3577-186">Questa modifica aggiunge le informazioni sui tipi al membro `PSTypeNames` se disponibili dal file CSV.</span><span class="sxs-lookup"><span data-stu-id="d3577-186">This change adds the type information to `PSTypeNames` member if available from the CSV file.</span></span>

### <a name="-notypeinformation-should-be-default-on-export-csv-5131"></a><span data-ttu-id="d3577-187">`-NoTypeInformation` deve essere l'impostazione predefinita per `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)</span><span class="sxs-lookup"><span data-stu-id="d3577-187">`-NoTypeInformation` should be default on `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)</span></span>

<span data-ttu-id="d3577-188">Questa modifica è stata apportata in risposta ai commenti e suggerimenti dei clienti in merito al comportamento predefinito di `Export-CSV` per includere le informazioni sui tipi.</span><span class="sxs-lookup"><span data-stu-id="d3577-188">This change was made to address customer feedback on the default behavior of `Export-CSV` to include type information.</span></span>

<span data-ttu-id="d3577-189">In precedenza, il cmdlet restituiva un commento come prima riga, contenente il nome del tipo dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="d3577-189">Previously, the cmdlet would output a comment as the first line containing the type name of the object.</span></span> <span data-ttu-id="d3577-190">La modifica prevede l'esclusione di questo comportamento per impostazione predefinita, perché non è riconosciuto dalla maggior parte degli strumenti.</span><span class="sxs-lookup"><span data-stu-id="d3577-190">The change is to suppress this by default as it's not understood by most tools.</span></span> <span data-ttu-id="d3577-191">Usare `-IncludeTypeInformation` per mantenere il comportamento precedente.</span><span class="sxs-lookup"><span data-stu-id="d3577-191">Use `-IncludeTypeInformation` to retain the previous behavior.</span></span>

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112"></a><span data-ttu-id="d3577-192">I cmdlet Web devono generare un avviso in caso di invio di `-Credential` su connessioni non crittografate [#5112](https://github.com/PowerShell/PowerShell/issues/5112)</span><span class="sxs-lookup"><span data-stu-id="d3577-192">Web Cmdlets should warn when `-Credential` is sent over unencrypted connections [#5112](https://github.com/PowerShell/PowerShell/issues/5112)</span></span>

<span data-ttu-id="d3577-193">Quando si usa HTTP, il contenuto che include password viene inviato come testo non crittografato.</span><span class="sxs-lookup"><span data-stu-id="d3577-193">When using HTTP, content including passwords are sent as clear-text.</span></span> <span data-ttu-id="d3577-194">La modifica consiste nel non consentire questo comportamento per impostazione predefinita, con restituzione di un errore se le credenziali vengono passate in modo non sicuro.</span><span class="sxs-lookup"><span data-stu-id="d3577-194">This change is to not allow this by default and return an error if credentials are being passed in an insecure manner.</span></span> <span data-ttu-id="d3577-195">Gli utenti possono ignorare questa nuova impostazione usando l'opzione `-AllowUnencryptedAuthentication`.</span><span class="sxs-lookup"><span data-stu-id="d3577-195">Users can bypass this by using the `-AllowUnencryptedAuthentication` switch.</span></span>

## <a name="api-changes"></a><span data-ttu-id="d3577-196">Modifiche all'API</span><span class="sxs-lookup"><span data-stu-id="d3577-196">API changes</span></span>

### <a name="remove-addtypecommandbase-class-5407"></a><span data-ttu-id="d3577-197">Rimuovere la classe `AddTypeCommandBase`[#5407](https://github.com/PowerShell/PowerShell/issues/5407)</span><span class="sxs-lookup"><span data-stu-id="d3577-197">Remove `AddTypeCommandBase` class [#5407](https://github.com/PowerShell/PowerShell/issues/5407)</span></span>

<span data-ttu-id="d3577-198">La classe `AddTypeCommandBase` è stata rimossa da `Add-Type` per migliorare le prestazioni.</span><span class="sxs-lookup"><span data-stu-id="d3577-198">The `AddTypeCommandBase` class was removed from `Add-Type` to improve performance.</span></span> <span data-ttu-id="d3577-199">Questa classe viene usata solo dal cmdlet Add-Type e non dovrebbe avere effetti sugli utenti.</span><span class="sxs-lookup"><span data-stu-id="d3577-199">This class is only used by the Add-Type cmdlet and should not impact users.</span></span>

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080"></a><span data-ttu-id="d3577-200">Unificare i cmdlet con il parametro `-Encoding` in modo che siano di tipo `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)</span><span class="sxs-lookup"><span data-stu-id="d3577-200">Unify cmdlets with parameter `-Encoding` to be of type `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)</span></span>

<span data-ttu-id="d3577-201">Il valore `-Encoding``Byte` è stato rimosso dai cmdlet per il provider filesystem.</span><span class="sxs-lookup"><span data-stu-id="d3577-201">The `-Encoding` value `Byte` has been removed from the filesystem provider cmdlets.</span></span> <span data-ttu-id="d3577-202">Viene ora usato un nuovo parametro, `-AsByteStream`, per specificare che un flusso di byte è richiesto come input o che l'output è un flusso di byte.</span><span class="sxs-lookup"><span data-stu-id="d3577-202">A new parameter, `-AsByteStream`, is now used to specify that a byte stream is required as input or that the output is a stream of bytes.</span></span>

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055"></a><span data-ttu-id="d3577-203">Aggiunta di un messaggio di errore migliore per il parametro `-UFormat` vuoto o Null [#5055](https://github.com/PowerShell/PowerShell/issues/5055)</span><span class="sxs-lookup"><span data-stu-id="d3577-203">Add better error message for empty and null `-UFormat` parameter [#5055](https://github.com/PowerShell/PowerShell/issues/5055)</span></span>

<span data-ttu-id="d3577-204">In precedenza, al passaggio di una stringa di formato vuota a `-UFormat` veniva visualizzato un messaggio di errore poco utile.</span><span class="sxs-lookup"><span data-stu-id="d3577-204">Previously, when passing an empty format string to `-UFormat`, an unhelpful error message would appear.</span></span> <span data-ttu-id="d3577-205">È stato aggiunto un errore più descrittivo.</span><span class="sxs-lookup"><span data-stu-id="d3577-205">A more descriptive error has been added.</span></span>

### <a name="clean-up-console-code-4995"></a><span data-ttu-id="d3577-206">Pulizia del codice della console [#4995](https://github.com/PowerShell/PowerShell/issues/4995)</span><span class="sxs-lookup"><span data-stu-id="d3577-206">Clean up console code [#4995](https://github.com/PowerShell/PowerShell/issues/4995)</span></span>

<span data-ttu-id="d3577-207">Le funzionalità seguenti sono state rimosse e non sono supportate in PowerShell Core e non è prevista l'aggiunta del supporto perché esistono per motivi legacy per Windows PowerShell: opzione `-psconsolefile` e codice, opzione `-importsystemmodules` e codice e codice per la modifica del tipo di carattere.</span><span class="sxs-lookup"><span data-stu-id="d3577-207">The following features were removed as they are not supported in PowerShell Core, and there are no plans to add support as they exist for legacy reasons for Windows PowerShell: `-psconsolefile` switch and code, `-importsystemmodules` switch and code, and font changing code.</span></span>

### <a name="removed-runspaceconfiguration-support-4942"></a><span data-ttu-id="d3577-208">Rimuovere il supporto di `RunspaceConfiguration`[#4942](https://github.com/PowerShell/PowerShell/issues/4942)</span><span class="sxs-lookup"><span data-stu-id="d3577-208">Removed `RunspaceConfiguration` support [#4942](https://github.com/PowerShell/PowerShell/issues/4942)</span></span>

<span data-ttu-id="d3577-209">In precedenza, per la creazione di uno spazio di esecuzione di PowerShell a livello di codice con l'API era possibile usare la classe legacy [`RunspaceConfiguration`][runspaceconfig] o la più recente [`InitialSessionState`][iss].</span><span class="sxs-lookup"><span data-stu-id="d3577-209">Previously, when creating a PowerShell runspace programmatically using the API you could use the legacy [`RunspaceConfiguration`][runspaceconfig] or the newer [`InitialSessionState`][iss].</span></span> <span data-ttu-id="d3577-210">Con questa modifica viene rimosso il supporto per `RunspaceConfiguration` ed è ora supportata solo la classe `InitialSessionState`.</span><span class="sxs-lookup"><span data-stu-id="d3577-210">This change removed support for `RunspaceConfiguration` and only supports `InitialSessionState`.</span></span>

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923"></a><span data-ttu-id="d3577-211">`CommandInvocationIntrinsics.InvokeScript` associa gli argomenti a `$input` invece che a `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)</span><span class="sxs-lookup"><span data-stu-id="d3577-211">`CommandInvocationIntrinsics.InvokeScript` bind arguments to `$input` instead of `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)</span></span>

<span data-ttu-id="d3577-212">A causa della posizione non corretta di un parametro, gli argomenti vengono passati come input invece che come argomenti.</span><span class="sxs-lookup"><span data-stu-id="d3577-212">An incorrect position of a parameter resulted in the args passed as input instead of as args.</span></span>

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903"></a><span data-ttu-id="d3577-213">Rimuovere l'opzione `-showwindow` non supportata da `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)</span><span class="sxs-lookup"><span data-stu-id="d3577-213">Remove unsupported `-showwindow` switch from `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)</span></span>

<span data-ttu-id="d3577-214">`-showwindow` si basa su WPF, che non è supportato in CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d3577-214">`-showwindow` relies on WPF, which is not supported on CoreCLR.</span></span>

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866"></a><span data-ttu-id="d3577-215">Consentire l'uso di \* nel percorso del Registro di sistema per `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)</span><span class="sxs-lookup"><span data-stu-id="d3577-215">Allow \* to be used in registry path for `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)</span></span>

<span data-ttu-id="d3577-216">In precedenza, `-LiteralPath` con un carattere jolly specificato veniva considerato uguale a `-Path` e se il carattere jolly non trovava alcun file, il cmdlet veniva chiuso senza messaggi.</span><span class="sxs-lookup"><span data-stu-id="d3577-216">Previously, `-LiteralPath` given a wildcard would treat it the same as `-Path` and if the wildcard found no files, it would silently exit.</span></span> <span data-ttu-id="d3577-217">Il comportamento corretto prevede che `-LiteralPath` sia un valore letterale in modo che generi un errore se il file non esiste.</span><span class="sxs-lookup"><span data-stu-id="d3577-217">Correct behavior should be that `-LiteralPath` is literal so if the file doesn't exist, it should error.</span></span> <span data-ttu-id="d3577-218">La modifica consiste nel considerare i caratteri jolly usati con `-Literal` come valore letterale.</span><span class="sxs-lookup"><span data-stu-id="d3577-218">Change is to treat wildcards used with `-Literal` as literal.</span></span>

### <a name="fix-set-service-failing-test-4802"></a><span data-ttu-id="d3577-219">Correzione per l'esito negativo del test per `Set-Service`[#4802](https://github.com/PowerShell/PowerShell/issues/4802)</span><span class="sxs-lookup"><span data-stu-id="d3577-219">Fix `Set-Service` failing test [#4802](https://github.com/PowerShell/PowerShell/issues/4802)</span></span>

<span data-ttu-id="d3577-220">In precedenza, usando `New-Service -StartupType foo``foo` veniva ignorato e il servizio veniva creato con un tipo di avvio predefinito.</span><span class="sxs-lookup"><span data-stu-id="d3577-220">Previously, if `New-Service -StartupType foo` was used, `foo` was ignored and the service was created with some default startup type.</span></span> <span data-ttu-id="d3577-221">La modifica consiste nel generare in modo esplicito un errore per un tipo di avvio non valido.</span><span class="sxs-lookup"><span data-stu-id="d3577-221">This change is to explicitly throw an error for an invalid startup type.</span></span>

### <a name="rename-isosx-to-ismacos-4700"></a><span data-ttu-id="d3577-222">Rinominare `$IsOSX` in `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)</span><span class="sxs-lookup"><span data-stu-id="d3577-222">Rename `$IsOSX` to `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)</span></span>

<span data-ttu-id="d3577-223">La denominazione in PowerShell dovrebbe essere coerente con la denominazione Microsoft e conforme all'uso da parte di Apple di macOS invece di OSX.</span><span class="sxs-lookup"><span data-stu-id="d3577-223">The naming in PowerShell should be consistent with our naming and conform to Apple's use of macOS instead of OSX.</span></span> <span data-ttu-id="d3577-224">Ai fini della leggibilità e della coerenza, tuttavia, viene mantenuta la combinazione di maiuscole/minuscole Pascal.</span><span class="sxs-lookup"><span data-stu-id="d3577-224">However, for readability and consistently we are staying with Pascal casing.</span></span>

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573"></a><span data-ttu-id="d3577-225">Rendere coerente il messaggio di errore quando viene passato uno script non valido a - File, miglioramento dell'errore per il passaggio di un argomento ambiguo [#4573](https://github.com/PowerShell/PowerShell/issues/4573)</span><span class="sxs-lookup"><span data-stu-id="d3577-225">Make error message consistent when invalid script is passed to -File, better error when passed ambiguous argument [#4573](https://github.com/PowerShell/PowerShell/issues/4573)</span></span>

<span data-ttu-id="d3577-226">Modificare i codici di uscita di `pwsh.exe` per allinearsi alle convenzioni di Unix</span><span class="sxs-lookup"><span data-stu-id="d3577-226">Change the exit codes of `pwsh.exe` to align with Unix conventions</span></span>

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302-4303"></a><span data-ttu-id="d3577-227">Rimozione di `LocalAccount` e dei cmdlet dai moduli `Diagnostics`.</span><span class="sxs-lookup"><span data-stu-id="d3577-227">Removal of `LocalAccount` and cmdlets from  `Diagnostics` modules.</span></span> <span data-ttu-id="d3577-228">[#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)</span><span class="sxs-lookup"><span data-stu-id="d3577-228">[#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)</span></span>

<span data-ttu-id="d3577-229">A causa di API non supportate, il modulo `LocalAccounts` e i cmdlet `Counter` nel modulo `Diagnostics` sono stati rimossi fino a quando non viene trovata una soluzione migliore.</span><span class="sxs-lookup"><span data-stu-id="d3577-229">Due to unsupported APIs, the `LocalAccounts` module and the `Counter` cmdlets in the `Diagnostics` module were removed until a better solution is found.</span></span>

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036"></a><span data-ttu-id="d3577-230">L'esecuzione dello script di PowerShell con il parametro bool non funziona [#4036](https://github.com/PowerShell/PowerShell/issues/4036)</span><span class="sxs-lookup"><span data-stu-id="d3577-230">Executing PowerShell script with bool parameter does not work [#4036](https://github.com/PowerShell/PowerShell/issues/4036)</span></span>

<span data-ttu-id="d3577-231">In precedenza, l'uso di **powershell.exe** (ora **pwsh.exe**) per eseguire uno script di PowerShell tramite `-File` non consentiva in alcun modo di passare `$true`/`$false` come valori di parametro.</span><span class="sxs-lookup"><span data-stu-id="d3577-231">Previously, using **powershell.exe** (now **pwsh.exe**) to execute a PowerShell script using `-File` provided no way to pass `$true`/`$false` as parameter values.</span></span> <span data-ttu-id="d3577-232">È stato aggiunto il supporto di `$true`/`$false` come valori analizzati ai parametri.</span><span class="sxs-lookup"><span data-stu-id="d3577-232">Support for `$true`/`$false` as parsed values to parameters was added.</span></span> <span data-ttu-id="d3577-233">Sono supportati anche valori di parametro perché la sintassi attualmente documentata non funziona.</span><span class="sxs-lookup"><span data-stu-id="d3577-233">Switch values are also supported as currently documented syntax doesn't work.</span></span>

### <a name="remove-clrversion-property-from-psversiontable-4027"></a><span data-ttu-id="d3577-234">Rimuovere la proprietà `ClrVersion` da `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)</span><span class="sxs-lookup"><span data-stu-id="d3577-234">Remove `ClrVersion` property from `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)</span></span>

<span data-ttu-id="d3577-235">La proprietà `ClrVersion` di `$PSVersionTable` non è utile con CoreCLR. Gli utenti finali non devono usare tale valore per determinare la compatibilità.</span><span class="sxs-lookup"><span data-stu-id="d3577-235">The `ClrVersion` property of `$PSVersionTable` is not useful with CoreCLR, end users should not be using that value to determine compatibility.</span></span>

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019"></a><span data-ttu-id="d3577-236">Modificare il parametro posizionale per `powershell.exe` da `-Command` a `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)</span><span class="sxs-lookup"><span data-stu-id="d3577-236">Change positional parameter for `powershell.exe` from `-Command` to `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)</span></span>

<span data-ttu-id="d3577-237">Abilitare l'uso di shebang di PowerShell su piattaforme non Windows.</span><span class="sxs-lookup"><span data-stu-id="d3577-237">Enable shebang use of PowerShell on non-Windows platforms.</span></span> <span data-ttu-id="d3577-238">Nei sistemi basati su Unix questo significa che è possibile rendere uno script eseguibile per richiamare automaticamente PowerShell invece di richiamare in modo esplicito `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="d3577-238">This means on Unix based systems, you can make a script executable that would invoke PowerShell automatically rather than explicitly invoking `pwsh`.</span></span> <span data-ttu-id="d3577-239">Significa anche che è ora possibile eseguire operazioni come `powershell foo.ps1` o `powershell fooScript` senza specificare `-File`.</span><span class="sxs-lookup"><span data-stu-id="d3577-239">This also means that you can now do things like `powershell foo.ps1` or `powershell fooScript` without specifying `-File`.</span></span> <span data-ttu-id="d3577-240">Tuttavia, questa modifica richiede ora di specificare in modo esplicito `-c` o `-Command` quando si tenta di eseguire operazioni come `powershell.exe Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="d3577-240">However, this change now requires that you explicitly specify `-c` or `-Command` when trying to do things like `powershell.exe Get-Command`.</span></span>

### <a name="implement-unicode-escape-parsing-3958"></a><span data-ttu-id="d3577-241">Implementare l'analisi per escape Unicode [#3958](https://github.com/PowerShell/PowerShell/issues/3958)</span><span class="sxs-lookup"><span data-stu-id="d3577-241">Implement Unicode escape parsing [#3958](https://github.com/PowerShell/PowerShell/issues/3958)</span></span>

<span data-ttu-id="d3577-242">`` `u####`` o `` `u{####}`` viene convertito nel carattere Unicode corrispondente.</span><span class="sxs-lookup"><span data-stu-id="d3577-242">`` `u####`` or `` `u{####}`` is converted to the corresponding Unicode character.</span></span> <span data-ttu-id="d3577-243">Per restituire un valore letterale `` `u``, usare il carattere di escape per l'apice inverso: ``` ``u```.</span><span class="sxs-lookup"><span data-stu-id="d3577-243">To output a literal `` `u``, escape the backtick: ``` ``u```.</span></span>

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940"></a><span data-ttu-id="d3577-244">Modificare la codifica `New-ModuleManifest` in `UTF8NoBOM` nelle piattaforme non Windows [#3940](https://github.com/PowerShell/PowerShell/issues/3940)</span><span class="sxs-lookup"><span data-stu-id="d3577-244">Change `New-ModuleManifest` encoding to `UTF8NoBOM` on non-Windows platforms [#3940](https://github.com/PowerShell/PowerShell/issues/3940)</span></span>

<span data-ttu-id="d3577-245">In precedenza, `New-ModuleManifest` creava manifesti psd1 in UTF-16 con BOM, con conseguenti problemi per gli strumenti Linux.</span><span class="sxs-lookup"><span data-stu-id="d3577-245">Previously, `New-ModuleManifest` creates psd1 manifests in UTF-16 with BOM, creating a problem for Linux tools.</span></span> <span data-ttu-id="d3577-246">Questa modifica importante cambia la codifica di `New-ModuleManifest` in UTF (senza BOM) nelle piattaforme non Windows.</span><span class="sxs-lookup"><span data-stu-id="d3577-246">This breaking change changes the encoding of `New-ModuleManifest` to be UTF (no BOM) in non-Windows platforms.</span></span>

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780"></a><span data-ttu-id="d3577-247">Evitare la ricorsione di `Get-ChildItem` in collegamenti simbolici (#1875).</span><span class="sxs-lookup"><span data-stu-id="d3577-247">Prevent `Get-ChildItem` from recursing into symlinks (#1875).</span></span> [<span data-ttu-id="d3577-248">#3780</span><span class="sxs-lookup"><span data-stu-id="d3577-248">#3780</span></span>](https://github.com/PowerShell/PowerShell/issues/3780)

<span data-ttu-id="d3577-249">Questa modifica allinea `Get-ChildItem` maggiormente ai comandi nativi Unix `ls -r` e Windows `dir /s`.</span><span class="sxs-lookup"><span data-stu-id="d3577-249">This change brings `Get-ChildItem` more in line with the Unix `ls -r` and the Windows `dir /s` native commands.</span></span> <span data-ttu-id="d3577-250">Come i comandi indicati, il cmdlet consente di visualizzare i collegamenti simbolici alle directory individuate durante la ricorsione, ma non esegue la ricorsione.</span><span class="sxs-lookup"><span data-stu-id="d3577-250">Like the mentioned commands, the cmdlet displays symbolic links to directories found during recursion, but does not recurse into them.</span></span>

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706"></a><span data-ttu-id="d3577-251">Correggere `Get-Content -Delimiter` per non includere il delimitatore nelle righe restituite [#3706](https://github.com/PowerShell/PowerShell/issues/3706)</span><span class="sxs-lookup"><span data-stu-id="d3577-251">Fix `Get-Content -Delimiter` to not include the delimiter in the returned lines [#3706](https://github.com/PowerShell/PowerShell/issues/3706)</span></span>

<span data-ttu-id="d3577-252">In precedenza, l'output durante l'uso di `Get-Content -Delimiter` era incoerente e poco pratico, perché richiedeva ulteriori elaborazioni dei dati per rimuovere il delimitatore.</span><span class="sxs-lookup"><span data-stu-id="d3577-252">Previously, the output while using `Get-Content -Delimiter` was inconsistent and inconvenient as it required further processing of the data to remove the delimiter.</span></span> <span data-ttu-id="d3577-253">Questa modifica rimuove il delimitatore nelle righe restituite.</span><span class="sxs-lookup"><span data-stu-id="d3577-253">This change removes the delimiter in returned lines.</span></span>

### <a name="implement-format-hex-in-c-3320"></a><span data-ttu-id="d3577-254">Implementare Format-Hex in C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)</span><span class="sxs-lookup"><span data-stu-id="d3577-254">Implement Format-Hex in C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)</span></span>

<span data-ttu-id="d3577-255">Il parametro `-Raw` è ora "no-op" (in quanto non esegue alcuna operazione).</span><span class="sxs-lookup"><span data-stu-id="d3577-255">The `-Raw` parameter is now a "no-op" (in that it does nothing).</span></span> <span data-ttu-id="d3577-256">In futuro, tutto l'output verrà visualizzato con una rappresentazione reale di numeri che includono tutti i byte per il tipo (quello che il parametro `-Raw` faceva formalmente prima di questa modifica).</span><span class="sxs-lookup"><span data-stu-id="d3577-256">Going forward all of the output will be displayed with a true representation of numbers that includes all of the bytes for its type (what the `-Raw` parameter was formally doing prior to this change).</span></span>

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319"></a><span data-ttu-id="d3577-257">PowerShell come shell predefinita non funziona con il comando script [#3319](https://github.com/PowerShell/PowerShell/issues/3319)</span><span class="sxs-lookup"><span data-stu-id="d3577-257">PowerShell as a default shell doesn't work with script command [#3319](https://github.com/PowerShell/PowerShell/issues/3319)</span></span>

<span data-ttu-id="d3577-258">In Unix, l'accettazione di `-i` per una shell interattiva è una convenzione per le shell e molti strumenti si aspettano questo comportamento (`script` ad esempio e quando si imposta PowerShell come la shell predefinita) e chiamano la shell con l'opzione `-i`.</span><span class="sxs-lookup"><span data-stu-id="d3577-258">On Unix, it is a convention for shells to accept `-i` for an interactive shell and many tools expect this behavior (`script` for example, and when setting PowerShell as the default shell) and calls the shell with the `-i` switch.</span></span> <span data-ttu-id="d3577-259">Questa modifica è significativa, perché `-i` si poteva usare in precedenza come forma breve di `-inputformat`, mentre è ora necessario specificare `-in`.</span><span class="sxs-lookup"><span data-stu-id="d3577-259">This change is breaking in that `-i` previously could be used as short hand to match `-inputformat`, which now needs to be `-in`.</span></span>

### <a name="typo-fix-in-get-computerinfo-property-name-3167"></a><span data-ttu-id="d3577-260">Correggere un errore di digitazione nel nome della proprietà Get-ComputerInfo [#3167](https://github.com/PowerShell/PowerShell/issues/3167)</span><span class="sxs-lookup"><span data-stu-id="d3577-260">Typo fix in Get-ComputerInfo property name [#3167](https://github.com/PowerShell/PowerShell/issues/3167)</span></span>

<span data-ttu-id="d3577-261">`BiosSerialNumber` era digitata in modo errato come `BiosSeralNumber` ed è stata corretta.</span><span class="sxs-lookup"><span data-stu-id="d3577-261">`BiosSerialNumber` was misspelled as `BiosSeralNumber` and has been changed to the correct spelling.</span></span>

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024"></a><span data-ttu-id="d3577-262">Aggiunta dei cmdlet `Get-StringHash` e `Get-FileHash`[#3024](https://github.com/PowerShell/PowerShell/issues/3024)</span><span class="sxs-lookup"><span data-stu-id="d3577-262">Add `Get-StringHash` and `Get-FileHash` cmdlets [#3024](https://github.com/PowerShell/PowerShell/issues/3024)</span></span>

<span data-ttu-id="d3577-263">Questa modifica riguarda alcuni algoritmi di hash non supportati da CoreFX, che pertanto non sono più disponibili:</span><span class="sxs-lookup"><span data-stu-id="d3577-263">This change is that some hash algorithms are not supported by CoreFX, therefore they are no longer available:</span></span>

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672"></a><span data-ttu-id="d3577-264">Aggiungere la convalida per i cmdlet `Get-*` in cui il passaggio di $null restituisce tutti gli oggetti invece di un errore [#2672](https://github.com/PowerShell/PowerShell/issues/2672)</span><span class="sxs-lookup"><span data-stu-id="d3577-264">Add validation on `Get-*` cmdlets where passing $null returns all objects instead of error [#2672](https://github.com/PowerShell/PowerShell/issues/2672)</span></span>

<span data-ttu-id="d3577-265">Il passaggio di `$null` a uno qualsiasi dei cmdlet seguenti ora genera un errore:</span><span class="sxs-lookup"><span data-stu-id="d3577-265">Passing `$null` to any of the following now throws an error:</span></span>

- `Get-Credential -UserName`
- `Get-Event -SourceIdentifier`
- `Get-EventSubscriber -SourceIdentifier`
- `Get-Help -Name`
- `Get-PSBreakpoint -Script`
- `Get-PSProvider -PSProvider`
- `Get-PSSessionConfiguration -Name`
- `Get-PSSnapin -Name`
- `Get-Runspace -Name`
- `Get-RunspaceDebug -RunspaceName`
- `Get-Service -Name`
- `Get-TraceSource -Name`
- `Get-Variable -Name`
- `Get-WmiObject -Class`
- `Get-WmiObject -Property`

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482"></a><span data-ttu-id="d3577-266">Aggiungere il supporto del formato di file di log esteso W3C in `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)</span><span class="sxs-lookup"><span data-stu-id="d3577-266">Add support W3C Extended Log File Format in `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)</span></span>

<span data-ttu-id="d3577-267">In precedenza, il cmdlet `Import-Csv` non poteva essere usato per importare direttamente i file di log in formato W3C esteso ed era necessaria un'azione aggiuntiva.</span><span class="sxs-lookup"><span data-stu-id="d3577-267">Previously, the `Import-Csv` cmdlet cannot be used to directly import the log files in W3C extended log format and additional action would be required.</span></span> <span data-ttu-id="d3577-268">Con questa modifica, il formato di log esteso W3C è ora supportato.</span><span class="sxs-lookup"><span data-stu-id="d3577-268">With this change, W3C extended log format is supported.</span></span>

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035"></a><span data-ttu-id="d3577-269">Problema di associazione di parametro con `ValueFromRemainingArguments` nelle funzioni PS [#2035](https://github.com/PowerShell/PowerShell/issues/2035)</span><span class="sxs-lookup"><span data-stu-id="d3577-269">Parameter binding problem with `ValueFromRemainingArguments` in PS functions [#2035](https://github.com/PowerShell/PowerShell/issues/2035)</span></span>

<span data-ttu-id="d3577-270">`ValueFromRemainingArguments` restituisce ora i valori come matrice anziché come valore singolo che è a sua volta una matrice.</span><span class="sxs-lookup"><span data-stu-id="d3577-270">`ValueFromRemainingArguments` now returns the values as an array instead of a single value which itself is an array.</span></span>

### <a name="buildversion-is-removed-from-psversiontable-1415"></a><span data-ttu-id="d3577-271">`BuildVersion` viene rimosso da `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)</span><span class="sxs-lookup"><span data-stu-id="d3577-271">`BuildVersion` is removed from `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)</span></span>

<span data-ttu-id="d3577-272">Rimuovere la proprietà `BuildVersion` da `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="d3577-272">Remove the `BuildVersion` property from `$PSVersionTable`.</span></span> <span data-ttu-id="d3577-273">Questa proprietà era associata alla versione della build di Windows.</span><span class="sxs-lookup"><span data-stu-id="d3577-273">This property was tied to the Windows build version.</span></span> <span data-ttu-id="d3577-274">Si consiglia invece di usare `GitCommitId` per recuperare la versione build esatta di PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="d3577-274">Instead, we recommend that you use `GitCommitId` to retrieve the exact build version of PowerShell Core.</span></span>

### <a name="changes-to-web-cmdlets"></a><span data-ttu-id="d3577-275">Modifiche ai cmdlet Web</span><span class="sxs-lookup"><span data-stu-id="d3577-275">Changes to Web Cmdlets</span></span>

<span data-ttu-id="d3577-276">L'API .NET sottostante dei cmdlet Web è stato modificata in `System.Net.Http.HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="d3577-276">The underlying .NET API of the Web Cmdlets has been changed to `System.Net.Http.HttpClient`.</span></span> <span data-ttu-id="d3577-277">Questa modifica offre numerosi vantaggi.</span><span class="sxs-lookup"><span data-stu-id="d3577-277">This change provides many benefits.</span></span> <span data-ttu-id="d3577-278">Tuttavia, questa modifica insieme a una mancanza di interoperabilità con Internet Explorer ha dato luogo a diverse modifiche di rilievo all'interno di `Invoke-WebRequest` e `Invoke-RestMethod`.</span><span class="sxs-lookup"><span data-stu-id="d3577-278">However, this change along with a lack of interoperability with Internet Explorer have resulted in several breaking changes within `Invoke-WebRequest` and `Invoke-RestMethod`.</span></span>

- <span data-ttu-id="d3577-279">`Invoke-WebRequest` ora supporta solo l'analisi HTML di base.</span><span class="sxs-lookup"><span data-stu-id="d3577-279">`Invoke-WebRequest` now supports basic HTML Parsing only.</span></span> <span data-ttu-id="d3577-280">`Invoke-WebRequest` restituisce sempre un oggetto `BasicHtmlWebResponseObject`.</span><span class="sxs-lookup"><span data-stu-id="d3577-280">`Invoke-WebRequest` always returns a `BasicHtmlWebResponseObject` object.</span></span> <span data-ttu-id="d3577-281">Le proprietà `ParsedHtml` e `Forms` sono state rimosse.</span><span class="sxs-lookup"><span data-stu-id="d3577-281">The `ParsedHtml` and `Forms` properties have been removed.</span></span>
- <span data-ttu-id="d3577-282">I valori `BasicHtmlWebResponseObject.Headers` sono ora `String[]` invece di `String`.</span><span class="sxs-lookup"><span data-stu-id="d3577-282">`BasicHtmlWebResponseObject.Headers` values are now `String[]` instead of `String`.</span></span>
- <span data-ttu-id="d3577-283">`BasicHtmlWebResponseObject.BaseResponse` è ora un oggetto `System.Net.Http.HttpResponseMessage`.</span><span class="sxs-lookup"><span data-stu-id="d3577-283">`BasicHtmlWebResponseObject.BaseResponse` is now a `System.Net.Http.HttpResponseMessage` object.</span></span>
- <span data-ttu-id="d3577-284">La proprietà `Response` per le eccezioni di cmdlet Web è ora un oggetto `System.Net.Http.HttpResponseMessage`.</span><span class="sxs-lookup"><span data-stu-id="d3577-284">The `Response` property on Web Cmdlet exceptions is now a `System.Net.Http.HttpResponseMessage` object.</span></span>
- <span data-ttu-id="d3577-285">L'analisi delle intestazioni conforme a RFC è ora l'impostazione predefinita per il parametro `-Headers` e `-UserAgent`.</span><span class="sxs-lookup"><span data-stu-id="d3577-285">Strict RFC header parsing is now default for the `-Headers` and `-UserAgent` parameter.</span></span> <span data-ttu-id="d3577-286">Questa impostazione può essere ignorata con `-SkipHeaderValidation`.</span><span class="sxs-lookup"><span data-stu-id="d3577-286">This can be bypassed with `-SkipHeaderValidation`.</span></span>
- <span data-ttu-id="d3577-287">Gli schemi URI `file://` e `ftp://` non sono più supportati.</span><span class="sxs-lookup"><span data-stu-id="d3577-287">`file://` and `ftp://` URI schemes are no longer supported.</span></span>
- <span data-ttu-id="d3577-288">Le impostazioni di `System.Net.ServicePointManager` non vengono più rispettate.</span><span class="sxs-lookup"><span data-stu-id="d3577-288">`System.Net.ServicePointManager` settings are no longer honored.</span></span>
- <span data-ttu-id="d3577-289">Non è attualmente disponibile l'autenticazione basata su certificati in macOS.</span><span class="sxs-lookup"><span data-stu-id="d3577-289">There is currently no certificate based authentication available on macOS.</span></span>
- <span data-ttu-id="d3577-290">L'uso di `-Credential` su un URI `http://` genererà un errore.</span><span class="sxs-lookup"><span data-stu-id="d3577-290">Use of `-Credential` over an `http://` URI will result in an error.</span></span> <span data-ttu-id="d3577-291">Usare un URI `https://` oppure specificare il parametro `-AllowUnencryptedAuthentication` per eliminare l'errore.</span><span class="sxs-lookup"><span data-stu-id="d3577-291">Use an `https://` URI or supply the `-AllowUnencryptedAuthentication` parameter to suppress the error.</span></span>
- <span data-ttu-id="d3577-292">`-MaximumRedirection` genera ora un errore fatale quando i tentativi di reindirizzamento superano il limite specificato anziché restituire i risultati dell'ultimo reindirizzamento.</span><span class="sxs-lookup"><span data-stu-id="d3577-292">`-MaximumRedirection` now produces a terminating error when redirection attempts exceed the provided limit instead of returning the results of the last redirection.</span></span>
- <span data-ttu-id="d3577-293">In PowerShell 6.2 è stata apportata una modifica all'impostazione predefinita della codifica UTF-8 per le risposte JSON.</span><span class="sxs-lookup"><span data-stu-id="d3577-293">In PowerShell 6.2, a change was made to default to UTF-8 encoding for JSON responses.</span></span> <span data-ttu-id="d3577-294">Quando non viene specificato un set di caratteri per una risposta JSON la codifica predefinita deve essere UTF-8, in base alla specifica RFC 8259.</span><span class="sxs-lookup"><span data-stu-id="d3577-294">When a charset is not supplied for a JSON response, the default encoding should be UTF-8 per RFC 8259.</span></span>
