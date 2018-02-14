---
ms.date: 2018-02-02
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Servizio di pull DSC
ms.openlocfilehash: d5e24dcc093c73d8ebbaa618517193dacc4f2aaf
ms.sourcegitcommit: 755d7bc0740573d73613cedcf79981ca3dc81c5e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="9b781-103">Servizio di pull DSC (Desired State Configuration)</span><span class="sxs-lookup"><span data-stu-id="9b781-103">Desired State Configuration Pull Service</span></span>

> <span data-ttu-id="9b781-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9b781-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="9b781-105">Gestione configurazione locale può essere gestito a livello centralizzato da una soluzione servizio di pull.</span><span class="sxs-lookup"><span data-stu-id="9b781-105">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="9b781-106">Con questo approccio, il nodo gestito viene registrato con un servizio e gli viene assegnata una configurazione nelle impostazioni di Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="9b781-106">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="9b781-107">La configurazione e tutte le risorse DSC necessarie come dipendenze per la configurazione vengono scaricate nel computer e usate da Gestione configurazione locale per gestire la configurazione.</span><span class="sxs-lookup"><span data-stu-id="9b781-107">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="9b781-108">Nel servizio vengono caricate informazioni sullo stato del computer gestito per la creazione di report.</span><span class="sxs-lookup"><span data-stu-id="9b781-108">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="9b781-109">Questo concetto è noto come "servizio di pull".</span><span class="sxs-lookup"><span data-stu-id="9b781-109">This concept is referred to as "pull service".</span></span>

<span data-ttu-id="9b781-110">Le opzioni correnti per il servizio di pull includono:</span><span class="sxs-lookup"><span data-stu-id="9b781-110">The current options for pull service include:</span></span>

- <span data-ttu-id="9b781-111">Servizio DSC (Desired State Configuration) di Automazione di Azure</span><span class="sxs-lookup"><span data-stu-id="9b781-111">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="9b781-112">Un servizio di pull in esecuzione in Windows Server</span><span class="sxs-lookup"><span data-stu-id="9b781-112">A pull service running on Windows Server</span></span>
- <span data-ttu-id="9b781-113">Soluzioni open source gestite dalla community</span><span class="sxs-lookup"><span data-stu-id="9b781-113">Community maintained open source solutions</span></span>
- <span data-ttu-id="9b781-114">Una condivisione SMB</span><span class="sxs-lookup"><span data-stu-id="9b781-114">An SMB share</span></span>

