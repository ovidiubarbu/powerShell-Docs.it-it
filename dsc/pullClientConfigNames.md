---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Configurazione di un client di pull usando nomi di configurazione
ms.openlocfilehash: 11de53fc349ce0ebacf0d4855d82fa8a22d55c99
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="setting-up-a-pull-client-using-configuration-names"></a><span data-ttu-id="82478-103">Configurazione di un client di pull usando nomi di configurazione</span><span class="sxs-lookup"><span data-stu-id="82478-103">Setting up a pull client using configuration names</span></span>

> <span data-ttu-id="82478-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="82478-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="82478-105">Per ogni nodo di destinazione è necessario specificare che venga usata la modalità pull e fornire l'URL per contattare il server di pull da cui ottenere le configurazioni.</span><span class="sxs-lookup"><span data-stu-id="82478-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span>
<span data-ttu-id="82478-106">A tale scopo, è necessario configurare Gestione configurazione locale con le informazioni richieste.</span><span class="sxs-lookup"><span data-stu-id="82478-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span>
<span data-ttu-id="82478-107">Per configurare Gestione configurazione locale, è necessario creare un tipo speciale di configurazione usando l'attributo **DSCLocalConfigurationManager**.</span><span class="sxs-lookup"><span data-stu-id="82478-107">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span>
<span data-ttu-id="82478-108">Per altre informazioni sulla configurazione di Gestione configurazione locale, vedere [Configurazione di Gestione configurazione locale](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="82478-108">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="82478-109">**Nota**: questo argomento si applica a PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="82478-109">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="82478-110">Per informazioni sulla configurazione di un client di pull in PowerShell 4.0, vedere [Configurazione di un client di pull usando un ID configurazione in PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="82478-110">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="82478-111">Lo script seguente configura Gestione configurazione locale per il pull delle configurazioni da un server denominato "CONTOSO-PullSrv":</span><span class="sxs-lookup"><span data-stu-id="82478-111">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv":</span></span>

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

<span data-ttu-id="82478-112">Nello script il blocco **ConfigurationRepositoryWeb** definisce il server di pull.</span><span class="sxs-lookup"><span data-stu-id="82478-112">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span>
<span data-ttu-id="82478-113">La proprietà **ServerURL** specifica l'endpoint per il server di pull.</span><span class="sxs-lookup"><span data-stu-id="82478-113">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

<span data-ttu-id="82478-114">La proprietà **RegistrationKey** è una chiave condivisa tra tutti i nodi client per un server di pull e il server di pull stesso.</span><span class="sxs-lookup"><span data-stu-id="82478-114">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span>
<span data-ttu-id="82478-115">Lo stesso valore viene archiviato in un file nel server di pull.</span><span class="sxs-lookup"><span data-stu-id="82478-115">The same value is stored in a file on the pull server.</span></span>

<span data-ttu-id="82478-116">La proprietà **ConfigurationNames** è una matrice che specifica i nomi delle configurazioni per il nodo client.</span><span class="sxs-lookup"><span data-stu-id="82478-116">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
<span data-ttu-id="82478-117">Nel server di pull il file MOF di configurazione per il nodo client deve essere denominato *ConfigurationNames*.mof, dove *ConfigurationNames* corrisponde al valore della proprietà **ConfigurationNames** impostata in questa metaconfigurazione.</span><span class="sxs-lookup"><span data-stu-id="82478-117">On the pull server, the configuration MOF file for this client node must be named *ConfigurationNames*.mof, where *ConfigurationNames* matches the value of the **ConfigurationNames** property you set in this metaconfiguration.</span></span>

><span data-ttu-id="82478-118">**Nota:** se si specifica più di un valore in **ConfigurationNames**, è necessario specificare nella configurazione anche i blocchi di **PartialConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="82478-118">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
<span data-ttu-id="82478-119">Per informazioni sulle configurazioni parziali, vedere [configurazioni parziali di PowerShell DSC](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="82478-119">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

<span data-ttu-id="82478-120">Dopo essere stato eseguito, questo script crea una nuova cartella di output denominata **PullClientConfigNames** e inserisce in questa cartella un file MOF di metaconfigurazione.</span><span class="sxs-lookup"><span data-stu-id="82478-120">After this script runs, it creates a new output folder named **PullClientConfigNames** and puts a metaconfiguration MOF file there.</span></span>
<span data-ttu-id="82478-121">In questo caso, il file MOF di metaconfigurazione sarà denominato `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="82478-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="82478-122">Per applicare la configurazione, chiamare il cmdlet **Set-DscLocalConfigurationManager**, con il valore di **Path** impostato sul percorso del file MOF di metaconfigurazione.</span><span class="sxs-lookup"><span data-stu-id="82478-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span>

```powershell
Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigNames –Verbose.
```

> <span data-ttu-id="82478-123">**Nota**: le chiavi di registrazione funzionano solo con i server di pull Web.</span><span class="sxs-lookup"><span data-stu-id="82478-123">**Note**: Registration keys work only with web pull servers.</span></span>
<span data-ttu-id="82478-124">Con un server di pull SMB è necessario usare **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="82478-124">You must still use **ConfigurationID** with an SMB pull server.</span></span>
<span data-ttu-id="82478-125">Per informazioni sulla configurazione di un server di pull usando **ConfigurationID**, vedere [Configurazione di un client di pull usando un ID configurazione](PullClientConfigNames.md).</span><span class="sxs-lookup"><span data-stu-id="82478-125">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](PullClientConfigNames.md)</span></span>

## <a name="resource-and-report-servers"></a><span data-ttu-id="82478-126">Server delle risorse e di report</span><span class="sxs-lookup"><span data-stu-id="82478-126">Resource and report servers</span></span>

<span data-ttu-id="82478-127">Se si specifica solo un blocco **ConfigurationRepositoryWeb** o **ConfigurationRepositoryShare** nella configurazione di Gestione configurazione locale, come nell'esempio precedente, il client di pull eseguirà il pull delle risorse dal server specificato, ma non invierà report al server.</span><span class="sxs-lookup"><span data-stu-id="82478-127">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span>
<span data-ttu-id="82478-128">È possibile usare un singolo server di pull per le configurazioni, le risorse e i report, ma è necessario creare un blocco **ReportRepositoryWeb** per configurare la creazione di report.</span><span class="sxs-lookup"><span data-stu-id="82478-128">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>
<span data-ttu-id="82478-129">Nell'esempio seguente viene illustrata una metaconfigurazione che configura un client per il pull di configurazioni e risorse e per l'invio di dati di report a un singolo server di pull.</span><span class="sxs-lookup"><span data-stu-id="82478-129">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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
        }
    }
}
PullClientConfigNames
```

<span data-ttu-id="82478-130">È anche possibile specificare server di pull diversi per le risorse e i report.</span><span class="sxs-lookup"><span data-stu-id="82478-130">You can also specify different pull servers for resources and reporting.</span></span>
<span data-ttu-id="82478-131">Per specificare un server delle risorse, usare un blocco **ResourceRepositoryWeb** (per un server di pull Web) o **ResourceRepositoryShare** (per un server di pull SMB).</span><span class="sxs-lookup"><span data-stu-id="82478-131">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="82478-132">Per specificare un server di report, usare un blocco **ReportRepositoryWeb**.</span><span class="sxs-lookup"><span data-stu-id="82478-132">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span>
<span data-ttu-id="82478-133">Un server di report non può essere un server SMB.</span><span class="sxs-lookup"><span data-stu-id="82478-133">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="82478-134">La metaconfigurazione seguente configura un client di pull in modo da ottenere le configurazioni da **CONTOSO-PullSrv** e le risorse da **CONTOSO-ResourceSrv** e inviare i report sullo stato a **CONTOSO-ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="82478-134">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-ResourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-ReportSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '6b392c6a-818c-4b24-bf38-47124f1e2f14'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="82478-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="82478-135">See Also</span></span>

* [<span data-ttu-id="82478-136">Configurazione di un client di pull usando un ID configurazione</span><span class="sxs-lookup"><span data-stu-id="82478-136">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="82478-137">Configurazione di un server di pull Web DSC</span><span class="sxs-lookup"><span data-stu-id="82478-137">Setting up a DSC web pull server</span></span>](pullServer.md)

