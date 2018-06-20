---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: risoluzione dei problemi di accesso in accesso web windows powershell
ms.openlocfilehash: ef476d8e386e5380cb2c9dda69180dfce8748bf4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953447"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="c6acb-103">Risoluzione dei problemi di accesso in Accesso Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c6acb-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="c6acb-104">Aggiornamento: 24 giugno 2013 (revisione: 23 agosto 2017)</span><span class="sxs-lookup"><span data-stu-id="c6acb-104">Updated: June 24, 2013 (revised August 23, 2017)</span></span>

<span data-ttu-id="c6acb-105">Si applica a: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="c6acb-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="c6acb-106">Le sezioni seguenti illustrano alcuni problemi comuni che possono verificarsi quando si prova a connettersi a un computer remoto con Accesso Web Windows PowerShell e includono alcuni suggerimenti per la risoluzione di tali problemi.</span><span class="sxs-lookup"><span data-stu-id="c6acb-106">The following sections identify some common problems when attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

## <a name="sign-in-failure"></a><span data-ttu-id="c6acb-107">Errore di accesso</span><span class="sxs-lookup"><span data-stu-id="c6acb-107">Sign-in failure</span></span>

<span data-ttu-id="c6acb-108">Il problema può essere dovuto a uno dei motivi seguenti.</span><span class="sxs-lookup"><span data-stu-id="c6acb-108">Failure could occur because of any of the following.</span></span>

