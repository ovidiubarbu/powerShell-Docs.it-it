---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Configurazione di un client di pull usando un ID configurazione
ms.openlocfilehash: 6e3dda1de0bfbf52fb876fdcd2dd2e99da4583dd
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id"></a><span data-ttu-id="1069b-103">Configurazione di un client di pull usando un ID configurazione</span><span class="sxs-lookup"><span data-stu-id="1069b-103">Setting up a pull client using configuration ID</span></span>

> <span data-ttu-id="1069b-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1069b-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="1069b-105">Per ogni nodo di destinazione è necessario specificare che venga usata la modalità pull e fornire l'URL per contattare il server di pull da cui ottenere le configurazioni.</span><span class="sxs-lookup"><span data-stu-id="1069b-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="1069b-106">A tale scopo, è necessario configurare Gestione configurazione locale con le informazioni richieste.</span><span class="sxs-lookup"><span data-stu-id="1069b-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="1069b-107">Per configurare Gestione configurazione locale, è necessario creare un tipo speciale di configurazione usando l'attributo **DSCLocalConfigurationManager**.</span><span class="sxs-lookup"><span data-stu-id="1069b-107">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="1069b-108">Per altre informazioni sulla configurazione di Gestione configurazione locale, vedere [Configurazione di Gestione configurazione locale](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="1069b-108">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="1069b-109">**Nota**: questo argomento si applica a PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="1069b-109">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="1069b-110">Per informazioni sulla configurazione di un client di pull in PowerShell 4.0, vedere [Configurazione di un client di pull usando un ID configurazione in PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="1069b-110">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="1069b-111">Lo script seguente configura Gestione configurazione locale per il pull delle configurazioni da un server denominato "CONTOSO-PullSrv".</span><span class="sxs-lookup"><span data-stu-id="1069b-111">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="1069b-112">Nello script il blocco **ConfigurationRepositoryWeb** definisce il server di pull.</span><span class="sxs-lookup"><span data-stu-id="1069b-112">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="1069b-113">**ServerURL** rappresenta l'URL del server.</span><span class="sxs-lookup"><span data-stu-id="1069b-113">The **ServerURL**</span></span>

<span data-ttu-id="1069b-114">Dopo essere stato eseguito, questo script crea una nuova cartella di output denominata **PullClientConfigID** e inserisce in questa cartella un file MOF di metaconfigurazione.</span><span class="sxs-lookup"><span data-stu-id="1069b-114">After this script runs, it creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="1069b-115">In questo caso, il file MOF di metaconfigurazione sarà denominato `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="1069b-115">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="1069b-116">Per applicare la configurazione, chiamare il cmdlet **Set-DscLocalConfigurationManager**, con il valore di **Path** impostato sul percorso del file MOF di metaconfigurazione.</span><span class="sxs-lookup"><span data-stu-id="1069b-116">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="1069b-117">Ad esempio: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span><span class="sxs-lookup"><span data-stu-id="1069b-117">For example: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span></span>

## <a name="configuration-id"></a><span data-ttu-id="1069b-118">ID configurazione</span><span class="sxs-lookup"><span data-stu-id="1069b-118">Configuration ID</span></span>

<span data-ttu-id="1069b-119">Lo script imposta la proprietà **ConfigurationID** di Gestione configurazione locale su un GUID creato in precedenza per questo scopo (è possibile creare un GUID usando il cmdlet **New-Guid**).</span><span class="sxs-lookup"><span data-stu-id="1069b-119">The script sets the **ConfigurationID** property of LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="1069b-120">Il valore di **ConfigurationID** viene usato da Gestione configurazione locale per trovare la configurazione appropriata nel server di pull.</span><span class="sxs-lookup"><span data-stu-id="1069b-120">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="1069b-121">Il file MOF di configurazione nel server di pull deve essere denominato _ConfigurationID.mof_, dove _ConfigurationID_ è il valore della proprietà **ConfigurationID** di Gestione configurazione locale del nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="1069b-121">The configuration MOF file on the pull server must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="smb-pull-server"></a><span data-ttu-id="1069b-122">Server di pull SMB</span><span class="sxs-lookup"><span data-stu-id="1069b-122">SMB pull server</span></span>

<span data-ttu-id="1069b-123">Per configurare un client per il pull delle configurazioni da un server SMB, usare un blocco **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="1069b-123">To set up a client to pull configurations from an SMB server, use a **ConfigurationRepositoryShare** block.</span></span> <span data-ttu-id="1069b-124">In un blocco **ConfigurationRepositoryShare** specificare il percorso del server impostando la proprietà **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="1069b-124">In a **ConfigurationRepositoryShare** block, you specify the path to the server by setting the **SourcePath** property.</span></span> <span data-ttu-id="1069b-125">La metaconfigurazione seguente consente di configurare il nodo di destinazione per il pull da un server di pull SMB denominato **SMBPullServer**.</span><span class="sxs-lookup"><span data-stu-id="1069b-125">The following metaconfiguration configures the target node to pull from an SMB pull server named **SMBPullServer**.</span></span>

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
            SourcePath = '\\SMBPullServer\PullSource'
            
        }     
    }
}
PullClientConfigID
```

## <a name="resource-and-report-servers"></a><span data-ttu-id="1069b-126">Server delle risorse e di report</span><span class="sxs-lookup"><span data-stu-id="1069b-126">Resource and report servers</span></span>

<span data-ttu-id="1069b-127">Se si specifica solo un blocco **ConfigurationRepositoryWeb** o **ConfigurationRepositoryShare** nella configurazione di Gestione configurazione locale, come nell'esempio precedente, il client di pull eseguirà il pull delle risorse dal server specificato, ma non invierà report al server.</span><span class="sxs-lookup"><span data-stu-id="1069b-127">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span> <span data-ttu-id="1069b-128">È possibile usare un singolo server di pull per le configurazioni, le risorse e i report, ma è necessario creare un blocco **ReportRepositoryWeb** per configurare la creazione di report.</span><span class="sxs-lookup"><span data-stu-id="1069b-128">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span> 

<span data-ttu-id="1069b-129">Nell'esempio seguente viene illustrata una metaconfigurazione che configura un client per il pull di configurazioni e risorse e per l'invio di dati di report a un singolo server di pull.</span><span class="sxs-lookup"><span data-stu-id="1069b-129">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="1069b-130">È anche possibile specificare server di pull diversi per le risorse e i report.</span><span class="sxs-lookup"><span data-stu-id="1069b-130">You can also specify different pull servers for resources and reporting.</span></span> <span data-ttu-id="1069b-131">Per specificare un server delle risorse, usare un blocco **ResourceRepositoryWeb** (per un server di pull Web) o **ResourceRepositoryShare** (per un server di pull SMB).</span><span class="sxs-lookup"><span data-stu-id="1069b-131">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="1069b-132">Per specificare un server di report, usare un blocco **ReportRepositoryWeb**.</span><span class="sxs-lookup"><span data-stu-id="1069b-132">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="1069b-133">Un server di report non può essere un server SMB.</span><span class="sxs-lookup"><span data-stu-id="1069b-133">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="1069b-134">La metaconfigurazione seguente configura un client di pull in modo da ottenere le configurazioni da **CONTOSO-PullSrv** e le risorse da **CONTOSO-ResourceSrv** e inviare i report sullo stato a **CONTOSO-ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="1069b-134">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1069b-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1069b-135">See Also</span></span>

* [<span data-ttu-id="1069b-136">Configurazione di un client di pull con nomi di configurazione</span><span class="sxs-lookup"><span data-stu-id="1069b-136">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)

