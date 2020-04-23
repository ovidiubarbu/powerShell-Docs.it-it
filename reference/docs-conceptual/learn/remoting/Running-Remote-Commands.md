---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Esecuzione di comandi remoti
ms.openlocfilehash: d6609deafd8dec4f34a8412439d87dacd20d46f1
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030325"
---
# <a name="running-remote-commands"></a><span data-ttu-id="e8c88-103">Esecuzione di comandi remoti</span><span class="sxs-lookup"><span data-stu-id="e8c88-103">Running Remote Commands</span></span>

<span data-ttu-id="e8c88-104">È possibile eseguire comandi in uno o centinaia di computer con un unico comando di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8c88-104">You can run commands on one or hundreds of computers with a single PowerShell command.</span></span> <span data-ttu-id="e8c88-105">Windows PowerShell supporta l'elaborazione remota tramite varie tecnologie, tra cui WMI, RPC e WS-Management.</span><span class="sxs-lookup"><span data-stu-id="e8c88-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

<span data-ttu-id="e8c88-106">PowerShell Core supporta WMI, WS-Management e la comunicazione remota SSH.</span><span class="sxs-lookup"><span data-stu-id="e8c88-106">PowerShell Core supports WMI, WS-Management, and SSH remoting.</span></span> <span data-ttu-id="e8c88-107">RPC non è più supportato.</span><span class="sxs-lookup"><span data-stu-id="e8c88-107">RPC is no longer supported.</span></span>

<span data-ttu-id="e8c88-108">Per altre informazioni sulla comunicazione remota in PowerShell Core, vedere gli articoli seguenti:</span><span class="sxs-lookup"><span data-stu-id="e8c88-108">For more information about remoting in PowerShell Core, see the following articles:</span></span>

