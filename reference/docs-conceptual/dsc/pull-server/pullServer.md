---
ms.date: 01/08/2020
keywords: dsc,powershell,configurazione,installazione
title: Servizio di pull DSC
ms.openlocfilehash: cf2420e6889f63ac3b2859e5ee36fa888b728afc
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402438"
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="4fbad-103">Servizio di pull DSC (Desired State Configuration)</span><span class="sxs-lookup"><span data-stu-id="4fbad-103">Desired State Configuration Pull Service</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4fbad-104">Il server di pull (funzionalità di Windows *servizio DSC*) è un componente supportato di Windows Server, tuttavia non si prevede di offrire nuove caratteristiche o funzionalità.</span><span class="sxs-lookup"><span data-stu-id="4fbad-104">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="4fbad-105">È consigliabile avviare la transizione dei client gestiti ad [Automation DSC per Azure](/azure/automation/automation-dsc-getting-started) (include funzionalità superiori al server di pull in Windows Server) o a una delle soluzioni della community riportate [qui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="4fbad-105">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="4fbad-106">Gestione configurazione locale può essere gestito a livello centralizzato da una soluzione servizio di pull.</span><span class="sxs-lookup"><span data-stu-id="4fbad-106">Local Configuration Manager (LCM) can be centrally managed by a Pull Service solution.</span></span> <span data-ttu-id="4fbad-107">Con questo approccio, il nodo gestito viene registrato con un servizio e gli viene assegnata una configurazione nelle impostazioni di Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="4fbad-107">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span> <span data-ttu-id="4fbad-108">La configurazione e tutte le risorse DSC necessarie come dipendenze per la configurazione vengono scaricate nel computer e usate da Gestione configurazione locale per gestire la configurazione.</span><span class="sxs-lookup"><span data-stu-id="4fbad-108">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span> <span data-ttu-id="4fbad-109">Nel servizio vengono caricate informazioni sullo stato del computer gestito per la creazione di report.</span><span class="sxs-lookup"><span data-stu-id="4fbad-109">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span> <span data-ttu-id="4fbad-110">Questo concetto è noto come "servizio di pull".</span><span class="sxs-lookup"><span data-stu-id="4fbad-110">This concept is referred to as "pull service".</span></span>

<span data-ttu-id="4fbad-111">Le opzioni correnti per il servizio di pull includono:</span><span class="sxs-lookup"><span data-stu-id="4fbad-111">The current options for pull service include:</span></span>

- <span data-ttu-id="4fbad-112">Servizio DSC (Desired State Configuration) di Automazione di Azure</span><span class="sxs-lookup"><span data-stu-id="4fbad-112">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="4fbad-113">Un servizio di pull in esecuzione in Windows Server</span><span class="sxs-lookup"><span data-stu-id="4fbad-113">A pull service running on Windows Server</span></span>
- <span data-ttu-id="4fbad-114">Soluzioni open source gestite dalla community</span><span class="sxs-lookup"><span data-stu-id="4fbad-114">Community maintained open-source solutions</span></span>
- <span data-ttu-id="4fbad-115">Una condivisione SMB</span><span class="sxs-lookup"><span data-stu-id="4fbad-115">An SMB share</span></span>

<span data-ttu-id="4fbad-116">La scalabilità consigliata per ogni soluzione è la seguente:</span><span class="sxs-lookup"><span data-stu-id="4fbad-116">The recommended scale for each solution is as follows:</span></span>

|                   <span data-ttu-id="4fbad-117">Soluzione</span><span class="sxs-lookup"><span data-stu-id="4fbad-117">Solution</span></span>                   |              <span data-ttu-id="4fbad-118">Nodi client</span><span class="sxs-lookup"><span data-stu-id="4fbad-118">Client nodes</span></span>              |
| -------------------------------------------- | -------------------------------------- |
| <span data-ttu-id="4fbad-119">Server di pull Windows con database MDB/ESENT</span><span class="sxs-lookup"><span data-stu-id="4fbad-119">Windows Pull Server using MDB/ESENT database</span></span> | <span data-ttu-id="4fbad-120">Fino a 500 nodi</span><span class="sxs-lookup"><span data-stu-id="4fbad-120">Up to 500 nodes</span></span>                        |
| <span data-ttu-id="4fbad-121">Server di pull Windows con database SQL</span><span class="sxs-lookup"><span data-stu-id="4fbad-121">Windows Pull Server using SQL database</span></span>       | <span data-ttu-id="4fbad-122">Fino a 3500 nodi</span><span class="sxs-lookup"><span data-stu-id="4fbad-122">Up to 3500 nodes</span></span>                       |
| <span data-ttu-id="4fbad-123">Automation DSC per Azure</span><span class="sxs-lookup"><span data-stu-id="4fbad-123">Azure Automation DSC</span></span>                         | <span data-ttu-id="4fbad-124">Ambienti di piccole e grandi dimensioni</span><span class="sxs-lookup"><span data-stu-id="4fbad-124">Both small and large environments</span></span>      |

