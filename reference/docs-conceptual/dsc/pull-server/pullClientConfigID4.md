---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Configurare un client di pull usando ID configurazione in PowerShell 4.0
ms.openlocfilehash: 9259c624c8725f7d76f61e9ad7caa42e1bfa308c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71955148"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a><span data-ttu-id="714a5-103">Configurare un client di pull usando ID configurazione in PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="714a5-103">Set up a Pull Client using Configuration IDs in PowerShell 4.0</span></span>

><span data-ttu-id="714a5-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="714a5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="714a5-105">Il server di pull (funzionalità di Windows *servizio DSC*) è un componente supportato di Windows Server, tuttavia non si prevede di offrire nuove caratteristiche o funzionalità.</span><span class="sxs-lookup"><span data-stu-id="714a5-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="714a5-106">È consigliabile avviare la transizione dei client gestiti ad [Automation DSC per Azure](/azure/automation/automation-dsc-getting-started) (include funzionalità superiori al server di pull in Windows Server) o a una delle soluzioni della community riportate [qui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="714a5-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="714a5-107">Prima di configurare un client di pull, è necessario configurare un server di pull.</span><span class="sxs-lookup"><span data-stu-id="714a5-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="714a5-108">Anche se quest'ordine non è obbligatorio, facilita la risoluzione dei problemi e agevola la riuscita della registrazione.</span><span class="sxs-lookup"><span data-stu-id="714a5-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="714a5-109">Per configurare un server di pull, è possibile usare le guide seguenti:</span><span class="sxs-lookup"><span data-stu-id="714a5-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="714a5-110">Configurare un server di pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="714a5-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="714a5-111">Configurare un server di pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="714a5-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="714a5-112">Ogni nodo di destinazione può essere configurato in modo che possa scaricare configurazioni e risorse e persino segnalare il proprio stato.</span><span class="sxs-lookup"><span data-stu-id="714a5-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="714a5-113">Le sezioni seguenti illustrano come configurare un client di pull con una condivisione SMB o on server di pull DSC HTTP.</span><span class="sxs-lookup"><span data-stu-id="714a5-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="714a5-114">Quando Gestione configurazione locale del nodo si aggiorna, contatta la posizione configurata per scaricare tutte le configurazioni assegnate.</span><span class="sxs-lookup"><span data-stu-id="714a5-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="714a5-115">Se una o più risorse necessarie non sono presenti nel nodo, le scarica automaticamente dalla posizione configurata.</span><span class="sxs-lookup"><span data-stu-id="714a5-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="714a5-116">Se il nodo è configurato con un [server di report](reportServer.md), segnala quindi lo stato dell'operazione.</span><span class="sxs-lookup"><span data-stu-id="714a5-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="714a5-117">Configurare Gestione configurazione locale del client di pull</span><span class="sxs-lookup"><span data-stu-id="714a5-117">Configure the pull client LCM</span></span>

<span data-ttu-id="714a5-118">L'esecuzione di uno degli esempi che seguono crea una nuova cartella di output denominata **PullClientConfigID** e inserisce in questa cartella un file MOF di metaconfigurazione.</span><span class="sxs-lookup"><span data-stu-id="714a5-118">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="714a5-119">In questo caso, il file MOF di metaconfigurazione sarà denominato `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="714a5-119">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="714a5-120">Per applicare la configurazione, chiamare il cmdlet **Set-DscLocalConfigurationManager**, con il valore di **Path** impostato sul percorso del file MOF di metaconfigurazione.</span><span class="sxs-lookup"><span data-stu-id="714a5-120">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="714a5-121">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="714a5-121">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="714a5-122">ID configurazione</span><span class="sxs-lookup"><span data-stu-id="714a5-122">Configuration ID</span></span>

