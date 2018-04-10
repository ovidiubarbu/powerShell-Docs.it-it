---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
title: Miglioramenti di DSC in WMF 5.1
ms.openlocfilehash: 04bf8ed820d24f1062e05d19c8f3b0c041298979
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="6ae43-103">Miglioramenti di Desired State Configuration (DSC) in WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="6ae43-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="6ae43-104">Miglioramenti delle risorse di classe DSC</span><span class="sxs-lookup"><span data-stu-id="6ae43-104">DSC class resource improvements</span></span>

<span data-ttu-id="6ae43-105">In WMF 5.1 sono stati corretti i problemi noti seguenti:</span><span class="sxs-lookup"><span data-stu-id="6ae43-105">In WMF 5.1, we have fixed the following known issues:</span></span>
* <span data-ttu-id="6ae43-106">Get-DscConfiguration può restituire valori vuoti (null) o errori se la funzione Get() di una risorsa DSC basata su classe restituisce un tipo complesso/Hashtable.</span><span class="sxs-lookup"><span data-stu-id="6ae43-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
* <span data-ttu-id="6ae43-107">Get-DscConfiguration restituisce un errore se nella configurazione DSC vengono usate le credenziali RunAs.</span><span class="sxs-lookup"><span data-stu-id="6ae43-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
* <span data-ttu-id="6ae43-108">La risorsa basata su classe non può essere usata in una configurazione composita.</span><span class="sxs-lookup"><span data-stu-id="6ae43-108">Class-based resource cannot be used in a composite configuration.</span></span>
* <span data-ttu-id="6ae43-109">Start-DscConfiguration si blocca se la risorsa basata su classe ha una proprietà di tipo specifico.</span><span class="sxs-lookup"><span data-stu-id="6ae43-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
* <span data-ttu-id="6ae43-110">La risorsa basata su classe non può essere usata come risorsa esclusiva.</span><span class="sxs-lookup"><span data-stu-id="6ae43-110">Class-based resource cannot be used as an exclusive resource.</span></span>


## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="6ae43-111">Miglioramenti del debug delle risorse DSC</span><span class="sxs-lookup"><span data-stu-id="6ae43-111">DSC resource debugging improvements</span></span>
<span data-ttu-id="6ae43-112">In WMF 5.0 il debugger di PowerShell non si arrestava in corrispondenza del metodo della risorsa basata su classe (Get/Set/Test).</span><span class="sxs-lookup"><span data-stu-id="6ae43-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span>
<span data-ttu-id="6ae43-113">In WMF 5.1 il debugger si arresta in corrispondenza del metodo della risorsa basata su classe nello stesso modo in cui si arresta per i metodi delle risorse basate su MOF.</span><span class="sxs-lookup"><span data-stu-id="6ae43-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="6ae43-114">Il client di pull DSC supporta TLS 1.1 e TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="6ae43-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>
<span data-ttu-id="6ae43-115">In precedenza, il client di pull DSC supportava solo SSL3.0 e TLS1.0 su connessioni HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6ae43-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span>
<span data-ttu-id="6ae43-116">Quando era necessario usare protocolli più sicuri, il client di pull smetteva di funzionare.</span><span class="sxs-lookup"><span data-stu-id="6ae43-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span>
<span data-ttu-id="6ae43-117">In WMF 5.1 il client di pull DSC non supporta più SSL 3.0 e aggiunge il supporto dei protocolli TLS 1.1 e TLS 1.2 più sicuri.</span><span class="sxs-lookup"><span data-stu-id="6ae43-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="6ae43-118">Miglioramento della registrazione del server di pull</span><span class="sxs-lookup"><span data-stu-id="6ae43-118">Improved pull server registration</span></span> ##

