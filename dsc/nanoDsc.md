---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Uso di DSC in Nano Server
ms.openlocfilehash: 9e26c525b48e8656a3479db9c0a760eaeb8cf58a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="72b4d-103">Uso di DSC in Nano Server</span><span class="sxs-lookup"><span data-stu-id="72b4d-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="72b4d-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="72b4d-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="72b4d-105">**DSC on Nano Server** (DSC su Nano Server) è un pacchetto opzionale contenuto nella cartella `NanoServer\Packages` del supporto Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="72b4d-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="72b4d-106">Il pacchetto può essere installato durante la creazione di un disco rigido virtuale per un Nano Server, specificando **Microsoft-NanoServer-DSC-Package** come valore del parametro **Packages** della funzione**New-NanoServerImage**.</span><span class="sxs-lookup"><span data-stu-id="72b4d-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="72b4d-107">Se ad esempio si sta creando un disco rigido virtuale per una macchina virtuale, il comando potrebbe essere simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="72b4d-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="72b4d-108">Per informazioni sull'installazione e l'uso di Nano Server e su come gestire Nano Server con la comunicazione remota di PowerShell, vedere [Getting Started with Nano Server](https://technet.microsoft.com/library/mt126167.aspx) (Guida introduttiva a Nano Server).</span><span class="sxs-lookup"><span data-stu-id="72b4d-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](https://technet.microsoft.com/library/mt126167.aspx).</span></span>


## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="72b4d-109">Funzionalità DSC disponibili su Nano Server</span><span class="sxs-lookup"><span data-stu-id="72b4d-109">DSC features available on Nano Server</span></span>

 <span data-ttu-id="72b4d-110">Poiché Nano Server supporta solo un set limitato di API rispetto a una versione completa di Windows Server, al momento DSC on Nano Server (DSC su Nano Server) non offre parità funzionale completa con DSC in esecuzione su SKU completi.</span><span class="sxs-lookup"><span data-stu-id="72b4d-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="72b4d-111">DSC on Nano Server (DSC su Nano Server) è in fase di sviluppo attivo e non è ancora completo di tutte le funzionalità.</span><span class="sxs-lookup"><span data-stu-id="72b4d-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

 <span data-ttu-id="72b4d-112">Le funzionalità DSC seguenti sono attualmente disponibili in Nano Server:</span><span class="sxs-lookup"><span data-stu-id="72b4d-112">The following DSC features are currently available on Nano Server:</span></span>


* <span data-ttu-id="72b4d-113">Modalità push e pull</span><span class="sxs-lookup"><span data-stu-id="72b4d-113">Both push and pull modes</span></span>

* <span data-ttu-id="72b4d-114">Tutti i cmdlet DSC presenti in una versione completa di Windows Server, inclusi i seguenti:</span><span class="sxs-lookup"><span data-stu-id="72b4d-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
  * [<span data-ttu-id="72b4d-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="72b4d-115">Get-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/library/dn407378.aspx)
  * [<span data-ttu-id="72b4d-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="72b4d-116">Set-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/library/dn521621.aspx)
  * [<span data-ttu-id="72b4d-117">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="72b4d-117">Enable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [<span data-ttu-id="72b4d-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="72b4d-118">Disable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517872.aspx)
  * [<span data-ttu-id="72b4d-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="72b4d-119">Start-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [<span data-ttu-id="72b4d-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="72b4d-120">Stop-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [<span data-ttu-id="72b4d-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="72b4d-121">Get-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [<span data-ttu-id="72b4d-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="72b4d-122">Test-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407382.aspx)
  * [<span data-ttu-id="72b4d-123">Publish-DscConfiguraiton</span><span class="sxs-lookup"><span data-stu-id="72b4d-123">Publish-DscConfiguraiton</span></span>](https://technet.microsoft.com/en-us/library/mt517875.aspx)
  * [<span data-ttu-id="72b4d-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="72b4d-124">Update-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [<span data-ttu-id="72b4d-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="72b4d-125">Restore-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [<span data-ttu-id="72b4d-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="72b4d-126">Remove-DscConfigurationDocument</span></span>](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [<span data-ttu-id="72b4d-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="72b4d-127">Get-DscConfigurationStatus</span></span>](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [<span data-ttu-id="72b4d-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="72b4d-128">Invoke-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [<span data-ttu-id="72b4d-129">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="72b4d-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [<span data-ttu-id="72b4d-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="72b4d-130">Get-DscResource</span></span>](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [<span data-ttu-id="72b4d-131">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="72b4d-131">New-DscChecksum</span></span>](https://technet.microsoft.com/en-us/library/dn521622.aspx)

* <span data-ttu-id="72b4d-132">Compilazione di configurazioni. Vedere [Configurazioni DSC](configurations.md)</span><span class="sxs-lookup"><span data-stu-id="72b4d-132">Compiling configurations (see [DSC configurations](configurations.md))</span></span>

  <span data-ttu-id="72b4d-133">**Problema:** la crittografia delle password durante la compilazione della configurazione non funziona. Vedere [Protezione del file MOF](securemof.md)</span><span class="sxs-lookup"><span data-stu-id="72b4d-133">**Issue:** Password encryption (see [Securing the MOF File](securemof.md)) during configuration compilation doesn't work.</span></span>

* <span data-ttu-id="72b4d-134">Compilazione di metaconfigurazioni. Vedere [Configurazione di Gestione configurazione locale](metaConfig.md)</span><span class="sxs-lookup"><span data-stu-id="72b4d-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](metaConfig.md))</span></span>

* <span data-ttu-id="72b4d-135">Esecuzione di una risorsa nel contesto utente. Vedere [Esecuzione di DSC con le credenziali dell'utente](runAsUser.md)</span><span class="sxs-lookup"><span data-stu-id="72b4d-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](runAsUser.md))</span></span>

* <span data-ttu-id="72b4d-136">Risorse basate su classi. Vedere [Scrittura di una risorsa DSC personalizzata con classi di PowerShell](authoringResourceClass.md)</span><span class="sxs-lookup"><span data-stu-id="72b4d-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](authoringResourceClass.md))</span></span>

* <span data-ttu-id="72b4d-137">Debug di risorse DSC. Vedere [Debug di risorse DSC](debugresource.md)</span><span class="sxs-lookup"><span data-stu-id="72b4d-137">Debugging of DSC resources (see [Debugging DSC resources](debugresource.md))</span></span>

  <span data-ttu-id="72b4d-138">**Problema:** non funziona se una risorsa usa PsDscRunAsCredential. Vedere [Esecuzione di DSC con le credenziali dell'utente](runAsUser.md)</span><span class="sxs-lookup"><span data-stu-id="72b4d-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](runAsUser.md))</span></span>

* [<span data-ttu-id="72b4d-139">Specifica delle dipendenze tra nodi</span><span class="sxs-lookup"><span data-stu-id="72b4d-139">Specifying cross-node dependencies</span></span>](crossNodeDependencies.md)

* [<span data-ttu-id="72b4d-140">Controllo delle versioni delle risorse</span><span class="sxs-lookup"><span data-stu-id="72b4d-140">Resource versioning</span></span>](sxsResource.md)

* <span data-ttu-id="72b4d-141">Client di pull, configurazione e risorse. Vedere [Configurazione di un client di pull usando nomi di configurazione](pullClientConfigNames.md)</span><span class="sxs-lookup"><span data-stu-id="72b4d-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](pullClientConfigNames.md))</span></span>

* [<span data-ttu-id="72b4d-142">Configurazioni parziali (pull e push)</span><span class="sxs-lookup"><span data-stu-id="72b4d-142">Partial configurations (pull & push)</span></span>](partialConfigs.md)

* [<span data-ttu-id="72b4d-143">Segnalazione a un server di pull</span><span class="sxs-lookup"><span data-stu-id="72b4d-143">Reporting to pull server</span></span>](reportServer.md)

* <span data-ttu-id="72b4d-144">Crittografia MOF</span><span class="sxs-lookup"><span data-stu-id="72b4d-144">MOF encryption</span></span>

* <span data-ttu-id="72b4d-145">Registrazione degli eventi</span><span class="sxs-lookup"><span data-stu-id="72b4d-145">Event logging</span></span>

* <span data-ttu-id="72b4d-146">Creazione di report DSC di Automazione di Azure</span><span class="sxs-lookup"><span data-stu-id="72b4d-146">Azure Automation DSC reporting</span></span>

* <span data-ttu-id="72b4d-147">Risorse completamente funzionanti</span><span class="sxs-lookup"><span data-stu-id="72b4d-147">Resources that are fully functional</span></span>
  * [<span data-ttu-id="72b4d-148">Archive</span><span class="sxs-lookup"><span data-stu-id="72b4d-148">Archive</span></span>](archiveResource.md)
  * [<span data-ttu-id="72b4d-149">Environment</span><span class="sxs-lookup"><span data-stu-id="72b4d-149">Environment</span></span>](environmentResource.md)
  * [<span data-ttu-id="72b4d-150">File</span><span class="sxs-lookup"><span data-stu-id="72b4d-150">File</span></span>](fileResource.md)
  * [<span data-ttu-id="72b4d-151">Log</span><span class="sxs-lookup"><span data-stu-id="72b4d-151">Log</span></span>](logResource.md)
  * <span data-ttu-id="72b4d-152">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="72b4d-152">ProcessSet</span></span>
  * [<span data-ttu-id="72b4d-153">Registry</span><span class="sxs-lookup"><span data-stu-id="72b4d-153">Registry</span></span>](registryResource.md)
  * [<span data-ttu-id="72b4d-154">Script</span><span class="sxs-lookup"><span data-stu-id="72b4d-154">Script</span></span>](scriptResource.md)
  * <span data-ttu-id="72b4d-155">WindowsPackageCab</span><span class="sxs-lookup"><span data-stu-id="72b4d-155">WindowsPackageCab</span></span>
  * [<span data-ttu-id="72b4d-156">WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="72b4d-156">WindowsProcess</span></span>](windowsProcessResource.md)
  * <span data-ttu-id="72b4d-157">WaitForAll. Vedere [Specifica delle dipendenze tra nodi](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="72b4d-157">WaitForAll (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="72b4d-158">WaitForAny. Vedere [Specifica delle dipendenze tra nodi](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="72b4d-158">WaitForAny (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="72b4d-159">WaitForSome. Vedere [Specifica delle dipendenze tra nodi](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="72b4d-159">WaitForSome (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>

* <span data-ttu-id="72b4d-160">Risorse parzialmente funzionanti</span><span class="sxs-lookup"><span data-stu-id="72b4d-160">Resources that are partially functional</span></span>
  * [<span data-ttu-id="72b4d-161">Gruppo</span><span class="sxs-lookup"><span data-stu-id="72b4d-161">Group</span></span>](groupResource.md)
  * <span data-ttu-id="72b4d-162">GroupSet</span><span class="sxs-lookup"><span data-stu-id="72b4d-162">GroupSet</span></span>

  <span data-ttu-id="72b4d-163">**Problema:** le risorse indicate sopra non funzionano se l'istanza specifica viene chiamata due volte, vale a dire se la stessa configurazione viene eseguita due volte</span><span class="sxs-lookup"><span data-stu-id="72b4d-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

  * [<span data-ttu-id="72b4d-164">Service</span><span class="sxs-lookup"><span data-stu-id="72b4d-164">Service</span></span>](serviceResource.md)
  * <span data-ttu-id="72b4d-165">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="72b4d-165">ServiceSet</span></span>

  <span data-ttu-id="72b4d-166">**Problema:** funziona solo per l'avvio/arresto del servizio (stato).</span><span class="sxs-lookup"><span data-stu-id="72b4d-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="72b4d-167">Non funziona se si tenta di modificare altri attributi del servizi, come startuptype, credentials, description e così via.</span><span class="sxs-lookup"><span data-stu-id="72b4d-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="72b4d-168">L'errore generato è simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="72b4d-168">The error thrown is similar to:</span></span>

  <span data-ttu-id="72b4d-169">*Impossibile trovare il tipo [management.managementobject]: verificare che l'assembly contenente questo tipo sia caricato.*</span><span class="sxs-lookup"><span data-stu-id="72b4d-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>

* <span data-ttu-id="72b4d-170">Risorse non funzionanti</span><span class="sxs-lookup"><span data-stu-id="72b4d-170">Resources that are not functional</span></span>
  * [<span data-ttu-id="72b4d-171">User</span><span class="sxs-lookup"><span data-stu-id="72b4d-171">User</span></span>](userResource.md)


## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="72b4d-172">Funzionalità DSC non disponibili su Nano Server</span><span class="sxs-lookup"><span data-stu-id="72b4d-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="72b4d-173">Le funzionalità DSC seguenti sono attualmente non disponibili in Nano Server:</span><span class="sxs-lookup"><span data-stu-id="72b4d-173">The following DSC features are not currently available on Nano Server:</span></span>

* <span data-ttu-id="72b4d-174">Decrittografia del documento MOF con password crittografate</span><span class="sxs-lookup"><span data-stu-id="72b4d-174">Decrypting MOF document with encrypted password(s)</span></span>
* <span data-ttu-id="72b4d-175">Server di pull: attualmente non è possibile impostare un server di pull su Nano Server</span><span class="sxs-lookup"><span data-stu-id="72b4d-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
* <span data-ttu-id="72b4d-176">Tutte le funzioni non presenti nel relativo elenco sono disponibili</span><span class="sxs-lookup"><span data-stu-id="72b4d-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="72b4d-177">Uso di risorse DSC personalizzate su Nano Server</span><span class="sxs-lookup"><span data-stu-id="72b4d-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="72b4d-178">A causa di un set limitato di API Windows e alle librerie CLR disponibili in Nano Server, le risorse DSC che funzionano sulla versione CLR completa di Windows non funzionano necessariamente anche su Nano server.</span><span class="sxs-lookup"><span data-stu-id="72b4d-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="72b4d-179">Eseguire un test completo prima di distribuire le risorse DSC personalizzate in un ambiente di produzione.</span><span class="sxs-lookup"><span data-stu-id="72b4d-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="72b4d-180">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="72b4d-180">See Also</span></span>
- [<span data-ttu-id="72b4d-181">Guida introduttiva a Nano Server</span><span class="sxs-lookup"><span data-stu-id="72b4d-181">Getting Started with Nano Server</span></span>](https://technet.microsoft.com/library/mt126167.aspx)