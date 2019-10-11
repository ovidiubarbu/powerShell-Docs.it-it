---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Configurare un client di pull usando nomi di configurazione in PowerShell 5.0 e versioni successive
ms.openlocfilehash: d591e2a757130ccecaf4eaf9f363f607fca82b93
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953628"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a><span data-ttu-id="7f403-103">Configurare un client di pull usando nomi di configurazione in PowerShell 5.0 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="7f403-103">Set up a Pull Client using Configuration Names in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="7f403-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7f403-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7f403-105">Il server di pull (funzionalità di Windows *servizio DSC*) è un componente supportato di Windows Server, tuttavia non si prevede di offrire nuove caratteristiche o funzionalità.</span><span class="sxs-lookup"><span data-stu-id="7f403-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="7f403-106">È consigliabile avviare la transizione dei client gestiti ad [Automation DSC per Azure](/azure/automation/automation-dsc-getting-started) (include funzionalità superiori al server di pull in Windows Server) o a una delle soluzioni della community riportate [qui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="7f403-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="7f403-107">Prima di configurare un client di pull, è necessario configurare un server di pull.</span><span class="sxs-lookup"><span data-stu-id="7f403-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="7f403-108">Anche se quest'ordine non è obbligatorio, facilita la risoluzione dei problemi e agevola la riuscita della registrazione.</span><span class="sxs-lookup"><span data-stu-id="7f403-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="7f403-109">Per configurare un server di pull, è possibile usare le guide seguenti:</span><span class="sxs-lookup"><span data-stu-id="7f403-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="7f403-110">Configurare un server di pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="7f403-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="7f403-111">Configurare un server di pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="7f403-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="7f403-112">Ogni nodo di destinazione può essere configurato in modo che possa scaricare configurazioni e risorse e persino segnalare il proprio stato.</span><span class="sxs-lookup"><span data-stu-id="7f403-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="7f403-113">Le sezioni seguenti illustrano come configurare un client di pull con una condivisione SMB o on server di pull DSC HTTP.</span><span class="sxs-lookup"><span data-stu-id="7f403-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="7f403-114">Quando Gestione configurazione locale del nodo si aggiorna, contatta la posizione configurata per scaricare tutte le configurazioni assegnate.</span><span class="sxs-lookup"><span data-stu-id="7f403-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="7f403-115">Se una o più risorse necessarie non sono presenti nel nodo, le scarica automaticamente dalla posizione configurata.</span><span class="sxs-lookup"><span data-stu-id="7f403-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="7f403-116">Se il nodo è configurato con un [server di report](reportServer.md), segnala quindi lo stato dell'operazione.</span><span class="sxs-lookup"><span data-stu-id="7f403-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="7f403-117">Questo argomento si applica a PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="7f403-117">This topic applies to PowerShell 5.0.</span></span>
> <span data-ttu-id="7f403-118">Per informazioni sulla configurazione di un client di pull in PowerShell 4.0, vedere [Configurare un client di pull usando un ID configurazione in PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="7f403-118">For information on setting up a pull client in PowerShell 4.0, see [Set up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="7f403-119">Configurare Gestione configurazione locale del client di pull</span><span class="sxs-lookup"><span data-stu-id="7f403-119">Configure the pull client LCM</span></span>

<span data-ttu-id="7f403-120">L'esecuzione di uno degli esempi che seguono crea una nuova cartella di output denominata **PullClientConfigName** e inserisce in questa cartella un file MOF di metaconfigurazione.</span><span class="sxs-lookup"><span data-stu-id="7f403-120">Executing any of the examples below creates a new output folder named **PullClientConfigName** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="7f403-121">In questo caso, il file MOF di metaconfigurazione sarà denominato `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="7f403-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="7f403-122">Per applicare la configurazione, chiamare il cmdlet **Set-DscLocalConfigurationManager**, con il valore di **Path** impostato sul percorso del file MOF di metaconfigurazione.</span><span class="sxs-lookup"><span data-stu-id="7f403-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="7f403-123">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="7f403-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a><span data-ttu-id="7f403-124">Nome della configurazione</span><span class="sxs-lookup"><span data-stu-id="7f403-124">Configuration Name</span></span>

<span data-ttu-id="7f403-125">Gli esempi seguenti impostano la proprietà **ConfigurationName** di Gestione configurazione locale sul nome di una configurazione compilata in precedenza, creato per questo scopo.</span><span class="sxs-lookup"><span data-stu-id="7f403-125">The examples below sets the **ConfigurationName** property of the LCM to the name of a previously compiled Configuration, created for this purpose.</span></span> <span data-ttu-id="7f403-126">Il valore di **ConfigurationName** viene usato da Gestione configurazione locale per trovare la configurazione appropriata nel server di pull.</span><span class="sxs-lookup"><span data-stu-id="7f403-126">The **ConfigurationName** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="7f403-127">Il nome del file MOF di configurazione nel server di pull deve essere `<ConfigurationName>.mof`, in questo caso, "ClientConfig.mof".</span><span class="sxs-lookup"><span data-stu-id="7f403-127">The configuration MOF file on the pull server must be named `<ConfigurationName>.mof`, in this case, "ClientConfig.mof".</span></span> <span data-ttu-id="7f403-128">Per altre informazioni, vedere [Pubblicare le configurazioni in un server di pull (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="7f403-128">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="7f403-129">Configurare un client di pull per scaricare configurazioni</span><span class="sxs-lookup"><span data-stu-id="7f403-129">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="7f403-130">Ogni client deve essere configurato in modalità **Pull** e deve ricevere l'URL del server di pull in cui è archiviata la sua configurazione.</span><span class="sxs-lookup"><span data-stu-id="7f403-130">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="7f403-131">A tale scopo, è necessario configurare Gestione configurazione locale con le informazioni richieste.</span><span class="sxs-lookup"><span data-stu-id="7f403-131">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="7f403-132">Per configurare Gestione configurazione locale, è necessario creare un tipo speciale di configurazione usando l'attributo **DSCLocalConfigurationManager**.</span><span class="sxs-lookup"><span data-stu-id="7f403-132">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="7f403-133">Per altre informazioni sulla configurazione di Gestione configurazione locale, vedere [Configurazione di Gestione configurazione locale](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="7f403-133">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="7f403-134">Lo script seguente configura Gestione configurazione locale per il pull delle configurazioni da un server denominato "CONTOSO-PullSrv".</span><span class="sxs-lookup"><span data-stu-id="7f403-134">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

- <span data-ttu-id="7f403-135">Nello script il blocco **ConfigurationRepositoryWeb** definisce il server di pull.</span><span class="sxs-lookup"><span data-stu-id="7f403-135">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="7f403-136">La proprietà **ServerURL** specifica l'endpoint per il server di pull.</span><span class="sxs-lookup"><span data-stu-id="7f403-136">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

- <span data-ttu-id="7f403-137">La proprietà **RegistrationKey** è una chiave condivisa tra tutti i nodi client per un server di pull e il server di pull stesso.</span><span class="sxs-lookup"><span data-stu-id="7f403-137">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span> <span data-ttu-id="7f403-138">Lo stesso valore viene archiviato in un file nel server di pull.</span><span class="sxs-lookup"><span data-stu-id="7f403-138">The same value is stored in a file on the pull server.</span></span>
  > [!NOTE]
  > <span data-ttu-id="7f403-139">Le chiavi di registrazione funzionano solo con i server di pull **Web**.</span><span class="sxs-lookup"><span data-stu-id="7f403-139">Registration keys work only with **web** pull servers.</span></span> <span data-ttu-id="7f403-140">Con un server di pull **SMB** è necessario usare **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="7f403-140">You must still use **ConfigurationID** with an **SMB** pull server.</span></span>
  > <span data-ttu-id="7f403-141">Per informazioni sulla configurazione di un server di pull usando **ConfigurationID**, vedere [Configurazione di un client di pull usando un ID configurazione](pullClientConfigId.md).</span><span class="sxs-lookup"><span data-stu-id="7f403-141">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigId.md)</span></span>

- <span data-ttu-id="7f403-142">La proprietà **ConfigurationNames** è una matrice che specifica i nomi delle configurazioni per il nodo client.</span><span class="sxs-lookup"><span data-stu-id="7f403-142">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
  ><span data-ttu-id="7f403-143">**Nota:** se si specifica più di un valore in **ConfigurationNames**, è necessario specificare anche i blocchi **PartialConfiguration** nella configurazione.</span><span class="sxs-lookup"><span data-stu-id="7f403-143">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
  ><span data-ttu-id="7f403-144">Per informazioni sulle configurazioni parziali, vedere [configurazioni parziali di PowerShell DSC](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="7f403-144">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="7f403-145">Configurare un client di pull per scaricare risorse</span><span class="sxs-lookup"><span data-stu-id="7f403-145">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="7f403-146">Se si specifica solo un blocco **ConfigurationRepositoryWeb** o **ConfigurationRepositoryShare** nella configurazione di Gestione configurazione locale, come nell'esempio precedente, il client di pull eseguirà il pull delle risorse dalla stessa posizione in cui sono archiviati i file con estensione "mof".</span><span class="sxs-lookup"><span data-stu-id="7f403-146">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from same location where your ".mof" files are stored.</span></span> <span data-ttu-id="7f403-147">È anche possibile specificare posizioni diverse per il download delle risorse da parte dei client.</span><span class="sxs-lookup"><span data-stu-id="7f403-147">You can also specify different locations where clients can download resources.</span></span> <span data-ttu-id="7f403-148">Per specificare un server delle risorse, usare un blocco **ResourceRepositoryWeb** (per un server di pull Web) o **ResourceRepositoryShare** (per un server di pull SMB).</span><span class="sxs-lookup"><span data-stu-id="7f403-148">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>

<span data-ttu-id="7f403-149">L'esempio seguente illustra una metaconfigurazione che configura un client per il download di configurazioni da un server di pull e per il download di risorse da una condivisione SMB.</span><span class="sxs-lookup"><span data-stu-id="7f403-149">The following example shows a metaconfiguration that sets up a client to download configurations from a Pull Server, and resources from an SMB share.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="7f403-150">Configurare un client di pull per la segnalazione dello stato</span><span class="sxs-lookup"><span data-stu-id="7f403-150">Set up a Pull Client to report status</span></span>

<span data-ttu-id="7f403-151">È possibile usare un unico server di pull per le configurazioni, le risorse e i report.</span><span class="sxs-lookup"><span data-stu-id="7f403-151">You can use a single pull server for configurations, resources, and reporting.</span></span> <span data-ttu-id="7f403-152">Per impostazione predefinita, la creazione di report non è configurata per i client.</span><span class="sxs-lookup"><span data-stu-id="7f403-152">Reporting is not configured for clients by default.</span></span> <span data-ttu-id="7f403-153">Per configurare un client per la segnalazione dello stato, è necessario creare un blocco **ReportRepositoryWeb**.</span><span class="sxs-lookup"><span data-stu-id="7f403-153">To configure a client to report status, you have to create a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="7f403-154">Nell'esempio seguente viene illustrata una metaconfigurazione che configura un client per il pull di configurazioni e risorse e per l'invio di dati di report a un singolo server di pull.</span><span class="sxs-lookup"><span data-stu-id="7f403-154">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="7f403-155">Un server di report non può fungere da condivisione SMB.</span><span class="sxs-lookup"><span data-stu-id="7f403-155">A report server cannot be an SMB share.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="7f403-156">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7f403-156">See Also</span></span>

* [<span data-ttu-id="7f403-157">Configurazione di un client di pull usando un ID configurazione</span><span class="sxs-lookup"><span data-stu-id="7f403-157">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="7f403-158">Configurazione di un server di pull Web DSC</span><span class="sxs-lookup"><span data-stu-id="7f403-158">Setting up a DSC web pull server</span></span>](pullServer.md)
