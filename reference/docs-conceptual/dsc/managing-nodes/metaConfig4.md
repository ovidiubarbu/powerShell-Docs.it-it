---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Configurazione di Gestione configurazione locale in PowerShell 4.0
ms.openlocfilehash: 747b15c483c79a7ecbb62214ef5a59f8dc137bd4
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953828"
---
# <a name="configuring-the-lcm-in-powershell-40"></a><span data-ttu-id="2cb05-103">Configurazione di Gestione configurazione locale in PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="2cb05-103">Configuring the LCM in PowerShell 4.0</span></span>

><span data-ttu-id="2cb05-104">Si applica a: Windows PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="2cb05-104">Applies To: Windows PowerShell 4.0</span></span>

<span data-ttu-id="2cb05-105">**Per informazioni correlate a Windows PowerShell 5.0 e versioni successive, vedere [Configurazione di Gestione configurazione locale](metaConfig.md).**</span><span class="sxs-lookup"><span data-stu-id="2cb05-105">**For information related to Windows PowerShell 5.0 and later, see [Configuring the Local Configuration Manager](metaConfig.md).**</span></span>

<span data-ttu-id="2cb05-106">Gestione configurazione locale è il motore di Windows PowerShell DSC (Desired State Configuration).</span><span class="sxs-lookup"><span data-stu-id="2cb05-106">Local Configuration Manager is the Windows PowerShell Desired State Configuration (DSC) engine.</span></span>
<span data-ttu-id="2cb05-107">Viene eseguito in tutti i nodi di destinazione e ha la responsabilità di chiamare le risorse di configurazione incluse in uno script di configurazione DSC.</span><span class="sxs-lookup"><span data-stu-id="2cb05-107">It runs on all target nodes, and it is responsible for calling the configuration resources that are included in a DSC configuration script.</span></span>
<span data-ttu-id="2cb05-108">Questo argomento contiene l'elenco delle proprietà di Gestione configurazione locale e descrive in che modo modificare le impostazioni di Gestione configurazione locale in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="2cb05-108">This topic lists the properties of Local Configuration Manager and describes how you can modify the Local Configuration Manager settings on a target node.</span></span>

## <a name="local-configuration-manager-properties"></a><span data-ttu-id="2cb05-109">Proprietà di Gestione configurazione locale</span><span class="sxs-lookup"><span data-stu-id="2cb05-109">Local Configuration Manager properties</span></span>

<span data-ttu-id="2cb05-110">Di seguito sono elencate le proprietà di Gestione configurazione locale che è possibile impostare o recuperare.</span><span class="sxs-lookup"><span data-stu-id="2cb05-110">The following lists the Local Configuration Manager properties that you can set or retrieve.</span></span>

