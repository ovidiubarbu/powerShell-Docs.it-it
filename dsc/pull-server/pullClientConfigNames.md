---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Configurare un Client di Pull usando nomi di configurazione in PowerShell 5.0 e versioni successive
ms.openlocfilehash: fd038a105da7a83ecad9b571e611b65c8ec847b3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401788"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a><span data-ttu-id="3a35b-103">Configurare un Client di Pull usando nomi di configurazione in PowerShell 5.0 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="3a35b-103">Set up a Pull Client using Configuration Names in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="3a35b-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3a35b-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3a35b-105">Il server di pull (funzionalità di Windows *servizio DSC*) è un componente supportato di Windows Server, tuttavia non si prevede di offrire nuove caratteristiche o funzionalità.</span><span class="sxs-lookup"><span data-stu-id="3a35b-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="3a35b-106">È consigliabile avviare la transizione dei client gestiti ad [Automation DSC per Azure](/azure/automation/automation-dsc-getting-started) (include funzionalità superiori al server di pull in Windows Server) o a una delle soluzioni della community riportate [qui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="3a35b-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="3a35b-107">Prima di configurare un client di pull, è necessario configurare un server di pull.</span><span class="sxs-lookup"><span data-stu-id="3a35b-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="3a35b-108">Anche se quest'ordine non sia obbligatorio, consente la risoluzione dei problemi e consente di assicurarsi che la registrazione è riuscita.</span><span class="sxs-lookup"><span data-stu-id="3a35b-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="3a35b-109">Per configurare un server di pull, è possibile usare le guide seguenti:</span><span class="sxs-lookup"><span data-stu-id="3a35b-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="3a35b-110">Configurare un server di pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="3a35b-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="3a35b-111">Configurare un server di pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="3a35b-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="3a35b-112">Ogni nodo di destinazione può essere configurato per scaricare le configurazioni, risorse e anche segnalare lo stato.</span><span class="sxs-lookup"><span data-stu-id="3a35b-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="3a35b-113">Le sezioni seguenti illustrano come configurare un client di pull con una condivisione SMB o HTTP Server di Pull DSC.</span><span class="sxs-lookup"><span data-stu-id="3a35b-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="3a35b-114">Quando Gestione configurazione locale del nodo viene aggiornato, ti contatterà per il percorso configurato per scaricare eventuali configurazioni assegnate.</span><span class="sxs-lookup"><span data-stu-id="3a35b-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="3a35b-115">Se tutte le risorse necessarie non sono presenti nel nodo, verrà automaticamente scaricato li dal percorso configurato.</span><span class="sxs-lookup"><span data-stu-id="3a35b-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="3a35b-116">Se il nodo è configurato con un [Server di Report](reportServer.md), quindi segnala lo stato dell'operazione.</span><span class="sxs-lookup"><span data-stu-id="3a35b-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> <span data-ttu-id="3a35b-117">**Nota**: Questo argomento si applica a PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="3a35b-117">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="3a35b-118">Per informazioni sulla configurazione di un client di pull in PowerShell 4.0, vedere [configurare un client di pull usando un ID configurazione in PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="3a35b-118">For information on setting up a pull client in PowerShell 4.0, see [Set up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="3a35b-119">Configurare il client di pull Gestione configurazione locale</span><span class="sxs-lookup"><span data-stu-id="3a35b-119">Configure the pull client LCM</span></span>

<span data-ttu-id="3a35b-120">L'esecuzione di uno degli esempi seguenti viene creata una nuova cartella di output denominata **PullClientConfigName** e inserisce un file MOF di metaconfigurazione esiste.</span><span class="sxs-lookup"><span data-stu-id="3a35b-120">Executing any of the examples below creates a new output folder named **PullClientConfigName** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="3a35b-121">In questo caso, il file MOF di metaconfigurazione sarà denominato `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="3a35b-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="3a35b-122">Per applicare la configurazione, chiamare il cmdlet **Set-DscLocalConfigurationManager**, con il valore di **Path** impostato sul percorso del file MOF di metaconfigurazione.</span><span class="sxs-lookup"><span data-stu-id="3a35b-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="3a35b-123">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="3a35b-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a><span data-ttu-id="3a35b-124">Nome della configurazione</span><span class="sxs-lookup"><span data-stu-id="3a35b-124">Configuration Name</span></span>

<span data-ttu-id="3a35b-125">Gli esempi seguenti set di **ConfigurationName** proprietà di Gestione configurazione locale per il nome di una configurazione compilata in precedenza, creato per questo scopo.</span><span class="sxs-lookup"><span data-stu-id="3a35b-125">The examples below sets the **ConfigurationName** property of the LCM to the name of a previously compiled Configuration, created for this purpose.</span></span> <span data-ttu-id="3a35b-126">Il **ConfigurationName** viene usato Gestione configurazione locale per trovare la configurazione appropriata nel server di pull.</span><span class="sxs-lookup"><span data-stu-id="3a35b-126">The **ConfigurationName** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="3a35b-127">Il file MOF di configurazione nel server di pull deve essere denominato `<ConfigurationName>.mof`, in questo caso, "ClientConfig.mof".</span><span class="sxs-lookup"><span data-stu-id="3a35b-127">The configuration MOF file on the pull server must be named `<ConfigurationName>.mof`, in this case, "ClientConfig.mof".</span></span> <span data-ttu-id="3a35b-128">Per altre informazioni, vedere [pubblicare le configurazioni a un Server di Pull (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="3a35b-128">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="3a35b-129">Configurare un Client di Pull per scaricare le configurazioni</span><span class="sxs-lookup"><span data-stu-id="3a35b-129">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="3a35b-130">Ogni client deve essere configurato **Pull** modalità e fornire l'url di server di pull in cui la configurazione viene archiviata.</span><span class="sxs-lookup"><span data-stu-id="3a35b-130">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="3a35b-131">A tale scopo, è necessario configurare Gestione configurazione locale con le informazioni richieste.</span><span class="sxs-lookup"><span data-stu-id="3a35b-131">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="3a35b-132">Per configurare Gestione configurazione locale, è necessario creare un tipo speciale di configurazione usando l'attributo **DSCLocalConfigurationManager**.</span><span class="sxs-lookup"><span data-stu-id="3a35b-132">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="3a35b-133">Per altre informazioni sulla configurazione di Gestione configurazione locale, vedere [Configurazione di Gestione configurazione locale](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="3a35b-133">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="3a35b-134">Lo script seguente configura Gestione configurazione locale per il pull delle configurazioni da un server denominato "CONTOSO-PullSrv".</span><span class="sxs-lookup"><span data-stu-id="3a35b-134">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

- <span data-ttu-id="3a35b-135">Nello script il blocco **ConfigurationRepositoryWeb** definisce il server di pull.</span><span class="sxs-lookup"><span data-stu-id="3a35b-135">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="3a35b-136">La proprietà **ServerURL** specifica l'endpoint per il server di pull.</span><span class="sxs-lookup"><span data-stu-id="3a35b-136">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

- <span data-ttu-id="3a35b-137">La proprietà **RegistrationKey** è una chiave condivisa tra tutti i nodi client per un server di pull e il server di pull stesso.</span><span class="sxs-lookup"><span data-stu-id="3a35b-137">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span> <span data-ttu-id="3a35b-138">Lo stesso valore viene archiviato in un file nel server di pull.</span><span class="sxs-lookup"><span data-stu-id="3a35b-138">The same value is stored in a file on the pull server.</span></span>
  > <span data-ttu-id="3a35b-139">**Nota**: Le chiavi di registrazione funzionano solo con **web** i server di pull.</span><span class="sxs-lookup"><span data-stu-id="3a35b-139">**Note**: Registration keys work only with **web** pull servers.</span></span> <span data-ttu-id="3a35b-140">Con un server di pull **SMB** è necessario usare **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="3a35b-140">You must still use **ConfigurationID** with an **SMB** pull server.</span></span>
  > <span data-ttu-id="3a35b-141">Per informazioni sulla configurazione di un server di pull usando **ConfigurationID**, vedere [Configurazione di un client di pull usando un ID configurazione](pullClientConfigId.md).</span><span class="sxs-lookup"><span data-stu-id="3a35b-141">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigId.md)</span></span>

- <span data-ttu-id="3a35b-142">La proprietà **ConfigurationNames** è una matrice che specifica i nomi delle configurazioni per il nodo client.</span><span class="sxs-lookup"><span data-stu-id="3a35b-142">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
  ><span data-ttu-id="3a35b-143">**Nota:** se si specifica più di un valore in **ConfigurationNames**, è necessario specificare anche i blocchi **PartialConfiguration** nella configurazione.</span><span class="sxs-lookup"><span data-stu-id="3a35b-143">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
  ><span data-ttu-id="3a35b-144">Per informazioni sulle configurazioni parziali, vedere [configurazioni parziali di PowerShell DSC](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="3a35b-144">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

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

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="3a35b-145">Configurare un Client di Pull per scaricare le risorse</span><span class="sxs-lookup"><span data-stu-id="3a35b-145">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="3a35b-146">Se si specifica solo un **ConfigurationRepositoryWeb** oppure **ConfigurationRepositoryShare** nella configurazione di Gestione configurazione locale (come nell'esempio precedente), il client di pull effettuerà il pull delle risorse da parte dello stesso posizione in cui sono archiviati i file "MOF".</span><span class="sxs-lookup"><span data-stu-id="3a35b-146">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from same location where your ".mof" files are stored.</span></span> <span data-ttu-id="3a35b-147">È anche possibile specificare percorsi diversi in cui i client possono scaricare le risorse.</span><span class="sxs-lookup"><span data-stu-id="3a35b-147">You can also specify different locations where clients can download resources.</span></span> <span data-ttu-id="3a35b-148">Per specificare un server delle risorse, usare un blocco **ResourceRepositoryWeb** (per un server di pull Web) o **ResourceRepositoryShare** (per un server di pull SMB).</span><span class="sxs-lookup"><span data-stu-id="3a35b-148">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>

<span data-ttu-id="3a35b-149">Nell'esempio seguente viene illustrata una metaconfigurazione che configura un client di scaricare le configurazioni da un Server di Pull e le risorse da una condivisione SMB.</span><span class="sxs-lookup"><span data-stu-id="3a35b-149">The following example shows a metaconfiguration that sets up a client to download configurations from a Pull Server, and resources from an SMB share.</span></span>

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

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="3a35b-150">Configurare un Client di Pull per segnalare lo stato</span><span class="sxs-lookup"><span data-stu-id="3a35b-150">Set up a Pull Client to report status</span></span>

<span data-ttu-id="3a35b-151">È possibile usare un singolo server di pull per le configurazioni, risorse e i report.</span><span class="sxs-lookup"><span data-stu-id="3a35b-151">You can use a single pull server for configurations, resources, and reporting.</span></span> <span data-ttu-id="3a35b-152">Creazione di report non è configurato per i client per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="3a35b-152">Reporting is not configured for clients by default.</span></span> <span data-ttu-id="3a35b-153">Per configurare un client per segnalare lo stato, è necessario creare un **ReportRepositoryWeb** blocco.</span><span class="sxs-lookup"><span data-stu-id="3a35b-153">To configure a client to report status, you have to create a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="3a35b-154">Nell'esempio seguente viene illustrata una metaconfigurazione che configura un client per il pull di configurazioni e risorse e per l'invio di dati di report a un singolo server di pull.</span><span class="sxs-lookup"><span data-stu-id="3a35b-154">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="3a35b-155">Un server di report non può essere una condivisione SMB.</span><span class="sxs-lookup"><span data-stu-id="3a35b-155">A report server cannot be an SMB share.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3a35b-156">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3a35b-156">See Also</span></span>

* [<span data-ttu-id="3a35b-157">Configurazione di un client di pull usando un ID configurazione</span><span class="sxs-lookup"><span data-stu-id="3a35b-157">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="3a35b-158">Configurazione di un server di pull Web DSC</span><span class="sxs-lookup"><span data-stu-id="3a35b-158">Setting up a DSC web pull server</span></span>](pullServer.md)
