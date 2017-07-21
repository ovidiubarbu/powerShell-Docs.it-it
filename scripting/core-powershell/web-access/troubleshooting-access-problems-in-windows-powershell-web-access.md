---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: risoluzione dei problemi di accesso in accesso web windows powershell
ms.openlocfilehash: c10e19b177110ff62d44f28b6a523380b55b79e0
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
#  <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="b2ebd-103">Risoluzione dei problemi di accesso in Accesso Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b2ebd-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="b2ebd-104">Ultimo aggiornamento: 24 giugno 2013</span><span class="sxs-lookup"><span data-stu-id="b2ebd-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="b2ebd-105">Si applica a: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="b2ebd-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<a href="" id="BKMK_trouble"></a>

------------------------------------------------------------------------

<span data-ttu-id="b2ebd-106">La tabella seguente illustra alcuni problemi comuni che possono verificarsi quando gli utenti provano a connettersi a un computer remoto con Accesso Web Windows PowerShell e include alcuni suggerimenti per la risoluzione di tali problemi.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-106">The following table identifies some common problems that users might experience when they are attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="b2ebd-107">Problema</span><span class="sxs-lookup"><span data-stu-id="b2ebd-107">Problem</span></span></p></th>
<th><p><span data-ttu-id="b2ebd-108">Possibile causa e soluzione</span><span class="sxs-lookup"><span data-stu-id="b2ebd-108">Possible cause and solution</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="b2ebd-109">Errore di accesso</span><span class="sxs-lookup"><span data-stu-id="b2ebd-109">Sign-in failure</span></span></p></td>
<td><p><span data-ttu-id="b2ebd-110">Il problema può essere dovuto a uno dei motivi seguenti.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-110">Failure could occur because of any of the following.</span></span></p>
<ul>
<li><p><span data-ttu-id="b2ebd-111">Non esiste una regola di autorizzazione che consenta all'utente di accedere al computer o a una configurazione di sessione specifica sul computer remoto.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-111">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span> <span data-ttu-id="b2ebd-112">La sicurezza di Accesso Web Windows PowerShell è restrittiva, quindi è necessario consentire esplicitamente agli utenti l'accesso ai computer remoti, usando le regole di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-112">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span> <span data-ttu-id="b2ebd-113">Per altre informazioni sulla creazione delle regole di autorizzazione, vedere la sezione <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell</a> in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-113">For more information about creating authorization rules, see <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a> in this guide.</span></span></p></li>
<li><p><span data-ttu-id="b2ebd-114">L'utente non è autorizzato ad accedere al computer di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-114">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="b2ebd-115">Tale autorizzazione è determinata dagli elenchi di controllo di accesso (ACL).</span><span class="sxs-lookup"><span data-stu-id="b2ebd-115">This is determined by access control lists (ACLs).</span></span> <span data-ttu-id="b2ebd-116">Per altre informazioni, vedere la sezione "Connessione ad Accesso Web Windows PowerShell" dell'articolo <a href="https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx">Usare la console di Windows PowerShell basata sul Web</a> o consultare il <a href="https://msdn.microsoft.com/library/windows/desktop/ee706585.aspx">blog del team di Windows PowerShell</a>.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-116">For more information, see “Signing in to Windows PowerShell Web Access” in <a href="https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx">Use the Web-based Windows PowerShell Console</a>, or the <a href="https://msdn.microsoft.com/library/windows/desktop/ee706585.aspx">Windows PowerShell Team Blog</a>.</span></span></p>
<ul>
<li><p><span data-ttu-id="b2ebd-117">La gestione remota di Windows PowerShell potrebbe non essere abilitata nel computer di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-117">Windows PowerShell remote management might not be enabled on the destination computer.</span></span> <span data-ttu-id="b2ebd-118">Verificare che tale funzione sia abilitata nel computer a cui l'utente sta tentando di connettersi.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-118">Verify that it is enabled on the computer to which the user is trying to connect.</span></span> <span data-ttu-id="b2ebd-119">Per altre informazioni, vedere la sezione "Modalità di configurazione del computer per la comunicazione remota" dell'argomento <a href="https://technet.microsoft.com/library/dd315349.aspx">about_Remote_Requirements</a> negli argomenti della Guida di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-119">For more information, see “How to Configure Your Computer for Remoting” in <a href="https://technet.microsoft.com/library/dd315349.aspx">about_Remote_Requirements</a> in the Windows PowerShell About Help Topics.</span></span></p></li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b2ebd-120">Quando gli utenti provano a connettersi a Accesso Web Windows PowerShell da una finestra di Internet Explorer, viene visualizzata una pagina di <strong>Errore interno del server</strong> oppure Internet Explorer smette di rispondere.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-120">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an <strong>Internal Server Error</strong> page, or Internet Explorer stops responding.</span></span> <span data-ttu-id="b2ebd-121">Si tratta di un problema specifico di Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-121">This issue is specific to Internet Explorer.</span></span></p></td>
<td><p><span data-ttu-id="b2ebd-122">Questo problema può verificarsi per gli utenti che effettuano l'accesso con un nome di dominio contenente caratteri cinesi, oppure se il nome del server gateway contiene uno o più caratteri cinesi.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span> <span data-ttu-id="b2ebd-123">Per risolvere il problema, l'utente deve <a href="http://ie.microsoft.com/testdrive/info/downloads/Default.html">installare ed eseguire Internet Explorer 10</a>, quindi effettuare la procedura seguente.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-123">To work around this issue, the user should <a href="http://ie.microsoft.com/testdrive/info/downloads/Default.html">install and run Internet Explorer 10</a>, and then perform the following steps.</span></span></p>
<ol>
<li><p><span data-ttu-id="b2ebd-124">Impostare su <strong>Standard di IE10</strong> la <strong>Modalità documento</strong> di Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-124">Change the Internet Explorer <strong>Document Mode</strong> setting to <strong>IE10 standards</strong>.</span></span></p>
<ol>
<li><p><span data-ttu-id="b2ebd-125">Premere <strong>F12</strong> per aprire la console degli strumenti di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-125">Press <strong>F12</strong> to open the Developer Tools console.</span></span></p></li>
<li><p><span data-ttu-id="b2ebd-126">In Internet Explorer 10 fare clic su <strong>Modalità browser</strong> e selezionare <strong>Internet Explorer 10</strong>.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-126">In Internet Explorer 10, click <strong>Browser Mode</strong>, and then select <strong>Internet Explorer 10</strong>.</span></span></p></li>
<li><p><span data-ttu-id="b2ebd-127">Fare clic su <strong>Modalità documento</strong> e fare clic su <strong>Standard di IE10</strong>.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-127">Click <strong>Document Mode</strong>, and then click <strong>IE10 standards</strong>.</span></span></p></li>
<li><p><span data-ttu-id="b2ebd-128">Premere di nuovo <strong>F12</strong> per chiudere la console degli strumenti di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-128">Press <strong>F12</strong> again to close the Developer Tools console.</span></span></p></li>
</ol></li>
<li><p><span data-ttu-id="b2ebd-129">Disabilitare la configurazione automatica del proxy.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-129">Disable automatic proxy configuration.</span></span></p>
<ol>
<li><p><span data-ttu-id="b2ebd-130">In Internet Explorer 10 scegliere <strong>Opzioni Internet</strong> dal menu <strong>Strumenti</strong>.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-130">In Internet Explorer 10, click <strong>Tools</strong>, and then click <strong>Internet Options</strong>.</span></span></p></li>
<li><p><span data-ttu-id="b2ebd-131">Nella finestra di dialogo <strong>Opzioni Internet</strong> passare alla scheda <strong>Connessioni</strong> e fare clic su <strong>Impostazioni LAN</strong>.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-131">In the <strong>Internet Options</strong> dialog box, on the <strong>Connections</strong> tab, click <strong>LAN settings</strong>.</span></span></p></li>
<li><p><span data-ttu-id="b2ebd-132">Deselezionare la casella di controllo <strong>Rileva automaticamente impostazioni</strong>.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-132">Clear the <strong>Automatically detect settings</strong> check box.</span></span> <span data-ttu-id="b2ebd-133">Fare clic su <strong>OK</strong>, quindi fare di nuovo clic su <strong>OK</strong> per chiudere la finestra di dialogo <strong>Opzioni Internet</strong>.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-133">Click <strong>OK</strong>, and then click <strong>OK</strong> again to close the <strong>Internet Options</strong> dialog box.</span></span></p></li>
</ol></li>
</ol></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b2ebd-134">Non è possibile connettersi a un computer remoto del gruppo di lavoro</span><span class="sxs-lookup"><span data-stu-id="b2ebd-134">Cannot connect to a remote workgroup computer</span></span></p></td>
<td><p><span data-ttu-id="b2ebd-135">Se il computer di destinazione è membro di un gruppo di lavoro, usare la sintassi seguente per fornire il nome utente e accedere al computer: &lt;<em>nome_gruppo_di_lavoro</em>&gt;\&lt;<em>nome_utente</em>&gt;</span><span class="sxs-lookup"><span data-stu-id="b2ebd-135">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: &lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b2ebd-136">Non è possibile trovare gli strumenti di gestione del server Web (IIS) anche se il ruolo corrispondente è stato installato</span><span class="sxs-lookup"><span data-stu-id="b2ebd-136">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span></p></td>
<td><p><span data-ttu-id="b2ebd-137">Se Accesso Web Windows PowerShell viene installato con il cmdlet <span class="code">Install-WindowsFeature</span>, gli strumenti di gestione non vengono installati, a meno che non si aggiunga il parametro <span class="code">IncludeManagementTools</span> al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-137">If you installed Windows PowerShell Web Access by using the <span class="code">Install-WindowsFeature</span> cmdlet, management tools are not installed unless the <span class="code">IncludeManagementTools</span> parameter is added to the cmdlet.</span></span> <span data-ttu-id="b2ebd-138">Per un esempio, vedere la sezione relativa all'installazione di Accesso Web Windows PowerShell con i cmdlet di Windows PowerShell in <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Installare e usare Accesso Web Windows PowerShell</a>.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-138">For an example, see “To install Windows PowerShell Web Access by using Windows PowerShell cmdlets” in <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Install and Use Windows PowerShell Web Access</a>.</span></span> <span data-ttu-id="b2ebd-139">Per aggiungere la console Gestione IIS e altri strumenti di gestione di IIS necessari, selezionarli in una sessione di Aggiunta guidata ruoli e funzionalità aperta con il server gateway.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-139">You can add the IIS Manager console and other IIS management tools that you need by selecting the tools in an Add Roles and Features Wizard session that is targeted at the gateway server.</span></span> <span data-ttu-id="b2ebd-140">L'Aggiunta guidata ruoli e funzionalità viene aperta in Server Manager.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-140">The Add Roles and Features Wizard is opened from within Server Manager.</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b2ebd-141">Il sito Web di Accesso Web Windows PowerShell non è accessibile</span><span class="sxs-lookup"><span data-stu-id="b2ebd-141">The Windows PowerShell Web Access website is not accessible</span></span></p></td>
<td><p><span data-ttu-id="b2ebd-142">Se in Internet Explorer è abilitata la funzione Configurazione sicurezza avanzata, è possibile aggiungere il sito Web di Accesso Web Windows PowerShell all'elenco dei siti attendibili o disabilitare la funzione.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-142">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites, or disable IE ESC.</span></span> <span data-ttu-id="b2ebd-143">È possibile disabilitare Sicurezza avanzata di Internet Explorer nel riquadro <strong>Proprietà</strong> della pagina <strong>Server locale</strong> in Server Manager.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-143">You can disable IE ESC in the <strong>Properties</strong> tile on the <strong>Local Server</strong> page in Server Manager.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b2ebd-144">Il messaggio di errore seguente viene visualizzato quando si prova a stabilire una connessione e il computer di destinazione è il server gateway ed è anche incluso in un gruppo di lavoro: <strong>Errore di autorizzazione. Verificare di essere autorizzati a connettersi al computer di destinazione.</strong></span><span class="sxs-lookup"><span data-stu-id="b2ebd-144">The following error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup: <strong>An authorization failure occurred. Verify that you are authorized to connect to the destination computer.</strong></span></span></p></td>
<td><p><span data-ttu-id="b2ebd-145">Se il server di destinazione è costituito dal server gateway e quest'ultimo è incluso in un gruppo di lavoro, specificare il nome dell'utente, il nome del computer e il nome del gruppo di utenti come mostrato nella tabella seguente,</span><span class="sxs-lookup"><span data-stu-id="b2ebd-145">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name as shown in the following table.</span></span> <span data-ttu-id="b2ebd-146">evitando di usare solo un punto (.) per rappresentare il nome del computer.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-146">Do not use a dot (.) by itself to represent the computer name.</span></span></p>
<div>
<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="b2ebd-147">Scenario</span><span class="sxs-lookup"><span data-stu-id="b2ebd-147">Scenario</span></span></p></th>
<th><p><span data-ttu-id="b2ebd-148">Parametro UserName</span><span class="sxs-lookup"><span data-stu-id="b2ebd-148">UserName Parameter</span></span></p></th>
<th><p><span data-ttu-id="b2ebd-149">Parametro UserGroup</span><span class="sxs-lookup"><span data-stu-id="b2ebd-149">UserGroup Parameter</span></span></p></th>
<th><p><span data-ttu-id="b2ebd-150">Parametro ComputerName</span><span class="sxs-lookup"><span data-stu-id="b2ebd-150">ComputerName Parameter</span></span></p></th>
<th><p><span data-ttu-id="b2ebd-151">Parametro ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="b2ebd-151">ComputerGroup Parameter</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="b2ebd-152">Il server gateway è in un dominio</span><span class="sxs-lookup"><span data-stu-id="b2ebd-152">Gateway server is in a domain</span></span></p></td>
<td><p><span data-ttu-id="b2ebd-153"><em>Nome_server</em>\<em>nome_utente</em>, Localhost\<em>nome_utente</em> o .\<em>nome_utente</em></span><span class="sxs-lookup"><span data-stu-id="b2ebd-153"><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em>, or .\<em>user_name</em></span></span></p></td>
<td><p><span data-ttu-id="b2ebd-154"><em>Nome_server</em>\<em>gruppo_utenti</em>, Localhost\<em>gruppo_utenti</em> o .\<em>gruppo_utenti</em></span><span class="sxs-lookup"><span data-stu-id="b2ebd-154"><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em>, or .\<em>user_group</em></span></span></p></td>
<td><p><span data-ttu-id="b2ebd-155">Nome completo del server gateway o Localhost</span><span class="sxs-lookup"><span data-stu-id="b2ebd-155">Fully qualified name of gateway server, or Localhost</span></span></p></td>
<td><p><span data-ttu-id="b2ebd-156"><em>Nome_server</em>\<em>gruppo_computer</em>, Localhost\<em>gruppo_computer</em> o .\<em>gruppo_computer</em></span><span class="sxs-lookup"><span data-stu-id="b2ebd-156"><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em>, or .\<em>computer_group</em></span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b2ebd-157">Il server gateway è in un gruppo di lavoro</span><span class="sxs-lookup"><span data-stu-id="b2ebd-157">Gateway server is in a workgroup</span></span></p></td>
<td><p><span data-ttu-id="b2ebd-158"><em>Nome_server</em>\<em>nome_utente</em>, Localhost\<em>nome_utente</em> o .\<em>nome_utente</em></span><span class="sxs-lookup"><span data-stu-id="b2ebd-158"><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em>, or .\<em>user_name</em></span></span></p></td>
<td><p><span data-ttu-id="b2ebd-159"><em>Nome_server</em>\<em>gruppo_utenti</em>, Localhost\<em>gruppo_utenti</em> o .\<em>gruppo_utenti</em></span><span class="sxs-lookup"><span data-stu-id="b2ebd-159"><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em> or .\<em>user_group</em></span></span></p></td>
<td><p><span data-ttu-id="b2ebd-160">Nome server</span><span class="sxs-lookup"><span data-stu-id="b2ebd-160">Server name</span></span></p></td>
<td><p><span data-ttu-id="b2ebd-161"><em>Nome_server</em>\<em>gruppo_computer</em>, Localhost\<em>gruppo_computer</em> o .\<em>gruppo_computer</em></span><span class="sxs-lookup"><span data-stu-id="b2ebd-161"><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em> or .\<em>computer_group</em></span></span></p></td>
</tr>
</tbody>
</table>
</div>
<p><span data-ttu-id="b2ebd-162">Effettuare l'accesso specificando il server gateway come computer di destinazione e utilizzando credenziali formattate in uno dei modi seguenti.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-162">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span></p>
<ul>
<li><p><span data-ttu-id="b2ebd-163"><em>Nome_server</em>\<em>nome_utente</em></span><span class="sxs-lookup"><span data-stu-id="b2ebd-163"><em>Server_name</em>\<em>user_name</em></span></span></p></li>
<li><p><span data-ttu-id="b2ebd-164">Localhost\<em>nome_utente</em></span><span class="sxs-lookup"><span data-stu-id="b2ebd-164">Localhost\<em>user_name</em></span></span></p></li>
<li><p><span data-ttu-id="b2ebd-165">.\<em>nome_utente</em></span><span class="sxs-lookup"><span data-stu-id="b2ebd-165">.\<em>user_name</em></span></span></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b2ebd-166">In una regola di autorizzazione, al posto della sintassi <em>nome_utente</em>/<em>nome_computer</em>  viene visualizzato un ID di sicurezza (SID)</span><span class="sxs-lookup"><span data-stu-id="b2ebd-166">A security identifier (SID) is displayed in an authorization rule instead of the syntax <em>user_name</em>/<em>computer_name</em> </span></span></p></td>
<td><p><span data-ttu-id="b2ebd-167">La regola non è più valida o la query in Servizi di dominio Active Directory non è riuscita.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-167">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span> <span data-ttu-id="b2ebd-168">In genere, una regola di autorizzazione non risulta valida nel caso in cui un server gateway che in precedenza apparteneva a un gruppo di lavoro venga aggiunto a un dominio.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-168">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b2ebd-169">Non è possibile accedere a un computer di destinazione che nelle regole di autorizzazione è stato specificato sotto forma di indirizzo IPv6 di dominio</span><span class="sxs-lookup"><span data-stu-id="b2ebd-169">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span></p></td>
<td><p><span data-ttu-id="b2ebd-170">Le regole di autorizzazione non supportano gli indirizzi IPv6 nel formato dei nomi di dominio.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-170">Authorization rules do not support an IPv6 address in form of a domain name.</span></span> <span data-ttu-id="b2ebd-171">Per specificare un computer di destinazione tramite un indirizzo IPv6, nella regola di autorizzazione utilizzare l'indirizzo IPv6 originale, che contiene due punti (:).</span><span class="sxs-lookup"><span data-stu-id="b2ebd-171">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span> <span data-ttu-id="b2ebd-172">Sia i nomi di dominio che gli indirizzi IPv6 in formato numerico, ovvero con i due punti (:) sono supportati come nome del computer di destinazione nella pagina di accesso di Accesso Web Windows PowerShell, ma non nelle regole di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-172">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span> <span data-ttu-id="b2ebd-173">Per altre informazioni sugli indirizzi IPv6, vedere l'articolo <a href="https://technet.microsoft.com/library/cc781672.aspx">Funzionamento di IPv6</a>.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-173">For more information about IPv6 addresses, see <a href="https://technet.microsoft.com/library/cc781672.aspx">How IPv6 Works</a>.</span></span></p></td>
</tr>
</tbody>
</table><span data-ttu-id="b2ebd-174">

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Vedere anche</span></a>
<a href="/en-us/library/dn282395(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="b2ebd-174">

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/dn282395(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="b2ebd-175">[Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
[Usare la console di Windows PowerShell basata sul Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
[about_Remote_Requirements](https://technet.microsoft.com/library/dd315349.aspx)</span><span class="sxs-lookup"><span data-stu-id="b2ebd-175">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
[about_Remote_Requirements](https://technet.microsoft.com/library/dd315349.aspx)</span></span>

<span data-ttu-id="b2ebd-176"><span>Show:</span> Inherited Protected</span><span class="sxs-lookup"><span data-stu-id="b2ebd-176"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="b2ebd-177"><span class="stdr-votetitle">Questa pagina è stata utile?</span></span><span class="sxs-lookup"><span data-stu-id="b2ebd-177"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="b2ebd-178">Sì No</span><span class="sxs-lookup"><span data-stu-id="b2ebd-178">Yes No</span></span>

<span data-ttu-id="b2ebd-179">Altri suggerimenti?</span><span class="sxs-lookup"><span data-stu-id="b2ebd-179">Additional feedback?</span></span>

<span data-ttu-id="b2ebd-180"><span class="stdr-count"><span class="stdr-charcnt">1500</span> caratteri rimanenti</span> Invia Ignora</span><span class="sxs-lookup"><span data-stu-id="b2ebd-180"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="b2ebd-181"><span class="stdr-thankyou">Grazie</span></span><span class="sxs-lookup"><span data-stu-id="b2ebd-181"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="b2ebd-182"><span class="stdr-appreciate">I suggerimenti degli utenti sono importanti.</span></span><span class="sxs-lookup"><span data-stu-id="b2ebd-182"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="b2ebd-183">Gestisci il tuo profilo</span><span class="sxs-lookup"><span data-stu-id="b2ebd-183">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="b2ebd-184"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Commenti e suggerimenti sul sito</a> Commenti e suggerimenti sul sito</span><span class="sxs-lookup"><span data-stu-id="b2ebd-184"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="b2ebd-185"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="b2ebd-185"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="b2ebd-186">Raccontaci la tua esperienza</span><span class="sxs-lookup"><span data-stu-id="b2ebd-186">Tell us about your experience...</span></span>

<span data-ttu-id="b2ebd-187">La pagina è stata caricata rapidamente?</span><span class="sxs-lookup"><span data-stu-id="b2ebd-187">Did the page load quickly?</span></span>

<span data-ttu-id="b2ebd-188"><span> Sì<span> </span></span> <span> No<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="b2ebd-188"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="b2ebd-189">Ti piace la grafica?</span><span class="sxs-lookup"><span data-stu-id="b2ebd-189">Do you like the page design?</span></span>

<span data-ttu-id="b2ebd-190"><span> Sì<span> </span></span> <span> No<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="b2ebd-190"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="b2ebd-191">Parla con noi</span><span class="sxs-lookup"><span data-stu-id="b2ebd-191">Tell us more</span></span>

-   [<span data-ttu-id="b2ebd-192">Newsletter Flash</span><span class="sxs-lookup"><span data-stu-id="b2ebd-192">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="b2ebd-193">Contattaci</span><span class="sxs-lookup"><span data-stu-id="b2ebd-193">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="b2ebd-194">Informativa sulla privacy</span><span class="sxs-lookup"><span data-stu-id="b2ebd-194">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="b2ebd-195">Condizioni per l'utilizzo</span><span class="sxs-lookup"><span data-stu-id="b2ebd-195">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="b2ebd-196">Marchi</span><span class="sxs-lookup"><span data-stu-id="b2ebd-196">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="b2ebd-197">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="b2ebd-197">© 2016 Microsoft</span></span>

<span data-ttu-id="b2ebd-198">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="b2ebd-198">© 2016 Microsoft</span></span>

<span data-ttu-id="b2ebd-199">Il codice e gli script di terze parti, collegati al presente sito o a cui il sito Web fa riferimento, vengono ceduti in licenza all'utente dalle terze parti proprietarie di tale codice, non da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-199">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="b2ebd-200">Vedere le condizioni d'uso di Ajax CDN di ASP.NET – http://www.asp.net/ajaxlibrary/CDN.ashx.</span><span class="sxs-lookup"><span data-stu-id="b2ebd-200">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

