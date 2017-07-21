---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: usare la console di windows powershell basata sul web
ms.openlocfilehash: 48ed1646c00f909c4e950f197f51a30205060ef0
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
#  <a name="use-the-web-based-windows-powershell-console"></a><span data-ttu-id="64b46-103">Usare la console di Windows PowerShell basata sul Web</span><span class="sxs-lookup"><span data-stu-id="64b46-103">Use the Web-based Windows PowerShell Console</span></span>

<span data-ttu-id="64b46-104">Ultimo aggiornamento: 24 giugno 2013</span><span class="sxs-lookup"><span data-stu-id="64b46-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="64b46-105">Si applica a: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="64b46-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="64b46-106">Accesso Web Windows PowerShell® consente agli utenti di Windows PowerShell® di accedere a un sito Web protetto da SSL (Secure Sockets Layer) per usare sessioni, cmdlet e script di Windows PowerShell per la gestione di un computer remoto.</span><span class="sxs-lookup"><span data-stu-id="64b46-106">Windows PowerShell® Web Access lets Windows PowerShell® users sign in to a Secure Sockets Layer (SSL)-secured website to use Windows PowerShell sessions, cmdlets, and scripts to manage a remote computer.</span></span> <span data-ttu-id="64b46-107">La console di Windows PowerShell viene eseguita in un Web browser, quindi può essere aperta da diversi dispositivi client, inclusi telefoni cellulari, tablet computer, chioschi multimediali pubblici, computer portatili oppure computer condivisi o presi in prestito.</span><span class="sxs-lookup"><span data-stu-id="64b46-107">Because the Windows PowerShell console runs in a web browser, it can be opened from a variety of client devices, including cell phones, tablet computers, public computing kiosks, laptop computers, or shared or borrowed computers.</span></span> <span data-ttu-id="64b46-108">La console di Windows PowerShell basata sul Web è destinata a un computer remoto specificato dagli utenti durante il processo di accesso.</span><span class="sxs-lookup"><span data-stu-id="64b46-108">The web-based Windows PowerShell console is targeted at a remote computer that is specified by users as part of the sign-in process.</span></span> <span data-ttu-id="64b46-109">Questo argomento descrive come accedere e iniziare a usare la console di Accesso Web Windows PowerShell basata sul Web.</span><span class="sxs-lookup"><span data-stu-id="64b46-109">This topic describes how to sign in to and start using the Windows PowerShell Web Access web-based console.</span></span>

<span data-ttu-id="64b46-110">Questo argomento non descrive come usare o eseguire i cmdlet o gli script di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="64b46-110">This topic does not describe how to use Windows PowerShell or run cmdlets or scripts.</span></span> <span data-ttu-id="64b46-111">Per informazioni su come usare Windows PowerShell e le risorse di script, vedere la sezione Vedere anche alla fine di questo argomento.</span><span class="sxs-lookup"><span data-stu-id="64b46-111">For information about how to use Windows PowerShell, and scripting resources, see the See Also section at the end of this topic.</span></span>

<span data-ttu-id="64b46-112">In questo argomento</span><span class="sxs-lookup"><span data-stu-id="64b46-112">In this topic:</span></span>

