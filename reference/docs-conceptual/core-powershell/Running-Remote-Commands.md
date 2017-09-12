---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Esecuzione di comandi remoti
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: c3bf002e7a3daa5afc8219dd846145808eef3c9b
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2017
---
# <a name="running-remote-commands"></a><span data-ttu-id="cbe31-103">Esecuzione di comandi remoti</span><span class="sxs-lookup"><span data-stu-id="cbe31-103">Running Remote Commands</span></span>
<span data-ttu-id="cbe31-104">È possibile eseguire comandi in uno o in centinaia di computer con un singolo comando di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cbe31-104">You can run commands on one or hundreds of computers with a single Windows PowerShell command.</span></span> <span data-ttu-id="cbe31-105">Windows PowerShell supporta l'elaborazione remota tramite varie tecnologie, tra cui WMI, RPC e WS-Management.</span><span class="sxs-lookup"><span data-stu-id="cbe31-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

## <a name="remoting-without-configuration"></a><span data-ttu-id="cbe31-106">Comunicazione remota senza configurazione</span><span class="sxs-lookup"><span data-stu-id="cbe31-106">Remoting Without Configuration</span></span>
<span data-ttu-id="cbe31-107">Molti cmdlet di Windows PowerShell hanno un parametro ComputerName che consente di raccogliere dati e modificare le impostazioni di uno o più computer remoti.</span><span class="sxs-lookup"><span data-stu-id="cbe31-107">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="cbe31-108">Usano un'ampia varietà di tecnologie per le comunicazioni, molte delle quali funzionano in tutti i sistemi operativi Windows supportati da Windows PowerShell senza nessuna configurazione speciale.</span><span class="sxs-lookup"><span data-stu-id="cbe31-108">They use a variety of communication technologies and many work on all Windows operating systems that Windows PowerShell supports without any special configuration.</span></span>

<span data-ttu-id="cbe31-109">Questi cmdlet sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="cbe31-109">These cmdlets include:</span></span>

