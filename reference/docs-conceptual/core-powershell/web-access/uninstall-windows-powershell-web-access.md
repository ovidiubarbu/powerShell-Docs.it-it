---
ms.date: 2017-08-23
keywords: powershell,cmdlet
title: disinstallare accesso web windows powershell
ms.openlocfilehash: 7c71a245be244c1883598cdcddbf35e43c0fc7b0
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2017
---
# <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="7a057-103">Disinstallare Accesso Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a057-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="7a057-104">Ultimo aggiornamento: 24 giugno 2013</span><span class="sxs-lookup"><span data-stu-id="7a057-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="7a057-105">Si applica a: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="7a057-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="7a057-106">I passaggi descritti in questo argomento consentono di rimuovere il sito Web di Accesso Web Windows PowerShell e l'applicazione corrispondente dal server gateway in cui sono installati.</span><span class="sxs-lookup"><span data-stu-id="7a057-106">The steps in this topic remove the Windows PowerShell Web Access website and corresponding application from the gateway server where it is installed.</span></span>

## <a name="notify-users"></a><span data-ttu-id="7a057-107">Informare gli utenti</span><span class="sxs-lookup"><span data-stu-id="7a057-107">Notify users</span></span>

<span data-ttu-id="7a057-108">Prima di iniziare, informare gli utenti della console basata sul Web di cui si intende rimuovere il sito Web.</span><span class="sxs-lookup"><span data-stu-id="7a057-108">Before you begin, notify users of the web-based console that you are removing the website.</span></span>


<span data-ttu-id="7a057-109">Prima di disinstallare Accesso Web Windows PowerShell dal server gateway, eseguire il cmdlet `Uninstall-PswaWebApplication` per rimuovere il sito Web e le applicazioni Web di Accesso Web Windows PowerShell oppure usare la procedura [Per eliminare le applicazioni Web e il sito Web di Accesso Web Windows PowerShell]() in Gestione IIS.</span><span class="sxs-lookup"><span data-stu-id="7a057-109">Before you uninstall Windows PowerShell Web Access from the gateway server, either run the `Uninstall-PswaWebApplication` cmdlet to remove the website and Windows PowerShell Web Access web applications, or use the IIS Manager procedure, [to delete the windows powershell web access website and web applications by using iis manager]().</span></span>

<span data-ttu-id="7a057-110">La procedura di disinstallazione di Accesso Web Windows PowerShell non disinstalla IIS o le altre funzionalità installate automaticamente, perché sono necessarie per l'esecuzione di Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a057-110">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span> <span data-ttu-id="7a057-111">La procedura di disinstallazione mantiene installate le funzionalità da cui dipende Accesso Web Windows PowerShell. Se necessario, è possibile disinstallare tali funzionalità separatamente.</span><span class="sxs-lookup"><span data-stu-id="7a057-111">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

## <a name="recommended-quick-uninstallation"></a><span data-ttu-id="7a057-112">Disinstallazione consigliata (rapida)</span><span class="sxs-lookup"><span data-stu-id="7a057-112">Recommended (quick) uninstallation</span></span>

<span data-ttu-id="7a057-113">Le procedure in questa sezione consentono di installare sia:</span><span class="sxs-lookup"><span data-stu-id="7a057-113">Procedures in this section help you uninstall both:</span></span>

- <span data-ttu-id="7a057-114">l'applicazione Web Accesso Web Windows PowerShell, sia</span><span class="sxs-lookup"><span data-stu-id="7a057-114">the Windows PowerShell Web Access web application, and</span></span>
- <span data-ttu-id="7a057-115">la funzionalità Accesso Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a057-115">the Windows PowerShell Web Access feature</span></span>
 
<span data-ttu-id="7a057-116">usando i cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a057-116">by using Windows PowerShell cmdlets.</span></span>

### <a name="step-1-delete-the-web-application-using-cmdlets"></a><span data-ttu-id="7a057-117">Passaggio 1: Eliminare l'applicazione Web usando i cmdlet</span><span class="sxs-lookup"><span data-stu-id="7a057-117">Step 1: Delete the web application using cmdlets</span></span>

