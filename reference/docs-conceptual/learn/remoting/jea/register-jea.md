---
ms.date: 07/10/2019
keywords: jea,powershell,sicurezza
title: Registrazione delle configurazioni JEA
ms.openlocfilehash: c85eddea2196e4db4bbeea54bde11074f3d1c927
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017712"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="d58b6-103">Registrazione delle configurazioni JEA</span><span class="sxs-lookup"><span data-stu-id="d58b6-103">Registering JEA Configurations</span></span>

<span data-ttu-id="d58b6-104">Dopo aver creato le [funzionalità del ruolo](role-capabilities.md) e i [file di configurazione della sessione](session-configurations.md), l'ultimo passaggio consiste nel registrare l'endpoint JEA.</span><span class="sxs-lookup"><span data-stu-id="d58b6-104">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step is to register the JEA endpoint.</span></span> <span data-ttu-id="d58b6-105">La registrazione dell'endpoint JEA nel sistema rende l'endpoint disponibile per l'uso da parte degli utenti e dei motori di automazione.</span><span class="sxs-lookup"><span data-stu-id="d58b6-105">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="d58b6-106">Configurazione di un computer singolo</span><span class="sxs-lookup"><span data-stu-id="d58b6-106">Single machine configuration</span></span>

<span data-ttu-id="d58b6-107">Per gli ambienti di piccole dimensioni, è possibile distribuire JEA registrando il file di configurazione sessione tramite il cmdlet [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration).</span><span class="sxs-lookup"><span data-stu-id="d58b6-107">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="d58b6-108">Prima di iniziare, verificare che siano soddisfatti i prerequisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="d58b6-108">Before you begin, ensure that the following prerequisites have been met:</span></span>

- <span data-ttu-id="d58b6-109">Sono stati creati uno o più ruoli e inseriti nella cartella **RoleCapabilities** di un modulo di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d58b6-109">One or more roles has been created and placed in the **RoleCapabilities** folder of a PowerShell module.</span></span>
- <span data-ttu-id="d58b6-110">È stato creato e verificato un file di configurazione sessione.</span><span class="sxs-lookup"><span data-stu-id="d58b6-110">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="d58b6-111">L'utente che registra la configurazione JEA ha diritti di amministratore nel sistema.</span><span class="sxs-lookup"><span data-stu-id="d58b6-111">The user registering the JEA configuration has administrator rights on the system.</span></span>
- <span data-ttu-id="d58b6-112">È stato selezionato un nome per l'endpoint JEA.</span><span class="sxs-lookup"><span data-stu-id="d58b6-112">You've selected a name for your JEA endpoint.</span></span>

