---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: disinstallare accesso web windows powershell
ms.openlocfilehash: 7231d5eadceda8e3b28d9a81c2b5dcbe43680ff2
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
#  <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="8761b-103">Disinstallare Accesso Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8761b-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="8761b-104">Ultimo aggiornamento: 24 giugno 2013</span><span class="sxs-lookup"><span data-stu-id="8761b-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="8761b-105">Si applica a: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="8761b-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="8761b-106">Seguire i passaggi indicati in questo argomento per eliminare l'applicazione e il sito Web di Accesso Web Windows PowerShell dal server gateway che esegue Windows Server 2012 R2 o Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="8761b-106">Follow steps in this topic to delete the Windows PowerShell Web Access website and application from the gateway server that is running either Windows Server 2012 R2 or Windows Server 2012.</span></span> <span data-ttu-id="8761b-107">Prima di iniziare, informare gli utenti della console basata sul Web di cui si intende rimuovere il sito Web.</span><span class="sxs-lookup"><span data-stu-id="8761b-107">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<a href="" id="BKMK_uninstall"></a>

------------------------------------------------------------------------

<span data-ttu-id="8761b-108">Prima di disinstallare Accesso Web Windows PowerShell dal server gateway, eseguire il cmdlet <span class="code">Uninstall-PswaWebApplication</span> per rimuovere il sito Web e le applicazioni Web di Accesso Web Windows PowerShell oppure eseguire la procedura [Per eliminare le applicazioni Web e il sito Web di Accesso Web Windows PowerShell in Gestione IIS](#BKMK_delsite).</span><span class="sxs-lookup"><span data-stu-id="8761b-108">Before you uninstall Windows PowerShell Web Access from the gateway server, either run the <span class="code">Uninstall-PswaWebApplication</span> cmdlet to remove the website and Windows PowerShell Web Access web applications, or use the IIS Manager procedure, [To delete the Windows PowerShell Web Access website and web applications by using IIS Manager](#BKMK_delsite).</span></span>

<span data-ttu-id="8761b-109">La procedura di disinstallazione di Accesso Web Windows PowerShell non disinstalla IIS o le altre funzionalità installate automaticamente, perché sono necessarie per l'esecuzione di Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8761b-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span> <span data-ttu-id="8761b-110">La procedura di disinstallazione mantiene installate le funzionalità da cui dipende Accesso Web Windows PowerShell. Se necessario, è possibile disinstallare tali funzionalità separatamente.</span><span class="sxs-lookup"><span data-stu-id="8761b-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

<span data-ttu-id="8761b-111"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Disinstallazione consigliata (rapida)</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="8761b-111"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Recommended (quick) uninstallation</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="8761b-112">Le procedure in questa sezione consentono di disinstallare l'applicazione Web Accesso Web Windows PowerShell e la funzionalità Accesso Web Windows PowerShell con i cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8761b-112">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using Windows PowerShell cmdlets.</span></span>

###

<span data-ttu-id="8761b-113"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Passaggio 1: Eliminare l'applicazione Web</span></a></span><span class="sxs-lookup"><span data-stu-id="8761b-113"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Delete the web application</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="8761b-114">Se è stato specificato il nome del sito Web personalizzato, aggiungere il parametro <span class="code">WebsiteName</span> al comando e specificare il nome del sito Web.</span><span class="sxs-lookup"><span data-stu-id="8761b-114">If you have specified your own, custom website name, add the <span class="code">WebsiteName</span> parameter to your command, and specify the website name.</span></span> <span data-ttu-id="8761b-115">Se è stata usata un'applicazione Web personalizzata (non l'applicazione predefinita, **pswa**), aggiungere il parametro <span class="code">WebApplicationName</span> al comando e specificare il nome dell'applicazione Web.</span><span class="sxs-lookup"><span data-stu-id="8761b-115">If you have used a custom web application (not the default application, **pswa**, add the <span class="code">WebApplicationName</span> parameter to your command, and specify the name of the web application.</span></span>

#### <a name="to-delete-the-website-and-web-applications-by-using-the-uninstall-pswawebapplication-cmdlet"></a><span data-ttu-id="8761b-116">Per eliminare il sito Web e le applicazioni Web tramite il cmdlet Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="8761b-116">To delete the website and web applications by using the Uninstall-PswaWebApplication cmdlet</span></span>

1.  <span data-ttu-id="8761b-117">Per aprire una sessione di Windows PowerShell, eseguire una di queste operazioni.</span><span class="sxs-lookup"><span data-stu-id="8761b-117">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="8761b-118">Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="8761b-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="8761b-119">Nella schermata **Start** di Windows fare clic su **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="8761b-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="8761b-120">Digitare **Uninstall-PswaWebApplication** e quindi premere **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="8761b-120">Type **Uninstall-PswaWebApplication**, and then press **Enter**.</span></span>

3.  <span data-ttu-id="8761b-121">Se si usa un certificato di prova, aggiungere il parametro <span class="code">DeleteTestCertificate</span> al cmdlet come mostrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="8761b-121">If you are using a test certificate, add the <span class="code">DeleteTestCertificate</span> parameter to the cmdlet, as shown in the following example.</span></span>

    [<span data-ttu-id="8761b-122">Copy</span><span class="sxs-lookup"><span data-stu-id="8761b-122">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_28147344-ab2f-49e7-b1c2-6dbe649d4366'); "Copia negli Appunti.")

        Uninstall-PswaWebApplication -DeleteTestCertificate

###

<span data-ttu-id="8761b-123"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Passaggio 2: Disinstallare Accesso Web Windows PowerShell</span></a></span><span class="sxs-lookup"><span data-stu-id="8761b-123"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Uninstall Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-uninstall-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a><span data-ttu-id="8761b-124">Per disinstallare Accesso Web Windows PowerShell tramite i cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8761b-124">To uninstall Windows PowerShell Web Access by using Windows PowerShell cmdlets</span></span>

1.  <span data-ttu-id="8761b-125">Per aprire una sessione di Windows PowerShell con diritti utente elevati, eseguire una di queste operazioni.</span><span class="sxs-lookup"><span data-stu-id="8761b-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="8761b-126">Se è presente una sessione aperta, continuare con il passaggio successivo.</span><span class="sxs-lookup"><span data-stu-id="8761b-126">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="8761b-127">Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni e scegliere **Esegui come amministratore**.</span><span class="sxs-lookup"><span data-stu-id="8761b-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="8761b-128">Nella schermata **Start** di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** e quindi scegliere **Esegui come amministratore**.</span><span class="sxs-lookup"><span data-stu-id="8761b-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="8761b-129">Digitare il codice seguente e premere **INVIO**, dove *nome_computer* rappresenta un server remoto da cui si vuole rimuovere Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8761b-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="8761b-130">Il parametro <span class="code">-Restart</span> riavvia automaticamente i server di destinazione, se richiesto dalla procedura di rimozione.</span><span class="sxs-lookup"><span data-stu-id="8761b-130">The <span class="code">-Restart</span> parameter automatically restarts destination servers if required by the removal.</span></span>

    [<span data-ttu-id="8761b-131">Copy</span><span class="sxs-lookup"><span data-stu-id="8761b-131">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_7b534520-f292-471f-89e3-a1079c03e369'); "Copia negli Appunti.")

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="8761b-132">Per rimuovere ruoli e funzionalità da un disco rigido virtuale offline, è necessario aggiungere i parametri <span class="code">-ComputerName</span> e <span class="code">-VHD</span>.</span><span class="sxs-lookup"><span data-stu-id="8761b-132">To remove roles and features from an offline VHD, you must add both the <span class="code">-ComputerName</span> parameter and the <span class="code">-VHD</span> parameter.</span></span> <span data-ttu-id="8761b-133">Il parametro <span class="code">-ComputerName</span> contiene il nome del server in cui montare il disco rigido virtuale e il parametro <span class="code">VHD</span> contiene il percorso del file VHD nel server specificato.</span><span class="sxs-lookup"><span data-stu-id="8761b-133">The <span class="code">-ComputerName</span> parameter contains the name of the server on which to mount the VHD, and the <span class="code">-VHD</span> parameter contains the path to the VHD file on the specified server.</span></span>

    [<span data-ttu-id="8761b-134">Copy</span><span class="sxs-lookup"><span data-stu-id="8761b-134">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_5d8f91ee-b91a-4653-b7df-e745187fd72d'); "Copia negli Appunti.")

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

3.  <span data-ttu-id="8761b-135">Terminata la rimozione verificare che Accesso Web Windows PowerShell sia stato rimosso, aprendo la pagina **Tutti i server** in Server Manager, selezionando un server da cui è stata rimossa la funzionalità e visualizzando il riquadro **Ruoli e funzionalità** nella pagina del server selezionato.</span><span class="sxs-lookup"><span data-stu-id="8761b-135">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span> <span data-ttu-id="8761b-136">È anche possibile eseguire il cmdlet <span class="code">Get-WindowsFeature</span> indicando come destinazione il server selezionato (Get-WindowsFeature -ComputerName &lt;*nome_computer*&gt;) per visualizzare un elenco di ruoli e funzionalità installati nel server.</span><span class="sxs-lookup"><span data-stu-id="8761b-136">You can also run the <span class="code">Get-WindowsFeature</span> cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

<span data-ttu-id="8761b-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Disinstallazione personalizzata</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="8761b-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Custom uninstallation</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="8761b-138">Le procedure in questa sezione consentono di disinstallare l'applicazione Web Accesso Web Windows PowerShell e la funzionalità Accesso Web Windows PowerShell usando la Rimozione guidata ruoli e funzionalità in Server Manager e la console Gestione IIS.</span><span class="sxs-lookup"><span data-stu-id="8761b-138">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

###

<span data-ttu-id="8761b-139"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Passaggio 1: Eliminare l'applicazione Web</span></a></span><span class="sxs-lookup"><span data-stu-id="8761b-139"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Delete the web application</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-delete-the-windows-powershell-web-access-website-and-web-applications-by-using-iis-manager"></a><span data-ttu-id="8761b-140">Per eliminare le applicazioni Web e il sito Web di Accesso Web Windows PowerShell tramite Gestione IIS</span><span class="sxs-lookup"><span data-stu-id="8761b-140">To delete the Windows PowerShell Web Access website and web applications by using IIS Manager</span></span>

1.  <span data-ttu-id="8761b-141">Aprire la console Gestione IIS eseguendo una delle operazioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="8761b-141">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="8761b-142">Se è già aperta, continuare con il passaggio successivo.</span><span class="sxs-lookup"><span data-stu-id="8761b-142">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="8761b-143">Nel desktop di Windows avviare Server Manager facendo clic su **Server Manager** nella barra delle applicazioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="8761b-143">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="8761b-144">Nel menu **Strumenti** di Server Manager fare clic su **Gestione Internet Information Services (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="8761b-144">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="8761b-145">Nella schermata **Start** di Windows digitare una parte qualsiasi del nome **Gestione Internet Information Services (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="8761b-145">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="8761b-146">Fare clic sul collegamento quando viene visualizzato nell'elenco dei risultati **App**.</span><span class="sxs-lookup"><span data-stu-id="8761b-146">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="8761b-147">Nel riquadro dell'albero di Gestione IIS selezionare il sito Web che esegue l'applicazione Web Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8761b-147">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

3.  <span data-ttu-id="8761b-148">Nel riquadro **Azioni**, in **Gestisci sito Web** fare clic su **Arresta**.</span><span class="sxs-lookup"><span data-stu-id="8761b-148">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

4.  <span data-ttu-id="8761b-149">Nel riquadro dell'albero fare clic con il pulsante destro del mouse sull'applicazione Web nel sito Web che esegue l'applicazione Web di Accesso Web Windows PowerShell, quindi fare clic su **Rimuovi**.</span><span class="sxs-lookup"><span data-stu-id="8761b-149">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

5.  <span data-ttu-id="8761b-150">Nel riquadro dell'albero selezionare **Pool di applicazioni**, selezionare la cartella del pool di applicazioni di Accesso Web Windows PowerShell, fare clic su **Arresta** nel riquadro **Azioni**, quindi fare clic su **Rimuovi** nel riquadro del contenuto.</span><span class="sxs-lookup"><span data-stu-id="8761b-150">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

6.  <span data-ttu-id="8761b-151">Chiudere Gestione Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="8761b-151">Close IIS Manager.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="8761b-152"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Nota </span></span><span class="sxs-lookup"><span data-stu-id="8761b-152"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="8761b-153">Durante la disinstallazione il certificato non viene eliminato.</span><span class="sxs-lookup"><span data-stu-id="8761b-153">The certificate is not deleted during uninstallation.</span></span> <span data-ttu-id="8761b-154">Se è stato creato un certificato autofirmato o si utilizza un certificato di prova e si desidera rimuoverlo, eliminare il certificato in Gestione IIS.</span><span class="sxs-lookup"><span data-stu-id="8761b-154">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span></p></td>
    </tr>
    </tbody>
    </table>

###

<span data-ttu-id="8761b-155"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Passaggio 2: Disinstallare Accesso Web Windows PowerShell</span></a></span><span class="sxs-lookup"><span data-stu-id="8761b-155"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Uninstall Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-uninstall-windows-powershell-web-access-by-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="8761b-156">Per disinstallare Accesso Web Windows PowerShell tramite Rimozione guidata ruoli e funzionalità</span><span class="sxs-lookup"><span data-stu-id="8761b-156">To uninstall Windows PowerShell Web Access by using the Remove Roles and Features Wizard</span></span>

1.  <span data-ttu-id="8761b-157">Se Server Manager è già aperto, andare al passaggio successivo.</span><span class="sxs-lookup"><span data-stu-id="8761b-157">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="8761b-158">Se Server Manager non è aperto, aprirlo in uno dei modi seguenti.</span><span class="sxs-lookup"><span data-stu-id="8761b-158">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="8761b-159">Nel desktop di Windows avviare Server Manager facendo clic su **Server Manager** nella barra delle applicazioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="8761b-159">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="8761b-160">Nella schermata **Start** di Windows fare clic su **Server Manager**.</span><span class="sxs-lookup"><span data-stu-id="8761b-160">On the Windows **Start** screen, click **Server Manager**.</span></span>

2.  <span data-ttu-id="8761b-161">Scegliere **Rimuovi ruoli e funzionalità** dal menu **Gestisci**.</span><span class="sxs-lookup"><span data-stu-id="8761b-161">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

3.  <span data-ttu-id="8761b-162">Nella pagina **Selezione server di destinazione** selezionare il server o il disco rigido virtuale offline da cui si vuole rimuovere la funzionalità.</span><span class="sxs-lookup"><span data-stu-id="8761b-162">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="8761b-163">Per selezionare un disco rigido virtuale offline, selezionare innanzitutto il server in cui montare il disco rigido virtuale, quindi selezionare il file del disco rigido virtuale.</span><span class="sxs-lookup"><span data-stu-id="8761b-163">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="8761b-164">Dopo aver selezionato il server di destinazione, fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="8761b-164">After you have selected the destination server, click **Next**.</span></span>

4.  <span data-ttu-id="8761b-165">Fare di nuovo clic su **Avanti** per ignorare la pagina **Rimuovi funzionalità**.</span><span class="sxs-lookup"><span data-stu-id="8761b-165">Click **Next** again to skip to the **Remove features** page.</span></span>

5.  <span data-ttu-id="8761b-166">Deselezionare la casella di controllo **Accesso Web Windows PowerShell** e fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="8761b-166">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

6.  <span data-ttu-id="8761b-167">Nella pagina **Conferma selezioni per la rimozione** fare clic su **Rimuovi**.</span><span class="sxs-lookup"><span data-stu-id="8761b-167">On the **Confirm removal selections** page, click **Remove**.</span></span>

<span data-ttu-id="8761b-168"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Vedere anche</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="8761b-168"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="8761b-169">[Installare e usare Accesso Web Windows PowerShell](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[Guida di Gestione IIS 7.0](https://technet.microsoft.com/library/cc732664.aspx)</span><span class="sxs-lookup"><span data-stu-id="8761b-169">[Install and Use Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[IIS Manager 7.0 Help](https://technet.microsoft.com/library/cc732664.aspx)</span></span>

<span data-ttu-id="8761b-170"><span>Show:</span> Inherited Protected</span><span class="sxs-lookup"><span data-stu-id="8761b-170"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="8761b-171"><span class="stdr-votetitle">Questa pagina è stata utile?</span></span><span class="sxs-lookup"><span data-stu-id="8761b-171"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="8761b-172">Sì No</span><span class="sxs-lookup"><span data-stu-id="8761b-172">Yes No</span></span>

<span data-ttu-id="8761b-173">Altri suggerimenti?</span><span class="sxs-lookup"><span data-stu-id="8761b-173">Additional feedback?</span></span>

<span data-ttu-id="8761b-174"><span class="stdr-count"><span class="stdr-charcnt">1500</span> caratteri rimanenti</span> Invia Ignora</span><span class="sxs-lookup"><span data-stu-id="8761b-174"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="8761b-175"><span class="stdr-thankyou">Grazie</span></span><span class="sxs-lookup"><span data-stu-id="8761b-175"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="8761b-176"><span class="stdr-appreciate">I suggerimenti degli utenti sono importanti.</span></span><span class="sxs-lookup"><span data-stu-id="8761b-176"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="8761b-177">Gestisci il tuo profilo</span><span class="sxs-lookup"><span data-stu-id="8761b-177">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="8761b-178"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Commenti e suggerimenti sul sito</a> Commenti e suggerimenti sul sito</span><span class="sxs-lookup"><span data-stu-id="8761b-178"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="8761b-179"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="8761b-179"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="8761b-180">Raccontaci la tua esperienza</span><span class="sxs-lookup"><span data-stu-id="8761b-180">Tell us about your experience...</span></span>

<span data-ttu-id="8761b-181">La pagina è stata caricata rapidamente?</span><span class="sxs-lookup"><span data-stu-id="8761b-181">Did the page load quickly?</span></span>

<span data-ttu-id="8761b-182"><span> Sì<span> </span></span> <span> No<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="8761b-182"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="8761b-183">Ti piace la grafica?</span><span class="sxs-lookup"><span data-stu-id="8761b-183">Do you like the page design?</span></span>

<span data-ttu-id="8761b-184"><span> Sì<span> </span></span> <span> No<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="8761b-184"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="8761b-185">Parla con noi</span><span class="sxs-lookup"><span data-stu-id="8761b-185">Tell us more</span></span>

-   [<span data-ttu-id="8761b-186">Newsletter Flash</span><span class="sxs-lookup"><span data-stu-id="8761b-186">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="8761b-187">Contattaci</span><span class="sxs-lookup"><span data-stu-id="8761b-187">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="8761b-188">Informativa sulla privacy</span><span class="sxs-lookup"><span data-stu-id="8761b-188">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="8761b-189">Condizioni per l'utilizzo</span><span class="sxs-lookup"><span data-stu-id="8761b-189">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="8761b-190">Marchi</span><span class="sxs-lookup"><span data-stu-id="8761b-190">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="8761b-191">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="8761b-191">© 2016 Microsoft</span></span>

<span data-ttu-id="8761b-192">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="8761b-192">© 2016 Microsoft</span></span>

<span data-ttu-id="8761b-193">Il codice e gli script di terze parti, collegati al presente sito o a cui il sito Web fa riferimento, vengono ceduti in licenza all'utente dalle terze parti proprietarie di tale codice, non da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8761b-193">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="8761b-194">Vedere le condizioni d'uso di Ajax CDN di ASP.NET – http://www.asp.net/ajaxlibrary/CDN.ashx.</span><span class="sxs-lookup"><span data-stu-id="8761b-194">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