<span data-ttu-id="9b781-115">**La soluzione consigliata**, e l'opzione con il maggior numero di funzionalità disponibili, è [Automation DSC di Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="9b781-115">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="9b781-116">Il servizio di Azure può gestire i nodi in locale nei data center privati o in cloud pubblici, come Azure e AWS.</span><span class="sxs-lookup"><span data-stu-id="9b781-116">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="9b781-117">Per gli ambienti privati in cui i server non possono connettersi direttamente a Internet, è consigliabile limitare il traffico in uscita esclusivamente all'intervallo di indirizzi IP di Azure pubblicato (vedere gli [intervalli di indirizzi IP dei data center di Azure](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="9b781-117">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="9b781-118">Le funzionalità del servizio online che non sono attualmente disponibili nel servizio di pull in Windows Server includono:</span><span class="sxs-lookup"><span data-stu-id="9b781-118">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>
- <span data-ttu-id="9b781-119">Tutti i dati vengono crittografati in transito e quando inattivi</span><span class="sxs-lookup"><span data-stu-id="9b781-119">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="9b781-120">I certificati client vengono creati e gestiti automaticamente</span><span class="sxs-lookup"><span data-stu-id="9b781-120">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="9b781-121">Archivio dei segreti per la gestione centralizzata di [password/credenziali](https://docs.microsoft.com/en-us/azure/automation/automation-credentials) o [variabili](https://docs.microsoft.com/en-us/azure/automation/automation-variables) come nomi dei server o stringhe di connessione</span><span class="sxs-lookup"><span data-stu-id="9b781-121">Secrets store for centrally managing [passwords/credentials](https://docs.microsoft.com/en-us/azure/automation/automation-credentials), or [variables](https://docs.microsoft.com/en-us/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="9b781-122">Gestione centralizzata della [configurazione di Gestione configurazione locale](metaConfig.md#basic-settings) del nodo</span><span class="sxs-lookup"><span data-stu-id="9b781-122">Centrally manage node [LCM configuration](metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="9b781-123">Assegnazione centralizzata delle configurazioni ai nodi client</span><span class="sxs-lookup"><span data-stu-id="9b781-123">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="9b781-124">Rilascio delle modifiche di configurazione a "gruppi canary" per i test prima della distribuzione in ambiente di produzione</span><span class="sxs-lookup"><span data-stu-id="9b781-124">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="9b781-125">Creazione di report grafici</span><span class="sxs-lookup"><span data-stu-id="9b781-125">Graphical reporting</span></span>
  - <span data-ttu-id="9b781-126">Dettagli sullo stato al livello di granularità delle risorse DSC</span><span class="sxs-lookup"><span data-stu-id="9b781-126">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="9b781-127">Messaggi di errore dettagliati dai computer client per la risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="9b781-127">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="9b781-128">[Integrazione con Azure Log Analytics](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-diagnostics) per gli avvisi, attività automatizzate, app Android o iOS per report e avvisi</span><span class="sxs-lookup"><span data-stu-id="9b781-128">[Integration with Azure Log Analytics](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="9b781-129">Servizio di pull DSC in Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="9b781-129">DSC pull service in Windows Server</span></span>

<span data-ttu-id="9b781-130">È possibile configurare un servizio di pull per l'esecuzione in Windows Server.</span><span class="sxs-lookup"><span data-stu-id="9b781-130">It is possible to configuring a pull service to run on Windows Server.</span></span>
<span data-ttu-id="9b781-131">Si noti che la soluzione di servizio di pull inclusa in Windows Server include solo le funzionalità di archiviazione di configurazioni/moduli per il download e di acquisizione di dati di report in un database.</span><span class="sxs-lookup"><span data-stu-id="9b781-131">Please be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="9b781-132">Non include molte delle funzionalità offerte dal servizio in Azure e pertanto non rappresenta uno strumento ottimale per la valutazione delle modalità d'uso del servizio.</span><span class="sxs-lookup"><span data-stu-id="9b781-132">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="9b781-133">Il servizio di pull offerto in Windows Server è un servizio Web in IIS che usa un'interfaccia OData per rendere i file di configurazione DSC disponibili ai nodi di destinazione quando questi li richiedono.</span><span class="sxs-lookup"><span data-stu-id="9b781-133">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="9b781-134">Requisiti per l'uso di un server di pull:</span><span class="sxs-lookup"><span data-stu-id="9b781-134">Requirements for using a pull server:</span></span>

- <span data-ttu-id="9b781-135">Un server che esegue:</span><span class="sxs-lookup"><span data-stu-id="9b781-135">A server running:</span></span>
  - <span data-ttu-id="9b781-136">WMF/PowerShell 5.0 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="9b781-136">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="9b781-137">Ruolo del server IIS</span><span class="sxs-lookup"><span data-stu-id="9b781-137">IIS server role</span></span>
  - <span data-ttu-id="9b781-138">Servizio DSC</span><span class="sxs-lookup"><span data-stu-id="9b781-138">DSC Service</span></span>
- <span data-ttu-id="9b781-139">Idealmente, uno strumento per la generazione di un certificato, per proteggere le credenziali passate a Gestione configurazione locale nei nodi di destinazione</span><span class="sxs-lookup"><span data-stu-id="9b781-139">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="9b781-140">Il modo migliore per configurare Windows Server per ospitare un servizio di pull consiste nell'usare una configurazione DSC.</span><span class="sxs-lookup"><span data-stu-id="9b781-140">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="9b781-141">Di seguito è disponibile un esempio di script.</span><span class="sxs-lookup"><span data-stu-id="9b781-141">An example script is provided below.</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="9b781-142">Uso della risorsa xDSCWebService</span><span class="sxs-lookup"><span data-stu-id="9b781-142">Using the xDSCWebService resource</span></span>

<span data-ttu-id="9b781-143">Il metodo più semplice per configurare un server di pull Web consiste nell'usare la risorsa xWebService, inclusa nel modulo xPSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="9b781-143">The easiest way to set up a web pull server is to use the xWebService resource, included in the xPSDesiredStateConfiguration module.</span></span>
<span data-ttu-id="9b781-144">I passaggi seguenti descrivono come usare la risorsa in una configurazione che imposta il servizio Web.</span><span class="sxs-lookup"><span data-stu-id="9b781-144">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="9b781-145">Chiamare il cmdlet [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) per installare il modulo **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="9b781-145">Call the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="9b781-146">**Nota**: il cmdlet **Install-Module** è incluso nel modulo **PowerShellGet**, disponibile in PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="9b781-146">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="9b781-147">È possibile scaricare il modulo **PowerShellGet** per PowerShell 3.0 e 4.0 dalla pagina dell'[anteprima dei moduli PackageManagement di PowerShell](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="9b781-147">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> 
1. <span data-ttu-id="9b781-148">Ottenere un certificato SSL per il server di pull DSC da un'Autorità di certificazione attendibile, all'interno dell'organizzazione o pubblica.</span><span class="sxs-lookup"><span data-stu-id="9b781-148">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="9b781-149">Il certificato ricevuto dall'autorità è in genere in formato PFX.</span><span class="sxs-lookup"><span data-stu-id="9b781-149">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="9b781-150">Installare il certificato nel nodo che diventerà il server di pull DSC nel percorso predefinito, ossia CERT: \LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="9b781-150">Install the certificate on the node that will become the DSC Pull server in the default location which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="9b781-151">Prendere nota dell'identificazione personale del certificato.</span><span class="sxs-lookup"><span data-stu-id="9b781-151">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="9b781-152">Selezionare un GUID da usare come chiave di registrazione.</span><span class="sxs-lookup"><span data-stu-id="9b781-152">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="9b781-153">Per generarne uno tramite PowerShell, immettere quanto segue al prompt di PowerShell e premere Invio: ``` [guid]::newGuid()``` oppure ```New-Guid```.</span><span class="sxs-lookup"><span data-stu-id="9b781-153">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="9b781-154">Questa chiave verrà usata dai nodi client come chiave condivisa per l'autenticazione durante la registrazione.</span><span class="sxs-lookup"><span data-stu-id="9b781-154">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="9b781-155">Per altre informazioni, vedere la sezione Chiave di registrazione di seguito.</span><span class="sxs-lookup"><span data-stu-id="9b781-155">For more information see the Registration Key section below.</span></span>
1. <span data-ttu-id="9b781-156">In PowerShell ISE avviare (F5) lo script di configurazione seguente (incluso nella cartella Example del modulo **xPSDesiredStateConfiguration** come Sample_xDscWebService.ps1).</span><span class="sxs-lookup"><span data-stu-id="9b781-156">In the PowerShell ISE, start (F5) the following configuration script (included in the Example folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebService.ps1).</span></span> <span data-ttu-id="9b781-157">Questo script configura il server di pull.</span><span class="sxs-lookup"><span data-stu-id="9b781-157">This script sets up the pull server.</span></span>

```powershell
    configuration Sample_xDscPullServer
    {
        param
        (
                [string[]]$NodeName = 'localhost',

                [ValidateNotNullOrEmpty()]
                [string] $certificateThumbPrint,

                [Parameter(Mandatory)]
                [ValidateNotNullOrEmpty()]
                [string] $RegistrationKey
         )

         Import-DSCResource -ModuleName xPSDesiredStateConfiguration
         Import-DSCResource –ModuleName PSDesiredStateConfiguration

         Node $NodeName
         {
             WindowsFeature DSCServiceFeature
             {
                 Ensure = 'Present'
                 Name   = 'DSC-Service'
             }

             xDscWebService PSDSCPullServer
             {
                 Ensure                   = 'Present'
                 EndpointName             = 'PSDSCPullServer'
                 Port                     = 8080
                 PhysicalPath             = "$env:SystemDrive\inetpub\PSDSCPullServer"
                 CertificateThumbPrint    = $certificateThumbPrint
                 ModulePath               = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                 ConfigurationPath        = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                 State                    = 'Started'
                 DependsOn                = '[WindowsFeature]DSCServiceFeature'
                 UseSecurityBestPractices = $false
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

1. <span data-ttu-id="9b781-158">Eseguire la configurazione, passando l'identificazione personale del certificato SSL come parametro **certificateThumbPrint** e una chiave di registrazione GUID come parametro **RegistrationKey**:</span><span class="sxs-lookup"><span data-stu-id="9b781-158">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store 
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose

```

#### <a name="registration-key"></a><span data-ttu-id="9b781-159">Chiave di registrazione</span><span class="sxs-lookup"><span data-stu-id="9b781-159">Registration Key</span></span>

<span data-ttu-id="9b781-160">Per consentire ai nodi client di eseguire la registrazione nel server in modo da poter usare i nomi di configurazione invece di un ID configurazione, una chiave di registrazione creata dalla configurazione precedente viene salvata in un file denominato `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="9b781-160">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key which was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="9b781-161">La chiave di registrazione funziona come segreto condiviso usato durante la registrazione iniziale dal client con il server di pull.</span><span class="sxs-lookup"><span data-stu-id="9b781-161">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="9b781-162">Il client genererà un certificato autofirmato che viene usato per l'autenticazione univoca nel server di pull dopo il corretto completamento della registrazione.</span><span class="sxs-lookup"><span data-stu-id="9b781-162">The client will generate a self-signed certificate which is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="9b781-163">L'identificazione personale del certificato viene archiviata in locale e associata all'URL del server di pull.</span><span class="sxs-lookup"><span data-stu-id="9b781-163">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="9b781-164">**Nota**: le chiavi di registrazione non sono supportate in PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="9b781-164">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span> 

<span data-ttu-id="9b781-165">Per configurare un nodo per l'autenticazione nel server di pull, la chiave di registrazione deve essere inclusa nella metaconfigurazione per qualsiasi nodo di destinazione che si registrerà per questo server di pull.</span><span class="sxs-lookup"><span data-stu-id="9b781-165">In order to configure a node to authenticate with the pull server the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="9b781-166">Tenere presente che **RegistrationKey** nella metaconfigurazione seguente viene rimosso dopo la registrazione del computer di destinazione e che il valore '140a952b-b9d6-406b-b416-e0f759c9c0e4' deve corrispondere al valore archiviato nel file RegistrationKeys.txt nel server di pull.</span><span class="sxs-lookup"><span data-stu-id="9b781-166">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="9b781-167">Gestire sempre il valore della chiave di registrazione tenendo conto della sicurezza, perché qualsiasi computer di destinazione a conoscenza di questo valore può registrarsi nel server di pull.</span><span class="sxs-lookup"><span data-stu-id="9b781-167">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded   = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey    = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
        }
    }
}

PullClientConfigID -OutputPath c:\Configs\TargetNodes


```

> <span data-ttu-id="9b781-168">**Nota**: la sezione **ReportServerWeb** consente l'invio dei dati di report al server di pull.</span><span class="sxs-lookup"><span data-stu-id="9b781-168">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="9b781-169">L'assenza della proprietà **ConfigurationID** nel file di metaconfigurazione significa implicitamente che il server di pull supporta la versione V2 del protocollo del server di pull e quindi è richiesta una registrazione iniziale.</span><span class="sxs-lookup"><span data-stu-id="9b781-169">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="9b781-170">Al contrario, la presenza di un valore **ConfigurationID** significa che viene usata la versione V1 del protocollo del server di pull e non è prevista l'elaborazione della registrazione.</span><span class="sxs-lookup"><span data-stu-id="9b781-170">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="9b781-171">**Nota**: in uno scenario PUSH esiste un bug nella versione corrente che rende necessario definire una proprietà ConfigurationID nel file di metaconfigurazione per i nodi mai registrati in un server di pull.</span><span class="sxs-lookup"><span data-stu-id="9b781-171">**Note**: In a PUSH scenario, a bug exists in the current relase that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="9b781-172">Verrà così forzato l'uso del protocollo V1 per il server di pull evitando messaggi di errori correlati alla registrazione.</span><span class="sxs-lookup"><span data-stu-id="9b781-172">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="9b781-173">Inserimento di configurazioni e risorse</span><span class="sxs-lookup"><span data-stu-id="9b781-173">Placing configurations and resources</span></span>

<span data-ttu-id="9b781-174">Dopo il completamento della configurazione del server di pull, le cartelle definite dalle proprietà **ConfigurationPath** e **ModulePath** nella configurazione del server di pull si trovano nella posizione in cui verranno posizionati i moduli e le configurazioni disponibili per il pull dai nodi di destinazione.</span><span class="sxs-lookup"><span data-stu-id="9b781-174">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="9b781-175">Questi file devono avere un formato specifico per consentire la corretta elaborazione dal server di pull.</span><span class="sxs-lookup"><span data-stu-id="9b781-175">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="9b781-176">Formato del pacchetto dei moduli di risorse DSC</span><span class="sxs-lookup"><span data-stu-id="9b781-176">DSC resource module package format</span></span>

<span data-ttu-id="9b781-177">Ogni modulo di risorse deve essere compresso e denominato in base alla convenzione seguente `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="9b781-177">Each resource module needs to be zipped and named according the following pattern `{Module Name}_{Module Version}.zip`.</span></span>
<span data-ttu-id="9b781-178">Ad esempio, un modulo denominato xWebAdminstration con versione 3.1.2.0 verrebbe denominato 'xWebAdministration_3.2.1.0.zip'.</span><span class="sxs-lookup"><span data-stu-id="9b781-178">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span>
<span data-ttu-id="9b781-179">Ogni versione di un modulo deve essere contenuta in un unico file ZIP.</span><span class="sxs-lookup"><span data-stu-id="9b781-179">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="9b781-180">Dato che esiste solo un'unica versione di una risorsa in ogni file ZIP, non è supportato il formato di modulo aggiunto in WMF 5.0 che supporta più versioni del modulo in una singola directory.</span><span class="sxs-lookup"><span data-stu-id="9b781-180">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="9b781-181">Ciò significa che prima di creare un pacchetto per i moduli di risorse DSC da usare con il server di pull è necessario apportare una piccola modifica alla struttura di directory.</span><span class="sxs-lookup"><span data-stu-id="9b781-181">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="9b781-182">Il formato predefinito dei moduli contenenti risorse DSC in WMF 5.0 è '{Cartella modulo}\{Versione modulo}\DscResources\{Cartella risorsa DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="9b781-182">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="9b781-183">Prima di creare il pacchetto per il server di pull, rimuovere la cartella **{Versione modulo}** in modo che il percorso diventi '{Cartella modulo}\DscResources\{Cartella risorsa DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="9b781-183">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="9b781-184">Con questa modifica, comprimere la cartella come descritto in precedenza e posizionare i file ZIP nella cartella **ModulePath**.</span><span class="sxs-lookup"><span data-stu-id="9b781-184">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="9b781-185">Usare `new-dscchecksum {module zip file}` per creare un file di checksum per il modulo appena aggiunto.</span><span class="sxs-lookup"><span data-stu-id="9b781-185">Use `new-dscchecksum {module zip file}` to create a checksum file for the newly-added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="9b781-186">Formato del file MOF di configurazione</span><span class="sxs-lookup"><span data-stu-id="9b781-186">Configuration MOF format</span></span>

<span data-ttu-id="9b781-187">Un file MOF di configurazione deve essere associato a un file di checksum in modo che Gestione configurazione locale in un nodo di destinazione possa convalidare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="9b781-187">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="9b781-188">Per creare un checksum, chiamare il cmdlet [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx).</span><span class="sxs-lookup"><span data-stu-id="9b781-188">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span>
<span data-ttu-id="9b781-189">Il cmdlet accetta un parametro **Path** che specifica la cartella in cui si trova il file MOF di configurazione.</span><span class="sxs-lookup"><span data-stu-id="9b781-189">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="9b781-190">Il cmdlet crea un file di checksum denominato `ConfigurationMOFName.mof.checksum`, in cui `ConfigurationMOFName` è il nome del file MOF di configurazione.</span><span class="sxs-lookup"><span data-stu-id="9b781-190">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="9b781-191">Se nella cartella specificata sono presenti più file MOF di configurazione, viene creato un checksum per ogni configurazione nella cartella.</span><span class="sxs-lookup"><span data-stu-id="9b781-191">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="9b781-192">Posizionare i file MOF e i file di checksum associati nella cartella **ConfigurationPath**.</span><span class="sxs-lookup"><span data-stu-id="9b781-192">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="9b781-193">**Nota**: se si modifica il file MOF di configurazione in qualsiasi modo, è necessario ricreare anche il file di checksum.</span><span class="sxs-lookup"><span data-stu-id="9b781-193">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="9b781-194">Strumenti</span><span class="sxs-lookup"><span data-stu-id="9b781-194">Tooling</span></span>

<span data-ttu-id="9b781-195">Per facilitare la configurazione, la convalida e la gestione del server di pull, gli strumenti seguenti sono inclusi come esempi nella versione più recente del modulo xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="9b781-195">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="9b781-196">Un modulo che facilita la creazione di pacchetti per i moduli di risorse DSC e i file di configurazione per l'uso nel server di pull.</span><span class="sxs-lookup"><span data-stu-id="9b781-196">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="9b781-197">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="9b781-197">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="9b781-198">Ecco alcuni esempi:</span><span class="sxs-lookup"><span data-stu-id="9b781-198">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @("xWebAdministration", "xPhp") 
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="9b781-199">Uno script che convalida la corretta configurazione del server di pull.</span><span class="sxs-lookup"><span data-stu-id="9b781-199">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="9b781-200">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="9b781-200">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="9b781-201">Soluzioni della community per il servizio di pull</span><span class="sxs-lookup"><span data-stu-id="9b781-201">Community Solutions for Pull Service</span></span>

<span data-ttu-id="9b781-202">La community di DSC ha creato più soluzioni per implementare il protocollo del servizio di pull.</span><span class="sxs-lookup"><span data-stu-id="9b781-202">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="9b781-203">Per gli ambienti locali, queste soluzioni offrono funzionalità del servizio di pull e la possibilità di offrire il proprio contribuito alla community con miglioramenti incrementali.</span><span class="sxs-lookup"><span data-stu-id="9b781-203">For on-premises environments these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="9b781-204">Tug</span><span class="sxs-lookup"><span data-stu-id="9b781-204">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="9b781-205">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="9b781-205">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="9b781-206">Configurazione dei client di pull</span><span class="sxs-lookup"><span data-stu-id="9b781-206">Pull client configuration</span></span>

<span data-ttu-id="9b781-207">Gli argomenti seguenti descrivono in modo dettagliato la configurazione dei client di pull:</span><span class="sxs-lookup"><span data-stu-id="9b781-207">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="9b781-208">Configurazione di un client di pull DSC usando un ID configurazione</span><span class="sxs-lookup"><span data-stu-id="9b781-208">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="9b781-209">Configurazione di un client di pull DSC usando nomi di configurazione</span><span class="sxs-lookup"><span data-stu-id="9b781-209">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="9b781-210">Configurazioni parziali</span><span class="sxs-lookup"><span data-stu-id="9b781-210">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="9b781-211">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9b781-211">See also</span></span>

- <span data-ttu-id="9b781-212">[Panoramica di Windows PowerShell DSC (Desired State Configuration)](overview.md).</span><span class="sxs-lookup"><span data-stu-id="9b781-212">[Windows PowerShell Desired State Configuration Overview](overview.md)</span></span>
- [<span data-ttu-id="9b781-213">Applicazione delle configurazioni</span><span class="sxs-lookup"><span data-stu-id="9b781-213">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="9b781-214">Uso di un server di report DSC</span><span class="sxs-lookup"><span data-stu-id="9b781-214">Using a DSC report server</span></span>](reportServer.md)