- <span data-ttu-id="2cb05-111">**AllowModuleOverwrite**: controlla se le nuove configurazioni scaricate dal servizio di configurazione possono sovrascrivere quelle meno recenti nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="2cb05-111">**AllowModuleOverwrite**: Controls whether new configurations downloaded from the configuration service are allowed to overwrite the old ones on the target node.</span></span> <span data-ttu-id="2cb05-112">I possibili valori sono True e False.</span><span class="sxs-lookup"><span data-stu-id="2cb05-112">Possible values are True and False.</span></span>
- <span data-ttu-id="2cb05-113">**CertificateID**: Identificazione personale di un certificato usato per credenziali protette passate in una configurazione.</span><span class="sxs-lookup"><span data-stu-id="2cb05-113">**CertificateID**: The thumbprint of a certificate used to secure credentials passed in a configuration.</span></span> <span data-ttu-id="2cb05-114">Per altre informazioni, vedere [Protezione delle credenziali in Windows PowerShell DSC (Desired State Configuration)](https://blogs.msdn.microsoft.com/powershell/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/).</span><span class="sxs-lookup"><span data-stu-id="2cb05-114">For more information see [Want to secure credentials in Windows PowerShell Desired State Configuration?](https://blogs.msdn.microsoft.com/powershell/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/).</span></span>
- <span data-ttu-id="2cb05-115">**ConfigurationID**: indica un GUID usato per ottenere un file di configurazione specifico da un servizio di pull.</span><span class="sxs-lookup"><span data-stu-id="2cb05-115">**ConfigurationID**: Indicates a GUID which is used to get a particular configuration file from a pull service.</span></span> <span data-ttu-id="2cb05-116">Il GUID garantisce l'accesso al file di configurazione corretto.</span><span class="sxs-lookup"><span data-stu-id="2cb05-116">The GUID ensures that the correct configuration file is accessed.</span></span>
- <span data-ttu-id="2cb05-117">**ConfigurationMode**: specifica il modo in cui Gestione configurazione locale applica effettivamente la configurazione ai nodi di destinazione.</span><span class="sxs-lookup"><span data-stu-id="2cb05-117">**ConfigurationMode**: Specifies how the Local Configuration Manager actually applies the configuration to the target nodes.</span></span> <span data-ttu-id="2cb05-118">Può accettare i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="2cb05-118">It can take the following values:</span></span>
  - <span data-ttu-id="2cb05-119">**ApplyOnly**: con questa opzione, DSC applica la configurazione e non esegue altre operazioni, a meno che non venga rilevata una nuova configurazione quando si invia una nuova configurazione direttamente al nodo di destinazione o se ci si connette a un servizio di pull e DSC individua una nuova configurazione quando controlla nel servizio di pull.</span><span class="sxs-lookup"><span data-stu-id="2cb05-119">**ApplyOnly**: With this option, DSC applies the configuration and does nothing further unless a new configuration is detected, either by you sending a new configuration directly to the target node or if you are connecting to a pull service and DSC discovers a new configuration when it checks with the pull service.</span></span> <span data-ttu-id="2cb05-120">Se la configurazione del nodo di destinazione non è sincronizzata, non viene eseguita alcuna azione.</span><span class="sxs-lookup"><span data-stu-id="2cb05-120">If the target node's configuration drifts, no action is taken.</span></span>
  - <span data-ttu-id="2cb05-121">**ApplyAndMonitor**: con questa opzione, che corrisponde all'impostazione predefinita, DSC applica tutte le nuove configurazioni, sia quelle inviate direttamente al nodo di destinazione sia quelle individuate in un servizio di pull.</span><span class="sxs-lookup"><span data-stu-id="2cb05-121">**ApplyAndMonitor**: With this option (which is the default), DSC applies any new configurations, whether sent by you directly to the target node or discovered on a pull service.</span></span> <span data-ttu-id="2cb05-122">Quindi, se la configurazione del nodo di destinazione non è sincronizzata rispetto al file di configurazione, DSC segnala la discrepanza nei log.</span><span class="sxs-lookup"><span data-stu-id="2cb05-122">Thereafter, if the configuration of the target node drifts from the configuration file, DSC reports the discrepancy in logs.</span></span> <span data-ttu-id="2cb05-123">Per altre informazioni sulla registrazione di DSC, vedere la pagina sull'[uso di registri eventi per la diagnosi di errori in DSC (Desired State Configuration)](https://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).</span><span class="sxs-lookup"><span data-stu-id="2cb05-123">For more about DSC logging, see [Using Event Logs to Diagnose Errors in Desired State Configuration](https://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).</span></span>
  - <span data-ttu-id="2cb05-124">**ApplyAndAutoCorrect**: con questa opzione DSC applica tutte le nuove configurazioni, sia quelle inviate direttamente al nodo di destinazione sia quelle individuate in un servizio di pull.</span><span class="sxs-lookup"><span data-stu-id="2cb05-124">**ApplyAndAutoCorrect**: With this option, DSC applies any new configurations, whether sent by you directly to the target node or discovered on a pull service.</span></span> <span data-ttu-id="2cb05-125">Quindi, se la configurazione del nodo di destinazione non è sincronizzata rispetto al file di configurazione, DSC segnala la discrepanza nei log e quindi tenta di modificare la configurazione del nodo di destinazione per garantire la conformità con il file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="2cb05-125">Thereafter, if the configuration of the target node drifts from the configuration file, DSC reports the discrepancy in logs, and then attempts to adjust the target node configuration to bring in compliance with the configuration file.</span></span>
- <span data-ttu-id="2cb05-126">**ConfigurationModeFrequencyMins**: rappresenta la frequenza (in minuti) con cui l'applicazione in background di DSC prova a implementare la configurazione corrente nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="2cb05-126">**ConfigurationModeFrequencyMins**: Represents the frequency (in minutes) at which the background application of DSC attempts to implement the current configuration on the target node.</span></span> <span data-ttu-id="2cb05-127">Il valore predefinito è 15.</span><span class="sxs-lookup"><span data-stu-id="2cb05-127">The default value is 15.</span></span> <span data-ttu-id="2cb05-128">Questo valore può essere impostato insieme a RefreshMode.</span><span class="sxs-lookup"><span data-stu-id="2cb05-128">This value can be set in conjunction with RefreshMode.</span></span> <span data-ttu-id="2cb05-129">Quando la proprietà RefreshMode è impostata su PULL, il nodo di destinazione contatta il servizio di configurazione in base a un intervallo impostato tramite RefreshFrequencyMins e scarica la configurazione corrente.</span><span class="sxs-lookup"><span data-stu-id="2cb05-129">When RefreshMode is set to PULL, the target node contacts the configuration service at an interval set by RefreshFrequencyMins and downloads the current configuration.</span></span> <span data-ttu-id="2cb05-130">Indipendentemente dal valore di RefreshMode, il motore di coerenza applica la configurazione più recente scaricata al nodo di destinazione in base all'intervallo impostato tramite ConfigurationModeFrequencyMins.</span><span class="sxs-lookup"><span data-stu-id="2cb05-130">Regardless of the RefreshMode value, at the interval set by ConfigurationModeFrequencyMins, the consistency engine applies the latest configuration that was downloaded to the target node.</span></span> <span data-ttu-id="2cb05-131">La proprietà RefreshFrequencyMins deve essere impostata su un numero intero multiplo di ConfigurationModeFrequencyMins.</span><span class="sxs-lookup"><span data-stu-id="2cb05-131">RefreshFrequencyMins should be set to an integer multiple of ConfigurationModeFrequencyMins.</span></span>
- <span data-ttu-id="2cb05-132">**Credential**: indica, come con Get-Credential, le credenziali necessarie per accedere alle risorse remote, ad esempio per contattare il servizio di configurazione.</span><span class="sxs-lookup"><span data-stu-id="2cb05-132">**Credential**: Indicates credentials (as with Get-Credential) required to access remote resources, such as to contact the configuration service.</span></span>
- <span data-ttu-id="2cb05-133">**DownloadManagerCustomData**: rappresenta una matrice che contiene dati personalizzati specifici del gestore di download.</span><span class="sxs-lookup"><span data-stu-id="2cb05-133">**DownloadManagerCustomData**: Represents an array that contains custom data specific to the download manager.</span></span>
- <span data-ttu-id="2cb05-134">**DownloadManagerName**: indica il nome del gestore di download di configurazioni e moduli.</span><span class="sxs-lookup"><span data-stu-id="2cb05-134">**DownloadManagerName**: Indicates the name of the configuration and module download manager.</span></span>
- <span data-ttu-id="2cb05-135">**RebootNodeIfNeeded**: impostare questa opzione su `$true` per consentire alle risorse di riavviare il nodo tramite il flag `$global:DSCMachineStatus`.</span><span class="sxs-lookup"><span data-stu-id="2cb05-135">**RebootNodeIfNeeded**: Set this to `$true` to allow resources to reboot the Node using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="2cb05-136">In caso contrario, sarà necessario riavviare manualmente il nodo per qualsiasi configurazione che lo richiede.</span><span class="sxs-lookup"><span data-stu-id="2cb05-136">Otherwise, you will have to manually reboot the node for any configuration that requires it.</span></span> <span data-ttu-id="2cb05-137">Il valore predefinito è `$false`.</span><span class="sxs-lookup"><span data-stu-id="2cb05-137">The default value is `$false`.</span></span> <span data-ttu-id="2cb05-138">Per usare questa impostazione quando una condizione di ravvio viene applicata da un componente diverso da DSC (ad esempio Windows Installer), combinare questa impostazione con il modulo [xPendingReboot](https://github.com/powershell/xpendingreboot).</span><span class="sxs-lookup"><span data-stu-id="2cb05-138">To use this setting when a reboot condition is enacted by something other than DSC (such as Windows Installer), combine this setting with the [xPendingReboot](https://github.com/powershell/xpendingreboot) module.</span></span>
- <span data-ttu-id="2cb05-139">**RefreshFrequencyMins**: proprietà usata quando è stato configurato un servizio di pull.</span><span class="sxs-lookup"><span data-stu-id="2cb05-139">**RefreshFrequencyMins**: Used when you have set up a pull service.</span></span> <span data-ttu-id="2cb05-140">Rappresenta la frequenza (in minuti) in base alla quale Gestione configurazione locale contatta un servizio di pull per scaricare la configurazione corrente.</span><span class="sxs-lookup"><span data-stu-id="2cb05-140">Represents the frequency (in minutes) at which the Local Configuration Manager contacts a pull service to download the current configuration.</span></span> <span data-ttu-id="2cb05-141">Questo valore può essere impostato insieme a ConfigurationModeFrequencyMins.</span><span class="sxs-lookup"><span data-stu-id="2cb05-141">This value can be set in conjunction with ConfigurationModeFrequencyMins.</span></span> <span data-ttu-id="2cb05-142">Quando la proprietà RefreshMode è impostata su PULL, il nodo di destinazione contatta il servizio di pull in base a un intervallo impostato tramite RefreshFrequencyMins e scarica la configurazione corrente.</span><span class="sxs-lookup"><span data-stu-id="2cb05-142">When RefreshMode is set to PULL, the target node contacts the pull service at an interval set by RefreshFrequencyMins and downloads the current configuration.</span></span> <span data-ttu-id="2cb05-143">Il motore di coerenza applica la configurazione più recente scaricata al nodo di destinazione in base all'intervallo impostato tramite ConfigurationModeFrequencyMins.</span><span class="sxs-lookup"><span data-stu-id="2cb05-143">At the interval set by ConfigurationModeFrequencyMins, the consistency engine then applies the latest configuration that was downloaded to the target node.</span></span> <span data-ttu-id="2cb05-144">Se la proprietà RefreshFrequencyMins non è impostata su un numero intero multiplo di ConfigurationModeFrequencyMins, il sistema arrotonda questo valore.</span><span class="sxs-lookup"><span data-stu-id="2cb05-144">If RefreshFrequencyMins is not set to an integer multiple of ConfigurationModeFrequencyMins, the system will round it up.</span></span> <span data-ttu-id="2cb05-145">Il valore predefinito è 30.</span><span class="sxs-lookup"><span data-stu-id="2cb05-145">The default value is 30.</span></span>
- <span data-ttu-id="2cb05-146">**RefreshMode**: i valori possibili sono **Push** (impostazione predefinita) e **Pull**.</span><span class="sxs-lookup"><span data-stu-id="2cb05-146">**RefreshMode**: Possible values are **Push** (the default) and **Pull**.</span></span> <span data-ttu-id="2cb05-147">Nella configurazione "push" è necessario inserire un file di configurazione in ogni nodo di destinazione, usando qualsiasi computer client.</span><span class="sxs-lookup"><span data-stu-id="2cb05-147">In the "push" configuration, you must place a configuration file on each target node, using any client computer.</span></span> <span data-ttu-id="2cb05-148">In modalità "pull" è necessario configurare un servizio di pull perché Gestione configurazione locale possa contattare i file di configurazione e accedervi.</span><span class="sxs-lookup"><span data-stu-id="2cb05-148">In the "pull" mode, you must set up a pull service for Local Configuration Manager to contact and access the configuration files.</span></span>

> [!NOTE]
> <span data-ttu-id="2cb05-149">Gestione configurazione locale avvia il ciclo **ConfigurationModeFrequencyMins** in base agli eventi seguenti:</span><span class="sxs-lookup"><span data-stu-id="2cb05-149">The LCM starts the **ConfigurationModeFrequencyMins** cycle based on:</span></span>
>
> - <span data-ttu-id="2cb05-150">Applicazione di una nuova metaconfigurazione tramite `Set-DscLocalConfigurationManager`</span><span class="sxs-lookup"><span data-stu-id="2cb05-150">A new metaconfig is applied using `Set-DscLocalConfigurationManager`</span></span>
> - <span data-ttu-id="2cb05-151">Riavvio del computer</span><span class="sxs-lookup"><span data-stu-id="2cb05-151">A machine restart</span></span>
>
> <span data-ttu-id="2cb05-152">Per qualsiasi condizione in cui il processo timer rilevi un arresto anomalo del sistema, esso viene rilevato entro 30 secondi e il ciclo viene riavviato.</span><span class="sxs-lookup"><span data-stu-id="2cb05-152">For any condition where the timer process experiences a crash, that will be detected within 30 seconds and the cycle will be restarted.</span></span>
> <span data-ttu-id="2cb05-153">Un'operazione simultanea può ritardare l'avvio del ciclo. Se la durata dell'operazione supera la frequenza del ciclo configurata, il timer successivo non viene avviato.</span><span class="sxs-lookup"><span data-stu-id="2cb05-153">A concurrent operation could delay the cycle from being started, if the duration of this operation exceeds the configured cycle frequency, the next timer will not start.</span></span>
>
> <span data-ttu-id="2cb05-154">La metaconfigurazione di esempio è configurata con una frequenza di pull di 15 minuti e un'operazione di pull si verifica in corrispondenza di T1.</span><span class="sxs-lookup"><span data-stu-id="2cb05-154">Example, the metaconfig is configured at a 15 minute pull frequency and a pull occurs at T1.</span></span>  <span data-ttu-id="2cb05-155">Il nodo non completa l'operazione per 16 minuti.</span><span class="sxs-lookup"><span data-stu-id="2cb05-155">The Node does not finish work for 16 minutes.</span></span>  <span data-ttu-id="2cb05-156">Il primo ciclo di 15 minuti viene ignorato e l'operazione di pull successiva avverrà in corrispondenza di T1 + 15 + 15.</span><span class="sxs-lookup"><span data-stu-id="2cb05-156">The first 15 minute cycle is ignored, and next pull will happen at T1+15+15.</span></span>

### <a name="example-of-updating-local-configuration-manager-settings"></a><span data-ttu-id="2cb05-157">Esempio di aggiornamento delle impostazioni di Gestione configurazione locale</span><span class="sxs-lookup"><span data-stu-id="2cb05-157">Example of updating Local Configuration Manager settings</span></span>

<span data-ttu-id="2cb05-158">È possibile aggiornare le impostazioni di Gestione configurazione locale di un nodo di destinazione inserendo in uno script di configurazione un blocco **LocalConfigurationManager** all'interno del blocco del nodo, come mostrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="2cb05-158">You can update the Local Configuration Manager settings of a target node by including a **LocalConfigurationManager** block inside the node block in a configuration script, as shown in the following example.</span></span>

```powershell
Configuration ExampleConfig
{
    Node "Server001"
    {
        LocalConfigurationManager
        {
            ConfigurationID = "646e48cb-3082-4a12-9fd9-f71b9a562d4e"
            ConfigurationModeFrequencyMins = 45
            ConfigurationMode = "ApplyAndAutocorrect"
            RefreshMode = "Pull"
            RefreshFrequencyMins = 90
            DownloadManagerName = "WebDownloadManager"
            DownloadManagerCustomData = (@{ServerUrl="https://$PullService/psdscpullserver.svc"})
            CertificateID = "71AA68562316FE3F73536F1096B85D66289ED60E"
            Credential = $cred
            RebootNodeIfNeeded = $true
            AllowModuleOverwrite = $false
        }
# One or more resource blocks can be added here
    }
}

# The following line invokes the configuration and creates a file called Server001.meta.mof at the specified path
ExampleConfig -OutputPath "c:\users\public\dsc"
```

<span data-ttu-id="2cb05-159">L'esecuzione dello script dell'esempio precedente genera un file MOF che specifica e archivia le impostazioni desiderate.</span><span class="sxs-lookup"><span data-stu-id="2cb05-159">Running the script in the previous example generates a MOF file that specifies and stores the desired settings.</span></span>
<span data-ttu-id="2cb05-160">Per applicare le impostazioni, è possibile usare il cmdlet **Set-DscLocalConfigurationManager**, come mostrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="2cb05-160">To apply the settings, you can use the **Set-DscLocalConfigurationManager** cmdlet, as shown in the following example.</span></span>

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> [!NOTE]
> <span data-ttu-id="2cb05-161">per il parametro **Path**, è necessario specificare lo stesso percorso specificato per il parametro **OutputPath** quando è stata richiamata la configurazione nell'esempio precedente.</span><span class="sxs-lookup"><span data-stu-id="2cb05-161">For the **Path** parameter, you must specify the same path that you specified for the **OutputPath** parameter when you invoked the configuration in the previous example.</span></span>

<span data-ttu-id="2cb05-162">Per visualizzare le impostazioni di Gestione configurazione locale correnti, è possibile usare il cmdlet **Get-DscLocalConfigurationManager**.</span><span class="sxs-lookup"><span data-stu-id="2cb05-162">To see the current Local Configuration Manager settings, you can use the **Get-DscLocalConfigurationManager** cmdlet.</span></span>
<span data-ttu-id="2cb05-163">Se richiamato senza parametri, per impostazione predefinita questo cmdlet ottiene le impostazioni di Gestione configurazione locale per il nodo in cui viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="2cb05-163">If you invoke this cmdlet with no parameters, by default it will get the Local Configuration Manager settings for the node on which you run it.</span></span>
<span data-ttu-id="2cb05-164">Per specificare un altro nodo, usare il parametro **CimSession** con questo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2cb05-164">To specify another node, use the **CimSession** parameter with this cmdlet.</span></span>