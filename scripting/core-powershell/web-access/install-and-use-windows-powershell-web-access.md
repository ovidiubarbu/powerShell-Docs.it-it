---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: installare e usare accesso web windows powershell
ms.openlocfilehash: a860f7c22829da46f0458ea729fa0afd1fe4fb6f
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
#  <a name="install-and-use-windows-powershell-web-access"></a><span data-ttu-id="0e23c-103">Installare e usare Accesso Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e23c-103">Install and Use Windows PowerShell Web Access</span></span>

<span data-ttu-id="0e23c-104">Ultimo aggiornamento: 5 novembre 2013</span><span class="sxs-lookup"><span data-stu-id="0e23c-104">Updated: November 5, 2013</span></span>

<span data-ttu-id="0e23c-105">Si applica a: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="0e23c-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="0e23c-106">Introdotta per la prima volta in Windows Server® 2012, la funzionalità Accesso Web Windows PowerShell® funge da gateway di Windows PowerShell, fornendo una console di Windows PowerShell basata sul Web destinata a un computer remoto.</span><span class="sxs-lookup"><span data-stu-id="0e23c-106">Windows PowerShell® Web Access, first introduced in Windows Server® 2012, acts as a Windows PowerShell gateway, providing a web-based Windows PowerShell console that is targeted at a remote computer.</span></span> <span data-ttu-id="0e23c-107">Consente ai professionisti IT di eseguire comandi e script di Windows PowerShell da una console di Windows PowerShell in un Web browser, senza installare Windows PowerShell, software di gestione remoto o plug-in del browser nel dispositivo client.</span><span class="sxs-lookup"><span data-stu-id="0e23c-107">It enables IT Pros to run Windows PowerShell commands and scripts from a Windows PowerShell console in a web browser, with no Windows PowerShell, remote management software, or browser plug-in installation necessary on the client device.</span></span> <span data-ttu-id="0e23c-108">Per eseguire la console di Windows PowerShell basata sul Web sono sufficienti un gateway di Accesso Web Windows PowerShell configurato correttamente e un dispositivo client con un browser che supporta JavaScript® e accetta i cookie.</span><span class="sxs-lookup"><span data-stu-id="0e23c-108">All that is required to run the web-based Windows PowerShell console is a properly-configured Windows PowerShell Web Access gateway, and a client device browser that supports JavaScript® and accepts cookies.</span></span>

<span data-ttu-id="0e23c-109">Tali dispositivi client possono essere costituiti ad esempio da computer portatili, PC non utilizzati a scopo professionale, computer in prestito, computer tablet, chioschi Web, computer che non eseguono un sistema operativo Windows e telefoni cellulari dotati di browser.</span><span class="sxs-lookup"><span data-stu-id="0e23c-109">Examples of client devices include laptops, non-work personal computers, borrowed computers, tablet computers, web kiosks, computers that are not running a Windows-based operating system, and cell phone browsers.</span></span> <span data-ttu-id="0e23c-110">I professionisti IT possono eseguire attività di gestione critiche in server Windows remoti utilizzando dispositivi che hanno accesso a una connessione Internet e a un Web browser.</span><span class="sxs-lookup"><span data-stu-id="0e23c-110">IT Pros can perform critical management tasks on remote Windows-based servers from devices that have access to an Internet connection and a web browser.</span></span>

<span data-ttu-id="0e23c-111">Dopo avere installato e configurato correttamente il gateway, gli utenti possono accedere a una console di Windows PowerShell usando un Web browser.</span><span class="sxs-lookup"><span data-stu-id="0e23c-111">After successful gateway setup and configuration, users can access a Windows PowerShell console by using a web browser.</span></span> <span data-ttu-id="0e23c-112">Aprendo il sito Web protetto di Accesso Web Windows PowerShell ed effettuando l'autenticazione, possono quindi eseguire una console di Windows PowerShell basata sul Web.</span><span class="sxs-lookup"><span data-stu-id="0e23c-112">When users open the secured Windows PowerShell Web Access website, they can run a web-based Windows PowerShell console after successful authentication.</span></span>

<span data-ttu-id="0e23c-113">Per installare e configurare Accesso Web Windows PowerShell, è necessaria una procedura in tre passaggi:</span><span class="sxs-lookup"><span data-stu-id="0e23c-113">Windows PowerShell Web Access setup and configuration is a three-step process:</span></span>

1.  <span data-ttu-id="0e23c-114">Installazione di Accesso Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e23c-114">Installing Windows PowerShell Web Access</span></span>

2.  <span data-ttu-id="0e23c-115">Configurazione del gateway</span><span class="sxs-lookup"><span data-stu-id="0e23c-115">Configuring the gateway</span></span>

3.  <span data-ttu-id="0e23c-116">Configurazione delle regole di autorizzazione che consentono l'accesso utente alla console di Windows PowerShell basata sul Web</span><span class="sxs-lookup"><span data-stu-id="0e23c-116">Configuring authorization rules that allow users access to the web-based Windows PowerShell console</span></span>

<span data-ttu-id="0e23c-117">Prima di installare e configurare Accesso Web Windows PowerShell, è consigliabile leggere l'intera guida, che include istruzioni su come installare, proteggere e disinstallare Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0e23c-117">Before you install and configure Windows PowerShell Web Access, we recommend that you read this entire guide, which includes instructions about how to install, secure, and uninstall Windows PowerShell Web Access.</span></span> <span data-ttu-id="0e23c-118">L'argomento [Usare la console di Windows PowerShell basata sul Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx) illustra il modo in cui l'utente accede alla console basata sul Web e descrive le limitazioni e le differenze tra la console di Windows PowerShell basata sul Web e la console di **powershell.exe**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-118">The [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx) topic describes how users sign in to the web-based console, and covers limitations and differences between the web-based Windows PowerShell console and the **powershell.exe** console.</span></span> <span data-ttu-id="0e23c-119">Gli utenti finali della console basata sul Web devono leggere l'argomento [Usare la console di Windows PowerShell basata sul Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx), ma possono evitare di leggere il resto della guida.</span><span class="sxs-lookup"><span data-stu-id="0e23c-119">End users of the web-based console should read [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx), but do not need to read the rest of this guide.</span></span>

<span data-ttu-id="0e23c-120">Questo articolo non fornisce indicazioni dettagliate sulle operazioni nel server Web (IIS), ma illustra solo le procedure necessarie per configurare il gateway di Accesso Web Windows PowerShell come illustrato nell'argomento.</span><span class="sxs-lookup"><span data-stu-id="0e23c-120">This topic does not provide in-depth Web Server (IIS) operations guidance; only those steps required to configure the Windows PowerShell Web Access gateway are described in this topic.</span></span> <span data-ttu-id="0e23c-121">Per altre informazioni sulla configurazione e la protezione dei siti Web in IIS, consultare le risorse della documentazione di IIS indicate nella sezione Vedere anche.</span><span class="sxs-lookup"><span data-stu-id="0e23c-121">For more information about configuring and securing websites in IIS, see the IIS documentation resources in the See Also section.</span></span>

<span data-ttu-id="0e23c-122">Il diagramma seguente mostra come funziona Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0e23c-122">The following diagram shows how Windows PowerShell Web Access works.</span></span>

<span><img src="https://i-technet.sec.s-msft.com/dynimg/IC564303.jpeg" title="Windows PowerShell Web Access diagram" alt="Windows PowerShell Web Access diagram" id="ee15fa8f-ce13-49e5-933d-514f6d60a2b1" /></span>

<span data-ttu-id="0e23c-123">In questo argomento</span><span class="sxs-lookup"><span data-stu-id="0e23c-123">In this topic:</span></span>