-   [<span data-ttu-id="64b46-113">Browser e dispositivi client supportati</span><span class="sxs-lookup"><span data-stu-id="64b46-113">Supported browsers and client devices</span></span>](#BKMK_browser)

-   [<span data-ttu-id="64b46-114">Connessione ad Accesso Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="64b46-114">Signing in to Windows PowerShell Web Access</span></span>](#BKMK_sign)

-   [<span data-ttu-id="64b46-115">Disconnessione e timeout</span><span class="sxs-lookup"><span data-stu-id="64b46-115">Signing out and timing out</span></span>](#BKMK_timeout)

-   [<span data-ttu-id="64b46-116">Differenze nella console di Windows PowerShell basata sul Web</span><span class="sxs-lookup"><span data-stu-id="64b46-116">Differences in the web-based Windows PowerShell console</span></span>](#BKMK_web)

<a href="" id="BKMK_browser"></a>
------------------------------------------------------------------------

<span data-ttu-id="64b46-117">Accesso Web Windows PowerShell supporta i browser Internet seguenti.</span><span class="sxs-lookup"><span data-stu-id="64b46-117">Windows PowerShell Web Access supports the following Internet browsers.</span></span> <span data-ttu-id="64b46-118">Anche se i browser per dispositivi mobili non sono ufficialmente supportati, molti potrebbero essere in grado di eseguire la console di Windows PowerShell basata sul Web.</span><span class="sxs-lookup"><span data-stu-id="64b46-118">Although mobile browsers are not officially supported, many may be able to run the web-based Windows PowerShell console.</span></span> <span data-ttu-id="64b46-119">Anche gli altri browser che accettano cookie, eseguono JavaScript e aprono i siti Web HTTPS dovrebbero funzionare, ma non sono stati testati ufficialmente.</span><span class="sxs-lookup"><span data-stu-id="64b46-119">Other browsers that accept cookies, run JavaScript, and run HTTPS websites are expected to work, but are not officially tested.</span></span>

###

<span data-ttu-id="64b46-120"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser per computer desktop supportati</span></a></span><span class="sxs-lookup"><span data-stu-id="64b46-120"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Supported desktop computer browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="64b46-121">Windows® Internet Explorer® per Microsoft Windows® 8.0, 9.0, 10.0 e 11.0</span><span class="sxs-lookup"><span data-stu-id="64b46-121">Windows® Internet Explorer® for Microsoft Windows® 8.0, 9.0, 10.0, and 11.0</span></span>

-   <span data-ttu-id="64b46-122">Mozilla Firefox® 10.0.2</span><span class="sxs-lookup"><span data-stu-id="64b46-122">Mozilla Firefox® 10.0.2</span></span>

-   <span data-ttu-id="64b46-123">Google Chrome™ 17.0.963.56m per Windows</span><span class="sxs-lookup"><span data-stu-id="64b46-123">Google Chrome™ 17.0.963.56m for Windows</span></span>

-   <span data-ttu-id="64b46-124">Apple Safari® 5.1.2 per Windows</span><span class="sxs-lookup"><span data-stu-id="64b46-124">Apple Safari® 5.1.2 for Windows</span></span>

-   <span data-ttu-id="64b46-125">Apple Safari® 5.1.2 per Mac OS®</span><span class="sxs-lookup"><span data-stu-id="64b46-125">Apple Safari 5.1.2 for Mac OS®</span></span>

###

<span data-ttu-id="64b46-126"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Dispositivi mobili e browser sottoposti ai test minimi</span></a></span><span class="sxs-lookup"><span data-stu-id="64b46-126"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Minimally-tested mobile devices or browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="64b46-127">Windows Phone 7 e 7.5</span><span class="sxs-lookup"><span data-stu-id="64b46-127">Windows Phone 7 and 7.5</span></span>

-   <span data-ttu-id="64b46-128">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span><span class="sxs-lookup"><span data-stu-id="64b46-128">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span></span>

-   <span data-ttu-id="64b46-129">Apple Safari 5.0.1 per sistema operativo iPhone</span><span class="sxs-lookup"><span data-stu-id="64b46-129">Apple Safari for iPhone operating system 5.0.1</span></span>

-   <span data-ttu-id="64b46-130">Sistema operativo Apple Safari per iPad 2 5.0.1</span><span class="sxs-lookup"><span data-stu-id="64b46-130">Apple Safari for iPad 2 operating system 5.0.1</span></span>

###

<span data-ttu-id="64b46-131"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Requisiti del browser</span></a></span><span class="sxs-lookup"><span data-stu-id="64b46-131"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser requirements</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="64b46-132">Per usare la console di Accesso Web Windows PowerShell basata sul Web, i browser devono:</span><span class="sxs-lookup"><span data-stu-id="64b46-132">To use the Windows PowerShell Web Access web-based console, browsers must do the following.</span></span>

-   <span data-ttu-id="64b46-133">Consentire i cookie dal sito Web del gateway di Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="64b46-133">Allow cookies from the Windows PowerShell Web Access gateway website.</span></span>

-   <span data-ttu-id="64b46-134">Sia in grado di aprire e leggere le pagine HTTPS.</span><span class="sxs-lookup"><span data-stu-id="64b46-134">Be able to open and read HTTPS pages.</span></span>

-   <span data-ttu-id="64b46-135">Aprire ed eseguire siti Web che usano JavaScript.</span><span class="sxs-lookup"><span data-stu-id="64b46-135">Open and run websites that use JavaScript.</span></span>

<a href="" id="BKMK_sign"></a>

<span data-ttu-id="64b46-136"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Connessione ad Accesso Web Windows PowerShell</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="64b46-136"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Signing in to Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="64b46-137">L'amministratore di Accesso Web Windows PowerShell deve fornire all'utente l'URL corrispondente all'indirizzo del sito Web del gateway di Accesso Web Windows PowerShell dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="64b46-137">Your Windows PowerShell Web Access administrator should provide you with a URL that is the address of your organization’s Windows PowerShell Web Access gateway website.</span></span> <span data-ttu-id="64b46-138">Per impostazione predefinita, l'indirizzo di questo sito Web è https://&lt;nome_server&gt;/pswa.</span><span class="sxs-lookup"><span data-stu-id="64b46-138">By default, this website address is https://&lt;server_name&gt;/pswa.</span></span> <span data-ttu-id="64b46-139">Prima di accedere ad Accesso Web Windows PowerShell, assicurarsi di avere il nome o l'indirizzo IP del computer remoto da gestire.</span><span class="sxs-lookup"><span data-stu-id="64b46-139">Before you sign in to Windows PowerShell Web Access, be sure that you have the name or IP address of the remote computer that you want to manage.</span></span> <span data-ttu-id="64b46-140">È necessario essere un utente autorizzato nel computer remoto, che deve essere configurato per consentire la gestione remota.</span><span class="sxs-lookup"><span data-stu-id="64b46-140">You must be an authorized user on the remote computer, and it must be configured to allow remote management.</span></span> <span data-ttu-id="64b46-141">Per altre informazioni sulla configurazione del computer per consentire la gestione remota, vedere [Abilitare e usare i comandi remoti in Windows PowerShell](https://technet.microsoft.com/magazine/ff700227.aspx).</span><span class="sxs-lookup"><span data-stu-id="64b46-141">For more information about configuring your computer to allow remote management, see [Enable and Use Remote Commands in Windows PowerShell](https://technet.microsoft.com/magazine/ff700227.aspx).</span></span> <span data-ttu-id="64b46-142">Il metodo di configurazione del computer più semplice per consentire la gestione remota consiste nell'eseguire il cmdlet **Enable-PSRemoting -force** nel computer, in una sessione di Windows PowerShell aperta con diritti utente elevati, ovvero **Esegui come amministratore**.</span><span class="sxs-lookup"><span data-stu-id="64b46-142">The simplest method of configuring your computer to allow remote management is to run the **Enable-PSRemoting -force** cmdlet on the computer, in a Windows PowerShell session that has been opened with elevated user rights (**Run as Administrator**).</span></span>

### <a name="to-sign-in-to-windows-powershell-web-access"></a><span data-ttu-id="64b46-143">Per connettersi ad Accesso Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="64b46-143">To sign in to Windows PowerShell Web Access</span></span>

1.  <span data-ttu-id="64b46-144">Aprire il sito Web Accesso Web Windows PowerShell in una finestra o una scheda del browser Internet.</span><span class="sxs-lookup"><span data-stu-id="64b46-144">Open the Windows PowerShell Web Access website in an Internet browser window or tab.</span></span>

2.  <span data-ttu-id="64b46-145">Nella pagina di accesso di Accesso Web Windows PowerShell specificare il nome utente e la password di rete e il nome del computer che si vuole gestire e del quale si è un utente autorizzato.</span><span class="sxs-lookup"><span data-stu-id="64b46-145">On the Windows PowerShell Web Access sign-in page, provide your network user name, password, and the name of the computer that you want to manage (and on which you are an authorized user).</span></span> <span data-ttu-id="64b46-146">Se l'amministratore di Accesso Web Windows PowerShell ha specificato di usare un URI in un server del sito o un server proxy personalizzato invece di un nome computer, selezionare **URI connessione** nel campo **Tipo di connessione** e quindi specificare l'URI.</span><span class="sxs-lookup"><span data-stu-id="64b46-146">If the Windows PowerShell Web Access administrator has instructed you to use a URI to a custom site or proxy server instead of a computer name, select **Connection URI** in the **Connection type** field, and then provide the URI.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="64b46-147"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Nota </span></span><span class="sxs-lookup"><span data-stu-id="64b46-147"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><ul>
    <li><p><span data-ttu-id="64b46-148">Se il computer di destinazione fa parte di un gruppo di lavoro, usare la sintassi seguente per fornire il nome utente e accedere al computer:&lt;<em>nome_gruppo di lavoro</em>&gt;\&lt;<em>nome_utente</em>&gt;.</span><span class="sxs-lookup"><span data-stu-id="64b46-148">If the destination computer is in a workgroup, use the following syntax to provide your user name and sign in to the computer:&lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;.</span></span></p></li>
    <li><p><span data-ttu-id="64b46-149">Se il computer di destinazione è il server gateway, è possibile specificare <strong>localhost</strong> nel campo <strong>Nome computer</strong>.</span><span class="sxs-lookup"><span data-stu-id="64b46-149">If the destination computer is the gateway server, you can specify <strong>localhost</strong> in the <strong>Computer name</strong> field.</span></span></p></li>
    <li><p><span data-ttu-id="64b46-150">Se il computer di destinazione è il server gateway e questo fa parte di un gruppo di lavoro, è possibile usare <strong>localhost</strong> nel campo <strong>Nome computer</strong>, ma non localhost\&lt;<em>nome_utente</em>&gt; nel campo <strong>Nome utente</strong>.</span><span class="sxs-lookup"><span data-stu-id="64b46-150">If the destination computer is the gateway server, and the gateway server is in a workgroup, you can use <strong>localhost</strong> in the <strong>Computer name</strong> field, but do not use localhost\&lt;<em>user_name</em>&gt; in the <strong>User name</strong> field.</span></span> <span data-ttu-id="64b46-151">È necessario usare &lt;<em>nome gruppo di lavoro</em>&gt;\&lt;<em>nome_utente</em>&gt;.</span><span class="sxs-lookup"><span data-stu-id="64b46-151">You must use &lt;<em>workgroup name</em>&gt;\&lt;<em>user_name</em>&gt;.</span></span></p></li>
    </ul></td>
    </tr>
    </tbody>
    </table>

3.  <span data-ttu-id="64b46-152">La sezione **Impostazioni di connessione facoltative** è relativa ai requisiti di autorizzazione del computer remoto che si vuole gestire.</span><span class="sxs-lookup"><span data-stu-id="64b46-152">The **Optional Connection Settings** section relates to the authorization requirements of the remote computer that you want to manage.</span></span> <span data-ttu-id="64b46-153">Per altre informazioni sui parametri equivalenti alle impostazioni di connessione facoltative, vedere [Guida del cmdlet Enter-PSSession](https://technet.microsoft.com/library/dd315384.aspx).</span><span class="sxs-lookup"><span data-stu-id="64b46-153">For more information about the parameters that are equivalent to optional connection settings, see the [Enter-PSSession cmdlet Help](https://technet.microsoft.com/library/dd315384.aspx).</span></span>

    <span data-ttu-id="64b46-154">In genere, le credenziali che si usano per il passaggio attraverso il gateway di Accesso Web Windows PowerShell sono le stesse riconosciute dal computer remoto che si vuole gestire.</span><span class="sxs-lookup"><span data-stu-id="64b46-154">Typically, the credentials you use to pass through the Windows PowerShell Web Access gateway are the same that are recognized by the remote computer that you want to manage.</span></span> <span data-ttu-id="64b46-155">Se tuttavia si preferisce usare credenziali diverse per gestire il computer remoto specificato nel passaggio 2, espandere la sezione **Impostazioni di connessione facoltative** e fornire le credenziali alternative.</span><span class="sxs-lookup"><span data-stu-id="64b46-155">However, if you want to use different credentials to manage the remote computer that you specified in step 2, expand the **Optional Connection Settings** section, and provide the alternate credentials.</span></span> <span data-ttu-id="64b46-156">In caso contrario, andare al passaggio 6.</span><span class="sxs-lookup"><span data-stu-id="64b46-156">Otherwise, skip to step 6.</span></span>

4.  <span data-ttu-id="64b46-157">Se l'amministratore di Accesso Web Windows PowerShell ha creato una configurazione di sessione personalizzata per gli utenti di Accesso Web Windows PowerShell, digitare il nome della configurazione di sessione nel campo **Nome configurazione**.</span><span class="sxs-lookup"><span data-stu-id="64b46-157">If the Windows PowerShell Web Access administrator has created a custom session configuration for Windows PowerShell Web Access users, type the name of the session configuration name in the **Configuration name** field.</span></span> <span data-ttu-id="64b46-158">Per altre informazioni sulle configurazioni di sessione, vedere [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx) nel sito Web Microsoft.</span><span class="sxs-lookup"><span data-stu-id="64b46-158">For more information about session configurations, see [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx) on the Microsoft website.</span></span>

5.  <span data-ttu-id="64b46-159">Mantenere il valore di **Tipo di autenticazione** impostato su **Predefinito**, a meno che l'amministratore di Accesso Web Windows PowerShell non abbia fornito istruzioni per procedere diversamente.</span><span class="sxs-lookup"><span data-stu-id="64b46-159">Keep the **Authentication type** set to **Default** unless you have been instructed to do otherwise by the Windows PowerShell Web Access administrator.</span></span>

6.  <span data-ttu-id="64b46-160">Fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="64b46-160">Click **Sign in**.</span></span>

<a href="" id="BKMK_timeout"></a>

<span data-ttu-id="64b46-161"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Disconnessione e timeout</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="64b46-161"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Signing out and timing out</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="64b46-162">Una qualsiasi delle operazioni seguenti causa la disconnessione dell'utente da una sessione di Windows PowerShell basata sul Web.</span><span class="sxs-lookup"><span data-stu-id="64b46-162">Any of the following signs you out of a web-based Windows PowerShell session.</span></span>

-   <span data-ttu-id="64b46-163">Fare clic su **Disconnetti** nell'angolo in basso a destra della console.</span><span class="sxs-lookup"><span data-stu-id="64b46-163">Clicking **Sign out** in the lower right corner of the console.</span></span> <span data-ttu-id="64b46-164">Solo Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="64b46-164">(Windows Server 2012 only)</span></span>

-   <span data-ttu-id="64b46-165">Fare clic su **Salva** o **Esci** nell'angolo in basso a destra della console (solo Windows Server 2012 R2).</span><span class="sxs-lookup"><span data-stu-id="64b46-165">Clicking **Save** or **Exit** in the lower right corner of the console (Windows Server 2012 R2 only).</span></span> <span data-ttu-id="64b46-166">Se si fa clic su **Salva**, la sessione di Accesso Web Windows PowerShell viene salvata e chiusa. È possibile riconnettersi alla sessione in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="64b46-166">Clicking **Save** saves and closes your Windows PowerShell Web Access session; you can reconnect to the session later.</span></span> <span data-ttu-id="64b46-167">Quando si accede di nuovo ad Accesso Web Windows PowerShell, viene visualizzato un elenco delle sessioni salvate. È possibile selezionare una sessione salvata e riconnettersi o avviare una nuova sessione.</span><span class="sxs-lookup"><span data-stu-id="64b46-167">When you sign in to Windows PowerShell Web Access again, Windows PowerShell Web Access displays a list of your saved sessions; you can either select and reconnect to a saved session, or start a new session.</span></span> <span data-ttu-id="64b46-168">Il numero massimo di sessioni aperte consentito agli utenti, sia salvate che attive, viene configurato dall'amministratore del gateway.</span><span class="sxs-lookup"><span data-stu-id="64b46-168">The maximum number of open sessions that users are allowed, both saved and active, is configured by the gateway administrator.</span></span>

    <span data-ttu-id="64b46-169">Se si fa clic su **Esci**, la sessione di Accesso Web Windows PowerShell viene disconnessa senza essere salvata.</span><span class="sxs-lookup"><span data-stu-id="64b46-169">Clicking **Exit** signs you out of the Windows PowerShell Web Access session without saving it.</span></span>

-   <span data-ttu-id="64b46-170">Provare ad accedere per gestire un computer remoto diverso nella stessa sessione del browser o in una nuova scheda della stessa sessione del browser.</span><span class="sxs-lookup"><span data-stu-id="64b46-170">Attempting to sign in to manage a different remote computer in the same browser session, or in a new tab of the same browser session.</span></span> <span data-ttu-id="64b46-171">Questo approccio non è applicabile se il server gateway esegue Windows Server 2012 R2. L'esecuzione di Accesso Web Windows PowerShell in Windows Server 2012 R2 consente più sessioni utente in nuove schede della stessa sessione del browser. Per altre informazioni su come usare più sessioni attive nello stesso computer, vedere "Connessione a più computer di destinazione contemporaneamente" nella sezione [Limitazioni della console basata sul Web](#BKMK_limits) di questo argomento.</span><span class="sxs-lookup"><span data-stu-id="64b46-171">(This does not apply if the gateway server is running Windows Server 2012 R2; Windows PowerShell Web Access running on Windows Server 2012 R2 does allow multiple user sessions in new tabs in the same browser session.) For more information about how to use more than one active session on the same computer, see “Connecting to multiple target computers simultaneously” in the [Limitations of the web-based console](#BKMK_limits) section of this topic.</span></span>

-   <span data-ttu-id="64b46-172">20 minuti di inattività della sessione.</span><span class="sxs-lookup"><span data-stu-id="64b46-172">20 minutes of inactivity in the session.</span></span> <span data-ttu-id="64b46-173">L'amministratore del gateway può personalizzare il periodo di timeout di inattività. Per altre informazioni, vedere [Gestione delle sessioni](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx#BKMK_sesmgmt).</span><span class="sxs-lookup"><span data-stu-id="64b46-173">The gateway administrator can customize the inactivity time-out period; for more information, see [Session management](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx#BKMK_sesmgmt).</span></span>

    -   <span data-ttu-id="64b46-174">Se si viene disconnessi da una sessione nella console basata sul Web a causa di un errore di rete o di un altro arresto o errore non pianificato e non perché la sessione è stata volutamente chiusa, la sessione di Accesso Web Windows PowerShell rimane in esecuzione e connessa al computer di destinazione, finché non sarà trascorso il periodo di timeout sul lato client.</span><span class="sxs-lookup"><span data-stu-id="64b46-174">If you are disconnected from a session in the web-based console because of a network error or other unplanned shutdown or failure, and not because you have closed the session yourself, the Windows PowerShell Web Access session continues to run, connected to the target computer, until the time-out period on the client side lapses.</span></span> <span data-ttu-id="64b46-175">Per impostazione predefinita, questo periodo di timeout è di 20 minuti e viene configurato dall'amministratore del gateway.</span><span class="sxs-lookup"><span data-stu-id="64b46-175">By default, this time-out period is 20 minutes, and is configured by the gateway administrator.</span></span> <span data-ttu-id="64b46-176">La sessione viene disconnessa trascorsi i 20 minuti predefiniti o dopo il periodo di timeout specificato dall'amministratore del gateway, a seconda del valore inferiore.</span><span class="sxs-lookup"><span data-stu-id="64b46-176">The session is disconnected after either the default 20 minutes, or after the time-out period specified by the gateway administrator, whichever is shorter.</span></span>

        <span data-ttu-id="64b46-177">Se il server gateway esegue Windows Server 2012 R2, Accesso Web Windows PowerShell consente agli utenti di riconnettersi alle sessioni salvate in un secondo momento, ma non si possono visualizzare le sessioni salvate o riconnettersi finché non sarà trascorso il periodo di timeout specificato dall'amministratore del gateway.</span><span class="sxs-lookup"><span data-stu-id="64b46-177">If the gateway server is running Windows Server 2012 R2, Windows PowerShell Web Access lets users reconnect to saved sessions at a later time, but you cannot see or reconnect to saved sessions until after the time-out period specified by the gateway administrator has lapsed.</span></span>

-   <span data-ttu-id="64b46-178">Chiudere la finestra o la scheda del browser.</span><span class="sxs-lookup"><span data-stu-id="64b46-178">Closing the browser window or tab.</span></span>

-   <span data-ttu-id="64b46-179">Disattivare il dispositivo client in cui è in esecuzione il browser o disconnettersi dalla rete.</span><span class="sxs-lookup"><span data-stu-id="64b46-179">Turning off the client device on which the browser is running, or disconnecting it from the network.</span></span>

-   <span data-ttu-id="64b46-180">Esecuzione del comando **Esci** nella console Web.</span><span class="sxs-lookup"><span data-stu-id="64b46-180">Running the **Exit** command in the web console.</span></span> <span data-ttu-id="64b46-181">Questo comando non funziona se la configurazione della sessione a cui si è connessi è configurata per supportare la modalità [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) o si trova in uno spazio di esecuzione con restrizioni.</span><span class="sxs-lookup"><span data-stu-id="64b46-181">This command does not work if the session configuration to which you are connected to is configured to support [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) mode, or is in a restricted runspace.</span></span>

<span data-ttu-id="64b46-182">Per accedere di nuovo, riaprire la pagina Web di Accesso Web Windows PowerShell ed eseguire l'accesso con la procedura descritta nella sezione [Per connettersi ad Accesso Web Windows PowerShell](#BKMK_signin) di questo argomento.</span><span class="sxs-lookup"><span data-stu-id="64b46-182">If you want to sign in again, open the Windows PowerShell Web Access web page again, and sign in by following the steps in [To sign in to Windows PowerShell Web Access](#BKMK_signin) in this topic.</span></span>

<a href="" id="BKMK_web"></a>

<span data-ttu-id="64b46-183"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Differenze nella console di Windows PowerShell basata sul Web</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="64b46-183"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Differences in the web-based Windows PowerShell console</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="64b46-184">Dopo l'accesso a Accesso Web Windows PowerShell, viene aperta una console di Windows PowerShell basata sul Web nella finestra o in una scheda del browser.</span><span class="sxs-lookup"><span data-stu-id="64b46-184">After signing in to Windows PowerShell Web Access, a web-based Windows PowerShell console opens in your browser window or tab.</span></span> <span data-ttu-id="64b46-185">La console è connessa al computer remoto specificato durante il processo di accesso, di conseguenza nella console possono essere usati solo i cmdlet o gli script di Windows PowerShell disponibili nel computer remoto.</span><span class="sxs-lookup"><span data-stu-id="64b46-185">Because the console is connected to the remote computer that you specified during the sign-in process, only those Windows PowerShell cmdlets or scripts that are available on the remote computer can be used in the console.</span></span> <span data-ttu-id="64b46-186">Questa sezione descrive altre limitazioni delle console di Accesso Web Windows PowerShell e le differenze tra le console di Accesso Web Windows PowerShell e la console di **PowerShell.exe** installata.</span><span class="sxs-lookup"><span data-stu-id="64b46-186">This section describes other limitations of Windows PowerShell Web Access consoles, and differences between Windows PowerShell Web Access consoles and the installed **PowerShell.exe** console.</span></span>

###

<span data-ttu-id="64b46-187"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Disparità funzionale con PowerShell.exe</span></a></span><span class="sxs-lookup"><span data-stu-id="64b46-187"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Functional disparity with PowerShell.exe</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="64b46-188">Quasi tutte le funzionalità host di Windows PowerShell sono disponibili nella console di Accesso Web Windows PowerShell basata sul Web.</span><span class="sxs-lookup"><span data-stu-id="64b46-188">The majority of Windows PowerShell host functionality is available in the Windows PowerShell Web Access web-based console, but there are some features that are not available.</span></span>

-   <span data-ttu-id="64b46-189"><span class="label">Visualizzazioni di avanzamento annidate.</span></span><span class="sxs-lookup"><span data-stu-id="64b46-189"><span class="label">Nested progress displays.</span></span></span>  <span data-ttu-id="64b46-190">Accesso Web Windows PowerShell presenta un'interfaccia utente grafica di avanzamento per i cmdlet, che segnala lo stato di avanzamento, visualizzando però solo le informazioni di primo livello.</span><span class="sxs-lookup"><span data-stu-id="64b46-190">Windows PowerShell Web Access displays a progress GUI for cmdlets that report progress, but only top-level progress information is displayed.</span></span>

-   <span data-ttu-id="64b46-191"><span class="label">Modifica del colore di input.</span></span><span class="sxs-lookup"><span data-stu-id="64b46-191"><span class="label">Input color modification.</span></span></span>  <span data-ttu-id="64b46-192">Il colore di input, sia primo piano che di sfondo, non può essere modificato.</span><span class="sxs-lookup"><span data-stu-id="64b46-192">The input color (both foreground and background) cannot be changed.</span></span> <span data-ttu-id="64b46-193">Lo stile dei messaggi di output, di avviso, dettagliati e di errore possono essere tutti gestiti con l'esecuzione di uno script.</span><span class="sxs-lookup"><span data-stu-id="64b46-193">The style of output, warning, verbose, and error messages can all be changed by running a script.</span></span>

-   <span data-ttu-id="64b46-194"><span class="label">PSHostRawUserInterface.</span></span><span class="sxs-lookup"><span data-stu-id="64b46-194"><span class="label">PSHostRawUserInterface.</span></span></span>  <span data-ttu-id="64b46-195">Accesso Web Windows PowerShell è implementato nella gestione remota di Windows PowerShell e usa uno spazio di esecuzione remoto.</span><span class="sxs-lookup"><span data-stu-id="64b46-195">Windows PowerShell Web Access is implemented over Windows PowerShell remote management, and uses a remote runspace.</span></span> <span data-ttu-id="64b46-196">Accesso Web Windows PowerShell non implementa alcuni metodi in questa interfaccia, ad esempio, tutti i comandi che scrivono nella console di Windows.</span><span class="sxs-lookup"><span data-stu-id="64b46-196">Windows PowerShell Web Access does not implement some methods in this interface; for example, any command that writes to the Windows console.</span></span> <span data-ttu-id="64b46-197">I comandi come **PowerTab** non funzionano in Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="64b46-197">Commands such as **PowerTab** do not work in Windows PowerShell Web Access.</span></span>

-   <span data-ttu-id="64b46-198"><span class="label">Tasti funzione.</span></span><span class="sxs-lookup"><span data-stu-id="64b46-198"><span class="label">Function keys.</span></span></span>  <span data-ttu-id="64b46-199">Accesso Web Windows PowerShell non supporta alcuni tasti funzione, in molti casi perché i comandi sono riservati dal browser.</span><span class="sxs-lookup"><span data-stu-id="64b46-199">Windows PowerShell Web Access does not support some function keys, in many cases because the commands are reserved by the browser.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="64b46-200">Tasto funzione non supportato</span><span class="sxs-lookup"><span data-stu-id="64b46-200">Unsupported Function Key</span></span></p></th>
<th><p><span data-ttu-id="64b46-201">Azione</span><span class="sxs-lookup"><span data-stu-id="64b46-201">Action</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="64b46-202">CTRL+C</span><span class="sxs-lookup"><span data-stu-id="64b46-202">Ctrl+C</span></span></p></td>
<td><p><span data-ttu-id="64b46-203">In Accesso Web Windows PowerShell <strong>CTRL+C</strong> viene usato dal browser per copiare il contenuto.</span><span class="sxs-lookup"><span data-stu-id="64b46-203">In Windows PowerShell Web Access, <strong>Ctrl+C</strong> is used by the browser to copy content.</span></span> <span data-ttu-id="64b46-204">La console fornisce un pulsante <strong>Annulla</strong> e gli utenti possono anche usare <strong>CTRL+Q</strong> per annullare i comandi.</span><span class="sxs-lookup"><span data-stu-id="64b46-204">The console offers a <strong>Cancel</strong> button, and users can also use <strong>Ctrl+Q</strong> to cancel commands.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="64b46-205">ALT+BARRA SPAZ.+E+L</span><span class="sxs-lookup"><span data-stu-id="64b46-205">Alt-space, e, l</span></span></p></td>
<td><p><span data-ttu-id="64b46-206">Scorre il buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="64b46-206">Scroll through the screen buffer</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="64b46-207">ALT+BARRA SPAZ.+E+F</span><span class="sxs-lookup"><span data-stu-id="64b46-207">Alt+Space, e, f</span></span></p></td>
<td><p><span data-ttu-id="64b46-208">Cerca il testo nel buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="64b46-208">Search for text in the screen buffer</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="64b46-209">ALT+BARRA SPAZ.+E+K</span><span class="sxs-lookup"><span data-stu-id="64b46-209">Alt+Space, e, k</span></span></p></td>
<td><p><span data-ttu-id="64b46-210">Seleziona il testo da copiare dal buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="64b46-210">Select text to be copied from the screen buffer</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="64b46-211">ALT+BARRA SPAZ.+E+P</span><span class="sxs-lookup"><span data-stu-id="64b46-211">Alt+Space, e, p</span></span></p></td>
<td><p><span data-ttu-id="64b46-212">Incolla il contenuto degli Appunti nella console di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="64b46-212">Paste clipboard contents into the Windows PowerShell console</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="64b46-213">ALT+BARRA SPAZ.+C</span><span class="sxs-lookup"><span data-stu-id="64b46-213">Alt+Space, c</span></span></p></td>
<td><p><span data-ttu-id="64b46-214">Chiude la console di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="64b46-214">Close the Windows PowerShell console</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="64b46-215">CTRL+INTERR</span><span class="sxs-lookup"><span data-stu-id="64b46-215">Ctrl+Break</span></span></p></td>
<td><p><span data-ttu-id="64b46-216">Forza la chiusura della finestra di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="64b46-216">Force the Windows PowerShell window to close</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="64b46-217">CTRL+HOME</span><span class="sxs-lookup"><span data-stu-id="64b46-217">Ctrl+Home</span></span></p></td>
<td><p><span data-ttu-id="64b46-218">Elimina dall'inizio della riga di comando corrente.</span><span class="sxs-lookup"><span data-stu-id="64b46-218">Deletes from the beginning of the current command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="64b46-219">CTRL+FINE</span><span class="sxs-lookup"><span data-stu-id="64b46-219">Ctrl+End</span></span></p></td>
<td><p><span data-ttu-id="64b46-220">Elimina fino alla fine della riga di comando.</span><span class="sxs-lookup"><span data-stu-id="64b46-220">Deletes to end of the command line</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="64b46-221">F1</span><span class="sxs-lookup"><span data-stu-id="64b46-221">F1</span></span></p></td>
<td><p><span data-ttu-id="64b46-222">Sposta il cursore di un carattere a destra nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="64b46-222">Move cursor one character to the right on your command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="64b46-223">F2</span><span class="sxs-lookup"><span data-stu-id="64b46-223">F2</span></span></p></td>
<td><p><span data-ttu-id="64b46-224">Crea un nuovo comando copiando l'ultimo comando fino al carattere digitato.</span><span class="sxs-lookup"><span data-stu-id="64b46-224">Creates a new command by copying your last command up to the character that you type</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="64b46-225">F3</span><span class="sxs-lookup"><span data-stu-id="64b46-225">F3</span></span></p></td>
<td><p><span data-ttu-id="64b46-226">Completa la riga di comando con il contenuto dell'ultima riga di comando.</span><span class="sxs-lookup"><span data-stu-id="64b46-226">Complete the command line with content from your last command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="64b46-227">F4</span><span class="sxs-lookup"><span data-stu-id="64b46-227">F4</span></span></p></td>
<td><p><span data-ttu-id="64b46-228">Elimina i caratteri dalla posizione del cursore.</span><span class="sxs-lookup"><span data-stu-id="64b46-228">Deletes characters from cursor position</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="64b46-229">F5</span><span class="sxs-lookup"><span data-stu-id="64b46-229">F5</span></span></p></td>
<td><p><span data-ttu-id="64b46-230">Scorre all'indietro nella cronologia del comando.</span><span class="sxs-lookup"><span data-stu-id="64b46-230">Scan backward through your command history.</span></span> <span data-ttu-id="64b46-231">Per accedere ai comandi nella cronologia dei comandi in Accesso Web Windows PowerShell, fare clic sui pulsanti di scorrimento <strong>Cronologia</strong> disponibili nella console basata sul Web.</span><span class="sxs-lookup"><span data-stu-id="64b46-231">To access commands in the command history in Windows PowerShell Web Access, click the <strong>History</strong> scroll buttons in the web-based console.</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="64b46-232">F7</span><span class="sxs-lookup"><span data-stu-id="64b46-232">F7</span></span></p></td>
<td><p><span data-ttu-id="64b46-233">Seleziona in modo interattivo un comando dalla cronologia dei comandi.</span><span class="sxs-lookup"><span data-stu-id="64b46-233">Interactively select a command from your command history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="64b46-234">F8</span><span class="sxs-lookup"><span data-stu-id="64b46-234">F8</span></span></p></td>
<td><p><span data-ttu-id="64b46-235">Analizza la cronologia visualizzando i comandi che corrispondono al testo corrente.</span><span class="sxs-lookup"><span data-stu-id="64b46-235">Scan history displaying commands that match current text</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="64b46-236">F9</span><span class="sxs-lookup"><span data-stu-id="64b46-236">F9</span></span></p></td>
<td><p><span data-ttu-id="64b46-237">Esegue un comando numerato specifico dalla cronologia.</span><span class="sxs-lookup"><span data-stu-id="64b46-237">Run a specific numbered command from history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="64b46-238">PGSU</span><span class="sxs-lookup"><span data-stu-id="64b46-238">Page Up</span></span></p></td>
<td><p><span data-ttu-id="64b46-239">Esegue il primo comando nella cronologia.</span><span class="sxs-lookup"><span data-stu-id="64b46-239">Run the first command in the history</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="64b46-240">PGGIÙ</span><span class="sxs-lookup"><span data-stu-id="64b46-240">Page Down</span></span></p></td>
<td><p><span data-ttu-id="64b46-241">Esegue l'ultimo comando nella cronologia.</span><span class="sxs-lookup"><span data-stu-id="64b46-241">Run the last command in the history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="64b46-242">ALT+F7</span><span class="sxs-lookup"><span data-stu-id="64b46-242">Alt+F7</span></span></p></td>
<td><p><span data-ttu-id="64b46-243">Cancella l'elenco della cronologia dei comandi.</span><span class="sxs-lookup"><span data-stu-id="64b46-243">Clear the command history list</span></span></p></td>
</tr>
</tbody>
</table><span data-ttu-id="64b46-244">

<a href="" id="BKMK_limits"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Limitazioni della console basata sul Web</span></a></span><span class="sxs-lookup"><span data-stu-id="64b46-244">

<a href="" id="BKMK_limits"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Limitations of the web-based console</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="64b46-245"><span class="label">Doppio hop.</span></span><span class="sxs-lookup"><span data-stu-id="64b46-245"><span class="label">Double-hop.</span></span></span>   <span data-ttu-id="64b46-246">Se si prova a creare una nuova sessione o a usarla con Accesso Web Windows PowerShell, si potrebbe riscontrare una limitazione al doppio hop, ovvero la connessione a un secondo computer dalla prima connessione.</span><span class="sxs-lookup"><span data-stu-id="64b46-246">You can encounter the double-hop (or connecting to a second computer from the first connection) limitation if you try to create or work on a new session by using Windows PowerShell Web Access.</span></span> <span data-ttu-id="64b46-247">Accesso Web Windows PowerShell usa uno spazio di esecuzione remoto e attualmente **PowerShell.exe** non consente di stabilire una connessione remota a un secondo computer da uno spazio di esecuzione remoto.</span><span class="sxs-lookup"><span data-stu-id="64b46-247">Windows PowerShell Web Access uses a remote runspace, and currently, **PowerShell.exe** does not support establishing a remote connection to a second computer from a remote runspace.</span></span> <span data-ttu-id="64b46-248">Se si prova a connettersi a un secondo computer remoto da una connessione esistente con il cmdlet **Enter-PSSession**, potrebbero essere visualizzati diversi errori, ad esempio un messaggio simile a "Non è possibile ottenere risorse di rete".</span><span class="sxs-lookup"><span data-stu-id="64b46-248">If you attempt to connect to a second remote computer from an existing connection by using the **Enter-PSSession** cmdlet, for example, you can get various errors, such as “Cannot get network resources.”</span></span>

    <span data-ttu-id="64b46-249">Per evitare errori relativi al doppio hop, l'amministratore deve configurare l'autenticazione CredSSP nell'ambiente di rete dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="64b46-249">To avoid double-hop errors, your administrator should configure CredSSP authentication in your organization’s network environment.</span></span> <span data-ttu-id="64b46-250">Per altre informazioni sulla configurazione dell'autenticazione CredSSP, vedere il blog relativo a [CredSSP per la comunicazione remota con un secondo hop](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) nel sito Web Microsoft.</span><span class="sxs-lookup"><span data-stu-id="64b46-250">For more information about configuring CredSSP authentication, see [CredSSP for second-hop remoting](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) on the Microsoft website.</span></span> <span data-ttu-id="64b46-251">È anche possibile fornire credenziali esplicite quando si vuole gestire un secondo computer remoto. È improbabile che le credenziali implicite consentano il secondo hop.</span><span class="sxs-lookup"><span data-stu-id="64b46-251">You can also provide explicit credentials when you want to manage a second remote computer; implicit credentials are unlikely to allow the second hop.</span></span>

-   <span data-ttu-id="64b46-252">Accesso Web Windows PowerShell usa e ha le stesse limitazioni di una sessione remota di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="64b46-252">Windows PowerShell Web Access uses and has the same limitations as a remote Windows PowerShell session.</span></span> <span data-ttu-id="64b46-253">I comandi che chiamano direttamente le API della console di Windows, ad esempio quelle per gli editor basati su console o i programmi di menu basati su testo, non funzionano perché i comandi non leggono o scrivono su pipe standard di input, output e di errore.</span><span class="sxs-lookup"><span data-stu-id="64b46-253">Commands that directly call Windows console APIs, such as those for console-based editors or text-based menu programs, do not work because the commands do not read or write to standard input, output, and error pipes.</span></span> <span data-ttu-id="64b46-254">Di conseguenza, i comandi che avviano un file eseguibile, ad esempio **notepad.exe**, o che visualizzano un'interfaccia utente grafica, ad esempio <span class="code">OpenGridView</span> o <span class="code">ogv</span>, non funzionano.</span><span class="sxs-lookup"><span data-stu-id="64b46-254">Therefore, commands that launch an executable file, such as **notepad.exe**, or display a GUI, such as <span class="code">OpenGridView</span> or <span class="code">ogv</span>, do not work.</span></span> <span data-ttu-id="64b46-255">Questo comportamento influenza l'esperienza utente, perché sembra che Accesso Web Windows PowerShell non risponda al comando.</span><span class="sxs-lookup"><span data-stu-id="64b46-255">Your experience is affected by this behavior; to you, it appears that Windows PowerShell Web Access is not responding to your command.</span></span>

-   <span data-ttu-id="64b46-256">Il completamento tramite tasto TAB non funziona in una configurazione di sessione con uno spazio di esecuzione con restrizioni o in modalità **NoLanguage**.</span><span class="sxs-lookup"><span data-stu-id="64b46-256">Tab completion does not work in a session configuration with a restricted runspace or one that is in **NoLanguage** mode.</span></span> <span data-ttu-id="64b46-257">Anche se gli amministratori possono configurare una sessione per supportare il completamento tramite tasto TAB, è sconsigliato per motivi di sicurezza, perché può esporre le informazioni seguenti a utenti non autorizzati.</span><span class="sxs-lookup"><span data-stu-id="64b46-257">Although administrators can configure a session to support tab completion, it is discouraged for security reasons, because it can expose the following information to unauthorized users.</span></span>

    -   <span data-ttu-id="64b46-258">Percorsi interni del file system</span><span class="sxs-lookup"><span data-stu-id="64b46-258">Internal file system paths</span></span>

    -   <span data-ttu-id="64b46-259">Cartelle condivise in computer interni</span><span class="sxs-lookup"><span data-stu-id="64b46-259">Shared folders on internal computers</span></span>

    -   <span data-ttu-id="64b46-260">Variabili nello spazio di esecuzione</span><span class="sxs-lookup"><span data-stu-id="64b46-260">Variables in the runspace</span></span>

    -   <span data-ttu-id="64b46-261">Tipi caricati o spazi dei nomi di .NET Framework</span><span class="sxs-lookup"><span data-stu-id="64b46-261">Loaded types or.NET Framework namespaces</span></span>

    -   <span data-ttu-id="64b46-262">Variabili di ambiente</span><span class="sxs-lookup"><span data-stu-id="64b46-262">Environment variables</span></span>

-   <span data-ttu-id="64b46-263">Gli utenti connessi a una configurazione di sessione **NoLanguage** o a uno spazio di esecuzione con restrizioni in Accesso Web Windows PowerShell non possono eseguire il comando **Esci** per terminare la sessione.</span><span class="sxs-lookup"><span data-stu-id="64b46-263">Users who are signed in to a **NoLanguage** session configuration or a restricted runspace in Windows PowerShell Web Access cannot run the **Exit** command to end the session.</span></span> <span data-ttu-id="64b46-264">Per disconnettersi, gli utenti devono fare clic su **Disconnetti** nella pagina della console.</span><span class="sxs-lookup"><span data-stu-id="64b46-264">To sign out, users should click **Sign Out** on the console page.</span></span>

-   <span data-ttu-id="64b46-265"><span class="label">Connessione a più computer di destinazione contemporaneamente.</span></span><span class="sxs-lookup"><span data-stu-id="64b46-265"><span class="label">Connecting to multiple target computers simultaneously.</span></span></span>   <span data-ttu-id="64b46-266">Se il server gateway esegue Windows Server 2012, Accesso Web Windows PowerShell consente solo una connessione a un computer remoto per ogni sessione del browser. Non consente agli utenti di accedere una sola volta e connettersi a più computer remoti usando schede separate del browser.</span><span class="sxs-lookup"><span data-stu-id="64b46-266">If the gateway server is running Windows Server 2012, Windows PowerShell Web Access allows only one remote computer connection per browser session; it does not allow users to sign in once, and connect to multiple remote computers by using separate browser tabs.</span></span> <span data-ttu-id="64b46-267">Quando si apre una nuova scheda o una nuova finestra del browser, Accesso Web Windows PowerShell chiede di disconnettere la sessione corrente e avviare una nuova sessione, per potersi connettere al computer remoto nuovo o esistente.</span><span class="sxs-lookup"><span data-stu-id="64b46-267">When you open a new tab or new browser window, Windows PowerShell Web Access prompts you to disconnect your current session and start a new session, so that you can connect to the new (or the same) remote computer.</span></span> <span data-ttu-id="64b46-268">Se si vogliono stabilire due o più sessioni separate a diversi computer remoti, una funzionalità di Internet Explorer consente tuttavia di creare una nuova sessione.</span><span class="sxs-lookup"><span data-stu-id="64b46-268">If two or more separate sessions to different remote computers are desired, however, a feature in Internet Explorer lets you create a new session.</span></span> <span data-ttu-id="64b46-269">Per avviare una nuova sessione del browser in Internet Explorer, premere **ALT**, aprire il menu **File** e quindi scegliere **Nuova sessione**.</span><span class="sxs-lookup"><span data-stu-id="64b46-269">To start a new browser session in Internet Explorer, press **ALT**, open the **File** menu, and then select **New Session**.</span></span> <span data-ttu-id="64b46-270">Aprire quindi il sito Web di Accesso Web Windows PowerShell nella nuova sessione ed eseguire l'accesso a un altro computer remoto.</span><span class="sxs-lookup"><span data-stu-id="64b46-270">Then, open the Windows PowerShell Web Access website in the new session, and sign in to access another remote computer.</span></span>

    <span data-ttu-id="64b46-271">Quando il gateway di Accesso Web Windows PowerShell è in esecuzione in Windows Server 2012 R2, gli utenti possono aprire più connessioni a computer remoti in schede del browser diverse.</span><span class="sxs-lookup"><span data-stu-id="64b46-271">When the Windows PowerShell Web Access gateway is running on Windows Server 2012 R2, users can open multiple connections to remote computers in different browser tabs.</span></span> <span data-ttu-id="64b46-272">Per aprire più connessioni a un computer remoto con la console di Windows PowerShell basata sul Web, verificare con l'amministratore del gateway di Accesso Web Windows PowerShell se questa funzionalità è supportata dal server gateway.</span><span class="sxs-lookup"><span data-stu-id="64b46-272">If you want to open more than one connection to a remote computer by using the web-based Windows PowerShell console, check with your Windows PowerShell Web Access gateway administrator to see if this feature is supported by the gateway server.</span></span>

-   <span data-ttu-id="64b46-273"><span class="label">Sessioni di Windows PowerShell persistenti (riconnessione).</span></span><span class="sxs-lookup"><span data-stu-id="64b46-273"><span class="label">Persistent Windows PowerShell sessions (Reconnection).</span></span></span>   <span data-ttu-id="64b46-274">Dopo il timeout del gateway di Accesso Web Windows PowerShell, la connessione remota tra il gateway e il computer di destinazione viene chiusa.</span><span class="sxs-lookup"><span data-stu-id="64b46-274">After you time out of the Windows PowerShell Web Access gateway, the remote connection between the gateway and the target computer is closed.</span></span> <span data-ttu-id="64b46-275">L'elaborazione degli eventuali cmdlet e script in corso viene arrestata.</span><span class="sxs-lookup"><span data-stu-id="64b46-275">This stops any cmdlets or scripts that are currently in process.</span></span> <span data-ttu-id="64b46-276">È consigliabile usare l'infrastruttura **-Job** di Windows PowerShell quando si eseguono attività di lunga durata, in modo da avviare i processi, disconnettersi dal computer e riconnettersi in seguito mantenendo i processi persistenti.</span><span class="sxs-lookup"><span data-stu-id="64b46-276">You are encouraged to use the Windows PowerShell **-Job** infrastructure when you are performing long-running tasks, so that you can start jobs, disconnect from the computer, reconnect later, and have jobs persist.</span></span> <span data-ttu-id="64b46-277">Un altro vantaggio dell'uso dei cmdlet **-Job** è la possibilità di avviarli con Accesso Web Windows PowerShell e quindi disconnettersi e riconnettersi successivamente sia con Accesso Web Windows PowerShell che con un altro host, ad esempio Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="64b46-277">Another benefit of using **-Job** cmdlets is that you can start them by using Windows PowerShell Web Access, sign out, and then reconnect later, either by running Windows PowerShell Web Access or another host (such as Windows PowerShell® Integrated Scripting Environment (ISE)).</span></span>

-   <span data-ttu-id="64b46-278"><span class="label">Ridimensionamento della console.</span></span><span class="sxs-lookup"><span data-stu-id="64b46-278"><span class="label">Console resizing.</span></span></span>   <span data-ttu-id="64b46-279">La finestra della console di **PowerShell.exe** può essere ridimensionata nei tre modi seguenti.</span><span class="sxs-lookup"><span data-stu-id="64b46-279">The **PowerShell.exe** console window can be resized in the following three ways.</span></span>

    -   <span data-ttu-id="64b46-280">Trascinare e adattare le dimensioni della finestra della console con il mouse.</span><span class="sxs-lookup"><span data-stu-id="64b46-280">Drag and adjust the console window size with a mouse</span></span>

    -   <span data-ttu-id="64b46-281">Modificare le proprietà di altezza e larghezza tramite un'interfaccia utente grafica per le proprietà della console.</span><span class="sxs-lookup"><span data-stu-id="64b46-281">Change the height and width properties by using a GUI for console properties</span></span>

    -   <span data-ttu-id="64b46-282">Modificare l'altezza e la larghezza delle finestre della console con un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="64b46-282">Changing the height and width of console windows with a cmdlet</span></span>

        <span data-ttu-id="64b46-283">La finestra della console per Accesso Web Windows PowerShell può essere configurata con i cmdlet, come indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="64b46-283">The console window for Windows PowerShell Web Access can be configured by using the cmdlets as follows.</span></span> <span data-ttu-id="64b46-284">Nell'esempio seguente un utente modifica la larghezza della console di Accesso Web Windows PowerShell in **20**.</span><span class="sxs-lookup"><span data-stu-id="64b46-284">In the following example, a user changes the width of Windows PowerShell Web Access console to **20**.</span></span>

        [<span data-ttu-id="64b46-285">Copy</span><span class="sxs-lookup"><span data-stu-id="64b46-285">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_778d5e55-9195-4bd7-b313-d1fbca7876e4'); "Copia negli Appunti.")

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        <span data-ttu-id="64b46-286">Si può modificare l'altezza della console in modo simile.</span><span class="sxs-lookup"><span data-stu-id="64b46-286">You can change the height of the console in a similar manner.</span></span>

        <span data-ttu-id="64b46-287">Altri esempi per personalizzare la visualizzazione della console sono disponibili nel [Blog del Team di Windows PowerShell](http://blogs.msdn.com/b/powershell/).</span><span class="sxs-lookup"><span data-stu-id="64b46-287">Additional examples for customizing the console view are available in the [Windows PowerShell Team Blog](http://blogs.msdn.com/b/powershell/).</span></span>

<span data-ttu-id="64b46-288"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Vedere anche</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="64b46-288"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="64b46-289">[Informazioni di riferimento per i cmdlet di Windows PowerShell](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
[Windows PowerShell su Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
[Archivio di Script Center su TechNet](http://gallery.technet.microsoft.com/scriptcenter)
[Script Center: blog "Hey, Scripting Guy!"](https://technet.microsoft.com/scriptcenter)
[Blog del team di Windows PowerShell](http://blogs.msdn.com/b/powershell/)</span><span class="sxs-lookup"><span data-stu-id="64b46-289">[Windows PowerShell Cmdlet Reference](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
[Windows PowerShell on Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
[TechNet Script Center Repository](http://gallery.technet.microsoft.com/scriptcenter)
[Script Center - Hey, Scripting Guy!](https://technet.microsoft.com/scriptcenter)
[Windows PowerShell Team Blog](http://blogs.msdn.com/b/powershell/)</span></span>

<span data-ttu-id="64b46-290"><span>Show:</span> Inherited Protected</span><span class="sxs-lookup"><span data-stu-id="64b46-290"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="64b46-291"><span class="stdr-votetitle">Questa pagina è stata utile?</span></span><span class="sxs-lookup"><span data-stu-id="64b46-291"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="64b46-292">Sì No</span><span class="sxs-lookup"><span data-stu-id="64b46-292">Yes No</span></span>

<span data-ttu-id="64b46-293">Altri suggerimenti?</span><span class="sxs-lookup"><span data-stu-id="64b46-293">Additional feedback?</span></span>

<span data-ttu-id="64b46-294"><span class="stdr-count"><span class="stdr-charcnt">1500</span> caratteri rimanenti</span> Invia Ignora</span><span class="sxs-lookup"><span data-stu-id="64b46-294"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="64b46-295"><span class="stdr-thankyou">Grazie</span></span><span class="sxs-lookup"><span data-stu-id="64b46-295"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="64b46-296"><span class="stdr-appreciate">I suggerimenti degli utenti sono importanti.</span></span><span class="sxs-lookup"><span data-stu-id="64b46-296"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="64b46-297">Gestisci il tuo profilo</span><span class="sxs-lookup"><span data-stu-id="64b46-297">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="64b46-298"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Commenti e suggerimenti sul sito</a> Commenti e suggerimenti sul sito</span><span class="sxs-lookup"><span data-stu-id="64b46-298"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="64b46-299"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="64b46-299"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="64b46-300">Raccontaci la tua esperienza</span><span class="sxs-lookup"><span data-stu-id="64b46-300">Tell us about your experience...</span></span>

<span data-ttu-id="64b46-301">La pagina è stata caricata rapidamente?</span><span class="sxs-lookup"><span data-stu-id="64b46-301">Did the page load quickly?</span></span>

<span data-ttu-id="64b46-302"><span> Sì<span> </span></span> <span> No<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="64b46-302"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="64b46-303">Ti piace la grafica?</span><span class="sxs-lookup"><span data-stu-id="64b46-303">Do you like the page design?</span></span>

<span data-ttu-id="64b46-304"><span> Sì<span> </span></span> <span> No<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="64b46-304"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="64b46-305">Parla con noi</span><span class="sxs-lookup"><span data-stu-id="64b46-305">Tell us more</span></span>

-   [<span data-ttu-id="64b46-306">Newsletter Flash</span><span class="sxs-lookup"><span data-stu-id="64b46-306">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="64b46-307">Contattaci</span><span class="sxs-lookup"><span data-stu-id="64b46-307">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="64b46-308">Informativa sulla privacy</span><span class="sxs-lookup"><span data-stu-id="64b46-308">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="64b46-309">Condizioni per l'utilizzo</span><span class="sxs-lookup"><span data-stu-id="64b46-309">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="64b46-310">Marchi</span><span class="sxs-lookup"><span data-stu-id="64b46-310">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="64b46-311">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="64b46-311">© 2016 Microsoft</span></span>

<span data-ttu-id="64b46-312">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="64b46-312">© 2016 Microsoft</span></span>

<span data-ttu-id="64b46-313">Il codice e gli script di terze parti, collegati al presente sito o a cui il sito Web fa riferimento, vengono ceduti in licenza all'utente dalle terze parti proprietarie di tale codice, non da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="64b46-313">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="64b46-314">Vedere le condizioni d'uso di Ajax CDN di ASP.NET – http://www.asp.net/ajaxlibrary/CDN.ashx.</span><span class="sxs-lookup"><span data-stu-id="64b46-314">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