1. <span data-ttu-id="7a057-118">Per aprire una sessione di Windows PowerShell, eseguire una di queste operazioni.</span><span class="sxs-lookup"><span data-stu-id="7a057-118">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="7a057-119">Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="7a057-119">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="7a057-120">Nella schermata **Start** di Windows fare clic su **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="7a057-120">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2. <span data-ttu-id="7a057-121">Digitare `Uninstall-PswaWebApplication` e quindi premere **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="7a057-121">Type `Uninstall-PswaWebApplication`, and then press **Enter**.</span></span>
   1. <span data-ttu-id="7a057-122">Se è stato specificato il nome del sito Web personalizzato, aggiungere il parametro `-WebsiteName` al comando e specificare il nome del sito Web.</span><span class="sxs-lookup"><span data-stu-id="7a057-122">If you have specified your own, custom website name, add the `-WebsiteName` parameter to your command, and specify the website name.</span></span>

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. <span data-ttu-id="7a057-123">Se è stata usata un'applicazione Web personalizzata e non l'applicazione predefinita, **pswa**, aggiungere il parametro `-WebApplicationName` al comando e specificare il nome dell'applicazione Web.</span><span class="sxs-lookup"><span data-stu-id="7a057-123">If you have used a custom web application (not the default application, **pswa**, add the `-WebApplicationName` parameter to your command, and specify the name of the web application.</span></span>

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. <span data-ttu-id="7a057-124">Se si utilizza un certificato di prova, aggiungere il parametro `DeleteTestCertificate` al cmdlet come mostrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="7a057-124">If you are using a test certificate, add the `DeleteTestCertificate` parameter to the cmdlet, as shown in the following example.</span></span>

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a><span data-ttu-id="7a057-125">Passaggio 2: Disinstallare Accesso Web Windows PowerShell usando i cmdlet</span><span class="sxs-lookup"><span data-stu-id="7a057-125">Step 2: Uninstall Windows PowerShell Web Access using cmdlets</span></span>

1. <span data-ttu-id="7a057-126">Per aprire una sessione di Windows PowerShell con diritti utente elevati, eseguire una di queste operazioni.</span><span class="sxs-lookup"><span data-stu-id="7a057-126">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="7a057-127">Se è presente una sessione aperta, continuare con il passaggio successivo.</span><span class="sxs-lookup"><span data-stu-id="7a057-127">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="7a057-128">Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni e scegliere **Esegui come amministratore**.</span><span class="sxs-lookup"><span data-stu-id="7a057-128">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="7a057-129">Nella schermata **Start** di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** e quindi scegliere **Esegui come amministratore**.</span><span class="sxs-lookup"><span data-stu-id="7a057-129">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

1. <span data-ttu-id="7a057-130">Digitare il codice seguente e premere **INVIO**, dove *nome_computer* rappresenta un server remoto da cui si vuole rimuovere Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a057-130">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="7a057-131">Il parametro `-Restart` riavvia automaticamente i server di destinazione, se richiesto dalla procedura di rimozione.</span><span class="sxs-lookup"><span data-stu-id="7a057-131">The `-Restart` parameter automatically restarts destination servers if required by the removal.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="7a057-132">Per rimuovere ruoli e funzionalità da un disco rigido virtuale offline, è necessario aggiungere i parametri `-ComputerName` e `-VHD`.</span><span class="sxs-lookup"><span data-stu-id="7a057-132">To remove roles and features from an offline VHD, you must add both the `-ComputerName` parameter and the `-VHD` parameter.</span></span> <span data-ttu-id="7a057-133">Il parametro `-ComputerName` contiene il nome del server in cui montare il disco rigido virtuale e il parametro `-VHD` contiene il percorso del file VHD nel server specificato.</span><span class="sxs-lookup"><span data-stu-id="7a057-133">The `-ComputerName` parameter contains the name of the server on which to mount the VHD, and the `-VHD` parameter contains the path to the VHD file on the specified server.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. <span data-ttu-id="7a057-134">Terminata la rimozione verificare che Accesso Web Windows PowerShell sia stato rimosso, aprendo la pagina **Tutti i server** in Server Manager, selezionando un server da cui è stata rimossa la funzionalità e visualizzando il riquadro **Ruoli e funzionalità** nella pagina del server selezionato.</span><span class="sxs-lookup"><span data-stu-id="7a057-134">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span>

    <span data-ttu-id="7a057-135">È anche possibile eseguire il cmdlet `Get-WindowsFeature` indicando come destinazione il server selezionato (Get-WindowsFeature -ComputerName &lt;*nome_computer*&gt;) per visualizzare un elenco di ruoli e funzionalità installati nel server.</span><span class="sxs-lookup"><span data-stu-id="7a057-135">You can also run the `Get-WindowsFeature` cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