-   [<span data-ttu-id="0e23c-124">Requisiti per l'esecuzione di Accesso Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e23c-124">Requirements for running Windows PowerShell Web Access</span></span>](#BKMK_reqs)

-   [<span data-ttu-id="0e23c-125">Browser e dispositivi client supportati</span><span class="sxs-lookup"><span data-stu-id="0e23c-125">Browser and client device support</span></span>](#BKMK_browser)

-   [<span data-ttu-id="0e23c-126">Distribuzione consigliata (rapida)</span><span class="sxs-lookup"><span data-stu-id="0e23c-126">Recommended (quick) deployment</span></span>](#BKMK_recm)

-   [<span data-ttu-id="0e23c-127">Distribuzione personalizzata</span><span class="sxs-lookup"><span data-stu-id="0e23c-127">Custom deployment</span></span>](#BKMK_custom)

-   [<span data-ttu-id="0e23c-128">Configurare un certificato autentico</span><span class="sxs-lookup"><span data-stu-id="0e23c-128">Configure a genuine certificate</span></span>](#BKMK_configcert)

<a href="" id="BKMK_reqs"></a>

<span data-ttu-id="0e23c-129"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Requisiti per l'esecuzione di Accesso Web Windows PowerShell</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_0" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="0e23c-129"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Requirements for running Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_0" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="0e23c-130">Accesso Web Windows PowerShell richiede il server Web (IIS), .NET Framework 4.5 e Windows PowerShell 3.0 o 4.0 in esecuzione nel server in cui si vuole eseguire il gateway.</span><span class="sxs-lookup"><span data-stu-id="0e23c-130">Windows PowerShell Web Access requires Web Server (IIS), .NET Framework 4.5, and Windows PowerShell 3.0 or Windows PowerShell 4.0 to be running on the server on which you want to run the gateway.</span></span> <span data-ttu-id="0e23c-131">È possibile installare Accesso Web Windows PowerShell in un server che esegue Windows Server 2012 R2 o Windows Server 2012 usando l'Aggiunta guidata ruoli e funzionalità in Server Manager o i cmdlet di distribuzione di Windows PowerShell per Server Manager.</span><span class="sxs-lookup"><span data-stu-id="0e23c-131">You can install Windows PowerShell Web Access on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using either the Add Roles and Features Wizard in Server Manager, or Windows PowerShell deployment cmdlets for Server Manager.</span></span> <span data-ttu-id="0e23c-132">Se si installa Accesso Web Windows PowerShell con Server Manager o i relativi cmdlet di distribuzione, le funzionalità e ruoli necessari vengono aggiunti automaticamente durante il processo di installazione.</span><span class="sxs-lookup"><span data-stu-id="0e23c-132">When you install Windows PowerShell Web Access by using Server Manager or its deployment cmdlets, required roles and features are automatically added as part of the installation process.</span></span>

<span data-ttu-id="0e23c-133">Accesso Web Windows PowerShell consente agli utenti remoti di accedere ai computer dell'organizzazione usando Windows PowerShell in un Web browser.</span><span class="sxs-lookup"><span data-stu-id="0e23c-133">Windows PowerShell Web Access allows remote users to access computers in your organization by using Windows PowerShell in a web browser.</span></span> <span data-ttu-id="0e23c-134">Anche se Accesso Web Windows PowerShell è uno strumento di gestione pratico e potente, l'accesso basato sul Web costituisce un potenziale rischio per la sicurezza e deve essere configurato nel modo più sicuro possibile.</span><span class="sxs-lookup"><span data-stu-id="0e23c-134">Although Windows PowerShell Web Access is a convenient and powerful management tool, the web-based access poses security risks, and should be configured as securely as possible.</span></span> <span data-ttu-id="0e23c-135">Per la configurazione del gateway di Accesso Web Windows PowerShell si consiglia di usare tutti i livelli di sicurezza disponibili, ovvero sia le regole di autorizzazione basate su cmdlet incluse in Accesso Web Windows PowerShell, sia i livelli di sicurezza disponibili nel server Web (IIS) e nelle applicazioni di terze parti.</span><span class="sxs-lookup"><span data-stu-id="0e23c-135">We recommend that administrators who configure the Windows PowerShell Web Access gateway use available security layers, both the cmdlet-based authorization rules included with Windows PowerShell Web Access, and security layers that are available in Web Server (IIS) and third-party applications.</span></span> <span data-ttu-id="0e23c-136">Nel presente documento sono illustrati sia esempi non sicuri, da utilizzare solo negli ambienti di test, sia esempi di configurazione consigliati per le distribuzioni sicure.</span><span class="sxs-lookup"><span data-stu-id="0e23c-136">This documentation includes both unsecure examples that are only recommended for test environments, as well as examples that are recommended for secure deployments.</span></span>

<a href="" id="BKMK_browser"></a>

<span data-ttu-id="0e23c-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser e dispositivi client supportati</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="0e23c-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser and client device support</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="0e23c-138">Accesso Web Windows PowerShell supporta i browser Internet seguenti.</span><span class="sxs-lookup"><span data-stu-id="0e23c-138">Windows PowerShell Web Access supports the following Internet browsers.</span></span> <span data-ttu-id="0e23c-139">Anche se i browser per dispositivi mobili non sono ufficialmente supportati, molti potrebbero essere in grado di eseguire la console di Windows PowerShell basata sul Web.</span><span class="sxs-lookup"><span data-stu-id="0e23c-139">Although mobile browsers are not officially supported, many may be able to run the web-based Windows PowerShell console.</span></span> <span data-ttu-id="0e23c-140">Anche gli altri browser che accettano cookie, eseguono JavaScript e aprono i siti Web HTTPS dovrebbero funzionare, ma non sono stati testati ufficialmente.</span><span class="sxs-lookup"><span data-stu-id="0e23c-140">Other browsers that accept cookies, run JavaScript, and run HTTPS websites are expected to work, but are not officially tested.</span></span>

###

<span data-ttu-id="0e23c-141"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser per computer desktop supportati</span></a></span><span class="sxs-lookup"><span data-stu-id="0e23c-141"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Supported desktop computer browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="0e23c-142">Windows® Internet Explorer® per Microsoft Windows® 8.0, 9.0, 10.0 e 11.0</span><span class="sxs-lookup"><span data-stu-id="0e23c-142">Windows® Internet Explorer® for Microsoft Windows® 8.0, 9.0, 10.0, and 11.0</span></span>

-   <span data-ttu-id="0e23c-143">Mozilla Firefox® 10.0.2</span><span class="sxs-lookup"><span data-stu-id="0e23c-143">Mozilla Firefox® 10.0.2</span></span>

-   <span data-ttu-id="0e23c-144">Google Chrome™ 17.0.963.56m per Windows</span><span class="sxs-lookup"><span data-stu-id="0e23c-144">Google Chrome™ 17.0.963.56m for Windows</span></span>

-   <span data-ttu-id="0e23c-145">Apple Safari® 5.1.2 per Windows</span><span class="sxs-lookup"><span data-stu-id="0e23c-145">Apple Safari® 5.1.2 for Windows</span></span>

-   <span data-ttu-id="0e23c-146">Apple Safari® 5.1.2 per Mac OS®</span><span class="sxs-lookup"><span data-stu-id="0e23c-146">Apple Safari 5.1.2 for Mac OS®</span></span>

###

<span data-ttu-id="0e23c-147"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Dispositivi mobili e browser sottoposti ai test minimi</span></a></span><span class="sxs-lookup"><span data-stu-id="0e23c-147"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Minimally-tested mobile devices or browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="0e23c-148">Windows Phone 7 e 7.5</span><span class="sxs-lookup"><span data-stu-id="0e23c-148">Windows Phone 7 and 7.5</span></span>

-   <span data-ttu-id="0e23c-149">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span><span class="sxs-lookup"><span data-stu-id="0e23c-149">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span></span>

-   <span data-ttu-id="0e23c-150">Apple Safari 5.0.1 per sistema operativo iPhone</span><span class="sxs-lookup"><span data-stu-id="0e23c-150">Apple Safari for iPhone operating system 5.0.1</span></span>

-   <span data-ttu-id="0e23c-151">Sistema operativo Apple Safari per iPad 2 5.0.1</span><span class="sxs-lookup"><span data-stu-id="0e23c-151">Apple Safari for iPad 2 operating system 5.0.1</span></span>

###

<span data-ttu-id="0e23c-152"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Requisiti del browser</span></a></span><span class="sxs-lookup"><span data-stu-id="0e23c-152"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser requirements</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="0e23c-153">Per usare la console di Accesso Web Windows PowerShell basata sul Web, i browser devono:</span><span class="sxs-lookup"><span data-stu-id="0e23c-153">To use the Windows PowerShell Web Access web-based console, browsers must do the following.</span></span>

-   <span data-ttu-id="0e23c-154">Consentire i cookie dal sito Web del gateway di Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0e23c-154">Allow cookies from the Windows PowerShell Web Access gateway website.</span></span>

-   <span data-ttu-id="0e23c-155">Sia in grado di aprire e leggere le pagine HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0e23c-155">Be able to open and read HTTPS pages.</span></span>

-   <span data-ttu-id="0e23c-156">Aprire ed eseguire siti Web che usano JavaScript.</span><span class="sxs-lookup"><span data-stu-id="0e23c-156">Open and run websites that use JavaScript.</span></span>

<a href="" id="BKMK_recm"></a>

<span data-ttu-id="0e23c-157"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Distribuzione consigliata (rapida)</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="0e23c-157"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Recommended (quick) deployment</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="0e23c-158">È possibile installare il gateway di Accesso Web Windows PowerShell in un server che esegue Windows Server 2012 R2 o Windows Server 2012 usando i cmdlet di Windows PowerShell o l'Aggiunta guidata ruoli e funzionalità aperta dall'interno di Server Manager.</span><span class="sxs-lookup"><span data-stu-id="0e23c-158">You can install the Windows PowerShell Web Access gateway on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using either Windows PowerShell cmdlets, or by using the Add Roles and Features Wizard that is opened from within Server Manager.</span></span> <span data-ttu-id="0e23c-159">Per l'installazione e la configurazione rapide, usare i cmdlet di Windows PowerShell, come illustrato in questa sezione.</span><span class="sxs-lookup"><span data-stu-id="0e23c-159">For quick installation and configuration, use Windows PowerShell cmdlets, as described in this section.</span></span>

-   [<span data-ttu-id="0e23c-160">Passaggio 1: Installare Accesso Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e23c-160">Step 1: Install Windows PowerShell Web Access</span></span>](#BKMK_step1)

-   [<span data-ttu-id="0e23c-161">Passaggio 2: Configurare il gateway</span><span class="sxs-lookup"><span data-stu-id="0e23c-161">Step 2: Configure the gateway</span></span>](#BKMK_step2)

-   [<span data-ttu-id="0e23c-162">Passaggio 3: Configurare una regola di autorizzazione restrittiva</span><span class="sxs-lookup"><span data-stu-id="0e23c-162">Step 3: Configure a restrictive authorization rule</span></span>](#BKMK_step3)

<a href="" id="BKMK_step1"></a>
###

<span data-ttu-id="0e23c-163"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Passaggio 1: Installare Accesso Web Windows PowerShell</span></a></span><span class="sxs-lookup"><span data-stu-id="0e23c-163"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Install Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a><span data-ttu-id="0e23c-164">Per installare Accesso Web Windows PowerShell tramite i cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e23c-164">To install Windows PowerShell Web Access by using Windows PowerShell cmdlets</span></span>

1.  <span data-ttu-id="0e23c-165">Per aprire una sessione di Windows PowerShell con diritti utente elevati, eseguire una di queste operazioni.</span><span class="sxs-lookup"><span data-stu-id="0e23c-165">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="0e23c-166">Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni e scegliere **Esegui come amministratore**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-166">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="0e23c-167">Nella schermata **Start** di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** e quindi scegliere **Esegui come amministratore**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-167">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="0e23c-168"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Nota </span></span><span class="sxs-lookup"><span data-stu-id="0e23c-168"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="0e23c-169">In Windows PowerShell 3.0 e 4.0 non è necessario importare il modulo dei cmdlet di Server Manager nella sessione di Windows PowerShell prima di eseguire i cmdlet che fanno parte di questo modulo.</span><span class="sxs-lookup"><span data-stu-id="0e23c-169">In Windows PowerShell 3.0 and 4.0, there is no need to import the Server Manager cmdlet module into the Windows PowerShell session before running cmdlets that are part of the module.</span></span> <span data-ttu-id="0e23c-170">Un modulo viene importato automaticamente alla prima esecuzione di un cmdlet che fa parte del modulo.</span><span class="sxs-lookup"><span data-stu-id="0e23c-170">A module is automatically imported the first time you run a cmdlet that is part of the module.</span></span> <span data-ttu-id="0e23c-171">Inoltre, per i cmdlet di Windows PowerShell non viene fatta distinzione tra maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="0e23c-171">Also, Windows PowerShell cmdlets are not case-sensitive.</span></span></p></td>
    </tr>
    </tbody>
    </table>

2.  <span data-ttu-id="0e23c-172">Digitare il codice seguente, in cui *nome_computer* rappresenta un computer remoto in cui si vuole installare Accesso Web Windows PowerShell, se applicabile, quindi premere **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-172">Type the following, and then press **Enter**, where *computer_name* represents a remote computer on which you want to install Windows PowerShell Web Access, if applicable.</span></span> <span data-ttu-id="0e23c-173">Il parametro <span class="code">Restart</span> riavvia automaticamente i server di destinazione, se necessario.</span><span class="sxs-lookup"><span data-stu-id="0e23c-173">The <span class="code">Restart</span> parameter automatically restarts destination servers if required.</span></span>

    [<span data-ttu-id="0e23c-174">Copy</span><span class="sxs-lookup"><span data-stu-id="0e23c-174">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_374a9c21-4f6e-471e-b957-bb190a594533'); "Copia negli Appunti.")

        Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="0e23c-175"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Nota </span></span><span class="sxs-lookup"><span data-stu-id="0e23c-175"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="0e23c-176">Se si installa Accesso Web Windows PowerShell usando i cmdlet di Windows PowerShell, gli strumenti di gestione del server Web (IIS) non vengono installati per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="0e23c-176">Installing Windows PowerShell Web Access by using Windows PowerShell cmdlets does not add Web Server (IIS) management tools by default.</span></span> <span data-ttu-id="0e23c-177">Per installare gli strumenti di gestione nello stesso server che ospita il gateway di Accesso Web Windows PowerShell, aggiungere il parametro <span class="code">IncludeManagementTools</span> al comando di installazione, come specificato in questo passaggio.</span><span class="sxs-lookup"><span data-stu-id="0e23c-177">If you want to install the management tools on the same server as the Windows PowerShell Web Access gateway, add the <span class="code">IncludeManagementTools</span> parameter to the installation command (as provided in this step).</span></span> <span data-ttu-id="0e23c-178">Se il sito Web di Accesso Web Windows PowerShell deve essere gestito da un computer remoto, installare lo snap-in Gestione IIS installando <a href="http://go.microsoft.com/fwlink/?LinkID=304145">Strumenti di amministrazione remota del server per Windows 8.1</a> o <a href="http://go.microsoft.com/fwlink/p/?LinkID=238560">Strumenti di amministrazione remota del server per Windows 8</a> nel computer da cui si vuole gestire il gateway.</span><span class="sxs-lookup"><span data-stu-id="0e23c-178">If you are managing the Windows PowerShell Web Access website from a remote computer, install the IIS Manager snap-in by installing <a href="http://go.microsoft.com/fwlink/?LinkID=304145">Remote Server Administration Tools for Windows 8.1</a> or <a href="http://go.microsoft.com/fwlink/p/?LinkID=238560">Remote Server Administration Tools for Windows 8</a> on the computer from which you want to manage the gateway.</span></span></p></td>
    </tr>
    </tbody>
    </table>

    <span data-ttu-id="0e23c-179">Per installare ruoli e funzionalità in un disco rigido virtuale offline, è necessario aggiungere i parametri <span class="code">ComputerName</span> e <span class="code">VHD</span>.</span><span class="sxs-lookup"><span data-stu-id="0e23c-179">To install roles and features on an offline VHD, you must add both the <span class="code">ComputerName</span> parameter and the <span class="code">VHD</span> parameter.</span></span> <span data-ttu-id="0e23c-180">Il parametro <span class="code">ComputerName</span> contiene il nome del server in cui montare il disco rigido virtuale e il parametro <span class="code">VHD</span> contiene il percorso del file VHD nel server specificato.</span><span class="sxs-lookup"><span data-stu-id="0e23c-180">The <span class="code">ComputerName</span> parameter contains the name of the server on which to mount the VHD, and the <span class="code">VHD</span> parameter contains the path to the VHD file on the specified server.</span></span>

    [<span data-ttu-id="0e23c-181">Copy</span><span class="sxs-lookup"><span data-stu-id="0e23c-181">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_d841d509-347e-49d0-bf54-8d1f306bece6'); "Copia negli Appunti.")

        Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart

3.  <span data-ttu-id="0e23c-182">Al termine dell'installazione verificare che Accesso Web Windows PowerShell sia stato installato nei server di destinazione eseguendo il cmdlet **Get-WindowsFeature** in un server di destinazione, all'interno di una console di Windows PowerShell aperta con diritti utente elevati.</span><span class="sxs-lookup"><span data-stu-id="0e23c-182">When installation is complete, verify that Windows PowerShell Web Access was installed on destination servers by running the **Get-WindowsFeature** cmdlet on a destination server, in a Windows PowerShell console that has been opened with elevated user rights.</span></span> <span data-ttu-id="0e23c-183">È anche possibile verificare che Accesso Web Windows PowerShell sia stato installato nella console di Server Manager selezionando un server di destinazione nella pagina **Tutti i server** e quindi visualizzando il riquadro **Ruoli e funzionalità** per il server selezionato.</span><span class="sxs-lookup"><span data-stu-id="0e23c-183">You can also verify that Windows PowerShell Web Access was installed in the Server Manager console, by selecting a destination server on the **All Servers** page, and then viewing the **Roles and Features** tile for the selected server.</span></span> <span data-ttu-id="0e23c-184">È anche possibile visualizzare il file Leggimi per Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0e23c-184">You can also view the readme file for Windows PowerShell Web Access.</span></span>

4.  <span data-ttu-id="0e23c-185">Dopo l'installazione di Accesso Web Windows PowerShell viene richiesto di esaminare il file Leggimi, che contiene istruzioni sulle operazioni di configurazione di base necessarie per il gateway.</span><span class="sxs-lookup"><span data-stu-id="0e23c-185">After Windows PowerShell Web Access is installed, you are prompted to review the readme file, which contains basic, required setup instructions for the gateway.</span></span> <span data-ttu-id="0e23c-186">Queste istruzioni sono riportate anche nella sezione successiva, [Passaggio 2: Configurare il gateway](#BKMK_step2).</span><span class="sxs-lookup"><span data-stu-id="0e23c-186">These setup instructions are also in the following section, [Step 2: Configure the gateway](#BKMK_step2).</span></span> <span data-ttu-id="0e23c-187">Il percorso del file Leggimi è: <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span><span class="sxs-lookup"><span data-stu-id="0e23c-187">The path to the readme file is <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span></span>

<a href="" id="BKMK_step2"></a>
###

<span data-ttu-id="0e23c-188"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Passaggio 2: Configurare il gateway</span></a></span><span class="sxs-lookup"><span data-stu-id="0e23c-188"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Configure the gateway</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="0e23c-189">Il cmdlet **Install-PswaWebApplication** costituisce una soluzione rapida per configurare Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0e23c-189">The **Install-PswaWebApplication** cmdlet is a quick way to get Windows PowerShell Web Access configured.</span></span> <span data-ttu-id="0e23c-190">Anche se è possibile aggiungere il parametro <span class="code">UseTestCertificate</span> al cmdlet <span class="code">Install-PswaWebApplication</span> per installare un certificato SSL autofirmato a scopo di test, questa configurazione non è sicura. Per un ambiente di produzione sicuro, usare sempre un certificato SSL valido firmato da un'autorità di certificazione (CA).</span><span class="sxs-lookup"><span data-stu-id="0e23c-190">Although you can add the <span class="code">UseTestCertificate</span> parameter to the <span class="code">Install-PswaWebApplication</span> cmdlet to install a self-signed SSL certificate for test purposes, this is not secure; for a secure production environment, always use a valid SSL certificate that has been signed by a certification authority (CA).</span></span> <span data-ttu-id="0e23c-191">Gli amministratori possono sostituire il certificato di test con un certificato firmato a scelta, utilizzando la console Gestione IIS.</span><span class="sxs-lookup"><span data-stu-id="0e23c-191">Administrators can replace the test certificate with a signed certificate of their choice by using the IIS Manager console.</span></span>

<span data-ttu-id="0e23c-192">Per completare la configurazione dell'applicazione Web Accesso Web Windows PowerShell, è possibile eseguire il cmdlet <span class="code">Install-PswaWebApplication</span> o la procedura di configurazione con interfaccia grafica in Gestione IIS.</span><span class="sxs-lookup"><span data-stu-id="0e23c-192">You can complete Windows PowerShell Web Access web application configuration either by running the <span class="code">Install-PswaWebApplication</span> cmdlet or by performing GUI-based configuration steps in IIS Manager.</span></span> <span data-ttu-id="0e23c-193">Per impostazione predefinita, il cmdlet installa l'applicazione Web **pswa** e il relativo pool di applicazioni **pswa_pool**, nel contenitore **Sito Web predefinito** visualizzato in Gestione IIS. Facoltativamente, è possibile indicare al cmdlet di cambiare il contenitore del sito predefinito dell'applicazione Web.</span><span class="sxs-lookup"><span data-stu-id="0e23c-193">By default, the cmdlet installs the web application, **pswa** (and an application pool for it, **pswa_pool**), in the **Default Web Site** container, as shown in IIS Manager; if desired, you can instruct the cmdlet to change the default site container of the web application.</span></span> <span data-ttu-id="0e23c-194">In Gestione IIS sono disponibili varie opzioni per la configurazione delle applicazioni Web, ad esempio per cambiare il numero di porta o il certificato SSL (Secure Sockets Layer).</span><span class="sxs-lookup"><span data-stu-id="0e23c-194">IIS Manager offers configuration options that are available for web applications, such as changing the port number or the Secure Sockets Layer (SSL) certificate.</span></span>

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="0e23c-195"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Nota sulla sicurezza </span></span><span class="sxs-lookup"><span data-stu-id="0e23c-195"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Security Note </span></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="0e23c-196">Si consiglia agli amministratori di configurare il gateway in modo che utilizzi un certificato valido firmato da una CA.</span><span class="sxs-lookup"><span data-stu-id="0e23c-196">We strongly recommend that administrators configure the gateway to use a valid certificate that has been signed by a CA.</span></span></p></td>
</tr>
</tbody>
</table>

-   [<span data-ttu-id="0e23c-197">Per configurare il gateway di Accesso Web Windows PowerShell con un certificato di test tramite Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="0e23c-197">To configure the Windows PowerShell Web Access gateway with a test certificate by using Install-PswaWebApplication</span></span>](#BKMK_testcert)

-   [<span data-ttu-id="0e23c-198">Per configurare il gateway di Accesso Web Windows PowerShell con un certificato autentico tramite Install-PswaWebApplication e Gestione IIS</span><span class="sxs-lookup"><span data-stu-id="0e23c-198">To configure the Windows PowerShell Web Access gateway with a genuine certificate by using Install-PswaWebApplication and IIS Manager</span></span>](#BKMK_gencert)

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a><span data-ttu-id="0e23c-199">Per configurare il gateway di Accesso Web Windows PowerShell con un certificato di test tramite Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="0e23c-199">To configure the Windows PowerShell Web Access gateway with a test certificate by using Install-PswaWebApplication</span></span>

1.  <span data-ttu-id="0e23c-200">Per aprire una sessione di Windows PowerShell, eseguire una di queste operazioni.</span><span class="sxs-lookup"><span data-stu-id="0e23c-200">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="0e23c-201">Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="0e23c-201">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="0e23c-202">Nella schermata **Start** di Windows fare clic su **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-202">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="0e23c-203">Digitare il comando seguente e quindi premere **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-203">Type the following, and then press **Enter**.</span></span>

    <span data-ttu-id="0e23c-204">**Install-PswaWebApplication -UseTestCertificate**</span><span class="sxs-lookup"><span data-stu-id="0e23c-204">**Install-PswaWebApplication -UseTestCertificate**</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="0e23c-205"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Nota sulla sicurezza </span></span><span class="sxs-lookup"><span data-stu-id="0e23c-205"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Security Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="0e23c-206">Usare il parametro <span class="code">UseTestCertificate</span> esclusivamente in un ambiente di test privato.</span><span class="sxs-lookup"><span data-stu-id="0e23c-206">The <span class="code">UseTestCertificate</span> parameter should only be used in a private test environment.</span></span> <span data-ttu-id="0e23c-207">Per un ambiente di produzione sicuro è consigliabile utilizzare un certificato valido firmato da una CA.</span><span class="sxs-lookup"><span data-stu-id="0e23c-207">For a secure production environment, we recommend using a valid certificate that has been signed by a CA.</span></span></p></td>
    </tr>
    </tbody>
    </table>

    <span data-ttu-id="0e23c-208">Eseguendo il cmdlet si installa l'applicazione Web Accesso Web Windows PowerShell nel contenitore di IIS Sito Web predefinito.</span><span class="sxs-lookup"><span data-stu-id="0e23c-208">Running the cmdlet installs the Windows PowerShell Web Access web application within the IIS Default Web Site container.</span></span> <span data-ttu-id="0e23c-209">Il cmdlet crea l'infrastruttura necessaria per eseguire Accesso Web Windows PowerShell nel sito Web predefinito, ovvero https://&lt;nome_server&gt;/pswa.</span><span class="sxs-lookup"><span data-stu-id="0e23c-209">The cmdlet creates the infrastructure required to run Windows PowerShell Web Access on the default website, https://&lt;server_name&gt;/pswa.</span></span> <span data-ttu-id="0e23c-210">Per installare l'applicazione Web in un altro sito Web, specificare il nome del sito Web aggiungendo il parametro <span class="code">WebSiteName</span>.</span><span class="sxs-lookup"><span data-stu-id="0e23c-210">To install the web application in a different website, provide the website name by adding the <span class="code">WebSiteName</span> parameter.</span></span> <span data-ttu-id="0e23c-211">Per modificare il nome dell'applicazione Web che per impostazione predefinita è <span class="code">pswa</span>, aggiungere il parametro <span class="code">WebApplicationName</span>.</span><span class="sxs-lookup"><span data-stu-id="0e23c-211">To change the name of the web application (the default is <span class="code">pswa</span>), add the <span class="code">WebApplicationName</span> parameter.</span></span>

    <span data-ttu-id="0e23c-212">Durante l'esecuzione del cmdlet vengono configurate le impostazioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="0e23c-212">The following settings are configured by running the cmdlet.</span></span> <span data-ttu-id="0e23c-213">Se si desidera, è possibile modificare tali impostazioni manualmente nella console Gestione IIS.</span><span class="sxs-lookup"><span data-stu-id="0e23c-213">You can change these manually in the IIS Manager console, if desired.</span></span>

    -   <span data-ttu-id="0e23c-214">Percorso: /pswa</span><span class="sxs-lookup"><span data-stu-id="0e23c-214">Path: /pswa</span></span>

    -   <span data-ttu-id="0e23c-215">ApplicationPool: pswa_pool</span><span class="sxs-lookup"><span data-stu-id="0e23c-215">ApplicationPool: pswa_pool</span></span>

    -   <span data-ttu-id="0e23c-216">EnabledProtocols: http</span><span class="sxs-lookup"><span data-stu-id="0e23c-216">EnabledProtocols: http</span></span>

    -   <span data-ttu-id="0e23c-217">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span><span class="sxs-lookup"><span data-stu-id="0e23c-217">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span></span>

    <span data-ttu-id="0e23c-218"><span class="label">Esempio:</span> <span class="code">Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate</span></span><span class="sxs-lookup"><span data-stu-id="0e23c-218"><span class="label">Example:</span> <span class="code">Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate</span></span></span>

    <span data-ttu-id="0e23c-219">In questo esempio l'indirizzo del sito Web di Accesso Web Windows PowerShell risultante è https://&lt; *nome_server*&gt;/myWebApp.</span><span class="sxs-lookup"><span data-stu-id="0e23c-219">In this example, the resulting website for Windows PowerShell Web Access is https://&lt; *server_name*&gt;/myWebApp.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="0e23c-220"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Nota </span></span><span class="sxs-lookup"><span data-stu-id="0e23c-220"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="0e23c-221">Non è possibile accedere al sito Web finché non si consente l'accesso agli utenti aggiungendo le regole di autorizzazione appropriate.</span><span class="sxs-lookup"><span data-stu-id="0e23c-221">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span> <span data-ttu-id="0e23c-222">Per altre informazioni, vedere <a href="#BKMK_step3">Passaggio 3: Configurare una regola di autorizzazione restrittiva</a> e <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell</a>.</span><span class="sxs-lookup"><span data-stu-id="0e23c-222">For more information, see <a href="#BKMK_step3">Step 3: Configure a restrictive authorization rule</a> and <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a>.</span></span></p></td>
    </tr>
    </tbody>
    </table>

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a><span data-ttu-id="0e23c-223">Per configurare il gateway di Accesso Web Windows PowerShell con un certificato autentico tramite Install-PswaWebApplication e Gestione IIS</span><span class="sxs-lookup"><span data-stu-id="0e23c-223">To configure the Windows PowerShell Web Access gateway with a genuine certificate by using Install-PswaWebApplication and IIS Manager</span></span>

1.  <span data-ttu-id="0e23c-224">Per aprire una sessione di Windows PowerShell, eseguire una di queste operazioni.</span><span class="sxs-lookup"><span data-stu-id="0e23c-224">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="0e23c-225">Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="0e23c-225">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="0e23c-226">Nella schermata **Start** di Windows fare clic su **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-226">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="0e23c-227">Digitare il comando seguente e quindi premere **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-227">Type the following, and then press **Enter**.</span></span>

    <span data-ttu-id="0e23c-228">**Install-PswaWebApplication**</span><span class="sxs-lookup"><span data-stu-id="0e23c-228">**Install-PswaWebApplication**</span></span>

    <span data-ttu-id="0e23c-229">Durante l'esecuzione del cmdlet vengono configurate le seguenti impostazioni del gateway.</span><span class="sxs-lookup"><span data-stu-id="0e23c-229">The following gateway settings are configured by running the cmdlet.</span></span> <span data-ttu-id="0e23c-230">Se si desidera, è possibile modificare tali impostazioni manualmente nella console Gestione IIS.</span><span class="sxs-lookup"><span data-stu-id="0e23c-230">You can change these manually in the IIS Manager console, if desired.</span></span> <span data-ttu-id="0e23c-231">È anche possibile specificare i valori per i parametri <span class="code">WebsiteName</span> e <span class="code">WebApplicationName</span> del cmdlet <span class="code">Install-PswaWebApplication</span>.</span><span class="sxs-lookup"><span data-stu-id="0e23c-231">You can also specify values for the <span class="code">WebsiteName</span> and <span class="code">WebApplicationName</span> parameters of the <span class="code">Install-PswaWebApplication</span> cmdlet.</span></span>

    -   <span data-ttu-id="0e23c-232">Percorso: /pswa</span><span class="sxs-lookup"><span data-stu-id="0e23c-232">Path: /pswa</span></span>

    -   <span data-ttu-id="0e23c-233">ApplicationPool: pswa_pool</span><span class="sxs-lookup"><span data-stu-id="0e23c-233">ApplicationPool: pswa_pool</span></span>

    -   <span data-ttu-id="0e23c-234">EnabledProtocols: http</span><span class="sxs-lookup"><span data-stu-id="0e23c-234">EnabledProtocols: http</span></span>

    -   <span data-ttu-id="0e23c-235">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span><span class="sxs-lookup"><span data-stu-id="0e23c-235">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span></span>

3.  <span data-ttu-id="0e23c-236">Aprire la console Gestione IIS eseguendo una delle operazioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="0e23c-236">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="0e23c-237">Nel desktop di Windows avviare Server Manager facendo clic su **Server Manager** nella barra delle applicazioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="0e23c-237">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="0e23c-238">Nel menu **Strumenti** di Server Manager fare clic su **Gestione Internet Information Services (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-238">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="0e23c-239">Nella schermata **Start** di Windows fare clic su **Server Manager**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-239">On the Windows **Start** screen, click **Server Manager**.</span></span>

4.  <span data-ttu-id="0e23c-240">Nel riquadro dell'albero di Gestione IIS espandere il nodo del server in cui è installato Accesso Web Windows PowerShell finché non viene visualizzata la cartella **Siti**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-240">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="0e23c-241">Espandere la cartella **Siti**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-241">Expand the **Sites** folder.</span></span>

5.  <span data-ttu-id="0e23c-242">Selezionare il sito Web in cui è stata installata l'applicazione Web Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0e23c-242">Select the website in which you have installed the Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="0e23c-243">Nel riquadro **Azioni** fare clic su **Binding**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-243">In the **Actions** pane, click **Bindings**.</span></span>

6.  <span data-ttu-id="0e23c-244">Nella finestra di dialogo **Binding sito** fare clic su **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-244">In the **Site Binding** dialog box, click **Add**.</span></span>

7.  <span data-ttu-id="0e23c-245">Nella finestra di dialogo **Aggiungi binding sito** selezionare **https** nel campo **Tipo**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-245">In the **Add Site Binding** dialog box, in the **Type** field, select **https**.</span></span>

8.  <span data-ttu-id="0e23c-246">Nel campo **Certificato SSL** selezionare il certificato firmato dal menu a discesa.</span><span class="sxs-lookup"><span data-stu-id="0e23c-246">In the **SSL certificate** field, select your signed certificate from the drop-down menu.</span></span> <span data-ttu-id="0e23c-247">Fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-247">Click **OK**.</span></span> <span data-ttu-id="0e23c-248">Per altre informazioni su come ottenere un certificato, vedere [Per configurare un certificato SSL in Gestione IIS](#BKMK_cert) in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="0e23c-248">See [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic for more information about how to obtain a certificate.</span></span>

    <span data-ttu-id="0e23c-249">L'applicazione Web Accesso Web Windows PowerShell ora è configurata per usare il certificato SSL firmato.</span><span class="sxs-lookup"><span data-stu-id="0e23c-249">The Windows PowerShell Web Access web application is now configured to use your signed SSL certificate.</span></span> <span data-ttu-id="0e23c-250">Per accedere a Accesso Web Windows PowerShell è possibile aprire https://&lt;nome_server&gt;/pswa in una finestra del browser.</span><span class="sxs-lookup"><span data-stu-id="0e23c-250">You can access Windows PowerShell Web Access by opening https://&lt;server_name&gt;/pswa in a browser window.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="0e23c-251"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Nota </span></span><span class="sxs-lookup"><span data-stu-id="0e23c-251"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="0e23c-252">Non è possibile accedere al sito Web finché non si consente l'accesso agli utenti aggiungendo le regole di autorizzazione appropriate.</span><span class="sxs-lookup"><span data-stu-id="0e23c-252">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span> <span data-ttu-id="0e23c-253">Per altre informazioni, vedere <a href="#BKMK_step3">Passaggio 3: Configurare una regola di autorizzazione restrittiva</a> e <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell</a>.</span><span class="sxs-lookup"><span data-stu-id="0e23c-253">For more information, see <a href="#BKMK_step3">Step 3: Configure a restrictive authorization rule</a> and <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a>.</span></span></p></td>
    </tr>
    </tbody>
    </table><span data-ttu-id="0e23c-254">

<a href="" id="BKMK_step3"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Passaggio 3: Configurare una regola di autorizzazione restrittiva</span></a></span><span class="sxs-lookup"><span data-stu-id="0e23c-254">

<a href="" id="BKMK_step3"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 3: Configure a restrictive authorization rule</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="0e23c-255">Dopo che Accesso Web Windows PowerShell è stato installato e il gateway è stato configurato, gli utenti possono aprire la pagina di accesso in un browser, ma non possono accedere finché l'amministratore di Accesso Web Windows PowerShell non concede esplicitamente l'accesso.</span><span class="sxs-lookup"><span data-stu-id="0e23c-255">After Windows PowerShell Web Access is installed and the gateway is configured, users can open the sign-in page in a browser, but they cannot sign in until the Windows PowerShell Web Access administrator grants users access explicitly.</span></span> <span data-ttu-id="0e23c-256">Il controllo di accesso di Accesso Web Windows PowerShell viene gestito con il set di cmdlet di Windows PowerShell descritto nella tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="0e23c-256">Windows PowerShell Web Access access control is managed by using the set of Windows PowerShell cmdlets described in the following table.</span></span> <span data-ttu-id="0e23c-257">Non esiste un'interfaccia grafica paragonabile per aggiungere o gestire le regole di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="0e23c-257">There is no comparable GUI for adding or managing authorization rules.</span></span> <span data-ttu-id="0e23c-258">Per informazioni dettagliate sui cmdlet di Accesso Web Windows PowerShell, vedere gli argomenti di riferimento sui cmdlet in [Cmdlet di Accesso Web Windows PowerShell](https://technet.microsoft.com/library/hh918342.aspx).</span><span class="sxs-lookup"><span data-stu-id="0e23c-258">For more detailed information about Windows PowerShell Web Access cmdlets, see the cmdlet reference topics, [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).</span></span>

<span data-ttu-id="0e23c-259">Per altre informazioni sulla sicurezza e sulle regole di autorizzazione di Accesso Web Windows PowerShell, vedere [Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span><span class="sxs-lookup"><span data-stu-id="0e23c-259">For more detail about Windows PowerShell Web Access authorization rules and security, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span></span>

#### <a name="to-add-a-restrictive-authorization-rule"></a><span data-ttu-id="0e23c-260">Per aggiungere una regola di autorizzazione restrittiva</span><span class="sxs-lookup"><span data-stu-id="0e23c-260">To add a restrictive authorization rule</span></span>

1.  <span data-ttu-id="0e23c-261">Per aprire una sessione di Windows PowerShell con diritti utente elevati, eseguire una di queste operazioni.</span><span class="sxs-lookup"><span data-stu-id="0e23c-261">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="0e23c-262">Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni e scegliere **Esegui come amministratore**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-262">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="0e23c-263">Nella schermata **Start** di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** e quindi scegliere **Esegui come amministratore**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-263">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="0e23c-264"><span class="label">Passaggio facoltativo per la limitazione dell'accesso utente con configurazioni di sessione:</span> verificare che le configurazioni di sessione da usare nelle proprie regole esistano già.</span><span class="sxs-lookup"><span data-stu-id="0e23c-264"><span class="label">Optional step for restricting user access by using session configurations:</span> Verify that session configurations that you want to use in your rules already exist.</span></span> <span data-ttu-id="0e23c-265">Se non sono ancora state create, utilizzare le istruzioni per la creazione di configurazioni di sessione disponibili nell'articolo [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) di MSDN.</span><span class="sxs-lookup"><span data-stu-id="0e23c-265">If they have not yet been created, use instructions for creating session configurations in [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) on MSDN.</span></span>

3.  <span data-ttu-id="0e23c-266">Digitare il comando seguente e quindi premere **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-266">Type the following, and then press **Enter**.</span></span>

    [<span data-ttu-id="0e23c-267">Copy</span><span class="sxs-lookup"><span data-stu-id="0e23c-267">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_f9e7959b-75d0-4d63-8f8e-02334a8dd09d'); "Copia negli Appunti.")

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    <span data-ttu-id="0e23c-268">Questa regola di autorizzazione consente a un utente specifico di accedere a un computer della rete a cui ha accesso normalmente, tramite una specifica configurazione di sessione con ambito limitato alle esigenze tipiche di utilizzo di script e cmdlet dell'utente.</span><span class="sxs-lookup"><span data-stu-id="0e23c-268">This authorization rule allows a specific user access to one computer on the network to which they typically have access, with access to a specific session configuration that is scoped to the user’s typical scripting and cmdlet needs.</span></span> <span data-ttu-id="0e23c-269">Nell'esempio seguente, a un utente di nome <span class="code">JSmith</span> nel dominio <span class="code">Contoso</span> viene consentito l'accesso per la gestione del computer <span class="code">Contoso_214</span>, con una configurazione di sessione denominata <span class="code">NewAdminsOnly</span>.</span><span class="sxs-lookup"><span data-stu-id="0e23c-269">In the following example, a user named <span class="code">JSmith</span> in the <span class="code">Contoso</span> domain is granted access to manage the computer <span class="code">Contoso_214</span>, and use a session configuration named <span class="code">NewAdminsOnly</span>.</span></span>

    [<span data-ttu-id="0e23c-270">Copy</span><span class="sxs-lookup"><span data-stu-id="0e23c-270">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_ebd5bc5e-ec5d-4955-a86a-63843e480e37'); "Copia negli Appunti.")

        Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  <span data-ttu-id="0e23c-271">Per verificare che la regola sia stata creata, eseguire il cmdlet **Get-PswaAuthorizationRule** o **Test-PswaAuthorizationRule -UserName &lt;dominio\\utente | computer\\utente&gt; -ComputerName** &lt;nome_computer&gt;.</span><span class="sxs-lookup"><span data-stu-id="0e23c-271">Verify that the rule has been created by running either the **Get-PswaAuthorizationRule** cmdlet, or **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;.</span></span> <span data-ttu-id="0e23c-272">Ad esempio, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-272">For example, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span></span>

<span data-ttu-id="0e23c-273">Dopo la configurazione di una regola di autorizzazione, gli utenti autorizzati possono accedere alla console basata sul Web e iniziare a usare Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0e23c-273">After you have configured an authorization rule, you are ready for authorized users to sign in to the web-based console and begin using Windows PowerShell Web Access.</span></span>

<a href="" id="BKMK_custom"></a>

<span data-ttu-id="0e23c-274"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Distribuzione personalizzata</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="0e23c-274"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Custom deployment</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="0e23c-275">È possibile installare il gateway di Accesso Web Windows PowerShell in un server che esegue Windows Server 2012 R2 o Windows Server 2012 usando l'Aggiunta guidata ruoli e funzionalità in Server Manager.</span><span class="sxs-lookup"><span data-stu-id="0e23c-275">You can install the Windows PowerShell Web Access gateway on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using the Add Roles and Features Wizard in Server Manager.</span></span> <span data-ttu-id="0e23c-276">Dopo l'installazione di Accesso Web Windows PowerShell, è possibile personalizzare la configurazione del gateway in Gestione IIS.</span><span class="sxs-lookup"><span data-stu-id="0e23c-276">After Windows PowerShell Web Access is installed, you can customize the configuration of the gateway in IIS Manager.</span></span>

<a href="" id="BKMK_custom1"></a>
###

<span data-ttu-id="0e23c-277"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Passaggio 1: Installare Accesso Web Windows PowerShell</span></a></span><span class="sxs-lookup"><span data-stu-id="0e23c-277"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Install Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-install-windows-powershell-web-access-by-using-the-add-roles-and-features-wizard"></a><span data-ttu-id="0e23c-278">Per installare Accesso Web Windows PowerShell tramite Aggiunta guidata ruoli e funzionalità</span><span class="sxs-lookup"><span data-stu-id="0e23c-278">To install Windows PowerShell Web Access by using the Add Roles and Features Wizard</span></span>

1.  <span data-ttu-id="0e23c-279">Se Server Manager è già aperto, andare al passaggio successivo.</span><span class="sxs-lookup"><span data-stu-id="0e23c-279">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="0e23c-280">Se Server Manager non è aperto, aprirlo in uno dei modi seguenti.</span><span class="sxs-lookup"><span data-stu-id="0e23c-280">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="0e23c-281">Nel desktop di Windows avviare Server Manager facendo clic su **Server Manager** nella barra delle applicazioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="0e23c-281">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="0e23c-282">Nella schermata **Start** di Windows fare clic su **Server Manager**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-282">On the Windows **Start** screen, click **Server Manager**.</span></span>

2.  <span data-ttu-id="0e23c-283">Scegliere **Aggiungi ruoli e funzionalità** dal menu **Gestione**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-283">On the **Manage** menu, click **Add Roles and Features**.</span></span>

3.  <span data-ttu-id="0e23c-284">Nella pagina **Selezione tipo di installazione** selezionare **Installazione basata su ruoli o basata su funzionalità**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-284">On the **Select installation type** page, select **Role-based or feature-based installation**.</span></span> <span data-ttu-id="0e23c-285">Fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-285">Click **Next**.</span></span>

4.  <span data-ttu-id="0e23c-286">Nella pagina **Selezione server di destinazione** scegliere un server dal pool di server oppure selezionare un disco rigido virtuale offline.</span><span class="sxs-lookup"><span data-stu-id="0e23c-286">On the **Select destination server** page, select a server from the server pool, or select an offline VHD.</span></span> <span data-ttu-id="0e23c-287">Per selezionare un disco rigido virtuale offline come server di destinazione, selezionare innanzitutto il server in cui montare il disco rigido virtuale, quindi selezionare il file del disco rigido virtuale.</span><span class="sxs-lookup"><span data-stu-id="0e23c-287">To select an offline VHD as your destination server, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="0e23c-288">Per informazioni su come aggiungere server al pool di server, vedere la Guida di Server Manager.</span><span class="sxs-lookup"><span data-stu-id="0e23c-288">For information about how to add servers to your server pool, see the Server Manager Help.</span></span> <span data-ttu-id="0e23c-289">Dopo aver selezionato il server di destinazione, fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-289">After you have selected the destination server, click **Next**.</span></span>

5.  <span data-ttu-id="0e23c-290">Nella pagina **Selezione funzionalità** della procedura guidata espandere **Windows PowerShell**e selezionare **Accesso Web Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-290">On the **Select features** page of the wizard, expand **Windows PowerShell**, and then select **Windows PowerShell Web Access**.</span></span>

6.  <span data-ttu-id="0e23c-291">Viene richiesto di aggiungere le funzionalità necessarie, quali .NET Framework 4.5 e i servizi ruolo del server Web (IIS).</span><span class="sxs-lookup"><span data-stu-id="0e23c-291">Note that you are prompted to add required features, such as .NET Framework 4.5, and role services of Web Server (IIS).</span></span> <span data-ttu-id="0e23c-292">Aggiungere le funzionalità necessarie e continuare.</span><span class="sxs-lookup"><span data-stu-id="0e23c-292">Add required features and continue.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="0e23c-293"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Nota </span></span><span class="sxs-lookup"><span data-stu-id="0e23c-293"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="0e23c-294">Se si installa Accesso Web Windows PowerShell usando l'Aggiunta guidata ruoli e funzionalità, viene installato anche il server Web (IIS), che include lo snap-in Gestione IIS.</span><span class="sxs-lookup"><span data-stu-id="0e23c-294">Installing Windows PowerShell Web Access by using the Add Roles and Features Wizard also installs Web Server (IIS), including the IIS Manager snap-in.</span></span> <span data-ttu-id="0e23c-295">Se si usa l'Aggiunta guidata ruoli e funzionalità, lo snap-in e gli altri strumenti di gestione di IIS vengono installati per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="0e23c-295">The snap-in and other IIS management tools are installed by default if you use Add Roles and Features Wizard.</span></span> <span data-ttu-id="0e23c-296">Se si installa Accesso Web Windows PowerShell usando i cmdlet di Windows PowerShell come illustrato nella procedura seguente, gli strumenti di gestione non vengono aggiunti per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="0e23c-296">If you install Windows PowerShell Web Access by using Windows PowerShell cmdlets as described in the following procedure, management tools are not added by default.</span></span></p></td>
    </tr>
    </tbody>
    </table>

7.  <span data-ttu-id="0e23c-297">Se i file delle funzionalità di Accesso Web Windows PowerShell non sono archiviati nel server di destinazione selezionato nel passaggio 4, nella pagina **Conferma selezioni per l'installazione** fare clic su **Specificare un percorso di origine alternativo** e immettere il percorso dei file delle funzionalità.</span><span class="sxs-lookup"><span data-stu-id="0e23c-297">On the **Confirm installation selections** page, if the feature files for Windows PowerShell Web Access are not stored on the destination server that you selected in step 4, click **Specify an alternate source path**, and provide the path to the feature files.</span></span> <span data-ttu-id="0e23c-298">In caso contrario, fare clic su **Installa**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-298">Otherwise, click **Install**.</span></span>

8.  <span data-ttu-id="0e23c-299">Dopo aver fatto clic su **Installa**, la pagina **Stato dell'installazione** visualizza lo stato dell'installazione, i risultati e messaggi quali avvisi, errori o procedure di configurazione successive all'installazione necessarie per Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0e23c-299">After you click **Install**, the **Installation progress** page displays installation progress, results, and messages such as warnings, failures, or post-installation configuration steps that are required for Windows PowerShell Web Access.</span></span> <span data-ttu-id="0e23c-300">Dopo l'installazione di Accesso Web Windows PowerShell viene richiesto di esaminare il file Leggimi, che contiene istruzioni sulle operazioni di configurazione di base necessarie per il gateway.</span><span class="sxs-lookup"><span data-stu-id="0e23c-300">After Windows PowerShell Web Access is installed, you are prompted to review the readme file, which contains basic, required setup instructions for the gateway.</span></span> <span data-ttu-id="0e23c-301">Le istruzioni sono incluse anche in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="0e23c-301">These instructions are also included in this topic.</span></span> <span data-ttu-id="0e23c-302">Il percorso del file Leggimi è: <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span><span class="sxs-lookup"><span data-stu-id="0e23c-302">The path to the readme file is <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span></span>

###

<span data-ttu-id="0e23c-303"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Passaggio 2: Configurare il gateway</span></a></span><span class="sxs-lookup"><span data-stu-id="0e23c-303"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Configure the gateway</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="0e23c-304">Le istruzioni in questa sezione mostrano come installare l'applicazione Web Accesso Web Windows PowerShell in una sottodirectory del sito Web, anziché nella directory radice.</span><span class="sxs-lookup"><span data-stu-id="0e23c-304">Instructions in this section are for installing the Windows PowerShell Web Access web application in a subdirectory—and not in the root directory—of your website.</span></span> <span data-ttu-id="0e23c-305">Viene usata una procedura con interfaccia grafica equivalente alle operazioni eseguite dal cmdlet <span class="code">Install-PswaWebApplication</span>.</span><span class="sxs-lookup"><span data-stu-id="0e23c-305">This procedure is the GUI-based equivalent of the actions performed by the <span class="code">Install-PswaWebApplication</span> cmdlet.</span></span> <span data-ttu-id="0e23c-306">Questa sezione include anche le istruzioni su come usare Gestione IIS per configurare il gateway di Accesso Web Windows PowerShell come sito Web radice.</span><span class="sxs-lookup"><span data-stu-id="0e23c-306">This section also includes instructions for how to use IIS Manager to configure the Windows PowerShell Web Access gateway as a root website.</span></span>

-   [<span data-ttu-id="0e23c-307">Per usare Gestione IIS per configurare il gateway in un sito Web esistente</span><span class="sxs-lookup"><span data-stu-id="0e23c-307">To use IIS Manager to configure the gateway in an existing website</span></span>](#BKMK_configman)

-   [<span data-ttu-id="0e23c-308">Per usare Gestione IIS per configurare il gateway come sito Web radice con un certificato di test</span><span class="sxs-lookup"><span data-stu-id="0e23c-308">To use IIS Manager to configure the gateway as a root website with a test certificate</span></span>](#BKMK_configroot)

-   

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a><span data-ttu-id="0e23c-309">Per utilizzare Gestione IIS per configurare il gateway in un sito Web esistente</span><span class="sxs-lookup"><span data-stu-id="0e23c-309">To use IIS Manager to configure the gateway in an existing website</span></span>

1.  <span data-ttu-id="0e23c-310">Aprire la console Gestione IIS eseguendo una delle operazioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="0e23c-310">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="0e23c-311">Nel desktop di Windows avviare Server Manager facendo clic su **Server Manager** nella barra delle applicazioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="0e23c-311">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="0e23c-312">Nel menu **Strumenti** di Server Manager fare clic su **Gestione Internet Information Services (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-312">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="0e23c-313">Nella schermata **Start** di Windows digitare una parte qualsiasi del nome **Gestione Internet Information Services (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-313">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="0e23c-314">Fare clic sul collegamento quando viene visualizzato nell'elenco dei risultati **App**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-314">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="0e23c-315">Creare un nuovo pool di applicazioni per Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0e23c-315">Create a new application pool for Windows PowerShell Web Access.</span></span> <span data-ttu-id="0e23c-316">Espandere il nodo del server gateway nel riquadro dell'albero di Gestione IIS, selezionare **Pool di applicazioni** e fare clic su **Aggiungi pool di applicazioni** nel riquadro **Azioni**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-316">Expand the node of the gateway server in the IIS Manager tree pane, select **Application Pools**, and click **Add Application Pool** in the **Actions** pane.</span></span>

3.  <span data-ttu-id="0e23c-317">Aggiungere un nuovo pool di applicazioni con il nome **pswa_pool**o specificare un altro nome.</span><span class="sxs-lookup"><span data-stu-id="0e23c-317">Add a new application pool with the name **pswa_pool**, or provide another name.</span></span> <span data-ttu-id="0e23c-318">Fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-318">Click **OK**.</span></span>

4.  <span data-ttu-id="0e23c-319">Nel riquadro dell'albero di Gestione IIS espandere il nodo del server in cui è installato Accesso Web Windows PowerShell finché non viene visualizzata la cartella **Siti**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-319">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="0e23c-320">Selezionare la cartella **Siti**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-320">Select the **Sites** folder.</span></span>

5.  <span data-ttu-id="0e23c-321">Fare clic con il pulsante destro del mouse sul sito Web, ad esempio **Sito Web predefinito**, a cui si vuole aggiungere il sito Web di Accesso Web Windows PowerShell e quindi fare clic su **Aggiungi applicazione**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-321">Right-click the website (for example, **Default Web Site**) to which you would like to add the Windows PowerShell Web Access website, and then click **Add Application**.</span></span>

6.  <span data-ttu-id="0e23c-322">Nel campo **Alias** digitare pswa o specificare un altro alias.</span><span class="sxs-lookup"><span data-stu-id="0e23c-322">In the **Alias** field, type pswa, or provide another alias.</span></span> <span data-ttu-id="0e23c-323">L'alias determina il nome della directory virtuale.</span><span class="sxs-lookup"><span data-stu-id="0e23c-323">The alias becomes the virtual directory name.</span></span> <span data-ttu-id="0e23c-324">Ad esempio, nell'URL seguente **pswa** corrisponde all'alias specificato in questo passaggio: https://&lt;nome_server&gt;/pswa.</span><span class="sxs-lookup"><span data-stu-id="0e23c-324">For example, **pswa** in the following URL represents the alias specified in this step: https://&lt;server_name&gt;/pswa.</span></span>

7.  <span data-ttu-id="0e23c-325">Nel campo **Pool di applicazioni** selezionare il pool di applicazioni creato nel passaggio 3.</span><span class="sxs-lookup"><span data-stu-id="0e23c-325">In the **Application pool** field, select the application pool that you created in step 3.</span></span>

8.  <span data-ttu-id="0e23c-326">Nel campo **Percorso fisico** cercare e selezionare il percorso dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="0e23c-326">In the **Physical path** field, browse for the location of the application.</span></span> <span data-ttu-id="0e23c-327">È possibile utilizzare il percorso predefinito, ovvero %windir%/Web/PowerShellWebAccess/wwwroot.</span><span class="sxs-lookup"><span data-stu-id="0e23c-327">You can use the default location, %windir%/Web/PowerShellWebAccess/wwwroot.</span></span> <span data-ttu-id="0e23c-328">Fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-328">Click **OK**.</span></span>

9.  <span data-ttu-id="0e23c-329">Eseguire i passaggi illustrati nella procedura [Per configurare un certificato SSL in Gestione IIS](#BKMK_cert) in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="0e23c-329">Follow the steps in the procedure [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic.</span></span>

10. <span data-ttu-id="0e23c-330"><span class="label">Passaggio di sicurezza facoltativo:</span> Con il sito Web selezionato nel riquadro dell'albero, fare doppio clic su **Impostazioni SSL** nel riquadro del contenuto.</span><span class="sxs-lookup"><span data-stu-id="0e23c-330"><span class="label">Optional security step:</span> With the website selected in the tree pane, double-click **SSL Settings** in the content pane.</span></span> <span data-ttu-id="0e23c-331">Selezionare **Richiedi SSL**, quindi fare clic su **Applica** nel riquadro **Azioni**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-331">Select **Require SSL**, and then in the **Actions** pane, click **Apply**.</span></span> <span data-ttu-id="0e23c-332">Facoltativamente, nel riquadro **Impostazioni SSL** è possibile richiedere l'uso di certificati client da parte degli utenti che si connettono al sito Web di Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0e23c-332">Optionally, in the **SSL Settings** pane, you can require that users connecting to the Windows PowerShell Web Access website have client certificates.</span></span> <span data-ttu-id="0e23c-333">Un certificato client consente di verificare l'identità dell'utente di un dispositivo client.</span><span class="sxs-lookup"><span data-stu-id="0e23c-333">Client certificates help to verify the identity of a client device user.</span></span> <span data-ttu-id="0e23c-334">Per altre informazioni su come aumentare la sicurezza di Accesso Web Windows PowerShell richiedendo i certificati client, vedere [Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx) in questa guida.</span><span class="sxs-lookup"><span data-stu-id="0e23c-334">For more information about how requiring client certificates can increase the security of Windows PowerShell Web Access, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx) in this guide.</span></span>

11. <span data-ttu-id="0e23c-335">Aprire una sessione del browser in un dispositivo client.</span><span class="sxs-lookup"><span data-stu-id="0e23c-335">Open a browser session on a client device.</span></span> <span data-ttu-id="0e23c-336">Per altre informazioni sui browser e i dispositivi supportati, vedere la sezione [Browser e dispositivi client supportati](#BKMK_browser) in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="0e23c-336">For more information about supported browsers and devices, see [Browser and client device support](#BKMK_browser) in this topic.</span></span>

12. <span data-ttu-id="0e23c-337">Aprire il nuovo sito Web di Accesso Web Windows PowerShell, https://&lt;*nome_server_gateway*&gt;/pswa.</span><span class="sxs-lookup"><span data-stu-id="0e23c-337">Open the new Windows PowerShell Web Access website, https://&lt; *gateway_server_name*&gt;/pswa.</span></span>

    <span data-ttu-id="0e23c-338">Il browser dovrebbe visualizzare la pagina di accesso della console di Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0e23c-338">The browser should display the Windows PowerShell Web Access console sign-in page.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="0e23c-339"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Nota </span></span><span class="sxs-lookup"><span data-stu-id="0e23c-339"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="0e23c-340">Non è possibile accedere al sito Web finché non si consente l'accesso agli utenti aggiungendo le regole di autorizzazione appropriate.</span><span class="sxs-lookup"><span data-stu-id="0e23c-340">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span></p></td>
    </tr>
    </tbody>
    </table>

13. <span data-ttu-id="0e23c-341">In una sessione di Windows PowerShell aperta con diritti utente elevati (Esegui come amministratore) eseguire lo script seguente, in cui *nome_pool_applicazioni* rappresenta il nome del pool di applicazioni creato nel passaggio 3, per concedere al pool di applicazioni i diritti di accesso al file di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="0e23c-341">In a Windows PowerShell session that has been opened with elevated user rights (Run as Administrator), run the following script, in which *application_pool_name* represents the name of the application pool that you created in step 3, to give the application pool access rights to the authorization file.</span></span>

    [<span data-ttu-id="0e23c-342">Copy</span><span class="sxs-lookup"><span data-stu-id="0e23c-342">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_c1a80a93-8fcf-4beb-a025-5f81bfb8bdae'); "Copia negli Appunti.")

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    <span data-ttu-id="0e23c-343">Per visualizzare i diritti di accesso esistenti per il file di autorizzazione, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="0e23c-343">To view existing access rights on the authorization file, run the following command:</span></span>

    [<span data-ttu-id="0e23c-344">Copy</span><span class="sxs-lookup"><span data-stu-id="0e23c-344">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_ac2179c2-9548-4a17-8663-267fdd105380'); "Copia negli Appunti.")

        c:\windows\system32\icacls.exe $authorizationFile

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a><span data-ttu-id="0e23c-345">Per usare Gestione IIS per configurare il gateway come sito Web radice con un certificato di test</span><span class="sxs-lookup"><span data-stu-id="0e23c-345">To use IIS Manager to configure the gateway as a root website with a test certificate</span></span>

1.  <span data-ttu-id="0e23c-346">Aprire la console Gestione IIS eseguendo una delle operazioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="0e23c-346">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="0e23c-347">Nel desktop di Windows avviare Server Manager facendo clic su **Server Manager** nella barra delle applicazioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="0e23c-347">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="0e23c-348">Nel menu **Strumenti** di Server Manager fare clic su **Gestione Internet Information Services (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-348">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="0e23c-349">Nella schermata **Start** di Windows digitare una parte qualsiasi del nome **Gestione Internet Information Services (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-349">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="0e23c-350">Fare clic sul collegamento quando viene visualizzato nell'elenco dei risultati **App**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-350">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="0e23c-351">Nel riquadro dell'albero di Gestione IIS espandere il nodo del server in cui è installato Accesso Web Windows PowerShell finché non viene visualizzata la cartella **Siti**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-351">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="0e23c-352">Selezionare la cartella **Siti**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-352">Select the **Sites** folder.</span></span>

3.  <span data-ttu-id="0e23c-353">Nel riquadro **Azioni** fare clic su **Aggiungi sito Web**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-353">In the **Actions** pane, click **Add Website**.</span></span>

4.  <span data-ttu-id="0e23c-354">Digitare il nome del sito Web, ad esempio **Accesso Web Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-354">Type a name for the website, such as **Windows PowerShell Web Access**.</span></span>

5.  <span data-ttu-id="0e23c-355">Per il nuovo sito Web viene automaticamente creato un pool di applicazioni.</span><span class="sxs-lookup"><span data-stu-id="0e23c-355">An application pool is automatically created for the new website.</span></span> <span data-ttu-id="0e23c-356">Per utilizzare un pool di applicazioni diverso, fare clic su **Seleziona** per selezionare il pool di applicazioni da associare al nuovo sito Web.</span><span class="sxs-lookup"><span data-stu-id="0e23c-356">To use a different application pool, click **Select** to select an application pool to associate with the new website.</span></span> <span data-ttu-id="0e23c-357">Selezionare il pool di applicazioni alternativo nella finestra di dialogo **Seleziona pool di applicazioni** , quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-357">Select the alternate application pool in the **Select Application Pool** dialog box, and then click **OK**.</span></span>

6.  <span data-ttu-id="0e23c-358">Nella casella di testo **Percorso fisico** accedere a %*windir*%/Web/PowerShellWebAccess/wwwroot.</span><span class="sxs-lookup"><span data-stu-id="0e23c-358">In the **Physical path** text box, navigate to %*windir*%/Web/PowerShellWebAccess/wwwroot.</span></span>

7.  <span data-ttu-id="0e23c-359">Nel campo **Tipo** dell'area **Binding** selezionare **https**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-359">In the **Type** field of the **Binding** area, select **https**.</span></span>

8.  <span data-ttu-id="0e23c-360">Assegnare al sito Web un numero di porta che non sia già in uso da un altro sito o applicazione.</span><span class="sxs-lookup"><span data-stu-id="0e23c-360">Assign a port number to the website that is not already in use by another site or application.</span></span> <span data-ttu-id="0e23c-361">Per individuare le porte aperte, è possibile eseguire il comando **netstat** in una finestra del prompt dei comandi.</span><span class="sxs-lookup"><span data-stu-id="0e23c-361">To locate open ports, you can run the **netstat** command in a Command Prompt window.</span></span> <span data-ttu-id="0e23c-362">Il numero di porta predefinito è 443.</span><span class="sxs-lookup"><span data-stu-id="0e23c-362">The default port number is 443.</span></span>

    <span data-ttu-id="0e23c-363">Cambiare la porta predefinita se un altro sito Web sta già utilizzando la porta 443 o esistono altri motivi di sicurezza per cambiare il numero di porta.</span><span class="sxs-lookup"><span data-stu-id="0e23c-363">Change the default port if another website is already using 443, or if you have other security reasons for changing the port number.</span></span> <span data-ttu-id="0e23c-364">Se la porta selezionata viene usata da un altro sito Web in esecuzione nel server gateway, quando si fa clic su **OK** nella finestra di dialogo **Aggiungi sito Web** viene visualizzato un avviso.</span><span class="sxs-lookup"><span data-stu-id="0e23c-364">If another website that is running on your gateway server is using your selected port, a warning is displayed when you click **OK** in the **Add Website** dialog box.</span></span> <span data-ttu-id="0e23c-365">Per eseguire Accesso Web Windows PowerShell è necessaria una porta inutilizzata.</span><span class="sxs-lookup"><span data-stu-id="0e23c-365">You must use an unused port to run Windows PowerShell Web Access.</span></span>

9.  <span data-ttu-id="0e23c-366">Facoltativamente, se è necessario per l'organizzazione, specificare un nome host significativo per l'organizzazione e gli utenti, ad esempio **www.contoso.com**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-366">Optionally, if needed for your organization, specify a host name that makes sense to your organization and users, such as **www.contoso.com**.</span></span> <span data-ttu-id="0e23c-367">Fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-367">Click **OK**.</span></span>

10. <span data-ttu-id="0e23c-368">Per un ambiente di produzione più sicuro, è consigliabile specificare un certificato valido firmato da una CA.</span><span class="sxs-lookup"><span data-stu-id="0e23c-368">For a more secure production environment, we strongly recommend providing a valid certificate that has been signed by a CA.</span></span> <span data-ttu-id="0e23c-369">È necessario fornire un certificato SSL perché gli utenti possono connettersi a Accesso Web Windows PowerShell solo con un sito Web HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0e23c-369">You must provide an SSL certificate, because users can only connect to Windows PowerShell Web Access through an HTTPS website.</span></span> <span data-ttu-id="0e23c-370">Per altre informazioni su come ottenere un certificato, vedere [Per configurare un certificato SSL in Gestione IIS](#BKMK_cert) in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="0e23c-370">See [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic for more information about how to obtain a certificate.</span></span>

11. <span data-ttu-id="0e23c-371">Fare clic su **OK** per chiudere la finestra di dialogo **Aggiungi sito Web**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-371">Click **OK** to close the **Add Website** dialog box.</span></span>

12. <span data-ttu-id="0e23c-372">In una sessione di Windows PowerShell aperta con diritti utente elevati (Esegui come amministratore) eseguire lo script seguente, in cui *nome_pool_applicazioni* rappresenta il nome del pool di applicazioni creato nel passaggio 4, per concedere al pool di applicazioni i diritti di accesso al file di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="0e23c-372">In a Windows PowerShell session that has been opened with elevated user rights (Run as Administrator), run the following script, in which *application_pool_name* represents the name of the application pool that you created in step 4, to give the application pool access rights to the authorization file.</span></span>

    [<span data-ttu-id="0e23c-373">Copy</span><span class="sxs-lookup"><span data-stu-id="0e23c-373">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_35ae9944-ca44-4af7-9c96-616083b3e3db'); "Copia negli Appunti.")

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    <span data-ttu-id="0e23c-374">Per visualizzare i diritti di accesso esistenti per il file di autorizzazione, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="0e23c-374">To view existing access rights on the authorization file, run the following command:</span></span>

    [<span data-ttu-id="0e23c-375">Copy</span><span class="sxs-lookup"><span data-stu-id="0e23c-375">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_0eb6d70a-2807-498b-b088-fa5233ed68d5'); "Copia negli Appunti.")

        c:\windows\system32\icacls.exe $authorizationFile

13. <span data-ttu-id="0e23c-376">Con il nuovo sito Web selezionato nel riquadro dell'albero di Gestione IIS, fare clic su **Avvia** nel riquadro **Azioni** per avviare il sito Web.</span><span class="sxs-lookup"><span data-stu-id="0e23c-376">With the new website selected in the IIS Manager tree pane, click **Start** in the **Actions** pane to start the website.</span></span>

14. <span data-ttu-id="0e23c-377">Aprire una sessione del browser in un dispositivo client.</span><span class="sxs-lookup"><span data-stu-id="0e23c-377">Open a browser session on a client device.</span></span> <span data-ttu-id="0e23c-378">Per altre informazioni sui browser e i dispositivi supportati, vedere la sezione [Browser e dispositivi client supportati](#BKMK_browser) in questo documento.</span><span class="sxs-lookup"><span data-stu-id="0e23c-378">For more information about supported browsers and devices, see [Browser and client device support](#BKMK_browser) in this document.</span></span>

15. <span data-ttu-id="0e23c-379">Aprire il nuovo sito Web di Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0e23c-379">Open the new Windows PowerShell Web Access website.</span></span>

    <span data-ttu-id="0e23c-380">Il sito Web radice punta alla cartella Accesso Web Windows PowerShell, quindi il browser dovrebbe visualizzare la pagina di accesso di Accesso Web Windows PowerShell quando si apre https://&lt;*nome_server_gateway*&gt;.</span><span class="sxs-lookup"><span data-stu-id="0e23c-380">Because the root website points to the Windows PowerShell Web Access folder, the browser should display the Windows PowerShell Web Access sign-in page when you open https://&lt; *gateway_server_name*&gt;.</span></span> <span data-ttu-id="0e23c-381">Non è necessario aggiungere **/pswa** all'URL.</span><span class="sxs-lookup"><span data-stu-id="0e23c-381">You should not need to add **/pswa** to the URL.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="0e23c-382"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Nota </span></span><span class="sxs-lookup"><span data-stu-id="0e23c-382"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="0e23c-383">Non è possibile accedere al sito Web finché non si consente l'accesso agli utenti aggiungendo le regole di autorizzazione appropriate.</span><span class="sxs-lookup"><span data-stu-id="0e23c-383">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span></p></td>
    </tr>
    </tbody>
    </table>

###

<span data-ttu-id="0e23c-384"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Passaggio 3: Configurare una regola di autorizzazione restrittiva</span></a></span><span class="sxs-lookup"><span data-stu-id="0e23c-384"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 3: Configure a restrictive authorization rule</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="0e23c-385">Dopo che Accesso Web Windows PowerShell è stato installato e il gateway è stato configurato, gli utenti possono aprire la pagina di accesso in un browser, ma non possono accedere finché l'amministratore di Accesso Web Windows PowerShell non concede esplicitamente l'accesso.</span><span class="sxs-lookup"><span data-stu-id="0e23c-385">After Windows PowerShell Web Access is installed and the gateway is configured, users can open the sign-in page in a browser, but they cannot sign in until the Windows PowerShell Web Access administrator grants users access explicitly.</span></span> <span data-ttu-id="0e23c-386">Il controllo di accesso di Accesso Web Windows PowerShell viene gestito con il set di cmdlet di Windows PowerShell descritto nella tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="0e23c-386">Windows PowerShell Web Access access control is managed by using the set of Windows PowerShell cmdlets described in the following table.</span></span> <span data-ttu-id="0e23c-387">Non esiste un'interfaccia grafica paragonabile per aggiungere o gestire le regole di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="0e23c-387">There is no comparable GUI for adding or managing authorization rules.</span></span> <span data-ttu-id="0e23c-388">Per informazioni dettagliate sui cmdlet di Accesso Web Windows PowerShell, vedere gli argomenti di riferimento sui cmdlet in [Cmdlet di Accesso Web Windows PowerShell](https://technet.microsoft.com/library/hh918342.aspx).</span><span class="sxs-lookup"><span data-stu-id="0e23c-388">For more detailed information about Windows PowerShell Web Access cmdlets, see the cmdlet reference topics, [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).</span></span>

<span data-ttu-id="0e23c-389">Per altre informazioni sulla sicurezza e sulle regole di autorizzazione di Accesso Web Windows PowerShell, vedere [Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span><span class="sxs-lookup"><span data-stu-id="0e23c-389">For more detail about Windows PowerShell Web Access authorization rules and security, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span></span>

#### <a name="to-add-a-restrictive-authorization-rule"></a><span data-ttu-id="0e23c-390">Per aggiungere una regola di autorizzazione restrittiva</span><span class="sxs-lookup"><span data-stu-id="0e23c-390">To add a restrictive authorization rule</span></span>

1.  <span data-ttu-id="0e23c-391">Per aprire una sessione di Windows PowerShell con diritti utente elevati, eseguire una di queste operazioni.</span><span class="sxs-lookup"><span data-stu-id="0e23c-391">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="0e23c-392">Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni e scegliere **Esegui come amministratore**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-392">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="0e23c-393">Nella schermata **Start** di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** e quindi scegliere **Esegui come amministratore**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-393">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="0e23c-394"><span class="label">Passaggio facoltativo per la limitazione dell'accesso utente con configurazioni di sessione:</span> verificare che le configurazioni di sessione da usare nelle proprie regole esistano già.</span><span class="sxs-lookup"><span data-stu-id="0e23c-394"><span class="label">Optional step for restricting user access by using session configurations:</span> Verify that session configurations that you want to use in your rules already exist.</span></span> <span data-ttu-id="0e23c-395">Se non sono ancora state create, utilizzare le istruzioni per la creazione di configurazioni di sessione disponibili nell'articolo [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) di MSDN.</span><span class="sxs-lookup"><span data-stu-id="0e23c-395">If they have not yet been created, use instructions for creating session configurations in [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) on MSDN.</span></span>

3.  <span data-ttu-id="0e23c-396">Digitare il comando seguente e quindi premere **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-396">Type the following, and then press **Enter**.</span></span>

    [<span data-ttu-id="0e23c-397">Copy</span><span class="sxs-lookup"><span data-stu-id="0e23c-397">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_4df22c91-f56f-4bb5-91e7-99f9b365ed5d'); "Copia negli Appunti.")

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    <span data-ttu-id="0e23c-398">Questa regola di autorizzazione consente a un utente specifico di accedere a un computer della rete a cui ha accesso normalmente, tramite una specifica configurazione di sessione con ambito limitato alle esigenze tipiche di utilizzo di script e cmdlet dell'utente.</span><span class="sxs-lookup"><span data-stu-id="0e23c-398">This authorization rule allows a specific user access to one computer on the network to which they typically have access, with access to a specific session configuration that is scoped to the user’s typical scripting and cmdlet needs.</span></span> <span data-ttu-id="0e23c-399">Nell'esempio seguente, a un utente di nome <span class="code">JSmith</span> nel dominio <span class="code">Contoso</span> viene consentito l'accesso per la gestione del computer <span class="code">Contoso_214</span>, con una configurazione di sessione denominata <span class="code">NewAdminsOnly</span>.</span><span class="sxs-lookup"><span data-stu-id="0e23c-399">In the following example, a user named <span class="code">JSmith</span> in the <span class="code">Contoso</span> domain is granted access to manage the computer <span class="code">Contoso_214</span>, and use a session configuration named <span class="code">NewAdminsOnly</span>.</span></span>

    [<span data-ttu-id="0e23c-400">Copy</span><span class="sxs-lookup"><span data-stu-id="0e23c-400">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_efc3999a-2905-453f-86cd-014b41658ffc'); "Copia negli Appunti.")

        Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  <span data-ttu-id="0e23c-401">Per verificare che la regola sia stata creata, eseguire il cmdlet **Get-PswaAuthorizationRule** o **Test-PswaAuthorizationRule -UserName &lt;dominio\\utente | computer\\utente&gt; -ComputerName** &lt;nome_computer&gt;.</span><span class="sxs-lookup"><span data-stu-id="0e23c-401">Verify that the rule has been created by running either the **Get-PswaAuthorizationRule** cmdlet, or **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;.</span></span> <span data-ttu-id="0e23c-402">Ad esempio, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-402">For example, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span></span>

<span data-ttu-id="0e23c-403">Dopo la configurazione di una regola di autorizzazione, gli utenti autorizzati possono accedere alla console basata sul Web e iniziare a usare Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0e23c-403">After you have configured an authorization rule, you are ready for authorized users to sign in to the web-based console and begin using Windows PowerShell Web Access.</span></span>

<a href="" id="BKMK_configcert"></a>

<span data-ttu-id="0e23c-404"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configurare un certificato autentico</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="0e23c-404"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configure a genuine certificate</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="0e23c-405">Per un ambiente di produzione sicuro, usare sempre un certificato SSL valido firmato da un'Autorità di certificazione (CA).</span><span class="sxs-lookup"><span data-stu-id="0e23c-405">For a secure production environment, always use a valid SSL certificate that has been signed by a certification authority (CA).</span></span> <span data-ttu-id="0e23c-406">La procedura descritta in questa sezione illustra come ottenere e applicare un certificato SSL valido da un'Autorità di certificazione.</span><span class="sxs-lookup"><span data-stu-id="0e23c-406">The procedure in this section describes how to obtain and apply a valid SSL certificate from a CA.</span></span>

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a><span data-ttu-id="0e23c-407">Per configurare un certificato SSL in Gestione IIS</span><span class="sxs-lookup"><span data-stu-id="0e23c-407">To configure an SSL certificate in IIS Manager</span></span>

1.  <span data-ttu-id="0e23c-408">Nel riquadro dell'albero di Gestione IIS selezionare il server in cui è installato Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0e23c-408">In the IIS Manager tree pane, select the server on which Windows PowerShell Web Access is installed.</span></span>

2.  <span data-ttu-id="0e23c-409">Nel riquadro del contenuto fare doppio clic su **Certificati server**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-409">In the content pane, double click **Server Certificates**.</span></span>

3.  <span data-ttu-id="0e23c-410">Nel riquadro **Azioni** eseguire una delle operazioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="0e23c-410">In the **Actions** pane, do one of the following.</span></span> <span data-ttu-id="0e23c-411">Per altre informazioni sulla configurazione di certificati server in IIS, vedere [Configurazione dei certificati del server in IIS 7](https://technet.microsoft.com/library/cc732230.aspx).</span><span class="sxs-lookup"><span data-stu-id="0e23c-411">For more information about configuring server certificates in IIS, see [Configuring Server Certificates in IIS 7](https://technet.microsoft.com/library/cc732230.aspx).</span></span>

    -   <span data-ttu-id="0e23c-412">Fare clic su **Importa** per importare un certificato valido esistente da un percorso della rete aziendale.</span><span class="sxs-lookup"><span data-stu-id="0e23c-412">Click **Import** to import an existing, valid certificate from a location on your network.</span></span>

    -   <span data-ttu-id="0e23c-413">Fare clic su **Crea richiesta di certificato** per richiedere un certificato a una CA quale VeriSign™, Thawte o GeoTrust®.</span><span class="sxs-lookup"><span data-stu-id="0e23c-413">Click **Create Certificate Request** to request a certificate from a CA such as VeriSign™, Thawte, or GeoTrust®.</span></span> <span data-ttu-id="0e23c-414">Il nome comune del certificato deve corrispondere all'intestazione host nella richiesta.</span><span class="sxs-lookup"><span data-stu-id="0e23c-414">The certificate's common name must match the host header in the request.</span></span> <span data-ttu-id="0e23c-415">Se ad esempio il browser client richiede http://www.contoso.com/, anche il nome comune deve essere http://www.contoso.com/.</span><span class="sxs-lookup"><span data-stu-id="0e23c-415">For example, if the client browser requests http://www.contoso.com/, then the common name must also be http://www.contoso.com/.</span></span> <span data-ttu-id="0e23c-416">Questa è l'opzione più sicura, e quindi consigliata, per fornire un certificato al gateway di Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0e23c-416">This is the most secure and recommended option for providing the Windows PowerShell Web Access gateway with a certificate.</span></span>

    -   <span data-ttu-id="0e23c-417">Fare clic su **Crea un certificato autofirmato** per creare un certificato da usare immediatamente e, se necessario, far firmare a una CA in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="0e23c-417">Click **Create a Self-Signed Certificate** to create a certificate that you can use immediately, and have signed later by a CA if desired.</span></span> <span data-ttu-id="0e23c-418">Specificare un nome descrittivo per il certificato autofirmato, ad esempio **Accesso Web Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-418">Specify a friendly name for the self-signed certificate, such as **Windows PowerShell Web Access**.</span></span> <span data-ttu-id="0e23c-419">Questa opzione non è considerata sicura ed è consigliabile utilizzarla solo per un ambiente di test privato.</span><span class="sxs-lookup"><span data-stu-id="0e23c-419">This option is not considered secure, and is recommended only for a private test environment.</span></span>

4.  <span data-ttu-id="0e23c-420">Dopo avere ottenuto o creato un certificato, selezionare il sito Web a cui è applicato (ad esempio **Sito Web predefinito**) nel riquadro dell'albero di Gestione IIS, quindi fare clic su **Binding** nel riquadro **Azioni** .</span><span class="sxs-lookup"><span data-stu-id="0e23c-420">After creating or obtaining a certificate, select the website to which the certificate is applied (for example, **Default Web Site**) in the IIS Manager tree pane, and then click **Bindings** in the **Actions** pane.</span></span>

5.  <span data-ttu-id="0e23c-421">Nella finestra di dialogo **Aggiungi binding sito** aggiungere un binding **https** al sito, se non è già visualizzato.</span><span class="sxs-lookup"><span data-stu-id="0e23c-421">In the **Add Site Binding** dialog box, add an **https** binding for the site, if one is not already displayed.</span></span> <span data-ttu-id="0e23c-422">Se non si utilizza un certificato autofirmato, specificare il nome host del passaggio 3 di questa procedura.</span><span class="sxs-lookup"><span data-stu-id="0e23c-422">If you are not using a self-signed certificate, specify the host name from step 3 of this procedure.</span></span> <span data-ttu-id="0e23c-423">Se si utilizza un certificato autofirmato, questo passaggio non è necessario.</span><span class="sxs-lookup"><span data-stu-id="0e23c-423">If you are using a self-signed certificate, this step is not required.</span></span>

6.  <span data-ttu-id="0e23c-424">Selezionare il certificato ottenuto o creato nel passaggio 3 di questa procedura e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="0e23c-424">Select the certificate that you obtained or created in step 3 of this procedure, and then click **OK**.</span></span>

<a href="" id="BKMK_using"></a>

<span data-ttu-id="0e23c-425"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Uso della console di Windows PowerShell basata sul Web</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_5" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="0e23c-425"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Using the web-based Windows PowerShell console</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_5" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="0e23c-426">Dopo avere installato Accesso Web Windows PowerShell e completato la configurazione del gateway come illustrato in questo argomento, la console di Windows PowerShell basata sul Web è pronta all'uso.</span><span class="sxs-lookup"><span data-stu-id="0e23c-426">After Windows PowerShell Web Access is installed and the gateway configuration is finished as described in this topic, the Windows PowerShell web-based console is ready to use.</span></span> <span data-ttu-id="0e23c-427">Per altre informazioni su come iniziare a usare la console basata sul Web, vedere [Usare la console di Windows PowerShell basata sul Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx).</span><span class="sxs-lookup"><span data-stu-id="0e23c-427">For more information about getting started in the web-based console, see [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx).</span></span>

<span data-ttu-id="0e23c-428"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Vedere anche</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_6" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="0e23c-428"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_6" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="0e23c-429">[Internet Information Services (IIS) 7.0 Documentation (Documentazione di Internet Information Services (IIS) 7.0)](https://technet.microsoft.com/library/cc753433.aspx)
[IIS Manager 7.0 Help (Guida di Gestione IIS 7.0)](https://technet.microsoft.com/library/cc732664.aspx)
[Configure Web Server Security (IIS 7) (Configurare la sicurezza del server Web (IIS 7))](https://technet.microsoft.com/library/cc731278.aspx)
[IPsec Deployment Resources (Risorse sulla distribuzione di IPsec)](https://technet.microsoft.com/network/bb531150)</span><span class="sxs-lookup"><span data-stu-id="0e23c-429">[Internet Information Services (IIS) 7.0 Documentation](https://technet.microsoft.com/library/cc753433.aspx)
[IIS Manager 7.0 Help](https://technet.microsoft.com/library/cc732664.aspx)
[Configure Web Server Security (IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
[IPsec Deployment Resources](https://technet.microsoft.com/network/bb531150)</span></span>

<span data-ttu-id="0e23c-430"><span>Show:</span> Inherited Protected</span><span class="sxs-lookup"><span data-stu-id="0e23c-430"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="0e23c-431"><span class="stdr-votetitle">Questa pagina è stata utile?</span></span><span class="sxs-lookup"><span data-stu-id="0e23c-431"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="0e23c-432">Sì No</span><span class="sxs-lookup"><span data-stu-id="0e23c-432">Yes No</span></span>

<span data-ttu-id="0e23c-433">Altri suggerimenti?</span><span class="sxs-lookup"><span data-stu-id="0e23c-433">Additional feedback?</span></span>

<span data-ttu-id="0e23c-434"><span class="stdr-count"><span class="stdr-charcnt">1500</span> caratteri rimanenti</span> Invia Ignora</span><span class="sxs-lookup"><span data-stu-id="0e23c-434"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="0e23c-435"><span class="stdr-thankyou">Grazie</span></span><span class="sxs-lookup"><span data-stu-id="0e23c-435"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="0e23c-436"><span class="stdr-appreciate">I suggerimenti degli utenti sono importanti.</span></span><span class="sxs-lookup"><span data-stu-id="0e23c-436"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="0e23c-437">Gestisci il tuo profilo</span><span class="sxs-lookup"><span data-stu-id="0e23c-437">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="0e23c-438"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Commenti e suggerimenti sul sito</a> Commenti e suggerimenti sul sito</span><span class="sxs-lookup"><span data-stu-id="0e23c-438"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="0e23c-439"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="0e23c-439"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="0e23c-440">Raccontaci la tua esperienza</span><span class="sxs-lookup"><span data-stu-id="0e23c-440">Tell us about your experience...</span></span>

<span data-ttu-id="0e23c-441">La pagina è stata caricata rapidamente?</span><span class="sxs-lookup"><span data-stu-id="0e23c-441">Did the page load quickly?</span></span>

<span data-ttu-id="0e23c-442"><span> Sì<span> </span></span> <span> No<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="0e23c-442"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="0e23c-443">Ti piace la grafica?</span><span class="sxs-lookup"><span data-stu-id="0e23c-443">Do you like the page design?</span></span>

<span data-ttu-id="0e23c-444"><span> Sì<span> </span></span> <span> No<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="0e23c-444"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="0e23c-445">Parla con noi</span><span class="sxs-lookup"><span data-stu-id="0e23c-445">Tell us more</span></span>

-   [<span data-ttu-id="0e23c-446">Newsletter Flash</span><span class="sxs-lookup"><span data-stu-id="0e23c-446">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="0e23c-447">Contattaci</span><span class="sxs-lookup"><span data-stu-id="0e23c-447">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="0e23c-448">Informativa sulla privacy</span><span class="sxs-lookup"><span data-stu-id="0e23c-448">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="0e23c-449">Condizioni per l'utilizzo</span><span class="sxs-lookup"><span data-stu-id="0e23c-449">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="0e23c-450">Marchi</span><span class="sxs-lookup"><span data-stu-id="0e23c-450">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="0e23c-451">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="0e23c-451">© 2016 Microsoft</span></span>

<span data-ttu-id="0e23c-452">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="0e23c-452">© 2016 Microsoft</span></span>

<span data-ttu-id="0e23c-453">Il codice e gli script di terze parti, collegati al presente sito o a cui il sito Web fa riferimento, vengono ceduti in licenza all'utente dalle terze parti proprietarie di tale codice, non da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0e23c-453">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="0e23c-454">Vedere le condizioni d'uso di Ajax CDN di ASP.NET – http://www.asp.net/ajaxlibrary/CDN.ashx.</span><span class="sxs-lookup"><span data-stu-id="0e23c-454">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

