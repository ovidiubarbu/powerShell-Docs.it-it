---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Configurare un Client di Pull usando un ID configurazione in PowerShell 5.0 e versioni successive
ms.openlocfilehash: 8d8cf478f9127e1b7005d1b9e832e84b11612c9c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680872"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a><span data-ttu-id="4d33f-103">Configurare un Client di Pull usando un ID configurazione in PowerShell 5.0 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="4d33f-103">Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="4d33f-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4d33f-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4d33f-105">Il server di pull (funzionalità di Windows *servizio DSC*) è un componente supportato di Windows Server, tuttavia non si prevede di offrire nuove caratteristiche o funzionalità.</span><span class="sxs-lookup"><span data-stu-id="4d33f-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="4d33f-106">È consigliabile avviare la transizione dei client gestiti ad [Automation DSC per Azure](/azure/automation/automation-dsc-getting-started) (include funzionalità superiori al server di pull in Windows Server) o a una delle soluzioni della community riportate [qui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="4d33f-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="4d33f-107">Prima di configurare un client di pull, è necessario configurare un server di pull.</span><span class="sxs-lookup"><span data-stu-id="4d33f-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="4d33f-108">Anche se quest'ordine non sia obbligatorio, consente la risoluzione dei problemi e consente di assicurarsi che la registrazione è riuscita.</span><span class="sxs-lookup"><span data-stu-id="4d33f-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="4d33f-109">Per configurare un server di pull, è possibile usare le guide seguenti:</span><span class="sxs-lookup"><span data-stu-id="4d33f-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="4d33f-110">Configurare un server di pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="4d33f-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="4d33f-111">Configurare un server di pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="4d33f-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="4d33f-112">Ogni nodo di destinazione può essere configurato per scaricare le configurazioni, risorse e anche segnalare lo stato.</span><span class="sxs-lookup"><span data-stu-id="4d33f-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="4d33f-113">Le sezioni seguenti illustrano come configurare un client di pull con una condivisione SMB o HTTP Server di Pull DSC.</span><span class="sxs-lookup"><span data-stu-id="4d33f-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="4d33f-114">Quando Gestione configurazione locale del nodo viene aggiornato, ti contatterà per il percorso configurato per scaricare eventuali configurazioni assegnate.</span><span class="sxs-lookup"><span data-stu-id="4d33f-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="4d33f-115">Se tutte le risorse necessarie non sono presenti nel nodo, verrà automaticamente scaricato li dal percorso configurato.</span><span class="sxs-lookup"><span data-stu-id="4d33f-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="4d33f-116">Se il nodo è configurato con un [Server di Report](reportServer.md), quindi segnala lo stato dell'operazione.</span><span class="sxs-lookup"><span data-stu-id="4d33f-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> <span data-ttu-id="4d33f-117">**Nota**: Questo argomento si applica a PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="4d33f-117">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="4d33f-118">Per informazioni sulla configurazione di un client di pull in PowerShell 4.0, vedere [Configurazione di un client di pull usando un ID configurazione in PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="4d33f-118">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="4d33f-119">Configurare il client di pull Gestione configurazione locale</span><span class="sxs-lookup"><span data-stu-id="4d33f-119">Configure the pull client LCM</span></span>

<span data-ttu-id="4d33f-120">L'esecuzione di uno degli esempi seguenti viene creata una nuova cartella di output denominata **PullClientConfigID** e inserisce un file MOF di metaconfigurazione esiste.</span><span class="sxs-lookup"><span data-stu-id="4d33f-120">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="4d33f-121">In questo caso, il file MOF di metaconfigurazione sarà denominato `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="4d33f-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="4d33f-122">Per applicare la configurazione, chiamare il cmdlet **Set-DscLocalConfigurationManager**, con il valore di **Path** impostato sul percorso del file MOF di metaconfigurazione.</span><span class="sxs-lookup"><span data-stu-id="4d33f-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="4d33f-123">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="4d33f-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="4d33f-124">ID configurazione</span><span class="sxs-lookup"><span data-stu-id="4d33f-124">Configuration ID</span></span>

<span data-ttu-id="4d33f-125">Gli esempi seguenti set il **ConfigurationID** proprietà di Gestione configurazione locale per un **Guid** che fosse stato creato in precedenza per questo scopo.</span><span class="sxs-lookup"><span data-stu-id="4d33f-125">The examples below sets the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="4d33f-126">Il valore di **ConfigurationID** viene usato da Gestione configurazione locale per trovare la configurazione appropriata nel server di pull.</span><span class="sxs-lookup"><span data-stu-id="4d33f-126">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="4d33f-127">Il file MOF di configurazione nel server di pull deve essere denominato `ConfigurationID.mof`, dove *ConfigurationID* è il valore della proprietà **ConfigurationID** di Gestione configurazione locale del nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="4d33f-127">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="4d33f-128">Per altre informazioni, vedere [pubblicare le configurazioni a un Server di Pull (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="4d33f-128">For more information see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="4d33f-129">È possibile creare uno casuale **Guid** usando l'esempio sotto, o tramite il [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4d33f-129">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="4d33f-130">Per altre informazioni sull'uso **GUID** nell'ambiente in uso, vedere [pianificare GUID](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="4d33f-130">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="4d33f-131">Configurare un Client di Pull per scaricare le configurazioni</span><span class="sxs-lookup"><span data-stu-id="4d33f-131">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="4d33f-132">Ogni client deve essere configurato **Pull** modalità e fornire l'url di server di pull in cui la configurazione viene archiviata.</span><span class="sxs-lookup"><span data-stu-id="4d33f-132">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="4d33f-133">A tale scopo, è necessario configurare Gestione configurazione locale con le informazioni richieste.</span><span class="sxs-lookup"><span data-stu-id="4d33f-133">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="4d33f-134">Per configurare Gestione configurazione locale, è necessario creare un tipo speciale di configurazione usando l'attributo **DSCLocalConfigurationManager**.</span><span class="sxs-lookup"><span data-stu-id="4d33f-134">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="4d33f-135">Per altre informazioni sulla configurazione di Gestione configurazione locale, vedere [Configurazione di Gestione configurazione locale](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="4d33f-135">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="4d33f-136">Server di Pull DSC HTTP</span><span class="sxs-lookup"><span data-stu-id="4d33f-136">HTTP DSC Pull Server</span></span>

<span data-ttu-id="4d33f-137">Lo script seguente configura Gestione configurazione locale per il pull delle configurazioni da un server denominato "CONTOSO-PullSrv".</span><span class="sxs-lookup"><span data-stu-id="4d33f-137">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

<span data-ttu-id="4d33f-138">Nello script il blocco **ConfigurationRepositoryWeb** definisce il server di pull.</span><span class="sxs-lookup"><span data-stu-id="4d33f-138">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="4d33f-139">Il **ServerUrl** specifica l'url di pull DSC</span><span class="sxs-lookup"><span data-stu-id="4d33f-139">The **ServerUrl** specifies the url of the DSC Pull</span></span>

### <a name="smb-share"></a><span data-ttu-id="4d33f-140">SMB Share</span><span class="sxs-lookup"><span data-stu-id="4d33f-140">SMB Share</span></span>

<span data-ttu-id="4d33f-141">Lo script seguente configura Gestione configurazione locale per il pull delle configurazioni da una condivisione SMB `\\SMBPullServer\Pull`.</span><span class="sxs-lookup"><span data-stu-id="4d33f-141">The following script configures the LCM to pull configurations from the SMB Share `\\SMBPullServer\Pull`.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="4d33f-142">Nello script, il **ConfigurationRepositoryShare** blocco definisce il server di pull, in questo caso, è sufficiente una condivisione SMB.</span><span class="sxs-lookup"><span data-stu-id="4d33f-142">In the script, the **ConfigurationRepositoryShare** block defines the pull server, which in this case, is just an SMB share.</span></span>

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="4d33f-143">Configurare un Client di Pull per scaricare le risorse</span><span class="sxs-lookup"><span data-stu-id="4d33f-143">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="4d33f-144">Se si specifica solo le **ConfigurationRepositoryWeb** oppure **ConfigurationRepositoryShare** nella configurazione di Gestione configurazione locale (come negli esempi precedenti), il client di pull effettuerà il pull delle risorse dallo stesso percorso recupera le configurazioni.</span><span class="sxs-lookup"><span data-stu-id="4d33f-144">If you specify only the **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous examples), the pull client will pull resources from the same location it retrieves its configurations.</span></span> <span data-ttu-id="4d33f-145">È anche possibile specificare posizioni distinte per le risorse.</span><span class="sxs-lookup"><span data-stu-id="4d33f-145">You can also specify separate locations for resources.</span></span> <span data-ttu-id="4d33f-146">Per specificare un percorso della risorsa come un server separato, usare il **ResourceRepositoryWeb** blocco.</span><span class="sxs-lookup"><span data-stu-id="4d33f-146">To specify a resource location as a separate server, use the **ResourceRepositoryWeb** block.</span></span> <span data-ttu-id="4d33f-147">Per specificare un percorso della risorsa come una condivisione SMB, usare il **ResourceRepositoryShare** blocco.</span><span class="sxs-lookup"><span data-stu-id="4d33f-147">To specify a resource location as an SMB share, use the **ResourceRepositoryShare** block.</span></span>

> [!NOTE]
> <span data-ttu-id="4d33f-148">È possibile combinare **ConfigurationRepositoryWeb** con **ResourceRepositoryShare** oppure **ConfigurationRepositoryShare** con **ResourceRepositoryWeb** .</span><span class="sxs-lookup"><span data-stu-id="4d33f-148">You can combine **ConfigurationRepositoryWeb** with **ResourceRepositoryShare** or **ConfigurationRepositoryShare** with **ResourceRepositoryWeb**.</span></span> <span data-ttu-id="4d33f-149">Esempi di questo oggetto non vengono visualizzati sotto.</span><span class="sxs-lookup"><span data-stu-id="4d33f-149">Examples of this are not shown below.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="4d33f-150">Server di Pull DSC HTTP</span><span class="sxs-lookup"><span data-stu-id="4d33f-150">HTTP DSC Pull Server</span></span>

<span data-ttu-id="4d33f-151">La metaconfigurazione seguente configura un client di pull per ottenere le configurazioni da **CONTOSO-PullSrv** e le relative risorse dalla **CONTOSO-ResourceSrv**.</span><span class="sxs-lookup"><span data-stu-id="4d33f-151">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a><span data-ttu-id="4d33f-152">SMB Share</span><span class="sxs-lookup"><span data-stu-id="4d33f-152">SMB Share</span></span>

<span data-ttu-id="4d33f-153">Nell'esempio seguente viene illustrata una metaconfigurazione che configura un client per il pull delle configurazioni da una condivisione SMB `\\SMBPullServer\Configurations`e le risorse da una condivisione SMB `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="4d33f-153">The following example shows a metaconfiguration that sets up a client to pull configurations from the SMB share `\\SMBPullServer\Configurations`, and resources from the SMB share `\\SMBPullServer\Resources`.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a><span data-ttu-id="4d33f-154">Scarica automaticamente le risorse in modalità Push</span><span class="sxs-lookup"><span data-stu-id="4d33f-154">Automatically download Resources in Push Mode</span></span>

<span data-ttu-id="4d33f-155">A partire da PowerShell 5.0, i client di pull possono scaricare i moduli da una condivisione SMB, anche quando sono configurati per la **Push** modalità.</span><span class="sxs-lookup"><span data-stu-id="4d33f-155">Beginning in PowerShell 5.0, your pull clients can download modules from an SMB share, even when they are configured for **Push** mode.</span></span> <span data-ttu-id="4d33f-156">Ciò è particolarmente utile negli scenari in cui non si desidera configurare un Server di Pull.</span><span class="sxs-lookup"><span data-stu-id="4d33f-156">This is especially useful in scenarios where you do not want to set up a Pull Server.</span></span> <span data-ttu-id="4d33f-157">Il **ResourceRepositoryShare** blocco può essere usato senza specificare un **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="4d33f-157">The **ResourceRepositoryShare** block can be used without specifying a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="4d33f-158">Nell'esempio seguente viene illustrata una metaconfigurazione che configura un client per recuperare le risorse da una condivisione SMB `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="4d33f-158">The following example shows a metaconfiguration that sets up a client to pull resources from an SMB Share `\\SMBPullServer\Resources`.</span></span> <span data-ttu-id="4d33f-159">Quando il nodo è **PUSHED** una configurazione, verrà automaticamente scaricato tutte le risorse necessarie, dalla condivisione specificata.</span><span class="sxs-lookup"><span data-stu-id="4d33f-159">When the Node is **PUSHED** a configuration, it will automatically download any required resources, from the share specified.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="4d33f-160">Configurare un Client di Pull per segnalare lo stato</span><span class="sxs-lookup"><span data-stu-id="4d33f-160">Set up a Pull Client to report status</span></span>

<span data-ttu-id="4d33f-161">Per impostazione predefinita, i nodi non invierà report a un Server di Pull configurato.</span><span class="sxs-lookup"><span data-stu-id="4d33f-161">By default, Nodes will not send reports to a configured Pull Server.</span></span> <span data-ttu-id="4d33f-162">È possibile usare un singolo server di pull per le configurazioni, le risorse e i report, ma è necessario creare un blocco **ReportRepositoryWeb** per configurare la creazione di report.</span><span class="sxs-lookup"><span data-stu-id="4d33f-162">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="4d33f-163">Server di Pull DSC HTTP</span><span class="sxs-lookup"><span data-stu-id="4d33f-163">HTTP DSC Pull Server</span></span>

<span data-ttu-id="4d33f-164">Nell'esempio seguente viene illustrata una metaconfigurazione che configura un client per il pull di configurazioni e risorse e per l'invio di dati di report a un singolo server di pull.</span><span class="sxs-lookup"><span data-stu-id="4d33f-164">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="4d33f-165">Per specificare un server di report, usare un blocco **ReportRepositoryWeb**.</span><span class="sxs-lookup"><span data-stu-id="4d33f-165">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="4d33f-166">Un server di report non può essere un server SMB.</span><span class="sxs-lookup"><span data-stu-id="4d33f-166">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="4d33f-167">La metaconfigurazione seguente configura un client di pull in modo da ottenere le configurazioni da **CONTOSO-PullSrv** e le risorse da **CONTOSO-ResourceSrv** e inviare i report sullo stato a **CONTOSO-ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="4d33f-167">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a><span data-ttu-id="4d33f-168">SMB Share</span><span class="sxs-lookup"><span data-stu-id="4d33f-168">SMB Share</span></span>

<span data-ttu-id="4d33f-169">Un server di report non può essere una condivisione SMB.</span><span class="sxs-lookup"><span data-stu-id="4d33f-169">A report server cannot be an SMB share.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4d33f-170">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="4d33f-170">Next Steps</span></span>

<span data-ttu-id="4d33f-171">Dopo aver configurato il client di pull, è possibile utilizzare le guide seguenti per eseguire i passaggi successivi:</span><span class="sxs-lookup"><span data-stu-id="4d33f-171">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="4d33f-172">Pubblicare le configurazioni in un server di pull (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="4d33f-172">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="4d33f-173">Creare un pacchetto e caricare le risorse in un server di pull (v4)</span><span class="sxs-lookup"><span data-stu-id="4d33f-173">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="4d33f-174">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4d33f-174">See Also</span></span>

* [<span data-ttu-id="4d33f-175">Configurazione di un client di pull con nomi di configurazione</span><span class="sxs-lookup"><span data-stu-id="4d33f-175">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)