<span data-ttu-id="714a5-123">Gli esempi che seguono impostano la proprietà **ConfigurationID** di Gestione configurazione locale su un **GUID** creato in precedenza per questo scopo.</span><span class="sxs-lookup"><span data-stu-id="714a5-123">The examples below set the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="714a5-124">Il valore di **ConfigurationID** viene usato da Gestione configurazione locale per trovare la configurazione appropriata nel server di pull.</span><span class="sxs-lookup"><span data-stu-id="714a5-124">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="714a5-125">Il file MOF di configurazione nel server di pull deve essere denominato `ConfigurationID.mof`, dove *ConfigurationID* è il valore della proprietà **ConfigurationID** di Gestione configurazione locale del nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="714a5-125">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="714a5-126">Per altre informazioni, vedere [Pubblicare le configurazioni in un server di pull (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="714a5-126">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="714a5-127">È possibile creare un **GUID** casuale usando l'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="714a5-127">You can create a random **Guid** using the example below.</span></span>

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="714a5-128">Configurare un client di pull per scaricare configurazioni</span><span class="sxs-lookup"><span data-stu-id="714a5-128">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="714a5-129">Ogni client deve essere configurato in modalità **Pull** e deve ricevere l'URL del server di pull in cui è archiviata la sua configurazione.</span><span class="sxs-lookup"><span data-stu-id="714a5-129">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="714a5-130">A tale scopo, è necessario configurare Gestione configurazione locale con le informazioni richieste.</span><span class="sxs-lookup"><span data-stu-id="714a5-130">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="714a5-131">Per configurare Gestione configurazione locale, è necessario creare un tipo speciale di configurazione con il blocco **LocalConfigurationManager**.</span><span class="sxs-lookup"><span data-stu-id="714a5-131">To configure the LCM, you create a special type of configuration, with a **LocalConfigurationManager** block.</span></span> <span data-ttu-id="714a5-132">Per altre informazioni sulla configurazione di Gestione configurazione locale, vedere [Configurazione di Gestione configurazione locale](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="714a5-132">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig4.md).</span></span>

## <a name="http-dsc-pull-server"></a><span data-ttu-id="714a5-133">Server di pull DSC HTTP</span><span class="sxs-lookup"><span data-stu-id="714a5-133">HTTP DSC Pull Server</span></span>

<span data-ttu-id="714a5-134">Se il server di pull è configurato come servizio Web, impostare **DownloadManagerName** su **WebDownloadManager**.</span><span class="sxs-lookup"><span data-stu-id="714a5-134">If the pull server is set up as a web service, you set the **DownloadManagerName** to **WebDownloadManager**.</span></span> <span data-ttu-id="714a5-135">**WebDownloadManager** richiede la specifica di un **ServerUrl** per la chiave **DownloadManagerCustomData**.</span><span class="sxs-lookup"><span data-stu-id="714a5-135">The **WebDownloadManager** requires that you specify a **ServerUrl** to the **DownloadManagerCustomData** key.</span></span> <span data-ttu-id="714a5-136">È anche possibile specificare un valore per **AllowUnsecureConnection**, come nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="714a5-136">You can also specify a value for **AllowUnsecureConnection**, as in the example below.</span></span> <span data-ttu-id="714a5-137">Lo script seguente configura Gestione configurazione locale per il pull delle configurazioni da un server denominato "PullServer".</span><span class="sxs-lookup"><span data-stu-id="714a5-137">The following script configures the LCM to pull configurations from a server named "PullServer".</span></span>

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = "TRUE"}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a><span data-ttu-id="714a5-138">Condivisione SMB</span><span class="sxs-lookup"><span data-stu-id="714a5-138">SMB Share</span></span>

<span data-ttu-id="714a5-139">Se il server di pull viene configurato come condivisione file SMB, piuttosto che come servizio Web, impostare **DownloadManagerName** su **DscFileDownloadManager** anziché su **WebDownLoadManager**.</span><span class="sxs-lookup"><span data-stu-id="714a5-139">If the pull server is set up as an SMB file share, rather than a web service, you set the **DownloadManagerName** to **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span> <span data-ttu-id="714a5-140">**DscFileDownloadManager** richiede la specifica della proprietà **SourcePath** in **DownloadManagerCustomData**.</span><span class="sxs-lookup"><span data-stu-id="714a5-140">The **DscFileDownloadManager** requires that you specify a **SourcePath** property in the **DownloadManagerCustomData**.</span></span> <span data-ttu-id="714a5-141">Lo script seguente configura Gestione configurazione locale per il pull da una condivisione SMB denominata "SmbDscShare" su un server chiamato "CONTOSO-SERVER".</span><span class="sxs-lookup"><span data-stu-id="714a5-141">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER".</span></span>

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
PullClientConfigId -Output "."
```

## <a name="next-steps"></a><span data-ttu-id="714a5-142">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="714a5-142">Next Steps</span></span>

<span data-ttu-id="714a5-143">Dopo la configurazione del client di pull, per eseguire i passaggi successivi è possibile usare le guide seguenti:</span><span class="sxs-lookup"><span data-stu-id="714a5-143">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="714a5-144">Pubblicare le configurazioni in un server di pull (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="714a5-144">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="714a5-145">Creare un pacchetto e caricare le risorse in un server di pull (v4)</span><span class="sxs-lookup"><span data-stu-id="714a5-145">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="714a5-146">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="714a5-146">See Also</span></span>

- [<span data-ttu-id="714a5-147">Configurare un server di pull Web DSC</span><span class="sxs-lookup"><span data-stu-id="714a5-147">Set up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="714a5-148">Configurare un server di pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="714a5-148">Set up a DSC SMB pull server</span></span>](pullServerSMB.md)