- <span data-ttu-id="e8c88-109">[Comunicazione remota di PowerShell su SSH][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="e8c88-109">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="e8c88-110">[Comunicazione remota di WS-Management in PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="e8c88-110">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="windows-powershell-remoting-without-configuration"></a><span data-ttu-id="e8c88-111">Comunicazione remota di Windows PowerShell senza configurazione</span><span class="sxs-lookup"><span data-stu-id="e8c88-111">Windows PowerShell Remoting Without Configuration</span></span>

<span data-ttu-id="e8c88-112">Molti cmdlet di Windows PowerShell hanno un parametro ComputerName che consente di raccogliere dati e modificare le impostazioni di uno o più computer remoti.</span><span class="sxs-lookup"><span data-stu-id="e8c88-112">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="e8c88-113">Questi cmdlet usano diversi protocolli di comunicazione e sono supportati in tutti i sistemi operativi senza alcuna configurazione speciale.</span><span class="sxs-lookup"><span data-stu-id="e8c88-113">These cmdlets use varying communication protocols and work on all Windows operating systems without any special configuration.</span></span>

<span data-ttu-id="e8c88-114">Questi cmdlet sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="e8c88-114">These cmdlets include:</span></span>

- [<span data-ttu-id="e8c88-115">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="e8c88-115">Restart-Computer</span></span>](/powershell/module/microsoft.powershell.management/restart-computer)
- [<span data-ttu-id="e8c88-116">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="e8c88-116">Test-Connection</span></span>](/powershell/module/microsoft.powershell.management/test-connection)
- [<span data-ttu-id="e8c88-117">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="e8c88-117">Clear-EventLog</span></span>](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [<span data-ttu-id="e8c88-118">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="e8c88-118">Get-EventLog</span></span>](/powershell/module/microsoft.powershell.management/get-eventlog)
- [<span data-ttu-id="e8c88-119">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="e8c88-119">Get-HotFix</span></span>](/powershell/module/microsoft.powershell.management/get-hotfix)
- [<span data-ttu-id="e8c88-120">Get-Process</span><span class="sxs-lookup"><span data-stu-id="e8c88-120">Get-Process</span></span>](/powershell/module/microsoft.powershell.management/get-process)
- [<span data-ttu-id="e8c88-121">Get-Service</span><span class="sxs-lookup"><span data-stu-id="e8c88-121">Get-Service</span></span>](/powershell/module/microsoft.powershell.management/get-service)
- [<span data-ttu-id="e8c88-122">Set-Service</span><span class="sxs-lookup"><span data-stu-id="e8c88-122">Set-Service</span></span>](/powershell/module/microsoft.powershell.management/set-service)
- [<span data-ttu-id="e8c88-123">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="e8c88-123">Get-WinEvent</span></span>](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [<span data-ttu-id="e8c88-124">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="e8c88-124">Get-WmiObject</span></span>](/powershell/module/microsoft.powershell.management/get-wmiobject)

<span data-ttu-id="e8c88-125">In genere, i cmdlet che supportano la comunicazione remota senza configurazioni speciali includono il parametro ComputerName e non includono invece il parametro Session.</span><span class="sxs-lookup"><span data-stu-id="e8c88-125">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and don't have the Session parameter.</span></span> <span data-ttu-id="e8c88-126">Per trovare questi cmdlet nella sessione, digitare:</span><span class="sxs-lookup"><span data-stu-id="e8c88-126">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="e8c88-127">Comunicazione remota di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e8c88-127">Windows PowerShell Remoting</span></span>

<span data-ttu-id="e8c88-128">Usando il protocollo WS-Management, la comunicazione remota di Windows PowerShell permette di eseguire qualsiasi comando di Windows PowerShell in uno o più computer remoti.</span><span class="sxs-lookup"><span data-stu-id="e8c88-128">Using the WS-Management protocol, Windows PowerShell remoting lets you run any Windows PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="e8c88-129">È possibile stabilire connessioni permanenti, avviare sessioni interattive ed eseguire script in computer remoti.</span><span class="sxs-lookup"><span data-stu-id="e8c88-129">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

<span data-ttu-id="e8c88-130">Per usare la comunicazione remota di Windows PowerShell, è necessario che il computer remoto sia configurato per la gestione remota.</span><span class="sxs-lookup"><span data-stu-id="e8c88-130">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="e8c88-131">Per altre informazioni, incluse le istruzioni, vedere [about_Remote_Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span><span class="sxs-lookup"><span data-stu-id="e8c88-131">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="e8c88-132">Una volta configurata la comunicazione remota di Windows PowerShell, sono disponibili diverse strategie per usarla.</span><span class="sxs-lookup"><span data-stu-id="e8c88-132">Once you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span>
<span data-ttu-id="e8c88-133">Questo articolo ne indica solo alcune.</span><span class="sxs-lookup"><span data-stu-id="e8c88-133">This article lists just a few of them.</span></span> <span data-ttu-id="e8c88-134">Per altre informazioni, vedere [about_Remote](/powershell/module/microsoft.powershell.core/about/about_remote).</span><span class="sxs-lookup"><span data-stu-id="e8c88-134">For more information, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="e8c88-135">Avviare una sessione interattiva</span><span class="sxs-lookup"><span data-stu-id="e8c88-135">Start an Interactive Session</span></span>

<span data-ttu-id="e8c88-136">Per avviare una sessione interattiva con un singolo computer remoto, usare il cmdlet [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="e8c88-136">To start an interactive session with a single remote computer, use the [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.</span></span>
<span data-ttu-id="e8c88-137">Ad esempio, per avviare una sessione interattiva con il computer remoto Server01, digitare:</span><span class="sxs-lookup"><span data-stu-id="e8c88-137">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="e8c88-138">Il prompt dei comandi cambia per visualizzare il nome del computer remoto.</span><span class="sxs-lookup"><span data-stu-id="e8c88-138">The command prompt changes to display the name of the remote computer.</span></span> <span data-ttu-id="e8c88-139">Qualsiasi comando digitato nel prompt viene eseguito nel computer remoto e i risultati vengono visualizzati nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="e8c88-139">Any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="e8c88-140">Per terminare una sessione interattiva, digitare:</span><span class="sxs-lookup"><span data-stu-id="e8c88-140">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="e8c88-141">Per altre informazioni sui cmdlet Enter-PSSession ed Exit-PSSession, vedere:</span><span class="sxs-lookup"><span data-stu-id="e8c88-141">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see:</span></span>

- [<span data-ttu-id="e8c88-142">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="e8c88-142">Enter-PSSession</span></span>](/powershell/module/microsoft.powershell.core/enter-pssession)
- [<span data-ttu-id="e8c88-143">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="e8c88-143">Exit-PSSession</span></span>](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a><span data-ttu-id="e8c88-144">Eseguire un comando remoto</span><span class="sxs-lookup"><span data-stu-id="e8c88-144">Run a Remote Command</span></span>

<span data-ttu-id="e8c88-145">Per eseguire un comando in uno o più computer, usare il cmdlet [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command).</span><span class="sxs-lookup"><span data-stu-id="e8c88-145">To run a command on one or more computers, use the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span> <span data-ttu-id="e8c88-146">Ad esempio, per eseguire un comando [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) nei computer remoti Server01 e Server02, digitare:</span><span class="sxs-lookup"><span data-stu-id="e8c88-146">For example, to run a [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="e8c88-147">L'output viene restituito nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="e8c88-147">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a><span data-ttu-id="e8c88-148">Eseguire uno script</span><span class="sxs-lookup"><span data-stu-id="e8c88-148">Run a Script</span></span>

<span data-ttu-id="e8c88-149">Per eseguire uno script in uno o più computer remoti, usare il parametro FilePath del cmdlet `Invoke-Command`.</span><span class="sxs-lookup"><span data-stu-id="e8c88-149">To run a script on one or many remote computers, use the FilePath parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="e8c88-150">Lo script deve essere attivo o accessibile sul computer locale.</span><span class="sxs-lookup"><span data-stu-id="e8c88-150">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="e8c88-151">I risultati vengono restituiti al computer locale.</span><span class="sxs-lookup"><span data-stu-id="e8c88-151">The results are returned to your local computer.</span></span>

<span data-ttu-id="e8c88-152">Ad esempio, il comando seguente esegue lo script DiskCollect.ps1 nei computer remoti Server01 e Server02.</span><span class="sxs-lookup"><span data-stu-id="e8c88-152">For example, the following command runs the DiskCollect.ps1 script on the remote computers, Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="e8c88-153">Stabilire una connessione permanente</span><span class="sxs-lookup"><span data-stu-id="e8c88-153">Establish a Persistent Connection</span></span>

<span data-ttu-id="e8c88-154">Usare il cmdlet `New-PSSession` per creare una sessione permanente in un computer remoto.</span><span class="sxs-lookup"><span data-stu-id="e8c88-154">Use the `New-PSSession` cmdlet to create a persistent session on a remote computer.</span></span> <span data-ttu-id="e8c88-155">L'esempio seguente crea sessioni remote in Server01 e Server02.</span><span class="sxs-lookup"><span data-stu-id="e8c88-155">The following example creates remote sessions on Server01 and Server02.</span></span> <span data-ttu-id="e8c88-156">Gli oggetti sessione vengono archiviati nella variabile `$s`.</span><span class="sxs-lookup"><span data-stu-id="e8c88-156">The session objects are stored in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="e8c88-157">Una volta stabilite le sessioni, è possibile eseguire qualsiasi comando al loro interno.</span><span class="sxs-lookup"><span data-stu-id="e8c88-157">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="e8c88-158">Poiché le sessioni sono permanenti, è possibile raccogliere dati da un comando e usarli in un altro comando.</span><span class="sxs-lookup"><span data-stu-id="e8c88-158">And because the sessions are persistent, you can collect data from one command and use it in another command.</span></span>

<span data-ttu-id="e8c88-159">Ad esempio, il comando seguente esegue un comando Get-Hotfix nelle sessioni nella variabile $s e salva i risultati nella variabile $h.</span><span class="sxs-lookup"><span data-stu-id="e8c88-159">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="e8c88-160">La variabile $h viene creata in ogni sessione in $s, ma non esiste nella sessione locale.</span><span class="sxs-lookup"><span data-stu-id="e8c88-160">The $h variable is created in each of the sessions in $s, but it doesn't exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="e8c88-161">È ora possibile usare i dati nella variabile `$h` con altri comandi nella stessa sessione.</span><span class="sxs-lookup"><span data-stu-id="e8c88-161">Now you can use the data in the `$h` variable with other commands in the same session.</span></span> <span data-ttu-id="e8c88-162">I risultati vengono visualizzati nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="e8c88-162">The results are displayed on the local computer.</span></span> <span data-ttu-id="e8c88-163">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="e8c88-163">For example:</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="e8c88-164">Comunicazione remota avanzata</span><span class="sxs-lookup"><span data-stu-id="e8c88-164">Advanced Remoting</span></span>

<span data-ttu-id="e8c88-165">La gestione remota di Windows PowerShell ha inizio in questo ambito.</span><span class="sxs-lookup"><span data-stu-id="e8c88-165">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="e8c88-166">Usando i cmdlet installati con Windows PowerShell, è possibile stabilire e configurare sessioni remote dalle estremità locali e remote, creare sessioni personalizzate e con restrizioni, consentire agli utenti di importare comandi da una sessione remota che vengono effettivamente eseguiti in modo implicito nella sessione remota, configurare la sicurezza di una sessione remota e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="e8c88-166">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="e8c88-167">Windows PowerShell include un provider WSMan.</span><span class="sxs-lookup"><span data-stu-id="e8c88-167">Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="e8c88-168">Il provider crea un'unità `WSMAN:` che permette di spostarsi all'interno di una gerarchia di impostazioni di configurazione nel computer locale e nei computer remoti.</span><span class="sxs-lookup"><span data-stu-id="e8c88-168">The provider creates a `WSMAN:` drive that lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>

<span data-ttu-id="e8c88-169">Per altre informazioni sul provider WSMan, vedere [Provider WSMan](https://technet.microsoft.com/library/dd819476.aspx) e [About WS-Management Cmdlets](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets) (Informazioni sui cmdlet WS-Management) oppure digitare `Get-Help wsman` nella console di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8c88-169">For more information about the WSMan provider, see [WSMan Provider](https://technet.microsoft.com/library/dd819476.aspx) and [About WS-Management Cmdlets](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), or in the Windows PowerShell console, type `Get-Help wsman`.</span></span>

<span data-ttu-id="e8c88-170">Per altre informazioni, vedere:</span><span class="sxs-lookup"><span data-stu-id="e8c88-170">For more information, see:</span></span>

- [<span data-ttu-id="e8c88-171">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="e8c88-171">About Remote FAQ</span></span>](https://technet.microsoft.com/library/dd315359.aspx)
- [<span data-ttu-id="e8c88-172">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="e8c88-172">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="e8c88-173">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="e8c88-173">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="e8c88-174">Per informazioni sugli errori di comunicazione remota, vedere [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="e8c88-174">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="e8c88-175">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e8c88-175">See Also</span></span>

- [<span data-ttu-id="e8c88-176">about_Remote</span><span class="sxs-lookup"><span data-stu-id="e8c88-176">about_Remote</span></span>](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="e8c88-177">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="e8c88-177">about_Remote_FAQ</span></span>](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="e8c88-178">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="e8c88-178">about_Remote_Requirements</span></span>](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="e8c88-179">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="e8c88-179">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="e8c88-180">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="e8c88-180">about_PSSessions</span></span>](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="e8c88-181">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="e8c88-181">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="e8c88-182">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="e8c88-182">Invoke-Command</span></span>](/powershell/module/microsoft.powershell.core/invoke-command)
- [<span data-ttu-id="e8c88-183">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="e8c88-183">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="e8c88-184">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="e8c88-184">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="e8c88-185">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="e8c88-185">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="e8c88-186">Provider WSMan</span><span class="sxs-lookup"><span data-stu-id="e8c88-186">WSMan Provider</span></span>](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md
