---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Esecuzione di comandi remoti
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 43f07abd642e7de235647fa151537c46ebe86cae
ms.sourcegitcommit: 6aed37d7f0c9652ae09bb8c11928da7e4783ed7f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="running-remote-commands"></a><span data-ttu-id="99363-103">Esecuzione di comandi remoti</span><span class="sxs-lookup"><span data-stu-id="99363-103">Running Remote Commands</span></span>

<span data-ttu-id="99363-104">È possibile eseguire comandi in uno o in centinaia di computer con un singolo comando di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99363-104">You can run commands on one or hundreds of computers with a single Windows PowerShell command.</span></span> <span data-ttu-id="99363-105">Windows PowerShell supporta l'elaborazione remota tramite varie tecnologie, tra cui WMI, RPC e WS-Management.</span><span class="sxs-lookup"><span data-stu-id="99363-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

## <a name="remoting-in-powershell-core"></a><span data-ttu-id="99363-106">Comunicazione remota in PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="99363-106">Remoting in PowerShell Core</span></span>

<span data-ttu-id="99363-107">PowerShell Core, l'edizione più recente di PowerShell in Windows, macOS e Linux, supporta la comunicazione remota WMI, WS-Management e SSH.</span><span class="sxs-lookup"><span data-stu-id="99363-107">PowerShell Core, the newer edition of PowerShell on Windows, macOS, and Linux, supports WMI, WS-Management, and SSH remoting.</span></span>
<span data-ttu-id="99363-108">RPC non è più supportato.</span><span class="sxs-lookup"><span data-stu-id="99363-108">(RPC is no longer supported.)</span></span>

<span data-ttu-id="99363-109">Per altre informazioni su come configurarla, vedere:</span><span class="sxs-lookup"><span data-stu-id="99363-109">For more information on setting this up, see:</span></span>

