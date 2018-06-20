---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Configurazioni parziali di PowerShell DSC (Desired State Configuration)
ms.openlocfilehash: e6d80b065ad9e68517d2952b7643e4c611d82a0f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189976"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="ca028-103">Configurazioni parziali di PowerShell DSC (Desired State Configuration)</span><span class="sxs-lookup"><span data-stu-id="ca028-103">PowerShell Desired State Configuration partial configurations</span></span>

><span data-ttu-id="ca028-104">Si applica a: Windows PowerShell 5.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ca028-104">Applies To: Windows PowerShell 5.0 and later.</span></span>

<span data-ttu-id="ca028-105">In PowerShell 5.0, DSC (Desired State Configuration) consente di distribuire le configurazioni in frammenti e da più origini.</span><span class="sxs-lookup"><span data-stu-id="ca028-105">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="ca028-106">Gestione configurazione locale nel nodo di destinazione riunisce i frammenti prima di applicarli come singola configurazione.</span><span class="sxs-lookup"><span data-stu-id="ca028-106">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="ca028-107">Questa funzionalità consente di condividere il controllo della configurazione tra team o singoli utenti.</span><span class="sxs-lookup"><span data-stu-id="ca028-107">This capability allows sharing control of configuration between teams or individuals.</span></span>
<span data-ttu-id="ca028-108">Ad esempio, se due o più team di sviluppatori collaborano a un servizio, ogni team potrebbe voler creare configurazioni per gestire la propria parte del servizio.</span><span class="sxs-lookup"><span data-stu-id="ca028-108">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="ca028-109">È possibile effettuare il pull di ognuna di queste configurazioni da server di pull diversi e aggiungere le configurazioni in fasi diverse del processo di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="ca028-109">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="ca028-110">Le configurazioni parziali consentono inoltre a persone o team diversi di controllare aspetti diversi della configurazione dei nodi senza la necessità di coordinare le modifiche di un singolo documento di configurazione.</span><span class="sxs-lookup"><span data-stu-id="ca028-110">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="ca028-111">Un team, ad esempio, potrebbe essere responsabile della distribuzione di una VM e un sistema operativo, mentre un altro team potrebbe distribuire altri servizi e applicazioni in tale VM.</span><span class="sxs-lookup"><span data-stu-id="ca028-111">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="ca028-112">Con le configurazioni parziali, ogni team può creare la sua configurazione, senza che alcuna di esse sia inutilmente complessa.</span><span class="sxs-lookup"><span data-stu-id="ca028-112">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="ca028-113">È possibile usare le configurazioni parziali in modalità push o pull o in una combinazione delle due modalità.</span><span class="sxs-lookup"><span data-stu-id="ca028-113">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="ca028-114">Configurazioni parziali in modalità push</span><span class="sxs-lookup"><span data-stu-id="ca028-114">Partial configurations in push mode</span></span>
<span data-ttu-id="ca028-115">Per usare le configurazioni parziali in modalità push, è necessario configurare Gestione configurazione locale nel nodo di destinazione per ricevere le configurazioni parziali.</span><span class="sxs-lookup"><span data-stu-id="ca028-115">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="ca028-116">Il push di ogni configurazione parziale nella destinazione viene effettuato usando il cmdlet Publish-DSCConfiguration.</span><span class="sxs-lookup"><span data-stu-id="ca028-116">Each partial configuration must be pushed to the target by using the Publish-DSCConfiguration cmdlet.</span></span> <span data-ttu-id="ca028-117">Il nodo di destinazione combina quindi la configurazione parziale in una singola configurazione, che è possibile applicare chiamando il cmdlet [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx).</span><span class="sxs-lookup"><span data-stu-id="ca028-117">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="ca028-118">Configurazione di Gestione configurazione locale per le configurazioni parziali in modalità push</span><span class="sxs-lookup"><span data-stu-id="ca028-118">Configuring the LCM for push-mode partial configurations</span></span>
<span data-ttu-id="ca028-119">Per configurare Gestione configurazione locale per le configurazioni parziali in modalità push, è necessario creare una configurazione **DSCLocalConfigurationManager** con un blocco **PartialConfiguration** per ogni configurazione parziale.</span><span class="sxs-lookup"><span data-stu-id="ca028-119">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="ca028-120">Per altre informazioni sulla configurazione di Gestione configurazione locale, vedere [Configurazione di Gestione configurazione locale](https://technet.microsoft.com/library/mt421188.aspx).</span><span class="sxs-lookup"><span data-stu-id="ca028-120">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](https://technet.microsoft.com/library/mt421188.aspx).</span></span>
<span data-ttu-id="ca028-121">L'esempio seguente illustra una configurazione di Gestione configurazione locale che prevede due configurazioni parziali, una che distribuisce il sistema operativo e una che distribuisce e configura SharePoint.</span><span class="sxs-lookup"><span data-stu-id="ca028-121">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {

           PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="ca028-122">Il valore di **RefreshMode** per ogni configurazione parziale è "Push".</span><span class="sxs-lookup"><span data-stu-id="ca028-122">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="ca028-123">I nomi dei blocchi **PartialConfiguration** (in questo caso, "ServiceAccountConfig" e "SharePointConfig") devono corrispondere esattamente ai nomi delle configurazioni di cui viene effettuato il push nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="ca028-123">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

><span data-ttu-id="ca028-124">**Nota:** il nome di ogni blocco **PartialConfiguration** deve corrispondere al nome effettivo della configurazione, come specificato nello script di configurazione, non al nome del file MOF, che deve essere il nome del nodo di destinazione o `localhost`.</span><span class="sxs-lookup"><span data-stu-id="ca028-124">**Note:** The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="ca028-125">Pubblicazione e avvio di configurazioni parziali in modalità push</span><span class="sxs-lookup"><span data-stu-id="ca028-125">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="ca028-126">Chiamare quindi [Publish-DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) per ogni configurazione, passando le cartelle che contengono i documenti di configurazione come parametri **Path**.</span><span class="sxs-lookup"><span data-stu-id="ca028-126">You then call [Publish-DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="ca028-127">`Publish-DSCConfiguration`inserisce i file MOF di configurazione nei nodi di destinazione.</span><span class="sxs-lookup"><span data-stu-id="ca028-127">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="ca028-128">Dopo la pubblicazione di entrambe le configurazioni, è possibile chiamare `Start-DSCConfiguration –UseExisting` nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="ca028-128">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="ca028-129">Ad esempio, se sono stati compilati i documenti MOF di configurazione seguenti nel nodo di creazione:</span><span class="sxs-lookup"><span data-stu-id="ca028-129">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

```powershell
PS C:\PartialConfigTest> Get-ChildItem -Recurse


    Directory: C:\PartialConfigTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        8/11/2016   1:55 PM                ServiceAccountConfig
d-----       11/17/2016   4:14 PM                SharePointConfig


    Directory: C:\PartialConfigTest\ServiceAccountConfig


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/11/2016   2:02 PM           2034 TestVM.mof


    Directory: C:\DscTests\SharePointConfig


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

<span data-ttu-id="ca028-130">Le configurazioni verrebbero pubblicate ed eseguite come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="ca028-130">You would publish and run the configurations as follows:</span></span>

```powershell
PS C:\PartialConfigTest> Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Start-DscConfiguration -UseExisting -ComputerName 'TestVM'

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

><span data-ttu-id="ca028-131">**Nota:** l'utente che esegue il cmdlet [Publish-DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) deve avere privilegi di amministratore nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="ca028-131">**Note:** The user running the [Publish-DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="ca028-132">Configurazioni parziali in modalità pull</span><span class="sxs-lookup"><span data-stu-id="ca028-132">Partial configurations in pull mode</span></span>

<span data-ttu-id="ca028-133">È possibile effettuare il pull delle configurazioni parziali da uno o più server di pull. Per altre informazioni sui server di pull, vedere [Server di pull Windows PowerShell DSC (Desired Configuration Pull)](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="ca028-133">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="ca028-134">A tale scopo, è necessario configurare Gestione configurazione locale nel nodo di destinazione per effettuare il pull delle configurazioni parziali, nonché assegnare un nome ai documenti di configurazione e posizionarli in modo appropriato nei server di pull.</span><span class="sxs-lookup"><span data-stu-id="ca028-134">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="ca028-135">Configurazione di Gestione configurazione locale per le configurazioni dei nodi di pull</span><span class="sxs-lookup"><span data-stu-id="ca028-135">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="ca028-136">Per configurare Gestione configurazione locale per il pull di configurazioni parziali da un server di pull, è necessario definire il server di pull in un blocco **ConfigurationRepositoryWeb** (per un server di pull HTTP) o **ConfigurationRepositoryShare** (per un server di pull SMB).</span><span class="sxs-lookup"><span data-stu-id="ca028-136">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="ca028-137">Creare quindi blocchi **PartialConfiguration** che fanno riferimento al server di pull usando la proprietà **ConfigurationSource**.</span><span class="sxs-lookup"><span data-stu-id="ca028-137">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="ca028-138">È anche necessario creare un blocco **Settings** per specificare che Gestione configurazione locale usa la modalità pull, nonché specificare il valore di **ConfigurationNames** o **ConfigurationID** usato dal server di pull e dal nodo di destinazione per identificare le configurazioni.</span><span class="sxs-lookup"><span data-stu-id="ca028-138">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="ca028-139">La metaconfigurazione seguente definisce un server di pull HTTP denominato CONTOSO-PullSrv e due configurazioni parziali che usano tale server di pull.</span><span class="sxs-lookup"><span data-stu-id="ca028-139">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="ca028-140">Per informazioni sulla configurazione di Gestione configurazione locale tramite **ConfigurationNames**, vedere [Configurazione di un client di pull usando nomi di configurazione](pullClientConfigNames.md).</span><span class="sxs-lookup"><span data-stu-id="ca028-140">For more information about configuring the LCM using **ConfigurationNames**, see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span>
<span data-ttu-id="ca028-141">Per informazioni sulla configurazione di Gestione configurazione locale tramite **ConfigurationID**, vedere [Configurazione di un client di pull usando un ID configurazione](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="ca028-141">For information about configuring the LCM using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="ca028-142">Configurazione di Gestione configurazione locale per configurazioni di modalità pull tramite nomi di configurazione</span><span class="sxs-lookup"><span data-stu-id="ca028-142">Configuring the LCM for pull mode configurations using configuration names</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }

}
```

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="ca028-143">Configurazione di Gestione configurazione locale per configurazioni di modalità pull tramite ID configurazione</span><span class="sxs-lookup"><span data-stu-id="ca028-143">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="ca028-144">È possibile effettuare il pull delle configurazioni parziali da più di un server di pull. A tale scopo, è sufficiente definire ogni server di pull e quindi fare riferimento al server di pull appropriato in ogni blocco **PartialConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="ca028-144">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="ca028-145">Dopo aver creato la metaconfigurazione, è necessario eseguirla per creare un documento di configurazione (un file MOF) e quindi chiamare [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) per configurare Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="ca028-145">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="ca028-146">Denominazione e posizionamento dei documenti di configurazione nel server di pull (ConfigurationNames)</span><span class="sxs-lookup"><span data-stu-id="ca028-146">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="ca028-147">I documenti di configurazione parziale devono essere inseriti nella cartella specificata come **ConfigurationPath** nel file `web.config` per il server di pull (in genere `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="ca028-147">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="ca028-148">Assegnazione dei nomi ai documenti di configurazione nel server di pull in PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="ca028-148">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="ca028-149">Se si esegue il pull solo di una configurazione parziale da un singolo server di pull, il documento di configurazione può avere qualsiasi nome.</span><span class="sxs-lookup"><span data-stu-id="ca028-149">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span>
<span data-ttu-id="ca028-150">Se si esegue il pull di più di una configurazione parziale da un server di pull, il nome del documento di configurazione può essere `<ConfigurationName>.mof`, dove _ConfigurationName_ è il nome della configurazione parziale, oppure `<ConfigurationName>.<NodeName>.mof`, dove _ConfigurationName_ è il nome della configurazione parziale e _NodeName_ è il nome del nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="ca028-150">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where _ConfigurationName_ is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where  _ConfigurationName_ is the name of the partial configuration, and _NodeName_ is the name of the target node.</span></span>
<span data-ttu-id="ca028-151">Questo consente di eseguire il pull delle configurazioni dal server di pull DSC di Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="ca028-151">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>


#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="ca028-152">Assegnazione dei nomi ai documenti di configurazione nel server di pull in PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ca028-152">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="ca028-153">I documenti di configurazione devono essere denominati come segue: `ConfigurationName.mof`, dove _ConfigurationName_ è il nome della configurazione parziale.</span><span class="sxs-lookup"><span data-stu-id="ca028-153">The configuration documents must be named as follows: `ConfigurationName.mof`, where _ConfigurationName_ is the name of the partial configuration.</span></span> <span data-ttu-id="ca028-154">In questo esempio i nomi dei documenti di configurazione devono essere quelli indicati di seguito:</span><span class="sxs-lookup"><span data-stu-id="ca028-154">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="ca028-155">Denominazione e posizionamento dei documenti di configurazione nel server di pull (ConfigurationID)</span><span class="sxs-lookup"><span data-stu-id="ca028-155">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="ca028-156">I documenti di configurazione parziale devono essere inseriti nella cartella specificata come **ConfigurationPath** nel file `web.config` per il server di pull (in genere `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="ca028-156">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="ca028-157">I documenti di configurazione devono essere denominati come segue: _ConfigurationName_.</span><span class="sxs-lookup"><span data-stu-id="ca028-157">The configuration documents must be named as follows: _ConfigurationName_.</span></span> <span data-ttu-id="ca028-158">_ConfigurationID_`.mof`, dove _ConfigurationName_ è il nome della configurazione parziale e _ConfigurationID_ è l'ID della configurazione definita in Gestione configurazione locale nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="ca028-158">_ConfigurationID_`.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="ca028-159">In questo esempio i nomi dei documenti di configurazione devono essere quelli indicati di seguito:</span><span class="sxs-lookup"><span data-stu-id="ca028-159">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```


### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="ca028-160">Esecuzione di configurazioni parziali da un server di pull</span><span class="sxs-lookup"><span data-stu-id="ca028-160">Running partial configurations from a pull server</span></span>

<span data-ttu-id="ca028-161">Dopo aver configurato Gestione configurazione locale nel nodo di destinazione e dopo aver creato i documenti di configurazione e aver assegnato loro i nomi appropriati nel server di pull, il nodo di destinazione effettuerà il pull delle configurazioni parziali, le combinerà e applicherà la configurazione risultante a intervalli regolari, come specificato dalla proprietà **RefreshFrequencyMins** di Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="ca028-161">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="ca028-162">Se si vuole forzare un aggiornamento, è possibile chiamare il cmdlet [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx) per effettuare il pull delle configurazioni e quindi `Start-DSCConfiguration –UseExisting` per applicare le configurazioni.</span><span class="sxs-lookup"><span data-stu-id="ca028-162">If you want to force a refresh, you can call the [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>


## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="ca028-163">Configurazioni parziali in modalità mista push e pull</span><span class="sxs-lookup"><span data-stu-id="ca028-163">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="ca028-164">È anche possibile combinare le modalità push e pull per le configurazioni parziali.</span><span class="sxs-lookup"><span data-stu-id="ca028-164">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="ca028-165">In altre parole, è possibile usare una configurazione parziale di cui viene effettuato il pull da un server di pull e un'altra configurazione parziale di cui viene effettuato il push.</span><span class="sxs-lookup"><span data-stu-id="ca028-165">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="ca028-166">Specificare la modalità di aggiornamento per ogni configurazione parziale, come descritto nelle sezioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="ca028-166">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span>
<span data-ttu-id="ca028-167">Ad esempio, la metaconfigurazione seguente descrive lo stesso esempio, con la configurazione parziale `ServiceAccountConfig` in modalità pull e la configurazione parziale `SharePointConfig` in modalità push.</span><span class="sxs-lookup"><span data-stu-id="ca028-167">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="ca028-168">Modalità miste push e pull che usano ConfigurationNames</span><span class="sxs-lookup"><span data-stu-id="ca028-168">Mixed push and pull modes using ConfigurationNames</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull'
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }

}
```

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="ca028-169">Modalità miste push e pull che usano ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="ca028-169">Mixed push and pull modes using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="ca028-170">Si noti che il valore di **RefreshMode** specificato nel blocco Settings è "Pull", mentre il valore di **RefreshMode** per la configurazione parziale `SharePointConfig` è "Push".</span><span class="sxs-lookup"><span data-stu-id="ca028-170">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="ca028-171">Denominare e posizionare i file MOF di configurazione come descritto in precedenza per le relative modalità di aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="ca028-171">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span> <span data-ttu-id="ca028-172">Chiamare **Publish-DSCConfiguration** per pubblicare la configurazione parziale `SharePointConfig` e attendere il pull della configurazione `ServiceAccountConfig` dal server di pull oppure forzare un aggiornamento chiamando [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx).</span><span class="sxs-lookup"><span data-stu-id="ca028-172">Call **Publish-DSCConfiguration** to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="ca028-173">Esempio di configurazione parziale di ServiceAccountConfig</span><span class="sxs-lookup"><span data-stu-id="ca028-173">Example ServiceAccountConfig Partial Configuration</span></span>

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration


    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential

        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig

```
## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="ca028-174">Esempio di configurazione parziale di SharePointConfig</span><span class="sxs-lookup"><span data-stu-id="ca028-174">Example SharePointConfig Partial Configuration</span></span>
```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```
##<a name="see-also"></a><span data-ttu-id="ca028-175">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ca028-175">See Also</span></span>

<span data-ttu-id="ca028-176">**Concetti**
[Server di pull Windows PowerShell DSC (Desired State Configuration)](pullServer.md)</span><span class="sxs-lookup"><span data-stu-id="ca028-176">**Concepts**
[Windows PowerShell Desired State Configuration Pull Servers](pullServer.md)</span></span>

[<span data-ttu-id="ca028-177">Configurazione di Gestione configurazione locale</span><span class="sxs-lookup"><span data-stu-id="ca028-177">Windows Configuring the Local Configuration Manager</span></span>](https://technet.microsoft.com/library/mt421188.aspx)