<span data-ttu-id="6ae43-119">Nelle versioni precedenti di WMF le richieste di registrazione o reporting simultanee al server di pull DSC, con uso del database ESENT, facevano sì che la gestione della configurazione locale non riuscisse a eseguire la registrazione o il reporting.</span><span class="sxs-lookup"><span data-stu-id="6ae43-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span>
<span data-ttu-id="6ae43-120">In questi casi, nei log eventi del server di pull viene visualizzato il messaggio di errore "Nome istanza già in uso".</span><span class="sxs-lookup"><span data-stu-id="6ae43-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span>
<span data-ttu-id="6ae43-121">Ciò era dovuto a un modello errato che veniva usato per accedere al database ESENT in uno scenario multithread.</span><span class="sxs-lookup"><span data-stu-id="6ae43-121">This was due to an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span>
<span data-ttu-id="6ae43-122">In WMF 5.1 questo problema è stato risolto.</span><span class="sxs-lookup"><span data-stu-id="6ae43-122">In WMF 5.1, this issue has been fixed.</span></span>
<span data-ttu-id="6ae43-123">Il reporting o le registrazioni simultanee, che comprendono l'uso del database ESENT, funzionano correttamente in WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="6ae43-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span>
<span data-ttu-id="6ae43-124">Tutto questo si applica solo al database ESENT, non al database OLE DB.</span><span class="sxs-lookup"><span data-stu-id="6ae43-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="6ae43-125">Abilitare il log circolare nell'istanza di database ESENT</span><span class="sxs-lookup"><span data-stu-id="6ae43-125">Enable Circular log on ESENT database instance</span></span>
<span data-ttu-id="6ae43-126">Nella versione precedente di DSC-PullServer, i file di log del database ESENT riempiono lo spazio su disco del server di pull perché l'istanza del database viene creata senza registrazione circolare.</span><span class="sxs-lookup"><span data-stu-id="6ae43-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="6ae43-127">In questa versione è possibile controllare il comportamento di registrazione circolare dell'istanza usando il file web.config del server di pull.</span><span class="sxs-lookup"><span data-stu-id="6ae43-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="6ae43-128">Per impostazione predefinita, CircularLogging è impostato su TRUE.</span><span class="sxs-lookup"><span data-stu-id="6ae43-128">By default CircularLogging is set to TRUE.</span></span>
```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```
## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="6ae43-129">Convenzione di denominazione della configurazione parziale pull</span><span class="sxs-lookup"><span data-stu-id="6ae43-129">Pull partial configuration naming convention</span></span>
<span data-ttu-id="6ae43-130">Nella versione precedente la convenzione di denominazione di una configurazione parziale prevedeva che il nome del file MOF del servizio o del server pull corrispondesse al nome della configurazione parziale specificato nelle impostazioni di Gestione configurazione locale che doveva a sua volta corrispondere al nome di configurazione incorporato nel file MOF.</span><span class="sxs-lookup"><span data-stu-id="6ae43-130">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="6ae43-131">Vedere gli snapshot seguenti:</span><span class="sxs-lookup"><span data-stu-id="6ae43-131">See the snapshots below:</span></span>

<span data-ttu-id="6ae43-132">•   Impostazioni della configurazione locale che definisce una configurazione parziale che un nodo è autorizzato a ricevere.</span><span class="sxs-lookup"><span data-stu-id="6ae43-132">•   Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

![Metaconfigurazione di esempio](../images/MetaConfigPartialOne.png)

<span data-ttu-id="6ae43-134">•   Definizione di configurazione parziale di esempio</span><span class="sxs-lookup"><span data-stu-id="6ae43-134">•   Sample partial configuration definition</span></span>

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

<span data-ttu-id="6ae43-135">•   'ConfigurationName' incorporato nel file MOF generato.</span><span class="sxs-lookup"><span data-stu-id="6ae43-135">•   'ConfigurationName' embedded in the generated MOF file.</span></span>

![Esempio di file MOF generato](../images/PartialGeneratedMof.png)

<span data-ttu-id="6ae43-137">•   FileName nel repository di configurazione pull</span><span class="sxs-lookup"><span data-stu-id="6ae43-137">•   FileName in the pull configuration repository</span></span>

![FileName nel repository di configurazione](../images/PartialInConfigRepository.png)