- <span data-ttu-id="c6acb-109">Non esiste una regola di autorizzazione che consenta all'utente di accedere al computer o a una configurazione di sessione specifica sul computer remoto.</span><span class="sxs-lookup"><span data-stu-id="c6acb-109">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span>

  <span data-ttu-id="c6acb-110">La sicurezza di Accesso Web Windows PowerShell è restrittiva, quindi è necessario consentire esplicitamente agli utenti l'accesso ai computer remoti, usando le regole di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="c6acb-110">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span>

  <span data-ttu-id="c6acb-111">Per altre informazioni sulla creazione delle regole di autorizzazione, vedere [Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="c6acb-111">For more information about creating authorization rules, see [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span></span>

- <span data-ttu-id="c6acb-112">L'utente non è autorizzato ad accedere al computer di destinazione.</span><span class="sxs-lookup"><span data-stu-id="c6acb-112">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="c6acb-113">Tale autorizzazione è determinata dagli elenchi di controllo di accesso (ACL).</span><span class="sxs-lookup"><span data-stu-id="c6acb-113">This is determined by access control lists (ACLs).</span></span>

  <span data-ttu-id="c6acb-114">Per altre informazioni, vedere [Connessione ad Accesso Web Windows PowerShell](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access) o il blog del team di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c6acb-114">For more information, see [Signing in to Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), or the Windows PowerShell Team Blog.</span></span>

- <span data-ttu-id="c6acb-115">La gestione remota di Windows PowerShell potrebbe non essere abilitata nel computer di destinazione.</span><span class="sxs-lookup"><span data-stu-id="c6acb-115">Windows PowerShell remote management might not be enabled on the destination computer.</span></span>

  <span data-ttu-id="c6acb-116">Verificare che tale funzione sia abilitata nel computer a cui l'utente sta tentando di connettersi.</span><span class="sxs-lookup"><span data-stu-id="c6acb-116">Verify remote management is enabled on the computer to which the user is trying to connect.</span></span>

  <span data-ttu-id="c6acb-117">Per altre informazioni, vedere [How to Configure Your Computer for Remoting](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting) (Come configurare il computer per la comunicazione remota).</span><span class="sxs-lookup"><span data-stu-id="c6acb-117">For more information, see [How to Configure Your Computer for Remoting](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span></span>

## <a name="internal-server-error"></a><span data-ttu-id="c6acb-118">Errore interno del server</span><span class="sxs-lookup"><span data-stu-id="c6acb-118">Internal Server Error</span></span>

<span data-ttu-id="c6acb-119">Quando gli utenti provano a connettersi ad Accesso Web Windows PowerShell da una finestra di Internet Explorer, viene visualizzata una pagina di **Errore interno del server** oppure *Internet Explorer* smette di rispondere.</span><span class="sxs-lookup"><span data-stu-id="c6acb-119">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an **Internal Server Error** page, or *Internet Explorer* stops responding.</span></span>

<span data-ttu-id="c6acb-120">Si tratta di un problema specifico di Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="c6acb-120">This issue is specific to Internet Explorer.</span></span>

### <a name="possible-cause"></a><span data-ttu-id="c6acb-121">Possibile causa</span><span class="sxs-lookup"><span data-stu-id="c6acb-121">Possible cause</span></span>

<span data-ttu-id="c6acb-122">Questo problema può verificarsi per gli utenti che effettuano l'accesso con un nome di dominio contenente caratteri cinesi, oppure se il nome del server gateway contiene uno o più caratteri cinesi.</span><span class="sxs-lookup"><span data-stu-id="c6acb-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span>

#### <a name="workaround"></a><span data-ttu-id="c6acb-123">Soluzione alternativa</span><span class="sxs-lookup"><span data-stu-id="c6acb-123">Workaround</span></span>

1. [<span data-ttu-id="c6acb-124">Installare ed eseguire Internet Explorer 10</span><span class="sxs-lookup"><span data-stu-id="c6acb-124">Install and run Internet Explorer 10</span></span>](http://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. <span data-ttu-id="c6acb-125">Modificare la **modalità documento** di Internet Explorer impostando gli standard *IE10*.</span><span class="sxs-lookup"><span data-stu-id="c6acb-125">Change Internet Explorer **Document Mode** setting to *IE10* standards.</span></span>
   1. <span data-ttu-id="c6acb-126">Premere **F12** per aprire la console di Strumenti di sviluppo</span><span class="sxs-lookup"><span data-stu-id="c6acb-126">Press **F12** to open the Developer Tools console</span></span>
   1. <span data-ttu-id="c6acb-127">In Internet Explorer 10 fare clic su **Modalità browser** e selezionare *Internet Explorer 10*.</span><span class="sxs-lookup"><span data-stu-id="c6acb-127">In Internet Explorer 10, click **Browser Mode**, and then select *Internet Explorer 10*.</span></span>
   1. <span data-ttu-id="c6acb-128">Fare clic su **Modalità documento** e selezionare gli standard *IE10*.</span><span class="sxs-lookup"><span data-stu-id="c6acb-128">Click **Document Mode**, and then click *IE10* standards.</span></span>
   1. <span data-ttu-id="c6acb-129">Premere di nuovo **F12** per chiudere la console degli strumenti di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="c6acb-129">Press **F12** again to close the Developer Tools console.</span></span>
1. <span data-ttu-id="c6acb-130">Disabilitare la configurazione automatica in Internet Explorer 10.</span><span class="sxs-lookup"><span data-stu-id="c6acb-130">Disable automatic proxy configuration in Internet Explorer 10.</span></span>
   1. <span data-ttu-id="c6acb-131">Scegliere **Opzioni Internet**dal menu **Strumenti**.</span><span class="sxs-lookup"><span data-stu-id="c6acb-131">Click **Tools**, and then click **Internet Options**.</span></span>
   1. <span data-ttu-id="c6acb-132">Nella finestra di dialogo **Opzioni Internet** passare alla scheda **Connessioni** e fare clic su **Impostazioni LAN**.</span><span class="sxs-lookup"><span data-stu-id="c6acb-132">In the **Internet Options** dialog box, on the **Connections** tab, click **LAN settings**.</span></span>
   1. <span data-ttu-id="c6acb-133">Deselezionare la casella di controllo **Rileva automaticamente impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="c6acb-133">Clear the **Automatically detect settings** check box.</span></span> <span data-ttu-id="c6acb-134">Fare clic su **OK**, quindi fare di nuovo clic su **OK** per chiudere la finestra di dialogo *Opzioni Internet*.</span><span class="sxs-lookup"><span data-stu-id="c6acb-134">Click **OK**, and then click **OK** again to close the *Internet Options* dialog box.</span></span>

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a><span data-ttu-id="c6acb-135">Non è possibile connettersi a un computer remoto del gruppo di lavoro</span><span class="sxs-lookup"><span data-stu-id="c6acb-135">Cannot connect to a remote workgroup computer</span></span>

<span data-ttu-id="c6acb-136">Se il computer di destinazione fa parte di un gruppo di lavoro, usare la sintassi seguente per specificare il nome utente e accedere al computer: `<workgroup_name>\<user_name>`</span><span class="sxs-lookup"><span data-stu-id="c6acb-136">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: `<workgroup_name>\<user_name>`</span></span>

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a><span data-ttu-id="c6acb-137">Non è possibile trovare gli strumenti di gestione del server Web (IIS) anche se il ruolo corrispondente è stato installato</span><span class="sxs-lookup"><span data-stu-id="c6acb-137">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span>

<span data-ttu-id="c6acb-138">Se Accesso Web Windows PowerShell viene installato tramite il cmdlet `Install-WindowsFeature`, gli strumenti di gestione non vengono installati, a meno che non si aggiunga il parametro `-IncludeManagementTools` al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c6acb-138">If you installed Windows PowerShell Web Access by using the `Install-WindowsFeature` cmdlet, management tools are not installed unless the `-IncludeManagementTools` parameter is added to the cmdlet.</span></span>

<span data-ttu-id="c6acb-139">Per un esempio, vedere [Per installare Accesso Web Windows PowerShell tramite i cmdlet di Windows PowerShell](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="c6acb-139">For an example, see [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span></span>

<span data-ttu-id="c6acb-140">Per aggiungere la console Gestione IIS e altri strumenti di gestione di IIS necessari, selezionarli in una sessione di **Aggiunta guidata ruoli e funzionalità** che ha come destinazione il server gateway.</span><span class="sxs-lookup"><span data-stu-id="c6acb-140">You can add the IIS Manager console, and other IIS management tools that you need, by selecting the tools in an **Add Roles and Features Wizard** session that is targeted at the gateway server.</span></span>
<span data-ttu-id="c6acb-141">L'Aggiunta guidata ruoli e funzionalità viene aperta in Server Manager.</span><span class="sxs-lookup"><span data-stu-id="c6acb-141">The Add Roles and Features Wizard is opened from within Server Manager.</span></span>

## <a name="windows-powershell-web-access-website-is-not-accessible"></a><span data-ttu-id="c6acb-142">Il sito Web di Accesso Web Windows PowerShell non è accessibile</span><span class="sxs-lookup"><span data-stu-id="c6acb-142">Windows PowerShell Web Access website is not accessible</span></span>

<span data-ttu-id="c6acb-143">Se in Internet Explorer è abilitata la Sicurezza avanzata, è possibile aggiungere il sito Web di Accesso Web Windows PowerShell all'elenco dei siti attendibili.</span><span class="sxs-lookup"><span data-stu-id="c6acb-143">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites.</span></span>

<span data-ttu-id="c6acb-144">Oppure è possibile disabilitare la Sicurezza avanzata di Internet Explorer, anche se, visti i rischi di sicurezza, non è un approccio molto consigliato.</span><span class="sxs-lookup"><span data-stu-id="c6acb-144">A less recommended approach, due to security risks, is to disable IE ESC.</span></span>
<span data-ttu-id="c6acb-145">È possibile disabilitare la Sicurezza avanzata di Internet Explorer nel riquadro Proprietà della pagina Server locale in Server Manager.</span><span class="sxs-lookup"><span data-stu-id="c6acb-145">You can disable IE ESC in the Properties tile on the Local Server page in Server Manager.</span></span>

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a><span data-ttu-id="c6acb-146">Errore di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="c6acb-146">An authorization failure occurred.</span></span> <span data-ttu-id="c6acb-147">Verificare di essere autorizzati a connettersi al computer di destinazione.</span><span class="sxs-lookup"><span data-stu-id="c6acb-147">Verify that you are authorized to connect to the destination computer.</span></span>

<span data-ttu-id="c6acb-148">Il messaggio di errore precedente viene visualizzato quando si prova a stabilire una connessione e il server gateway è il computer di destinazione ed è anche incluso in un gruppo di lavoro.</span><span class="sxs-lookup"><span data-stu-id="c6acb-148">The above error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup.</span></span>

<span data-ttu-id="c6acb-149">Se il server gateway è anche il server di destinazione, ed è incluso in un gruppo di lavoro, specificare il nome dell'utente, il nome del computer e il nome del gruppo di utenti,</span><span class="sxs-lookup"><span data-stu-id="c6acb-149">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name.</span></span>
<span data-ttu-id="c6acb-150">evitando di usare solo un punto (.) per rappresentare il nome del computer.</span><span class="sxs-lookup"><span data-stu-id="c6acb-150">Do not use a dot (.) by itself to represent the computer name.</span></span>

### <a name="scenarios-and-proper-values"></a><span data-ttu-id="c6acb-151">Scenari e i valori validi</span><span class="sxs-lookup"><span data-stu-id="c6acb-151">Scenarios and proper values</span></span>

#### <a name="all-cases"></a><span data-ttu-id="c6acb-152">Tutti i casi</span><span class="sxs-lookup"><span data-stu-id="c6acb-152">All cases</span></span>

<span data-ttu-id="c6acb-153">Parametro</span><span class="sxs-lookup"><span data-stu-id="c6acb-153">Parameter</span></span> | <span data-ttu-id="c6acb-154">Value</span><span class="sxs-lookup"><span data-stu-id="c6acb-154">Value</span></span>
-- | --
<span data-ttu-id="c6acb-155">UserName</span><span class="sxs-lookup"><span data-stu-id="c6acb-155">UserName</span></span> | <span data-ttu-id="c6acb-156">Server\_name\\user\_name</span><span class="sxs-lookup"><span data-stu-id="c6acb-156">Server\_name\\user\_name</span></span><br/><span data-ttu-id="c6acb-157">Localhost\\user\_name</span><span class="sxs-lookup"><span data-stu-id="c6acb-157">Localhost\\user\_name</span></span><br/><span data-ttu-id="c6acb-158">.\\user\_name</span><span class="sxs-lookup"><span data-stu-id="c6acb-158">.\\user\_name</span></span>
<span data-ttu-id="c6acb-159">UserGroup</span><span class="sxs-lookup"><span data-stu-id="c6acb-159">UserGroup</span></span> | <span data-ttu-id="c6acb-160">Server\_name\\user\_group</span><span class="sxs-lookup"><span data-stu-id="c6acb-160">Server\_name\\user\_group</span></span><br/><span data-ttu-id="c6acb-161">Localhost\\user\_group</span><span class="sxs-lookup"><span data-stu-id="c6acb-161">Localhost\\user\_group</span></span><br/><span data-ttu-id="c6acb-162">.\\user\_group</span><span class="sxs-lookup"><span data-stu-id="c6acb-162">.\\user\_group</span></span>
<span data-ttu-id="c6acb-163">ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="c6acb-163">ComputerGroup</span></span> | <span data-ttu-id="c6acb-164">Server\_name\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="c6acb-164">Server\_name\\computer\_group</span></span><br/><span data-ttu-id="c6acb-165">Localhost\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="c6acb-165">Localhost\\computer\_group</span></span><br/><span data-ttu-id="c6acb-166">.\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="c6acb-166">.\\computer\_group</span></span>

#### <a name="gateway-server-is-in-a-domain"></a><span data-ttu-id="c6acb-167">Il server gateway è in un dominio</span><span class="sxs-lookup"><span data-stu-id="c6acb-167">Gateway server is in a domain</span></span>

<span data-ttu-id="c6acb-168">Parametro</span><span class="sxs-lookup"><span data-stu-id="c6acb-168">Parameter</span></span> | <span data-ttu-id="c6acb-169">Value</span><span class="sxs-lookup"><span data-stu-id="c6acb-169">Value</span></span>
-- | --
<span data-ttu-id="c6acb-170">ComputerName</span><span class="sxs-lookup"><span data-stu-id="c6acb-170">ComputerName</span></span> | <span data-ttu-id="c6acb-171">Nome completo del server gateway o Localhost</span><span class="sxs-lookup"><span data-stu-id="c6acb-171">Fully qualified name of gateway server, or Localhost</span></span>

#### <a name="gateway-server-is-in-a-workgroup"></a><span data-ttu-id="c6acb-172">Il server gateway è in un gruppo di lavoro</span><span class="sxs-lookup"><span data-stu-id="c6acb-172">Gateway server is in a workgroup</span></span>

<span data-ttu-id="c6acb-173">Parametro</span><span class="sxs-lookup"><span data-stu-id="c6acb-173">Parameter</span></span> | <span data-ttu-id="c6acb-174">Value</span><span class="sxs-lookup"><span data-stu-id="c6acb-174">Value</span></span>
-- | --
<span data-ttu-id="c6acb-175">ComputerName</span><span class="sxs-lookup"><span data-stu-id="c6acb-175">ComputerName</span></span> | <span data-ttu-id="c6acb-176">Nome server</span><span class="sxs-lookup"><span data-stu-id="c6acb-176">Server name</span></span>

### <a name="gateway-credentials"></a><span data-ttu-id="c6acb-177">Credenziali del gateway</span><span class="sxs-lookup"><span data-stu-id="c6acb-177">Gateway credentials</span></span>

<span data-ttu-id="c6acb-178">Effettuare l'accesso specificando il server gateway come computer di destinazione e utilizzando credenziali formattate in uno dei modi seguenti.</span><span class="sxs-lookup"><span data-stu-id="c6acb-178">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span>

- <span data-ttu-id="c6acb-179">Server\_name\\user\_name</span><span class="sxs-lookup"><span data-stu-id="c6acb-179">Server\_name\\user\_name</span></span>
- <span data-ttu-id="c6acb-180">Localhost\\user\_name</span><span class="sxs-lookup"><span data-stu-id="c6acb-180">Localhost\\user\_name</span></span>
- <span data-ttu-id="c6acb-181">.\\user\_name</span><span class="sxs-lookup"><span data-stu-id="c6acb-181">.\\user\_name</span></span>

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a><span data-ttu-id="c6acb-182">In una regola di autorizzazione viene visualizzato un ID di sicurezza (SID)</span><span class="sxs-lookup"><span data-stu-id="c6acb-182">A security identifier (SID) is displayed in an authorization rule</span></span>

<span data-ttu-id="c6acb-183">In una regola di autorizzazione, al posto della sintassi user\_name/computer\_name viene visualizzato un ID di sicurezza (SID).</span><span class="sxs-lookup"><span data-stu-id="c6acb-183">A security identifier (SID) is displayed in an authorization rule instead of the syntax user\_name/computer\_name.</span></span>

<span data-ttu-id="c6acb-184">La regola non è più valida o la query in Servizi di dominio Active Directory non è riuscita.</span><span class="sxs-lookup"><span data-stu-id="c6acb-184">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span>
<span data-ttu-id="c6acb-185">In genere, una regola di autorizzazione non risulta valida nel caso in cui il server gateway che in precedenza apparteneva a un gruppo di lavoro venga poi aggiunto a un dominio</span><span class="sxs-lookup"><span data-stu-id="c6acb-185">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain</span></span>

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a><span data-ttu-id="c6acb-186">Impossibile accedere usando la regola con indirizzo IPv6 di dominio</span><span class="sxs-lookup"><span data-stu-id="c6acb-186">Cannot sign in with rule as an IPv6 address with a domain</span></span>

<span data-ttu-id="c6acb-187">Non è possibile accedere a un computer di destinazione che nelle regole di autorizzazione è stato specificato sotto forma di indirizzo IPv6 di dominio</span><span class="sxs-lookup"><span data-stu-id="c6acb-187">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span>

<span data-ttu-id="c6acb-188">Le regole di autorizzazione non supportano gli indirizzi IPv6 nel formato dei nomi di dominio.</span><span class="sxs-lookup"><span data-stu-id="c6acb-188">Authorization rules do not support an IPv6 address in form of a domain name.</span></span>

<span data-ttu-id="c6acb-189">Per specificare un computer di destinazione tramite un indirizzo IPv6, nella regola di autorizzazione utilizzare l'indirizzo IPv6 originale, che contiene due punti (:).</span><span class="sxs-lookup"><span data-stu-id="c6acb-189">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span>
<span data-ttu-id="c6acb-190">Sia i nomi di dominio che gli indirizzi IPv6 in formato numerico, ovvero con i due punti (:) sono supportati come nome del computer di destinazione nella pagina di accesso di Accesso Web Windows PowerShell, ma non nelle regole di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="c6acb-190">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span>

<span data-ttu-id="c6acb-191">Per altre informazioni sugli indirizzi IPv6, vedere l'articolo [Funzionamento di IPv6](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="c6acb-191">For more information about IPv6 addresses, see [How IPv6 Works](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="c6acb-192">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c6acb-192">See Also</span></span>

- <span data-ttu-id="c6acb-193">[Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="c6acb-193">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span></span>
- <span data-ttu-id="c6acb-194">[Usare la console di Windows PowerShell basata sul Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="c6acb-194">[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span></span>
- [<span data-ttu-id="c6acb-195">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="c6acb-195">about_Remote_Requirements</span></span>](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_remote_requirements)