- [<span data-ttu-id="cbe31-110">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="cbe31-110">Restart-Computer</span></span>](https://technet.microsoft.com/en-us/library/dd315301.aspx)

- [<span data-ttu-id="cbe31-111">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="cbe31-111">Test-Connection</span></span>](https://technet.microsoft.com/en-us/library/dd315259.aspx)

- [<span data-ttu-id="cbe31-112">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="cbe31-112">Clear-EventLog</span></span>](https://technet.microsoft.com/en-us/library/dd347552.aspx)

- [<span data-ttu-id="cbe31-113">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="cbe31-113">Get-EventLog</span></span>](https://technet.microsoft.com/en-us/library/dd315250.aspx)

- [<span data-ttu-id="cbe31-114">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="cbe31-114">Get-HotFix</span></span>](https://technet.microsoft.com/en-us/library/e1ef636f-5170-4675-b564-199d9ef6f101)

 -   [<span data-ttu-id="cbe31-115">Get-Process</span><span class="sxs-lookup"><span data-stu-id="cbe31-115">Get-Process</span></span>](https://technet.microsoft.com/en-us/library/dd347630.aspx)

- [<span data-ttu-id="cbe31-116">Get-Service</span><span class="sxs-lookup"><span data-stu-id="cbe31-116">Get-Service</span></span>](https://technet.microsoft.com/en-us/library/dd347591.aspx)

- [<span data-ttu-id="cbe31-117">Set-Service</span><span class="sxs-lookup"><span data-stu-id="cbe31-117">Set-Service</span></span>](https://technet.microsoft.com/en-us/library/dd315324.aspx)

- [<span data-ttu-id="cbe31-118">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="cbe31-118">Get-WinEvent</span></span>](https://technet.microsoft.com/en-us/library/dd315358.aspx)

- [<span data-ttu-id="cbe31-119">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="cbe31-119">Get-WmiObject</span></span>](https://technet.microsoft.com/en-us/library/dd315295.aspx)

<span data-ttu-id="cbe31-120">In genere, i cmdlet che supportano la comunicazione remota senza configurazione speciale hanno il parametro ComputerName, mentre non hanno il parametro Session.</span><span class="sxs-lookup"><span data-stu-id="cbe31-120">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and do not have the Session parameter.</span></span> <span data-ttu-id="cbe31-121">Per trovare questi cmdlet nella sessione, digitare:</span><span class="sxs-lookup"><span data-stu-id="cbe31-121">To find these cmdlets in your session, type:</span></span>

```
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="cbe31-122">Comunicazione remota di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cbe31-122">Windows PowerShell Remoting</span></span>
<span data-ttu-id="cbe31-123">La comunicazione remota di Windows PowerShell, basata sul protocollo WS-Management, consente di eseguire qualsiasi comando di Windows PowerShell in uno o più computer remoti.</span><span class="sxs-lookup"><span data-stu-id="cbe31-123">Windows PowerShell remoting, which uses the WS-Management protocol, lets you run any Windows PowerShell command on one or many remote computers.</span></span> <span data-ttu-id="cbe31-124">È possibile stabilire connessioni permanenti, avviare sessioni interattive 1:1 ed eseguire script in più computer.</span><span class="sxs-lookup"><span data-stu-id="cbe31-124">It lets you establish persistent connections, start 1:1 interactive sessions, and run scripts on multiple computers.</span></span>

<span data-ttu-id="cbe31-125">Per usare la comunicazione remota di Windows PowerShell, è necessario che il computer remoto sia configurato per la gestione remota.</span><span class="sxs-lookup"><span data-stu-id="cbe31-125">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span> <span data-ttu-id="cbe31-126">Per altre informazioni, incluse le istruzioni, vedere [about_Remote_Requirements](https://technet.microsoft.com/en-us/library/dd315349.aspx).</span><span class="sxs-lookup"><span data-stu-id="cbe31-126">For more information, including instructions, see [About Remote Requirements](https://technet.microsoft.com/en-us/library/dd315349.aspx).</span></span>

<span data-ttu-id="cbe31-127">Una volta configurata la comunicazione remota di Windows PowerShell, sono disponibili diverse strategie per usarla.</span><span class="sxs-lookup"><span data-stu-id="cbe31-127">After you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span> <span data-ttu-id="cbe31-128">Nella parte restante del documento ne verranno descritte alcune.</span><span class="sxs-lookup"><span data-stu-id="cbe31-128">The remainder of this document lists just a few of them.</span></span> <span data-ttu-id="cbe31-129">Per altre informazioni, vedere [about_Remote](https://technet.microsoft.com/en-us/library/dd347744.aspx) e [about_Remote_FAQ](https://technet.microsoft.com/en-us/library/dd347744.aspx).</span><span class="sxs-lookup"><span data-stu-id="cbe31-129">For more information, see [About Remote](https://technet.microsoft.com/en-us/library/dd347744.aspx) and [About Remote FAQ](https://technet.microsoft.com/en-us/library/dd347744.aspx).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="cbe31-130">Avviare una sessione interattiva</span><span class="sxs-lookup"><span data-stu-id="cbe31-130">Start an Interactive Session</span></span>
<span data-ttu-id="cbe31-131">Per avviare una sessione interattiva con un singolo computer remoto, usare il cmdlet [Enter-PSSession](https://technet.microsoft.com/en-us/library/dd315384.aspx).</span><span class="sxs-lookup"><span data-stu-id="cbe31-131">To start an interactive session with a single remote computer, use the [Enter-PSSession](https://technet.microsoft.com/en-us/library/dd315384.aspx) cmdlet.</span></span> <span data-ttu-id="cbe31-132">Ad esempio, per avviare una sessione interattiva con il computer remoto Server01, digitare:</span><span class="sxs-lookup"><span data-stu-id="cbe31-132">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```
Enter-PSSession Server01
```

<span data-ttu-id="cbe31-133">Il prompt dei comandi cambia per visualizzare il nome del computer con cui si è connessi.</span><span class="sxs-lookup"><span data-stu-id="cbe31-133">The command prompt changes to display the name of the computer to which you are connected.</span></span> <span data-ttu-id="cbe31-134">Da questo momento in poi, ogni comando digitato al prompt viene eseguito nel computer remoto e i risultati vengono visualizzati nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="cbe31-134">From then on, any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="cbe31-135">Per terminare una sessione interattiva, digitare:</span><span class="sxs-lookup"><span data-stu-id="cbe31-135">To end the interactive session, type:</span></span>

```
Exit-PSSession
```

<span data-ttu-id="cbe31-136">Per altre informazioni sui cmdlet Enter-PSSession ed Exit-PSSession, vedere [Enter-PSSession](https://technet.microsoft.com/en-us/library/dd315384.aspx) ed [Exit-PSSession](https://technet.microsoft.com/en-us/library/dd315322.aspx).</span><span class="sxs-lookup"><span data-stu-id="cbe31-136">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see [Enter-PSSession](https://technet.microsoft.com/en-us/library/dd315384.aspx) and [Exit-PSSession](https://technet.microsoft.com/en-us/library/dd315322.aspx).</span></span>

### <a name="run-a-remote-command"></a><span data-ttu-id="cbe31-137">Eseguire un comando remoto</span><span class="sxs-lookup"><span data-stu-id="cbe31-137">Run a Remote Command</span></span>
<span data-ttu-id="cbe31-138">Per eseguire qualsiasi comando in uno o più computer remoti, usare il cmdlet [Invoke-Command](https://technet.microsoft.com/en-us/library/dd347578.aspx).</span><span class="sxs-lookup"><span data-stu-id="cbe31-138">To run any command on one or many remote computers, use the [Invoke-Command](https://technet.microsoft.com/en-us/library/dd347578.aspx) cmdlet.</span></span>
<span data-ttu-id="cbe31-139">Ad esempio, per eseguire un comando [Get-UICulture](https://technet.microsoft.com/en-us/library/dd347742.aspx) nei computer remoti Server01 e Server02, digitare:</span><span class="sxs-lookup"><span data-stu-id="cbe31-139">For example, to run a [Get-UICulture](https://technet.microsoft.com/en-us/library/dd347742.aspx) command on the Server01 and Server02 remote computers, type:</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="cbe31-140">L'output viene restituito nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="cbe31-140">The output is returned to your computer.</span></span>

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```
<span data-ttu-id="cbe31-141">Per altre informazioni sul cmdlet Invoke-Command, vedere [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462).</span><span class="sxs-lookup"><span data-stu-id="cbe31-141">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462).</span></span>

### <a name="run-a-script"></a><span data-ttu-id="cbe31-142">Eseguire uno script</span><span class="sxs-lookup"><span data-stu-id="cbe31-142">Run a Script</span></span>
<span data-ttu-id="cbe31-143">Per eseguire uno script in uno o più computer remoti, usare il parametro FilePath del cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="cbe31-143">To run a script on one or many remote computers, use the FilePath parameter of the Invoke-Command cmdlet.</span></span> <span data-ttu-id="cbe31-144">Lo script deve essere attivo o accessibile sul computer locale.</span><span class="sxs-lookup"><span data-stu-id="cbe31-144">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="cbe31-145">I risultati vengono restituiti al computer locale.</span><span class="sxs-lookup"><span data-stu-id="cbe31-145">The results are returned to your local computer.</span></span>

<span data-ttu-id="cbe31-146">Ad esempio, il comando seguente esegue lo script DiskCollect.ps1 nei computer remoti Server01 e Server02.</span><span class="sxs-lookup"><span data-stu-id="cbe31-146">For example, the following command runs the DiskCollect.ps1 script on the Server01 and Server02 remote computers.</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

<span data-ttu-id="cbe31-147">Per altre informazioni sul cmdlet Invoke-Command, vedere [Invoke-Command](https://technet.microsoft.com/en-us/library/dd347578.aspx).</span><span class="sxs-lookup"><span data-stu-id="cbe31-147">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://technet.microsoft.com/en-us/library/dd347578.aspx).</span></span>

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="cbe31-148">Stabilire una connessione permanente</span><span class="sxs-lookup"><span data-stu-id="cbe31-148">Establish a Persistent Connection</span></span>
<span data-ttu-id="cbe31-149">Per eseguire una serie di comandi correlati che condividono dati, creare una sessione nel computer remoto e quindi usare il cmdlet Invoke-Command per eseguire i comandi nella sessione creata.</span><span class="sxs-lookup"><span data-stu-id="cbe31-149">To run a series of related commands that share data, create a session on the remote computer and then use the Invoke-Command cmdlet to run commands in the session that you create.</span></span> <span data-ttu-id="cbe31-150">Per creare una sessione remota, usare il cmdlet New-PSSession.</span><span class="sxs-lookup"><span data-stu-id="cbe31-150">To create a remote session, use the New-PSSession cmdlet.</span></span>

<span data-ttu-id="cbe31-151">Ad esempio, il comando seguente crea una sessione remota nel computer Server01 e un'altra nel computer Server02.</span><span class="sxs-lookup"><span data-stu-id="cbe31-151">For example, the following command creates a remote session on the Server01 computer and another remote session on the Server02 computer.</span></span> <span data-ttu-id="cbe31-152">Gli oggetti sessione vengono salvati nella variabile $s.</span><span class="sxs-lookup"><span data-stu-id="cbe31-152">It saves the session objects in the $s variable.</span></span>

```
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="cbe31-153">Una volta stabilite le sessioni, è possibile eseguire qualsiasi comando al loro interno.</span><span class="sxs-lookup"><span data-stu-id="cbe31-153">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="cbe31-154">Inoltre, poiché le sessioni sono permanenti, è possibile raccogliere dati in un comando e usarli in un comando successivo.</span><span class="sxs-lookup"><span data-stu-id="cbe31-154">And because the sessions are persistent, you can collect data in one command and use it in a subsequent command.</span></span>

<span data-ttu-id="cbe31-155">Ad esempio, il comando seguente esegue un comando Get-Hotfix nelle sessioni nella variabile $s e salva i risultati nella variabile $h.</span><span class="sxs-lookup"><span data-stu-id="cbe31-155">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="cbe31-156">La variabile $h viene creata in ogni sessione in $s, ma non esiste nella sessione locale.</span><span class="sxs-lookup"><span data-stu-id="cbe31-156">The $h variable is created in each of the sessions in $s, but it does not exist in the local session.</span></span>

```
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="cbe31-157">A questo punto è possibile usare i dati della variabile $h nei comandi successivi, ad esempio il seguente.</span><span class="sxs-lookup"><span data-stu-id="cbe31-157">Now you can use the data in the $h variable in subsequent commands, such as the following one.</span></span> <span data-ttu-id="cbe31-158">I risultati vengono visualizzati nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="cbe31-158">The results are displayed on the local computer.</span></span>

```
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="cbe31-159">Comunicazione remota avanzata</span><span class="sxs-lookup"><span data-stu-id="cbe31-159">Advanced Remoting</span></span>
<span data-ttu-id="cbe31-160">La gestione remota di Windows PowerShell ha inizio in questo ambito.</span><span class="sxs-lookup"><span data-stu-id="cbe31-160">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="cbe31-161">Usando i cmdlet installati con Windows PowerShell, è possibile stabilire e configurare sessioni remote dalle estremità locali e remote, creare sessioni personalizzate e con restrizioni, consentire agli utenti di importare comandi da una sessione remota che vengono effettivamente eseguiti in modo implicito nella sessione remota, configurare la sicurezza di una sessione remota e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="cbe31-161">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="cbe31-162">Per semplificare la configurazione remota, Windows PowerShell include un provider WSMan.</span><span class="sxs-lookup"><span data-stu-id="cbe31-162">To facilitate remote configuration, Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="cbe31-163">L'unità WSMAN: creata dal provider consente di spostarsi in una gerarchia di impostazioni di configurazione nel computer locale e nei computer remoti.</span><span class="sxs-lookup"><span data-stu-id="cbe31-163">The WSMAN: drive that the provider creates lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>
<span data-ttu-id="cbe31-164">Per altre informazioni sul provider di WS-Management, vedere [Provider WSMan](https://technet.microsoft.com/en-us/library/dd819476.aspx) e [about_WS-Management_Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx) oppure digitare "get-help wsman" nella console di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cbe31-164">For more information about the WSMan provider, see  [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) and [About WS-Management Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx), or in the Windows PowerShell console, type "Get-Help wsman".</span></span>

<span data-ttu-id="cbe31-165">Per altre informazioni, vedere:</span><span class="sxs-lookup"><span data-stu-id="cbe31-165">For more information, see:</span></span>
- [<span data-ttu-id="cbe31-166">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="cbe31-166">About Remote FAQ</span></span>](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [<span data-ttu-id="cbe31-167">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="cbe31-167">Register-PSSessionConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dd819496.aspx)
- <span data-ttu-id="cbe31-168">[Import-PSSession](https://technet.microsoft.com/en-us/library/dd347575.aspx).</span><span class="sxs-lookup"><span data-stu-id="cbe31-168">[Import-PSSession](https://technet.microsoft.com/en-us/library/dd347575.aspx).</span></span> 

<span data-ttu-id="cbe31-169">Per informazioni sugli errori di comunicazione remota, vedere [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="cbe31-169">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="cbe31-170">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cbe31-170">See Also</span></span>
- [<span data-ttu-id="cbe31-171">about_Remote</span><span class="sxs-lookup"><span data-stu-id="cbe31-171">about_Remote</span></span>](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="cbe31-172">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="cbe31-172">about_Remote_FAQ</span></span>](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="cbe31-173">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="cbe31-173">about_Remote_Requirements</span></span>](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="cbe31-174">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="cbe31-174">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="cbe31-175">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="cbe31-175">about_PSSessions</span></span>](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="cbe31-176">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="cbe31-176">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="cbe31-177">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="cbe31-177">Invoke-Command</span></span>](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)
- [<span data-ttu-id="cbe31-178">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="cbe31-178">Import-PSSession</span></span>](https://technet.microsoft.com/en-us/library/048c115e-a6fb-4e0d-8cea-c5ca24630c9d)
- [<span data-ttu-id="cbe31-179">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="cbe31-179">New-PSSession</span></span>](https://technet.microsoft.com/en-us/library/59452f12-a11d-4558-99ea-e6ca6ad5ffd3)
- [<span data-ttu-id="cbe31-180">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="cbe31-180">Register-PSSessionConfiguration</span></span>](https://technet.microsoft.com/en-us/library/af68867a-d201-4b19-a1de-594015ed8a25)
- [<span data-ttu-id="cbe31-181">Provider WSMan</span><span class="sxs-lookup"><span data-stu-id="cbe31-181">WSMan Provider</span></span>](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