<span data-ttu-id="6ae43-139">File MOF del nome del servizio di automazione di Azure generati come `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="6ae43-139">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="6ae43-140">La configurazione seguente viene compilata in PartialOne.localhost.mof.</span><span class="sxs-lookup"><span data-stu-id="6ae43-140">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

<span data-ttu-id="6ae43-141">Questo rendeva impossibile l'esecuzione del pull di una configurazione parziale dal servizio di automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="6ae43-141">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

<span data-ttu-id="6ae43-142">In WMF 5.1 una configurazione parziale nel server di pull/servizio può essere denominata `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="6ae43-142">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="6ae43-143">Inoltre, se un computer effettua il pull di una configurazione singola da un server di pull/servizio, il file di configurazione nel repository di configurazione del server pull potrà avere qualsiasi nome file.</span><span class="sxs-lookup"><span data-stu-id="6ae43-143">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span>
<span data-ttu-id="6ae43-144">Questa flessibilità di denominazione consente la gestione parziale dei nodi da parte del servizio di Automazione di Azure, dove parte della configurazione deriva da Automation DSC di Azure e una configurazione parziale viene gestita localmente.</span><span class="sxs-lookup"><span data-stu-id="6ae43-144">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

<span data-ttu-id="6ae43-145">La metaconfigurazione seguente imposta un nodo che viene gestito sia localmente che dal servizio di Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="6ae43-145">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

```powershell
  [DscLocalConfigurationManager()]
   Configuration RegistrationMetaConfig
   {
        Settings
        {
            RefreshFrequencyMins = 30
            RefreshMode = "PULL"
        }

        ConfigurationRepositoryWeb web
        {
            ServerURL =  $endPoint
            RegistrationKey = $registrationKey
            ConfigurationNames = $configurationName
        }

        # Partial configuration managed by Azure Automation service.
        PartialConfiguration PartialConfigurationManagedByAzureAutomation
        {
            ConfigurationSource = "[ConfigurationRepositoryWeb]Web"
        }

        # This partial configuration is managed locally.
        PartialConfiguration OnPremisesConfig
        {
            RefreshMode = "PUSH"
            ExclusiveResources = @("Script")
        }

   }

   RegistrationMetaConfig
   Set-DscLocalConfigurationManager -Path .\RegistrationMetaConfig -Verbose
 ```

# <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="6ae43-146">Usare PsDscRunAsCredential con le risorse composite DSC</span><span class="sxs-lookup"><span data-stu-id="6ae43-146">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="6ae43-147">È stato aggiunto il supporto per l'uso di [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) con le risorse [composite](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite) DSC.</span><span class="sxs-lookup"><span data-stu-id="6ae43-147">We have added support for using [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) with DSC [Composite](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="6ae43-148">È ora possibile specificare un valore per PsDscRunAsCredential quando si usano risorse composite all'interno delle configurazioni.</span><span class="sxs-lookup"><span data-stu-id="6ae43-148">You can now specify a value for PsDscRunAsCredential when using composite resources inside configurations.</span></span>
<span data-ttu-id="6ae43-149">Quando specificato, tutte le risorse vengono eseguite all'interno di una risorsa composita come utente RunAs.</span><span class="sxs-lookup"><span data-stu-id="6ae43-149">When specified, all resources run inside a composite resource as a RunAs user.</span></span>
<span data-ttu-id="6ae43-150">Se una risorsa composita chiama un'altra risorsa composita, tutte le relative risorse vengono eseguite come utente RunAs.</span><span class="sxs-lookup"><span data-stu-id="6ae43-150">If a composite resource calls another composite resource, all of its resources are also executed as RunAs user.</span></span>
<span data-ttu-id="6ae43-151">Le credenziali RunAs vengono propagate a tutti i livelli della gerarchia di risorse composite.</span><span class="sxs-lookup"><span data-stu-id="6ae43-151">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span>
<span data-ttu-id="6ae43-152">Se una risorsa all'interno di una risorsa composita specifica un valore per PsDscRunAsCredential, durante la compilazione della configurazione si verifica un errore di merge.</span><span class="sxs-lookup"><span data-stu-id="6ae43-152">If any resource inside a composite resource specifies its own value for PsDscRunAsCredential, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="6ae43-153">Questo esempio mostra l'uso con la risorsa composita [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) inclusa nel modulo PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="6ae43-153">This example shows usage with [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) composite resource included in PSDesiredStateConfiguration module.</span></span>