<span data-ttu-id="4fbad-125">**La soluzione consigliata**, e l'opzione con il maggior numero di funzionalità disponibili, è [Automation DSC di Azure](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="4fbad-125">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span> <span data-ttu-id="4fbad-126">Non è stato identificato un limite massimo del numero di nodi per l'account di Automazione.</span><span class="sxs-lookup"><span data-stu-id="4fbad-126">An upper limit for number of nodes per Automation Account has not been identified.</span></span>

<span data-ttu-id="4fbad-127">Il servizio di Azure può gestire i nodi in locale nei data center privati o in cloud pubblici, come Azure e AWS.</span><span class="sxs-lookup"><span data-stu-id="4fbad-127">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span> <span data-ttu-id="4fbad-128">Per gli ambienti privati in cui i server non possono connettersi direttamente a Internet, è consigliabile limitare il traffico in uscita esclusivamente all'intervallo di indirizzi IP di Azure pubblicato (vedere gli [intervalli di indirizzi IP dei data center di Azure](https://www.microsoft.com/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="4fbad-128">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="4fbad-129">Le funzionalità del servizio online che non sono attualmente disponibili nel servizio di pull in Windows Server includono:</span><span class="sxs-lookup"><span data-stu-id="4fbad-129">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>

- <span data-ttu-id="4fbad-130">Tutti i dati vengono crittografati in transito e quando inattivi</span><span class="sxs-lookup"><span data-stu-id="4fbad-130">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="4fbad-131">I certificati client vengono creati e gestiti automaticamente</span><span class="sxs-lookup"><span data-stu-id="4fbad-131">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="4fbad-132">Archivio dei segreti per la gestione centralizzata di [password/credenziali](/azure/automation/automation-credentials) o [variabili](/azure/automation/automation-variables) come nomi dei server o stringhe di connessione</span><span class="sxs-lookup"><span data-stu-id="4fbad-132">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="4fbad-133">Gestione centralizzata della [configurazione di Gestione configurazione locale](../managing-nodes/metaConfig.md#basic-settings) del nodo</span><span class="sxs-lookup"><span data-stu-id="4fbad-133">Centrally manage node [LCM configuration](../managing-nodes/metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="4fbad-134">Assegnazione centralizzata delle configurazioni ai nodi client</span><span class="sxs-lookup"><span data-stu-id="4fbad-134">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="4fbad-135">Rilascio delle modifiche di configurazione a "gruppi canary" per i test prima della distribuzione in ambiente di produzione</span><span class="sxs-lookup"><span data-stu-id="4fbad-135">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="4fbad-136">Creazione di report grafici</span><span class="sxs-lookup"><span data-stu-id="4fbad-136">Graphical reporting</span></span>
  - <span data-ttu-id="4fbad-137">Dettagli sullo stato al livello di granularità delle risorse DSC</span><span class="sxs-lookup"><span data-stu-id="4fbad-137">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="4fbad-138">Messaggi di errore dettagliati dai computer client per la risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="4fbad-138">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="4fbad-139">[Integrazione con Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) per gli avvisi, attività automatizzate, app Android o iOS per report e avvisi</span><span class="sxs-lookup"><span data-stu-id="4fbad-139">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="4fbad-140">Servizio di pull DSC in Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="4fbad-140">DSC pull service in Windows Server</span></span>

<span data-ttu-id="4fbad-141">È possibile configurare un servizio di pull per l'esecuzione in Windows Server.</span><span class="sxs-lookup"><span data-stu-id="4fbad-141">It is possible to configure a pull service to run on Windows Server.</span></span> <span data-ttu-id="4fbad-142">Si noti che la soluzione di servizio di pull inclusa in Windows Server contiene solo le funzionalità di archiviazione di configurazioni/moduli per il download e di acquisizione di dati di report in un database.</span><span class="sxs-lookup"><span data-stu-id="4fbad-142">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data into a database.</span></span> <span data-ttu-id="4fbad-143">Non include molte delle funzionalità offerte dal servizio in Azure e pertanto non rappresenta uno strumento ottimale per la valutazione delle modalità d'uso del servizio.</span><span class="sxs-lookup"><span data-stu-id="4fbad-143">It does not include many of the capabilities offered by the service in Azure and so, is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="4fbad-144">Il servizio di pull offerto in Windows Server è un servizio Web in IIS che usa un'interfaccia OData per rendere i file di configurazione DSC disponibili ai nodi di destinazione quando questi li richiedono.</span><span class="sxs-lookup"><span data-stu-id="4fbad-144">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="4fbad-145">Requisiti per l'uso di un server di pull:</span><span class="sxs-lookup"><span data-stu-id="4fbad-145">Requirements for using a pull server:</span></span>

- <span data-ttu-id="4fbad-146">Un server che esegue:</span><span class="sxs-lookup"><span data-stu-id="4fbad-146">A server running:</span></span>
  - <span data-ttu-id="4fbad-147">WMF/PowerShell 4.0 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="4fbad-147">WMF/PowerShell 4.0 or greater</span></span>
  - <span data-ttu-id="4fbad-148">Ruolo del server IIS</span><span class="sxs-lookup"><span data-stu-id="4fbad-148">IIS server role</span></span>
  - <span data-ttu-id="4fbad-149">Servizio DSC</span><span class="sxs-lookup"><span data-stu-id="4fbad-149">DSC Service</span></span>
- <span data-ttu-id="4fbad-150">Idealmente, uno strumento per la generazione di un certificato, per proteggere le credenziali passate a Gestione configurazione locale nei nodi di destinazione</span><span class="sxs-lookup"><span data-stu-id="4fbad-150">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="4fbad-151">Il modo migliore per configurare Windows Server per ospitare un servizio di pull consiste nell'usare una configurazione DSC.</span><span class="sxs-lookup"><span data-stu-id="4fbad-151">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span> <span data-ttu-id="4fbad-152">Di seguito è disponibile un esempio di script.</span><span class="sxs-lookup"><span data-stu-id="4fbad-152">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="4fbad-153">Sistemi di database supportati</span><span class="sxs-lookup"><span data-stu-id="4fbad-153">Supported database systems</span></span>

| <span data-ttu-id="4fbad-154">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="4fbad-154">WMF 4.0</span></span> |       <span data-ttu-id="4fbad-155">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="4fbad-155">WMF 5.0</span></span>        |       <span data-ttu-id="4fbad-156">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="4fbad-156">WMF 5.1</span></span>        | <span data-ttu-id="4fbad-157">WMF 5.1 (Windows Server Insider Preview 17090)</span><span class="sxs-lookup"><span data-stu-id="4fbad-157">WMF 5.1 (Windows Server Insider Preview 17090)</span></span> |
| ------- | -------------------- | -------------------- | ---------------------------------------------- |
| <span data-ttu-id="4fbad-158">MDB</span><span class="sxs-lookup"><span data-stu-id="4fbad-158">MDB</span></span>     | <span data-ttu-id="4fbad-159">ESENT (predefinito), MDB</span><span class="sxs-lookup"><span data-stu-id="4fbad-159">ESENT (Default), MDB</span></span> | <span data-ttu-id="4fbad-160">ESENT (predefinito), MDB</span><span class="sxs-lookup"><span data-stu-id="4fbad-160">ESENT (Default), MDB</span></span> | <span data-ttu-id="4fbad-161">ESENT (predefinito), SQL Server, MDB</span><span class="sxs-lookup"><span data-stu-id="4fbad-161">ESENT (Default), SQL Server, MDB</span></span>               |

<span data-ttu-id="4fbad-162">A partire dalla versione 17090 di [Windows Server Insider Preview](https://www.microsoft.com/software-download/windowsinsiderpreviewserver), SQL Server è un'opzione supportata per il servizio di pull (funzionalità di Windows *servizio DSC*).</span><span class="sxs-lookup"><span data-stu-id="4fbad-162">Starting in release 17090 of [Windows Server Insider Preview](https://www.microsoft.com/software-download/windowsinsiderpreviewserver), SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span> <span data-ttu-id="4fbad-163">In questo modo si rende disponibile una nuova opzione per il ridimensionamento di ambienti DSC di grandi dimensioni che non sono stati migrati ad [Automation DSC per Azure](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="4fbad-163">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> [!NOTE]
> <span data-ttu-id="4fbad-164">il supporto per SQL Server non verrà aggiunto alle versioni precedenti di WMF 5.1 (o versioni precedenti) e sarà disponibile solo nelle versioni di Windows Server maggiori o uguali alla 17090.</span><span class="sxs-lookup"><span data-stu-id="4fbad-164">SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="4fbad-165">Per configurare il server di pull per l'uso di SQL Server, impostare **SqlProvider** su `$true` e **SqlConnectionString** su una stringa di connessione di SQL Server valida.</span><span class="sxs-lookup"><span data-stu-id="4fbad-165">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span> <span data-ttu-id="4fbad-166">Per altre informazioni, vedere [Stringhe di connessione SqlClient](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span><span class="sxs-lookup"><span data-stu-id="4fbad-166">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="4fbad-167">Per un esempio di configurazione di SQL Server con **xDscWebService**, leggere prima [Uso della risorsa xDscWebService](#using-the-xdscwebservice-resource) e quindi vedere [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 in GitHub](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span><span class="sxs-lookup"><span data-stu-id="4fbad-167">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="4fbad-168">Uso della risorsa xDscWebService</span><span class="sxs-lookup"><span data-stu-id="4fbad-168">Using the xDscWebService resource</span></span>

<span data-ttu-id="4fbad-169">Il metodo più semplice per configurare un server di pull Web consiste nell'usare la risorsa **xDscWebService**, inclusa nel modulo **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="4fbad-169">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="4fbad-170">La procedura seguente descrive come usare la risorsa in un oggetto `Configuration` che imposta il servizio Web.</span><span class="sxs-lookup"><span data-stu-id="4fbad-170">The following steps explain how to use the resource in a `Configuration` that sets up the web service.</span></span>

1. <span data-ttu-id="4fbad-171">Chiamare il cmdlet [Install-Module](/reference/6/PowerShellGet/Install-Module.md) per installare il modulo **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="4fbad-171">Call the [Install-Module](/reference/6/PowerShellGet/Install-Module.md) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span>

   > [!NOTE]
   > <span data-ttu-id="4fbad-172">Il cmdlet `Install-Module` è incluso nel modulo **PowerShellGet**, disponibile in PowerShell 5.0 o versioni successive.</span><span class="sxs-lookup"><span data-stu-id="4fbad-172">`Install-Module` is included in the **PowerShellGet** module, which is included in PowerShell 5.0 and higher.</span></span>

1. <span data-ttu-id="4fbad-173">Ottenere un certificato SSL per il server di pull DSC da un'Autorità di certificazione attendibile, all'interno dell'organizzazione o pubblica.</span><span class="sxs-lookup"><span data-stu-id="4fbad-173">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="4fbad-174">Il certificato ricevuto dall'autorità è in genere in formato PFX.</span><span class="sxs-lookup"><span data-stu-id="4fbad-174">The certificate received from the authority is usually in the PFX format.</span></span>
1. <span data-ttu-id="4fbad-175">Installare il certificato nel nodo che diventerà il server di pull DSC nel percorso predefinito, ossia `CERT:\LocalMachine\My`.</span><span class="sxs-lookup"><span data-stu-id="4fbad-175">Install the certificate on the node that will become the DSC Pull server in the default location, which should be `CERT:\LocalMachine\My`.</span></span>
   - <span data-ttu-id="4fbad-176">Prendere nota dell'identificazione personale del certificato.</span><span class="sxs-lookup"><span data-stu-id="4fbad-176">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="4fbad-177">Selezionare un GUID da usare come chiave di registrazione.</span><span class="sxs-lookup"><span data-stu-id="4fbad-177">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="4fbad-178">Per generarne uno tramite PowerShell, immettere quanto segue al prompt di PowerShell e premere INVIO: `[guid]::newGuid()` oppure `New-Guid`.</span><span class="sxs-lookup"><span data-stu-id="4fbad-178">To generate one using PowerShell enter the following at the PS prompt and press enter: `[guid]::newGuid()` or `New-Guid`.</span></span> <span data-ttu-id="4fbad-179">Questa chiave verrà usata dai nodi client come chiave condivisa per l'autenticazione durante la registrazione.</span><span class="sxs-lookup"><span data-stu-id="4fbad-179">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="4fbad-180">Per altre informazioni, vedere la sezione Chiave di registrazione di seguito.</span><span class="sxs-lookup"><span data-stu-id="4fbad-180">For more information, see the Registration Key section below.</span></span>
1. <span data-ttu-id="4fbad-181">In PowerShell ISE avviare (<kbd>F5</kbd>) lo script di configurazione seguente, incluso nella cartella del modulo **xPSDesiredStateConfiguration** come `Sample_xDscWebServiceRegistration.ps1`.</span><span class="sxs-lookup"><span data-stu-id="4fbad-181">In the PowerShell ISE, start (<kbd>F5</kbd>) the following configuration script (included in the folder of the **xPSDesiredStateConfiguration** module as `Sample_xDscWebServiceRegistration.ps1`) .</span></span> <span data-ttu-id="4fbad-182">Questo script configura il server di pull.</span><span class="sxs-lookup"><span data-stu-id="4fbad-182">This script sets up the pull server.</span></span>

    ```powershell
    configuration Sample_xDscWebServiceRegistration
    {
        param
        (
            [string[]]$NodeName = 'localhost',

            [ValidateNotNullOrEmpty()]
            [string] $certificateThumbPrint,

            [Parameter(HelpMessage='This should be a string with enough entropy (randomness) to protect the registration of clients to the pull server.  We will use new GUID by default.')]
            [ValidateNotNullOrEmpty()]
            [string] $RegistrationKey   # A guid that clients use to initiate conversation with pull server
        )

        Import-DSCResource -ModuleName PSDesiredStateConfiguration
        Import-DSCResource -ModuleName xPSDesiredStateConfiguration

        Node $NodeName
        {
            WindowsFeature DSCServiceFeature
            {
                Ensure = "Present"
                Name   = "DSC-Service"
            }

            xDscWebService PSDSCPullServer
            {
                Ensure                  = "Present"
                EndpointName            = "PSDSCPullServer"
                Port                    = 8080
                PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer"
                CertificateThumbPrint   = $certificateThumbPrint
                ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                State                   = "Started"
                DependsOn               = "[WindowsFeature]DSCServiceFeature"
                RegistrationKeyPath     = "$env:PROGRAMFILES\WindowsPowerShell\DscService"
                AcceptSelfSignedCertificates = $true
                UseSecurityBestPractices     = $true
                Enable32BitAppOnWin64   = $false
            }

            File RegistrationKeyFile
            {
                Ensure          = 'Present'
                Type            = 'File'
                DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
                Contents        = $RegistrationKey
            }
        }
    }
    ```

1. <span data-ttu-id="4fbad-183">Eseguire la configurazione, passando l'identificazione personale del certificato SSL come parametro **certificateThumbPrint** e una chiave di registrazione GUID come parametro **RegistrationKey**:</span><span class="sxs-lookup"><span data-stu-id="4fbad-183">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a><span data-ttu-id="4fbad-184">Chiave di registrazione</span><span class="sxs-lookup"><span data-stu-id="4fbad-184">Registration Key</span></span>

<span data-ttu-id="4fbad-185">Per consentire ai nodi client di eseguire la registrazione nel server in modo da poter usare i nomi di configurazione invece di un ID configurazione, una chiave di registrazione creata dalla configurazione precedente viene salvata in un file denominato `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="4fbad-185">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="4fbad-186">La chiave di registrazione funziona come segreto condiviso usato durante la registrazione iniziale dal client con il server di pull.</span><span class="sxs-lookup"><span data-stu-id="4fbad-186">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="4fbad-187">Il client genererà un certificato autofirmato che viene usato per l'autenticazione univoca nel server di pull dopo il corretto completamento della registrazione.</span><span class="sxs-lookup"><span data-stu-id="4fbad-187">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="4fbad-188">L'identificazione personale del certificato viene archiviata in locale e associata all'URL del server di pull.</span><span class="sxs-lookup"><span data-stu-id="4fbad-188">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="4fbad-189">Le chiavi di registrazione non sono supportate in PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="4fbad-189">Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="4fbad-190">Per configurare un nodo per l'autenticazione nel server di pull, la chiave di registrazione deve essere inclusa nella metaconfigurazione per qualsiasi nodo di destinazione che si registrerà per questo server di pull.</span><span class="sxs-lookup"><span data-stu-id="4fbad-190">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="4fbad-191">Tenere presente che **RegistrationKey** nella metaconfigurazione seguente viene rimosso dopo la registrazione del computer di destinazione e che il valore deve corrispondere al valore archiviato nel file `RegistrationKeys.txt` nel server di pull (in questo esempio, '140a952b-b9d6-406b-b416-e0f759c9c0e4').</span><span class="sxs-lookup"><span data-stu-id="4fbad-191">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value must match the value stored in the `RegistrationKeys.txt` file on the pull server ('140a952b-b9d6-406b-b416-e0f759c9c0e4' for this example).</span></span> <span data-ttu-id="4fbad-192">Gestire sempre il valore della chiave di registrazione tenendo conto della sicurezza, perché qualsiasi computer di destinazione a conoscenza di questo valore può registrarsi nel server di pull.</span><span class="sxs-lookup"><span data-stu-id="4fbad-192">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to set up pull server in previous configuration

        [ValidateNotNullOrEmpty()]
        [string] $ServerName = 'localhost' #node name of the pull server, same as $NodeName used in previous configuration
    )

    Node $NodeName
    {
        Settings
        {
            RefreshMode        = 'Pull'
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey    = $RegistrationKey
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey = $RegistrationKey
        }
    }
}

Sample_MetaConfigurationToRegisterWithLessSecurePullServer -RegistrationKey $RegistrationKey -OutputPath c:\Configs\TargetNodes
```

> [!NOTE]
> <span data-ttu-id="4fbad-193">La sezione **ReportServerWeb** consente l'invio dei dati per la creazione di report al server di pull.</span><span class="sxs-lookup"><span data-stu-id="4fbad-193">The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="4fbad-194">L'assenza della proprietà **ConfigurationID** nel file di metaconfigurazione significa implicitamente che il server di pull supporta la versione V2 del protocollo del server di pull e quindi è richiesta una registrazione iniziale.</span><span class="sxs-lookup"><span data-stu-id="4fbad-194">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span> <span data-ttu-id="4fbad-195">Al contrario, la presenza di un valore **ConfigurationID** significa che viene usata la versione V1 del protocollo del server di pull e non è prevista l'elaborazione della registrazione.</span><span class="sxs-lookup"><span data-stu-id="4fbad-195">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

> [!NOTE]
> <span data-ttu-id="4fbad-196">in uno scenario PUSH esiste un bug nella versione corrente che rende necessario definire una proprietà ConfigurationID nel file di metaconfigurazione per i nodi mai registrati in un server di pull.</span><span class="sxs-lookup"><span data-stu-id="4fbad-196">In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="4fbad-197">Verrà così forzato l'uso del protocollo V1 per il server di pull evitando messaggi di errori correlati alla registrazione.</span><span class="sxs-lookup"><span data-stu-id="4fbad-197">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="4fbad-198">Inserimento di configurazioni e risorse</span><span class="sxs-lookup"><span data-stu-id="4fbad-198">Placing configurations and resources</span></span>

<span data-ttu-id="4fbad-199">Dopo il completamento della configurazione del server di pull, le cartelle definite dalle proprietà **ConfigurationPath** e **ModulePath** nella configurazione del server di pull si trovano nella posizione in cui verranno posizionati i moduli e le configurazioni disponibili per il pull dai nodi di destinazione.</span><span class="sxs-lookup"><span data-stu-id="4fbad-199">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span> <span data-ttu-id="4fbad-200">Questi file devono avere un formato specifico per consentire la corretta elaborazione dal server di pull.</span><span class="sxs-lookup"><span data-stu-id="4fbad-200">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="4fbad-201">Formato del pacchetto dei moduli di risorse DSC</span><span class="sxs-lookup"><span data-stu-id="4fbad-201">DSC resource module package format</span></span>

<span data-ttu-id="4fbad-202">Ogni modulo di risorse deve essere compresso e denominato in base alla convenzione seguente `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="4fbad-202">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>

<span data-ttu-id="4fbad-203">Ad esempio, un modulo denominato **xWebAdminstration** con versione 3.1.2.0 viene denominato `xWebAdministration_3.1.2.0.zip`.</span><span class="sxs-lookup"><span data-stu-id="4fbad-203">For example, a module named **xWebAdminstration** with a module version of 3.1.2.0 would be named `xWebAdministration_3.1.2.0.zip`.</span></span> <span data-ttu-id="4fbad-204">Ogni versione di un modulo deve essere contenuta in un unico file ZIP.</span><span class="sxs-lookup"><span data-stu-id="4fbad-204">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="4fbad-205">Dato che esiste solo un'unica versione di una risorsa in ogni file ZIP, non è supportato il formato di modulo aggiunto in WMF 5.0 che supporta più versioni del modulo in una singola directory.</span><span class="sxs-lookup"><span data-stu-id="4fbad-205">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="4fbad-206">Ciò significa che prima di creare un pacchetto per i moduli di risorse DSC da usare con il server di pull è necessario apportare una piccola modifica alla struttura di directory.</span><span class="sxs-lookup"><span data-stu-id="4fbad-206">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span> <span data-ttu-id="4fbad-207">Il formato predefinito dei moduli contenenti risorse DSC in WMF 5.0 è `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="4fbad-207">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="4fbad-208">Prima di creare il pacchetto per il server di pull, rimuovere la cartella **{Versione modulo}** , in modo che il percorso diventi `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="4fbad-208">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="4fbad-209">Con questa modifica, comprimere la cartella come descritto in precedenza e posizionare i file ZIP nella cartella **ModulePath**.</span><span class="sxs-lookup"><span data-stu-id="4fbad-209">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="4fbad-210">Usare `New-DscChecksum {module zip file}` per creare un file di checksum per il modulo appena aggiunto.</span><span class="sxs-lookup"><span data-stu-id="4fbad-210">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="4fbad-211">Formato del file MOF di configurazione</span><span class="sxs-lookup"><span data-stu-id="4fbad-211">Configuration MOF format</span></span>

<span data-ttu-id="4fbad-212">Un file MOF di configurazione deve essere associato a un file di checksum in modo che Gestione configurazione locale in un nodo di destinazione possa convalidare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="4fbad-212">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span> <span data-ttu-id="4fbad-213">Per creare un checksum, chiamare il cmdlet [New-DscChecksum](/reference/6/PSDesiredStateConfiguration/New-DSCCheckSum.md).</span><span class="sxs-lookup"><span data-stu-id="4fbad-213">To create a checksum, call the [New-DscChecksum](/reference/6/PSDesiredStateConfiguration/New-DSCCheckSum.md) cmdlet.</span></span> <span data-ttu-id="4fbad-214">Il cmdlet accetta un parametro **Path** che specifica la cartella in cui si trova il file MOF di configurazione.</span><span class="sxs-lookup"><span data-stu-id="4fbad-214">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="4fbad-215">Il cmdlet crea un file di checksum denominato `ConfigurationMOFName.mof.checksum`, in cui `ConfigurationMOFName` è il nome del file MOF di configurazione.</span><span class="sxs-lookup"><span data-stu-id="4fbad-215">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span> <span data-ttu-id="4fbad-216">Se nella cartella specificata sono presenti più file MOF di configurazione, viene creato un checksum per ogni configurazione nella cartella.</span><span class="sxs-lookup"><span data-stu-id="4fbad-216">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span> <span data-ttu-id="4fbad-217">Posizionare i file MOF e i file di checksum associati nella cartella **ConfigurationPath**.</span><span class="sxs-lookup"><span data-stu-id="4fbad-217">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

> [!NOTE]
> <span data-ttu-id="4fbad-218">Se si modifica il file MOF di configurazione in qualsiasi modo, è anche necessario ricreare il file di checksum.</span><span class="sxs-lookup"><span data-stu-id="4fbad-218">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="4fbad-219">Strumenti</span><span class="sxs-lookup"><span data-stu-id="4fbad-219">Tooling</span></span>

<span data-ttu-id="4fbad-220">Per facilitare la configurazione, la convalida e la gestione del server di pull, gli strumenti seguenti sono inclusi come esempi nella versione più recente del modulo xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="4fbad-220">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="4fbad-221">Un modulo che facilita la creazione di pacchetti per i moduli di risorse DSC e i file di configurazione per l'uso nel server di pull.</span><span class="sxs-lookup"><span data-stu-id="4fbad-221">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span>
   <span data-ttu-id="4fbad-222">[PublishModulesAndMofsToPullServer.psm1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetup.psm1).</span><span class="sxs-lookup"><span data-stu-id="4fbad-222">[PublishModulesAndMofsToPullServer.psm1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetup.psm1).</span></span>
   <span data-ttu-id="4fbad-223">Ecco alcuni esempi:</span><span class="sxs-lookup"><span data-stu-id="4fbad-223">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="4fbad-224">Uno script che convalida la corretta configurazione del server di pull.</span><span class="sxs-lookup"><span data-stu-id="4fbad-224">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="4fbad-225">[PullServerSetupTests.ps1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetupTest/DscPullServerSetupTest.ps1).</span><span class="sxs-lookup"><span data-stu-id="4fbad-225">[PullServerSetupTests.ps1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetupTest/DscPullServerSetupTest.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="4fbad-226">Soluzioni della community per il servizio di pull</span><span class="sxs-lookup"><span data-stu-id="4fbad-226">Community Solutions for Pull Service</span></span>

<span data-ttu-id="4fbad-227">La community di DSC ha creato più soluzioni per implementare il protocollo del servizio di pull.</span><span class="sxs-lookup"><span data-stu-id="4fbad-227">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span> <span data-ttu-id="4fbad-228">Per gli ambienti locali, queste soluzioni offrono funzionalità del servizio di pull e la possibilità di offrire il proprio contributo alla community con miglioramenti incrementali.</span><span class="sxs-lookup"><span data-stu-id="4fbad-228">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="4fbad-229">Tug</span><span class="sxs-lookup"><span data-stu-id="4fbad-229">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="4fbad-230">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="4fbad-230">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="4fbad-231">Configurazione dei client di pull</span><span class="sxs-lookup"><span data-stu-id="4fbad-231">Pull client configuration</span></span>

<span data-ttu-id="4fbad-232">Gli argomenti seguenti descrivono in modo dettagliato la configurazione dei client di pull:</span><span class="sxs-lookup"><span data-stu-id="4fbad-232">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="4fbad-233">Configurare un client di pull DSC usando un ID configurazione</span><span class="sxs-lookup"><span data-stu-id="4fbad-233">Set up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="4fbad-234">Configurare un client di pull DSC usando nomi di configurazione</span><span class="sxs-lookup"><span data-stu-id="4fbad-234">Set up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="4fbad-235">Configurazioni parziali</span><span class="sxs-lookup"><span data-stu-id="4fbad-235">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="4fbad-236">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4fbad-236">See also</span></span>

- [<span data-ttu-id="4fbad-237">Panoramica di PowerShell DSC</span><span class="sxs-lookup"><span data-stu-id="4fbad-237">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="4fbad-238">Applicazione delle configurazioni</span><span class="sxs-lookup"><span data-stu-id="4fbad-238">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="4fbad-239">Uso di un server di report DSC</span><span class="sxs-lookup"><span data-stu-id="4fbad-239">Using a DSC report server</span></span>](reportServer.md)
- <span data-ttu-id="4fbad-240">[[MS-DSCPM]: Protocollo del modello pull per la configurazione dello stato desiderato](https://docs.microsoft.com/openspecs/windows_protocols/ms-dscpm/ea744c01-51a2-4000-9ef2-312711dcc8c9)</span><span class="sxs-lookup"><span data-stu-id="4fbad-240">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://docs.microsoft.com/openspecs/windows_protocols/ms-dscpm/ea744c01-51a2-4000-9ef2-312711dcc8c9)</span></span>
- <span data-ttu-id="4fbad-241">[[MS-DSCPM]: Protocollo del modello pull per la configurazione dello stato desiderato - Errori](https://docs.microsoft.com/openspecs/windows_protocols/ms-winerrata/f5fc7ae3-9172-41e8-ac6a-2a5a5b7bfaf5)</span><span class="sxs-lookup"><span data-stu-id="4fbad-241">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://docs.microsoft.com/openspecs/windows_protocols/ms-winerrata/f5fc7ae3-9172-41e8-ac6a-2a5a5b7bfaf5)</span></span>