* <span data-ttu-id="99363-110">[Comunicazione remota SSH in PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="99363-110">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
* <span data-ttu-id="99363-111">[Comunicazione remota WinRM in PowerShell Core][winrm-remoting]</span><span class="sxs-lookup"><span data-stu-id="99363-111">[WinRM Remoting in PowerShell Core][winrm-remoting]</span></span>

## <a name="remoting-without-configuration"></a><span data-ttu-id="99363-112">Comunicazione remota senza configurazione</span><span class="sxs-lookup"><span data-stu-id="99363-112">Remoting Without Configuration</span></span>
<span data-ttu-id="99363-113">Molti cmdlet di Windows PowerShell hanno un parametro ComputerName che consente di raccogliere dati e modificare le impostazioni di uno o più computer remoti.</span><span class="sxs-lookup"><span data-stu-id="99363-113">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="99363-114">Usano un'ampia varietà di tecnologie per le comunicazioni, molte delle quali funzionano in tutti i sistemi operativi Windows supportati da Windows PowerShell senza nessuna configurazione speciale.</span><span class="sxs-lookup"><span data-stu-id="99363-114">They use a variety of communication technologies and many work on all Windows operating systems that Windows PowerShell supports without any special configuration.</span></span>

<span data-ttu-id="99363-115">Questi cmdlet sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="99363-115">These cmdlets include:</span></span>

* [<span data-ttu-id="99363-116">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="99363-116">Restart-Computer</span></span>](https://go.microsoft.com/fwlink/?LinkId=821625)
* [<span data-ttu-id="99363-117">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="99363-117">Test-Connection</span></span>](https://go.microsoft.com/fwlink/?LinkId=821646)
* [<span data-ttu-id="99363-118">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="99363-118">Clear-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821568)
* [<span data-ttu-id="99363-119">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="99363-119">Get-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821585)
* [<span data-ttu-id="99363-120">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="99363-120">Get-HotFix</span></span>](https://go.microsoft.com/fwlink/?LinkId=821586)
* [<span data-ttu-id="99363-121">Get-Process</span><span class="sxs-lookup"><span data-stu-id="99363-121">Get-Process</span></span>](https://go.microsoft.com/fwlink/?linkid=821590)
* [<span data-ttu-id="99363-122">Get-Service</span><span class="sxs-lookup"><span data-stu-id="99363-122">Get-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821593)
* [<span data-ttu-id="99363-123">Set-Service</span><span class="sxs-lookup"><span data-stu-id="99363-123">Set-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821633)
* [<span data-ttu-id="99363-124">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="99363-124">Get-WinEvent</span></span>](https://go.microsoft.com/fwlink/?linkid=821529)
* [<span data-ttu-id="99363-125">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="99363-125">Get-WmiObject</span></span>](https://go.microsoft.com/fwlink/?LinkId=821595)

<span data-ttu-id="99363-126">In genere, i cmdlet che supportano la comunicazione remota senza configurazione speciale hanno il parametro ComputerName, mentre non hanno il parametro Session.</span><span class="sxs-lookup"><span data-stu-id="99363-126">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and do not have the Session parameter.</span></span> <span data-ttu-id="99363-127">Per trovare questi cmdlet nella sessione, digitare:</span><span class="sxs-lookup"><span data-stu-id="99363-127">To find these cmdlets in your session, type:</span></span>

```
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="99363-128">Comunicazione remota di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="99363-128">Windows PowerShell Remoting</span></span>
<span data-ttu-id="99363-129">La comunicazione remota di Windows PowerShell, basata sul protocollo WS-Management, consente di eseguire qualsiasi comando di Windows PowerShell in uno o più computer remoti.</span><span class="sxs-lookup"><span data-stu-id="99363-129">Windows PowerShell remoting, which uses the WS-Management protocol, lets you run any Windows PowerShell command on one or many remote computers.</span></span> <span data-ttu-id="99363-130">È possibile stabilire connessioni permanenti, avviare sessioni interattive 1:1 ed eseguire script in più computer.</span><span class="sxs-lookup"><span data-stu-id="99363-130">It lets you establish persistent connections, start 1:1 interactive sessions, and run scripts on multiple computers.</span></span>

<span data-ttu-id="99363-131">Per usare la comunicazione remota di Windows PowerShell, è necessario che il computer remoto sia configurato per la gestione remota.</span><span class="sxs-lookup"><span data-stu-id="99363-131">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span> <span data-ttu-id="99363-132">Per altre informazioni, incluse le istruzioni, vedere [about_Remote_Requirements](https://technet.microsoft.com/en-us/library/dd315349.aspx).</span><span class="sxs-lookup"><span data-stu-id="99363-132">For more information, including instructions, see [About Remote Requirements](https://technet.microsoft.com/en-us/library/dd315349.aspx).</span></span>

<span data-ttu-id="99363-133">Una volta configurata la comunicazione remota di Windows PowerShell, sono disponibili diverse strategie per usarla.</span><span class="sxs-lookup"><span data-stu-id="99363-133">After you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span> <span data-ttu-id="99363-134">Nella parte restante del documento ne verranno descritte alcune.</span><span class="sxs-lookup"><span data-stu-id="99363-134">The remainder of this document lists just a few of them.</span></span> <span data-ttu-id="99363-135">Per altre informazioni, vedere [about_Remote](https://technet.microsoft.com/en-us/library/dd347744.aspx) e [about_Remote_FAQ](https://technet.microsoft.com/en-us/library/dd347744.aspx).</span><span class="sxs-lookup"><span data-stu-id="99363-135">For more information, see [About Remote](https://technet.microsoft.com/en-us/library/dd347744.aspx) and [About Remote FAQ](https://technet.microsoft.com/en-us/library/dd347744.aspx).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="99363-136">Avviare una sessione interattiva</span><span class="sxs-lookup"><span data-stu-id="99363-136">Start an Interactive Session</span></span>
<span data-ttu-id="99363-137">Per avviare una sessione interattiva con un singolo computer remoto, usare il cmdlet [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477).</span><span class="sxs-lookup"><span data-stu-id="99363-137">To start an interactive session with a single remote computer, use the [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet.</span></span>
<span data-ttu-id="99363-138">Ad esempio, per avviare una sessione interattiva con il computer remoto Server01, digitare:</span><span class="sxs-lookup"><span data-stu-id="99363-138">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```
Enter-PSSession Server01
```

<span data-ttu-id="99363-139">Il prompt dei comandi cambia per visualizzare il nome del computer con cui si è connessi.</span><span class="sxs-lookup"><span data-stu-id="99363-139">The command prompt changes to display the name of the computer to which you are connected.</span></span> <span data-ttu-id="99363-140">Da questo momento in poi, ogni comando digitato al prompt viene eseguito nel computer remoto e i risultati vengono visualizzati nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="99363-140">From then on, any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="99363-141">Per terminare una sessione interattiva, digitare:</span><span class="sxs-lookup"><span data-stu-id="99363-141">To end the interactive session, type:</span></span>

```
Exit-PSSession
```

<span data-ttu-id="99363-142">Per altre informazioni sui cmdlet Enter-PSSession ed Exit-PSSession, vedere [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) ed [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span><span class="sxs-lookup"><span data-stu-id="99363-142">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) and [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span></span>

### <a name="run-a-remote-command"></a><span data-ttu-id="99363-143">Eseguire un comando remoto</span><span class="sxs-lookup"><span data-stu-id="99363-143">Run a Remote Command</span></span>
<span data-ttu-id="99363-144">Per eseguire qualsiasi comando in uno o più computer remoti, usare il cmdlet [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="99363-144">To run any command on one or many remote computers, use the [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet.</span></span>
<span data-ttu-id="99363-145">Ad esempio, per eseguire un comando [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) nei computer remoti Server01 e Server02, digitare:</span><span class="sxs-lookup"><span data-stu-id="99363-145">For example, to run a [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) command on the Server01 and Server02 remote computers, type:</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="99363-146">L'output viene restituito nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="99363-146">The output is returned to your computer.</span></span>

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```
<span data-ttu-id="99363-147">Per altre informazioni sul cmdlet Invoke-Command, vedere [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="99363-147">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="run-a-script"></a><span data-ttu-id="99363-148">Eseguire uno script</span><span class="sxs-lookup"><span data-stu-id="99363-148">Run a Script</span></span>
<span data-ttu-id="99363-149">Per eseguire uno script in uno o più computer remoti, usare il parametro FilePath del cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="99363-149">To run a script on one or many remote computers, use the FilePath parameter of the Invoke-Command cmdlet.</span></span> <span data-ttu-id="99363-150">Lo script deve essere attivo o accessibile sul computer locale.</span><span class="sxs-lookup"><span data-stu-id="99363-150">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="99363-151">I risultati vengono restituiti al computer locale.</span><span class="sxs-lookup"><span data-stu-id="99363-151">The results are returned to your local computer.</span></span>

<span data-ttu-id="99363-152">Ad esempio, il comando seguente esegue lo script DiskCollect.ps1 nei computer remoti Server01 e Server02.</span><span class="sxs-lookup"><span data-stu-id="99363-152">For example, the following command runs the DiskCollect.ps1 script on the Server01 and Server02 remote computers.</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

<span data-ttu-id="99363-153">Per altre informazioni sul cmdlet Invoke-Command, vedere [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="99363-153">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="99363-154">Stabilire una connessione permanente</span><span class="sxs-lookup"><span data-stu-id="99363-154">Establish a Persistent Connection</span></span>
<span data-ttu-id="99363-155">Per eseguire una serie di comandi correlati che condividono dati, creare una sessione nel computer remoto e quindi usare il cmdlet Invoke-Command per eseguire i comandi nella sessione creata.</span><span class="sxs-lookup"><span data-stu-id="99363-155">To run a series of related commands that share data, create a session on the remote computer and then use the Invoke-Command cmdlet to run commands in the session that you create.</span></span> <span data-ttu-id="99363-156">Per creare una sessione remota, usare il cmdlet New-PSSession.</span><span class="sxs-lookup"><span data-stu-id="99363-156">To create a remote session, use the New-PSSession cmdlet.</span></span>

<span data-ttu-id="99363-157">Ad esempio, il comando seguente crea una sessione remota nel computer Server01 e un'altra nel computer Server02.</span><span class="sxs-lookup"><span data-stu-id="99363-157">For example, the following command creates a remote session on the Server01 computer and another remote session on the Server02 computer.</span></span> <span data-ttu-id="99363-158">Gli oggetti sessione vengono salvati nella variabile $s.</span><span class="sxs-lookup"><span data-stu-id="99363-158">It saves the session objects in the $s variable.</span></span>

```
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="99363-159">Una volta stabilite le sessioni, è possibile eseguire qualsiasi comando al loro interno.</span><span class="sxs-lookup"><span data-stu-id="99363-159">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="99363-160">Inoltre, poiché le sessioni sono permanenti, è possibile raccogliere dati in un comando e usarli in un comando successivo.</span><span class="sxs-lookup"><span data-stu-id="99363-160">And because the sessions are persistent, you can collect data in one command and use it in a subsequent command.</span></span>

<span data-ttu-id="99363-161">Ad esempio, il comando seguente esegue un comando Get-Hotfix nelle sessioni nella variabile $s e salva i risultati nella variabile $h.</span><span class="sxs-lookup"><span data-stu-id="99363-161">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="99363-162">La variabile $h viene creata in ogni sessione in $s, ma non esiste nella sessione locale.</span><span class="sxs-lookup"><span data-stu-id="99363-162">The $h variable is created in each of the sessions in $s, but it does not exist in the local session.</span></span>

```
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="99363-163">A questo punto è possibile usare i dati della variabile $h nei comandi successivi, ad esempio il seguente.</span><span class="sxs-lookup"><span data-stu-id="99363-163">Now you can use the data in the $h variable in subsequent commands, such as the following one.</span></span> <span data-ttu-id="99363-164">I risultati vengono visualizzati nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="99363-164">The results are displayed on the local computer.</span></span>

```
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="99363-165">Comunicazione remota avanzata</span><span class="sxs-lookup"><span data-stu-id="99363-165">Advanced Remoting</span></span>
<span data-ttu-id="99363-166">La gestione remota di Windows PowerShell ha inizio in questo ambito.</span><span class="sxs-lookup"><span data-stu-id="99363-166">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="99363-167">Usando i cmdlet installati con Windows PowerShell, è possibile stabilire e configurare sessioni remote dalle estremità locali e remote, creare sessioni personalizzate e con restrizioni, consentire agli utenti di importare comandi da una sessione remota che vengono effettivamente eseguiti in modo implicito nella sessione remota, configurare la sicurezza di una sessione remota e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="99363-167">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="99363-168">Per semplificare la configurazione remota, Windows PowerShell include un provider WSMan.</span><span class="sxs-lookup"><span data-stu-id="99363-168">To facilitate remote configuration, Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="99363-169">L'unità WSMAN: creata dal provider consente di spostarsi in una gerarchia di impostazioni di configurazione nel computer locale e nei computer remoti.</span><span class="sxs-lookup"><span data-stu-id="99363-169">The WSMAN: drive that the provider creates lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>
<span data-ttu-id="99363-170">Per altre informazioni sul provider di WS-Management, vedere [Provider WSMan](https://technet.microsoft.com/en-us/library/dd819476.aspx) e [about_WS-Management_Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx) oppure digitare "get-help wsman" nella console di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99363-170">For more information about the WSMan provider, see  [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) and [About WS-Management Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx), or in the Windows PowerShell console, type "Get-Help wsman".</span></span>

<span data-ttu-id="99363-171">Per altre informazioni, vedere:</span><span class="sxs-lookup"><span data-stu-id="99363-171">For more information, see:</span></span>
- [<span data-ttu-id="99363-172">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="99363-172">About Remote FAQ</span></span>](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [<span data-ttu-id="99363-173">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="99363-173">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="99363-174">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="99363-174">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="99363-175">Per informazioni sugli errori di comunicazione remota, vedere [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="99363-175">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="99363-176">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="99363-176">See Also</span></span>
- [<span data-ttu-id="99363-177">about_Remote</span><span class="sxs-lookup"><span data-stu-id="99363-177">about_Remote</span></span>](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="99363-178">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="99363-178">about_Remote_FAQ</span></span>](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="99363-179">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="99363-179">about_Remote_Requirements</span></span>](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="99363-180">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="99363-180">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="99363-181">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="99363-181">about_PSSessions</span></span>](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="99363-182">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="99363-182">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="99363-183">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="99363-183">Invoke-Command</span></span>](https://go.microsoft.com/fwlink/?LinkId=821493)
- [<span data-ttu-id="99363-184">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="99363-184">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="99363-185">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="99363-185">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="99363-186">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="99363-186">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="99363-187">Provider WSMan</span><span class="sxs-lookup"><span data-stu-id="99363-187">WSMan Provider</span></span>](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-resmoting]: SSH-Remoting-in-PowerShell-Core.md