## <a name="custom-uninstallation"></a><span data-ttu-id="7a057-136">Disinstallazione personalizzata</span><span class="sxs-lookup"><span data-stu-id="7a057-136">Custom uninstallation</span></span>

<span data-ttu-id="7a057-137">Le procedure in questa sezione consentono di disinstallare l'applicazione Web Accesso Web Windows PowerShell e la funzionalità Accesso Web Windows PowerShell usando la Rimozione guidata ruoli e funzionalità in Server Manager e la console Gestione IIS.</span><span class="sxs-lookup"><span data-stu-id="7a057-137">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

### <a name="step-1-delete-the-web-application-using-iis-manager"></a><span data-ttu-id="7a057-138">Passaggio 1: Eliminare l'applicazione Web usando Gestione IIS</span><span class="sxs-lookup"><span data-stu-id="7a057-138">Step 1: Delete the web application using IIS Manager</span></span>


1. <span data-ttu-id="7a057-139">Aprire la console Gestione IIS eseguendo una delle operazioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="7a057-139">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="7a057-140">Se è già aperta, continuare con il passaggio successivo.</span><span class="sxs-lookup"><span data-stu-id="7a057-140">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="7a057-141">Nel desktop di Windows avviare Server Manager facendo clic su **Server Manager** nella barra delle applicazioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="7a057-141">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="7a057-142">Nel menu **Strumenti** di Server Manager fare clic su **Gestione Internet Information Services (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="7a057-142">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="7a057-143">Nella schermata **Start** di Windows digitare una parte qualsiasi del nome **Gestione Internet Information Services (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="7a057-143">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="7a057-144">Fare clic sul collegamento quando viene visualizzato nell'elenco dei risultati **App**.</span><span class="sxs-lookup"><span data-stu-id="7a057-144">Click the shortcut when it is displayed in the **Apps** results.</span></span>

1. <span data-ttu-id="7a057-145">Nel riquadro dell'albero di Gestione IIS selezionare il sito Web che esegue l'applicazione Web Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a057-145">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

1. <span data-ttu-id="7a057-146">Nel riquadro **Azioni**, in **Gestisci sito Web** fare clic su **Arresta**.</span><span class="sxs-lookup"><span data-stu-id="7a057-146">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

1. <span data-ttu-id="7a057-147">Nel riquadro dell'albero fare clic con il pulsante destro del mouse sull'applicazione Web nel sito Web che esegue l'applicazione Web di Accesso Web Windows PowerShell, quindi fare clic su **Rimuovi**.</span><span class="sxs-lookup"><span data-stu-id="7a057-147">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

1. <span data-ttu-id="7a057-148">Nel riquadro dell'albero selezionare **Pool di applicazioni**, selezionare la cartella del pool di applicazioni di Accesso Web Windows PowerShell, fare clic su **Arresta** nel riquadro **Azioni**, quindi fare clic su **Rimuovi** nel riquadro del contenuto.</span><span class="sxs-lookup"><span data-stu-id="7a057-148">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

1. <span data-ttu-id="7a057-149">Chiudere Gestione Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="7a057-149">Close IIS Manager.</span></span>

> <span data-ttu-id="7a057-150">![Nota di avviso](images/SecurityNote.jpeg)**Nota**:</span><span class="sxs-lookup"><span data-stu-id="7a057-150">![Warning note](images/SecurityNote.jpeg)**Note**:</span></span>
>
> <span data-ttu-id="7a057-151">Durante la disinstallazione il certificato non viene eliminato.</span><span class="sxs-lookup"><span data-stu-id="7a057-151">The certificate is not deleted during uninstallation.</span></span> 
>
> <span data-ttu-id="7a057-152">Se è stato creato un certificato autofirmato o si utilizza un certificato di prova e si desidera rimuoverlo, eliminare il certificato in Gestione IIS.</span><span class="sxs-lookup"><span data-stu-id="7a057-152">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span> 

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="7a057-153">Passaggio 2: Disinstallare Accesso Web Windows PowerShell usando Rimozione guidata ruoli e funzionalità</span><span class="sxs-lookup"><span data-stu-id="7a057-153">Step 2: Uninstall Windows PowerShell Web Access using the Remove Roles and Features Wizard</span></span>

1. <span data-ttu-id="7a057-154">Se Server Manager è già aperto, andare al passaggio successivo.</span><span class="sxs-lookup"><span data-stu-id="7a057-154">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="7a057-155">Se Server Manager non è aperto, aprirlo in uno dei modi seguenti.</span><span class="sxs-lookup"><span data-stu-id="7a057-155">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="7a057-156">Nel desktop di Windows avviare Server Manager facendo clic su **Server Manager** nella barra delle applicazioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="7a057-156">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="7a057-157">Nella schermata **Start** di Windows fare clic su **Server Manager**.</span><span class="sxs-lookup"><span data-stu-id="7a057-157">On the Windows **Start** screen, click **Server Manager**.</span></span>

1. <span data-ttu-id="7a057-158">Scegliere **Rimuovi ruoli e funzionalità** dal menu **Gestisci**.</span><span class="sxs-lookup"><span data-stu-id="7a057-158">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

1. <span data-ttu-id="7a057-159">Nella pagina **Selezione server di destinazione** selezionare il server o il disco rigido virtuale offline da cui si vuole rimuovere la funzionalità.</span><span class="sxs-lookup"><span data-stu-id="7a057-159">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="7a057-160">Per selezionare un disco rigido virtuale offline, selezionare innanzitutto il server in cui montare il disco rigido virtuale, quindi selezionare il file del disco rigido virtuale.</span><span class="sxs-lookup"><span data-stu-id="7a057-160">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="7a057-161">Dopo aver selezionato il server di destinazione, fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="7a057-161">After you have selected the destination server, click **Next**.</span></span>

1. <span data-ttu-id="7a057-162">Fare di nuovo clic su **Avanti** per ignorare la pagina **Rimuovi funzionalità**.</span><span class="sxs-lookup"><span data-stu-id="7a057-162">Click **Next** again to skip to the **Remove features** page.</span></span>

1. <span data-ttu-id="7a057-163">Deselezionare la casella di controllo **Accesso Web Windows PowerShell** e fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="7a057-163">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

1. <span data-ttu-id="7a057-164">Nella pagina **Conferma selezioni per la rimozione** fare clic su **Rimuovi**.</span><span class="sxs-lookup"><span data-stu-id="7a057-164">On the **Confirm removal selections** page, click **Remove**.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a057-165">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7a057-165">See Also</span></span>

- [<span data-ttu-id="7a057-166">Installare e usare Accesso Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a057-166">Install and Use Windows PowerShell Web Access</span></span>](install-and-use-windows-powershell-web-access.md)
- [<span data-ttu-id="7a057-167">Guida di Gestione IIS 7.0</span><span class="sxs-lookup"><span data-stu-id="7a057-167">IIS Manager 7.0 Help</span></span>](https://technet.microsoft.com/library/cc732664.aspx)