```powershell

Configuration InstallWindowsFeature
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        WindowsFeatureSet features
        {
            Name = @("Telnet-Client","SNMP-Service")
            Ensure = "Present"
            IncludeAllSubFeature = $true
            PsDscRunAsCredential = Get-Credential
        }
    }

}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost'
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}


InstallWindowsFeature -ConfigurationData $configData

```

##<a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="6ae43-154">Convalide delle firme delle configurazioni e dei moduli DSC</span><span class="sxs-lookup"><span data-stu-id="6ae43-154">DSC module and configuration signing validations</span></span>
<span data-ttu-id="6ae43-155">In DSC le configurazioni e i moduli vengono distribuiti dal server di pull a computer gestiti.</span><span class="sxs-lookup"><span data-stu-id="6ae43-155">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span>
<span data-ttu-id="6ae43-156">Se il server di pull è compromesso, un utente malintenzionato potrebbe modificare le configurazioni e i moduli nel server di pull e distribuirli a tutti i nodi gestiti danneggiandoli.</span><span class="sxs-lookup"><span data-stu-id="6ae43-156">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes, compromising all of them.</span></span>

 <span data-ttu-id="6ae43-157">In WMF 5.1 DSC supporta la convalida delle firme digitali su file di catalogo e configurazione (file MOF).</span><span class="sxs-lookup"><span data-stu-id="6ae43-157">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span>
<span data-ttu-id="6ae43-158">Questa funzionalità impedisce che i nodi eseguano configurazioni o file di modulo non firmati da un'entità attendibile o manomessi dopo essere stati firmati da un'entità attendibile.</span><span class="sxs-lookup"><span data-stu-id="6ae43-158">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>



###<a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="6ae43-159">Come firmare la configurazione e il modulo</span><span class="sxs-lookup"><span data-stu-id="6ae43-159">How to sign configuration and module</span></span>
***
* <span data-ttu-id="6ae43-160">File di configurazione (.MOFs): il cmdlet di PowerShell esistente [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) supporta ora la firma dei file MOF.</span><span class="sxs-lookup"><span data-stu-id="6ae43-160">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) is extended to support signing of MOF files.</span></span>
* <span data-ttu-id="6ae43-161">Moduli: la firma dei moduli viene effettuata firmando il catalogo del modulo corrispondente eseguendo i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="6ae43-161">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
    1. <span data-ttu-id="6ae43-162">Creare un file di catalogo: un file di catalogo contiene una raccolta di hash di crittografia o identificazioni personali.</span><span class="sxs-lookup"><span data-stu-id="6ae43-162">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span>
       <span data-ttu-id="6ae43-163">Ogni identificazione personale corrisponde a un file incluso nel modulo.</span><span class="sxs-lookup"><span data-stu-id="6ae43-163">Each thumbprint corresponds to a file that is included in the module.</span></span>
       <span data-ttu-id="6ae43-164">Il nuovo cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) è stato aggiunto per consentire agli utenti di creare un file di catalogo per il modulo.</span><span class="sxs-lookup"><span data-stu-id="6ae43-164">The new cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), has been added to enable users to create a catalog file for their module.</span></span>
    2. <span data-ttu-id="6ae43-165">Firmare il file di catalogo: usare [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) per firmare il file di catalogo.</span><span class="sxs-lookup"><span data-stu-id="6ae43-165">Sign the catalog file: Use [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) to sign the catalog file.</span></span>
    3. <span data-ttu-id="6ae43-166">Posizionare il file di catalogo all'interno della cartella del modulo.</span><span class="sxs-lookup"><span data-stu-id="6ae43-166">Place the catalog file inside the module folder.</span></span>
<span data-ttu-id="6ae43-167">Per convenzione, il file di catalogo del modulo deve trovarsi nella cartella del modulo con lo stesso nome di quest'ultimo.</span><span class="sxs-lookup"><span data-stu-id="6ae43-167">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