<span data-ttu-id="d58b6-113">Il nome dell'endpoint JEA viene richiesto quando gli utenti si connettono al sistema tramite JEA.</span><span class="sxs-lookup"><span data-stu-id="d58b6-113">The name of the JEA endpoint is required when users connect to the system using JEA.</span></span> <span data-ttu-id="d58b6-114">Il cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) visualizza un elenco dei nomi degli endpoint di un sistema.</span><span class="sxs-lookup"><span data-stu-id="d58b6-114">The [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet lists the names of the endpoints on a system.</span></span> <span data-ttu-id="d58b6-115">Gli endpoint che iniziano con `microsoft` sono in genere inclusi in Windows.</span><span class="sxs-lookup"><span data-stu-id="d58b6-115">Endpoints that start with `microsoft` are typically shipped with Windows.</span></span> <span data-ttu-id="d58b6-116">L'endpoint `microsoft.powershell` è l'endpoint predefinito usato per la connessione a un endpoint di PowerShell remoto.</span><span class="sxs-lookup"><span data-stu-id="d58b6-116">The `microsoft.powershell` endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="d58b6-117">Eseguire il comando seguente per registrare l'endpoint.</span><span class="sxs-lookup"><span data-stu-id="d58b6-117">Run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="d58b6-118">Il comando precedente riavvia il servizio WinRM nel sistema.</span><span class="sxs-lookup"><span data-stu-id="d58b6-118">The previous command restarts the WinRM service on the system.</span></span> <span data-ttu-id="d58b6-119">Questo comando termina tutte le sessioni di comunicazione remota di PowerShell ed eventuali configurazioni DSC in corso.</span><span class="sxs-lookup"><span data-stu-id="d58b6-119">This terminates all PowerShell remoting sessions and any ongoing DSC configurations.</span></span> <span data-ttu-id="d58b6-120">Per evitare di interrompere le operazioni aziendali in corso, è consigliabile che i computer di produzione siano offline prima di eseguire il comando.</span><span class="sxs-lookup"><span data-stu-id="d58b6-120">We recommended you take production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="d58b6-121">Dopo la registrazione, sarà possibile [usare JEA](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="d58b6-121">After registration, you're ready to [use JEA](using-jea.md).</span></span> <span data-ttu-id="d58b6-122">È possibile eliminare il file di configurazione della sessione in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="d58b6-122">You may delete the session configuration file at any time.</span></span> <span data-ttu-id="d58b6-123">Il file di configurazione non viene usato dopo la registrazione dell'endpoint.</span><span class="sxs-lookup"><span data-stu-id="d58b6-123">The configuration file isn't used after registration of the endpoint.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="d58b6-124">Configurazione di più computer con DSC</span><span class="sxs-lookup"><span data-stu-id="d58b6-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="d58b6-125">Quando si distribuisce JEA su più computer, il modello di distribuzione più semplice consiste nell'usare la risorsa [Desired State Configuration (DSC)](/powershell/dsc/overview) di JEA per distribuire rapidamente e in modo coerente JEA in ogni computer.</span><span class="sxs-lookup"><span data-stu-id="d58b6-125">When deploying JEA on multiple machines, the simplest deployment model uses the JEA [Desired State Configuration (DSC)](/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="d58b6-126">Per distribuire JEA con DSC, assicurarsi che siano soddisfatti i prerequisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="d58b6-126">To deploy JEA with DSC, ensure the following prerequisites are met:</span></span>

- <span data-ttu-id="d58b6-127">Sono state create una o più funzionalità del ruolo e aggiunte a un modulo di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d58b6-127">One or more role capabilities have been authored and added to a PowerShell module.</span></span>
- <span data-ttu-id="d58b6-128">Il modulo di PowerShell che contiene i ruoli è archiviato in una condivisione di file (sola lettura) accessibile da ogni computer.</span><span class="sxs-lookup"><span data-stu-id="d58b6-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="d58b6-129">Le impostazioni per la configurazione sessione sono state determinate.</span><span class="sxs-lookup"><span data-stu-id="d58b6-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="d58b6-130">Non è necessario creare un file di configurazione della sessione quando si usa la risorsa DSC di JEA.</span><span class="sxs-lookup"><span data-stu-id="d58b6-130">You don't need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="d58b6-131">Sono disponibili le credenziali che consentono di eseguire azioni amministrative in ogni computer o di accedere a un server di pull DSC usato per la gestione dei computer.</span><span class="sxs-lookup"><span data-stu-id="d58b6-131">You have credentials that allow administrative actions on each machine or access to the DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="d58b6-132">È stata scaricata la [risorsa DSC di JEA](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).</span><span class="sxs-lookup"><span data-stu-id="d58b6-132">You've downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).</span></span>

<span data-ttu-id="d58b6-133">Creare una configurazione DSC per l'endpoint JEA in un computer di destinazione o server di pull.</span><span class="sxs-lookup"><span data-stu-id="d58b6-133">Create a DSC configuration for your JEA endpoint on a target machine or pull server.</span></span> <span data-ttu-id="d58b6-134">In questa configurazione la risorsa DSC **JustEnoughAdministration** definisce il file di configurazione della sessione mentre la risorsa **File** copia le funzionalità di ruolo dalla condivisione file.</span><span class="sxs-lookup"><span data-stu-id="d58b6-134">In this configuration, the **JustEnoughAdministration** DSC resource defines the session configuration file and the **File** resource copies the role capabilities from the file share.</span></span>

<span data-ttu-id="d58b6-135">Le proprietà seguenti possono essere configurate tramite la risorsa DSC:</span><span class="sxs-lookup"><span data-stu-id="d58b6-135">The following properties are configurable using the DSC resource:</span></span>

- <span data-ttu-id="d58b6-136">Definizioni dei ruoli</span><span class="sxs-lookup"><span data-stu-id="d58b6-136">Role Definitions</span></span>
- <span data-ttu-id="d58b6-137">Gruppi di account virtuali</span><span class="sxs-lookup"><span data-stu-id="d58b6-137">Virtual account groups</span></span>
- <span data-ttu-id="d58b6-138">Nome account del servizio gestito del gruppo</span><span class="sxs-lookup"><span data-stu-id="d58b6-138">Group-managed service account name</span></span>
- <span data-ttu-id="d58b6-139">Directory delle trascrizioni</span><span class="sxs-lookup"><span data-stu-id="d58b6-139">Transcript directory</span></span>
- <span data-ttu-id="d58b6-140">Unità utente</span><span class="sxs-lookup"><span data-stu-id="d58b6-140">User drive</span></span>
- <span data-ttu-id="d58b6-141">Regole di accesso condizionale</span><span class="sxs-lookup"><span data-stu-id="d58b6-141">Conditional access rules</span></span>
- <span data-ttu-id="d58b6-142">Script di avvio per la sessione JEA</span><span class="sxs-lookup"><span data-stu-id="d58b6-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="d58b6-143">La sintassi per ognuna di queste proprietà in una configurazione DSC è coerente con il file di configurazione sessione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d58b6-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="d58b6-144">Di seguito è riportato un esempio di configurazione DSC per un modulo di manutenzione generale del server.</span><span class="sxs-lookup"><span data-stu-id="d58b6-144">Below is a sample DSC configuration for a general server maintenance module.</span></span> <span data-ttu-id="d58b6-145">Si presuppone che un modulo valido di PowerShell che contiene le funzionalità di ruolo sia disponibile nella condivisione file `\\myfileshare\JEA`.</span><span class="sxs-lookup"><span data-stu-id="d58b6-145">It assumes that a valid PowerShell module containing role capabilities is located on the `\\myfileshare\JEA` file share.</span></span>

```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

<span data-ttu-id="d58b6-146">La configurazione viene quindi applicata in un sistema chiamando direttamente [Gestione configurazione locale](/powershell/dsc/managing-nodes/metaConfig) o aggiornando la [configurazione del server di pull](/powershell/dsc/pull-server/pullServer).</span><span class="sxs-lookup"><span data-stu-id="d58b6-146">Next, the configuration is applied on a system by directly invoking the [Local Configuration Manager](/powershell/dsc/managing-nodes/metaConfig) or updating the [pull server configuration](/powershell/dsc/pull-server/pullServer).</span></span>

<span data-ttu-id="d58b6-147">La risorsa DSC consente anche di sostituire l'endpoint **Microsoft.PowerShell** predefinito.</span><span class="sxs-lookup"><span data-stu-id="d58b6-147">The DSC resource also allows you to replace the default **Microsoft.PowerShell** endpoint.</span></span> <span data-ttu-id="d58b6-148">Quando viene eseguita la sostituzione, la risorsa registra automaticamente un endpoint di backup denominato **Microsoft.PowerShell.Restricted**.</span><span class="sxs-lookup"><span data-stu-id="d58b6-148">When replaced, the resource automatically registers a backup endpoint named **Microsoft.PowerShell.Restricted**.</span></span> <span data-ttu-id="d58b6-149">L'endpoint di backup ha un elenco di controllo di accesso WinRM predefinito che offre l'accesso agli utenti di gestione remota e ai membri del gruppo Amministratori locali.</span><span class="sxs-lookup"><span data-stu-id="d58b6-149">The backup endpoint has the default WinRM ACL that allows Remote Management Users and local Administrators group members to access it.</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="d58b6-150">Annullamento delle configurazioni JEA</span><span class="sxs-lookup"><span data-stu-id="d58b6-150">Unregistering JEA configurations</span></span>

<span data-ttu-id="d58b6-151">Il cmdlet [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) rimuove un endpoint JEA.</span><span class="sxs-lookup"><span data-stu-id="d58b6-151">The [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet removes a JEA endpoint.</span></span> <span data-ttu-id="d58b6-152">L'annullamento della registrazione di un endpoint JEA impedisce ai nuovi utenti di creare sessioni JEA nuove nel sistema.</span><span class="sxs-lookup"><span data-stu-id="d58b6-152">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span> <span data-ttu-id="d58b6-153">Ciò consente anche di aggiornare una configurazione JEA registrando di nuovo un file di configurazione sessione aggiornato con lo stesso nome di endpoint.</span><span class="sxs-lookup"><span data-stu-id="d58b6-153">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="d58b6-154">L'annullamento della registrazione di un endpoint JEA causa il riavvio del servizio WinRM.</span><span class="sxs-lookup"><span data-stu-id="d58b6-154">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span> <span data-ttu-id="d58b6-155">Questa operazione interrompe la maggior parte delle operazioni di gestione remota in corso, incluse altre sessioni di PowerShell, le chiamate WMI e alcuni strumenti di gestione.</span><span class="sxs-lookup"><span data-stu-id="d58b6-155">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span> <span data-ttu-id="d58b6-156">Annullare solo la registrazione degli endpoint di PowerShell nelle finestre di manutenzione pianificata.</span><span class="sxs-lookup"><span data-stu-id="d58b6-156">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d58b6-157">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="d58b6-157">Next steps</span></span>

[<span data-ttu-id="d58b6-158">Testare l'endpoint JEA</span><span class="sxs-lookup"><span data-stu-id="d58b6-158">Test the JEA endpoint</span></span>](using-jea.md)