###<a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="6ae43-168">Impostazioni LocalConfigurationManager per l'abilitazione delle convalide delle firme</span><span class="sxs-lookup"><span data-stu-id="6ae43-168">LocalConfigurationManager settings to enable signing validations</span></span>

####<a name="pull"></a><span data-ttu-id="6ae43-169">Pull</span><span class="sxs-lookup"><span data-stu-id="6ae43-169">Pull</span></span>
<span data-ttu-id="6ae43-170">La risorsa LocalConfigurationManager di un nodo esegue la convalida delle firme di moduli e configurazioni in base alle impostazioni correnti.</span><span class="sxs-lookup"><span data-stu-id="6ae43-170">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span>
<span data-ttu-id="6ae43-171">Per impostazione predefinita, la convalida delle firme è disabilitata.</span><span class="sxs-lookup"><span data-stu-id="6ae43-171">By default, signature validation is disabled.</span></span>
<span data-ttu-id="6ae43-172">La convalida delle firme può essere abilitata aggiungendo il blocco 'SignatureValidation' alla definizione della metaconfigurazione del nodo, come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="6ae43-172">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'
    }

    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # By default, LCM uses the default Windows trusted publisher store to validate the certificate chain. If TrustedStorePath property is specified, LCM uses this custom store for retrieving the trusted publishers to validate the content.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
 ```

<span data-ttu-id="6ae43-173">L'impostazione della metaconfigurazione precedente in un nodo abilita la convalida delle firme nelle configurazioni e nei moduli scaricati.</span><span class="sxs-lookup"><span data-stu-id="6ae43-173">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span>
<span data-ttu-id="6ae43-174">Gestione configurazione locale esegue i passaggi seguenti per verificare le firme digitali.</span><span class="sxs-lookup"><span data-stu-id="6ae43-174">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="6ae43-175">Verifica che la firma in un file di configurazione (file MOF) sia valida.</span><span class="sxs-lookup"><span data-stu-id="6ae43-175">Verify the signature on a configuration file (.MOF) is valid.</span></span>
   <span data-ttu-id="6ae43-176">Usa il cmdlet di PowerShell [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) che è stato esteso nella versione 5.1 per il supporto della convalida delle firme dei file MOF.</span><span class="sxs-lookup"><span data-stu-id="6ae43-176">It uses the PowerShell cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), which is extended in 5.1 to support MOF signature validation.</span></span>
2. <span data-ttu-id="6ae43-177">Verifica che l'autorità di certificazione che ha autorizzato il firmatario sia attendibile.</span><span class="sxs-lookup"><span data-stu-id="6ae43-177">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="6ae43-178">Scarica le dipendenze del modulo/risorsa della configurazione in un percorso temporaneo.</span><span class="sxs-lookup"><span data-stu-id="6ae43-178">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="6ae43-179">Verifica la firma del catalogo incluso all'interno del modulo.</span><span class="sxs-lookup"><span data-stu-id="6ae43-179">Verify the signature of the catalog included inside the module.</span></span>
    * <span data-ttu-id="6ae43-180">Individua un file `<moduleName>.cat` e ne verifica la firma usando il cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span><span class="sxs-lookup"><span data-stu-id="6ae43-180">Find a `<moduleName>.cat` file and verify its signature using the cmdlet  [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span></span>
    * <span data-ttu-id="6ae43-181">Verifica che l'autorità di certificazione che ha autenticato il firmatario sia attendibile.</span><span class="sxs-lookup"><span data-stu-id="6ae43-181">Verify the certification authority that authenticated the signer is trusted.</span></span>
    * <span data-ttu-id="6ae43-182">Usando il nuovo cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) verifica che il contenuto dei moduli non sia stato manomesso.</span><span class="sxs-lookup"><span data-stu-id="6ae43-182">Verify the content of the modules has not been tampered using the new cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span></span>
5. <span data-ttu-id="6ae43-183">Installa il modulo in $env:ProgramFiles\WindowsPowerShell\Modules\\</span><span class="sxs-lookup"><span data-stu-id="6ae43-183">Install-Module to $env:ProgramFiles\WindowsPowerShell\Modules\\</span></span>
6. <span data-ttu-id="6ae43-184">Configurazione del processo</span><span class="sxs-lookup"><span data-stu-id="6ae43-184">Process configuration</span></span>

> <span data-ttu-id="6ae43-185">Nota: la convalida della firma nel catalogo del modulo e nella configurazione viene eseguita solo quando la configurazione viene applicata al sistema per la prima volta o quando il modulo viene scaricato e installato.</span><span class="sxs-lookup"><span data-stu-id="6ae43-185">Note: Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
<span data-ttu-id="6ae43-186">I controlli di coerenza non convalidano la firma di Current.mof o le dipendenze del modulo.</span><span class="sxs-lookup"><span data-stu-id="6ae43-186">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span>
<span data-ttu-id="6ae43-187">Se la verifica ha esito negativo in una fase, ad esempio se la configurazione di cui viene eseguito il pull dal server di pull non è firmata, l'elaborazione della configurazione viene terminata con l'errore riportato di seguito e vengono eliminati tutti i file temporanei.</span><span class="sxs-lookup"><span data-stu-id="6ae43-187">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Configurazione di output degli errori di esempio](../images/PullUnsignedConfigFail.png)

<span data-ttu-id="6ae43-189">Analogamente, il pull di un modulo il cui catalogo non è firmato causa l'errore seguente:</span><span class="sxs-lookup"><span data-stu-id="6ae43-189">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Modulo di output degli errori di esempio](../images/PullUnisgnedCatalog.png)

####<a name="push"></a><span data-ttu-id="6ae43-191">Push</span><span class="sxs-lookup"><span data-stu-id="6ae43-191">Push</span></span>
<span data-ttu-id="6ae43-192">Una configurazione inviata mediante push potrebbe essere alterata in origine prima che venga recapitata al nodo.</span><span class="sxs-lookup"><span data-stu-id="6ae43-192">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span>
<span data-ttu-id="6ae43-193">Gestione configurazione locale esegue passaggi di convalida della firma simili per le configurazioni pubblicate o di cui è stato eseguito il push.</span><span class="sxs-lookup"><span data-stu-id="6ae43-193">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span>
<span data-ttu-id="6ae43-194">Di seguito è riportato un esempio completo di convalida della firma per il push.</span><span class="sxs-lookup"><span data-stu-id="6ae43-194">Below is a complete example of signature validation for push.</span></span>

* <span data-ttu-id="6ae43-195">Abilitazione della convalida delle firme nel nodo.</span><span class="sxs-lookup"><span data-stu-id="6ae43-195">Enable signature validation on the node.</span></span>

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PUSH'
    }
    SignatureValidation validations{
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType =  'Configuration','Module'
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```
* <span data-ttu-id="6ae43-196">Creazione di un file di configurazione di esempio.</span><span class="sxs-lookup"><span data-stu-id="6ae43-196">Create a sample configuration file.</span></span>

```powershell
# Sample configuration
Configuration Test
{

    File foo
    {
        DestinationPath =  "$env:TEMP\signingTest.txt"
        Contents = "ABC"
    }
}
Test
```

* <span data-ttu-id="6ae43-197">Tentativo di push del file di configurazione non firmato nel nodo.</span><span class="sxs-lookup"><span data-stu-id="6ae43-197">Try pushing the unsigned configuration file in to the node.</span></span>

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
```
![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

* <span data-ttu-id="6ae43-199">Firma del file di configurazione con il certificato di firma del codice.</span><span class="sxs-lookup"><span data-stu-id="6ae43-199">Sign the configuration file using code-signing certificate.</span></span>

![SignMofFile](../images/SignMofFile.png)

* <span data-ttu-id="6ae43-201">Tentativo di push del file MOF firmato.</span><span class="sxs-lookup"><span data-stu-id="6ae43-201">Try pushing the signed MOF file.</span></span>

![SignMofFile](../images/PushSignedMof.png)