---
ms.date: 06/12/2017
keywords: jea,powershell,sicurezza
title: Registrazione delle configurazioni JEA
ms.openlocfilehash: 6fa0ce434c8e70eb718545e99417bfe034cda6bf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2019
ms.locfileid: "58059440"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="190a7-103">Registrazione delle configurazioni JEA</span><span class="sxs-lookup"><span data-stu-id="190a7-103">Registering JEA Configurations</span></span>

> <span data-ttu-id="190a7-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="190a7-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="190a7-105">Dopo aver creato le [funzionalità del ruolo](role-capabilities.md) e i [file di configurazione sessione](session-configurations.md), l'ultimo passaggio prima di poter usare JEA consiste nel registrare l'endpoint JEA.</span><span class="sxs-lookup"><span data-stu-id="190a7-105">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step before you can use JEA is to register the JEA endpoint.</span></span>
<span data-ttu-id="190a7-106">La registrazione dell'endpoint JEA nel sistema rende l'endpoint disponibile per l'uso da parte degli utenti e dei motori di automazione.</span><span class="sxs-lookup"><span data-stu-id="190a7-106">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="190a7-107">Configurazione di un computer singolo</span><span class="sxs-lookup"><span data-stu-id="190a7-107">Single machine configuration</span></span>

<span data-ttu-id="190a7-108">Per gli ambienti di piccole dimensioni, è possibile distribuire JEA registrando il file di configurazione sessione tramite il cmdlet [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration).</span><span class="sxs-lookup"><span data-stu-id="190a7-108">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="190a7-109">Prima di iniziare, verificare che siano soddisfatti i prerequisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="190a7-109">Before you begin, ensure that the following prerequisites have been met:</span></span>
- <span data-ttu-id="190a7-110">Sono stati creati uno o più ruoli e inseriti nella cartella "RoleCapabilities" di un modulo di PowerShell valido.</span><span class="sxs-lookup"><span data-stu-id="190a7-110">One or more roles has been created and placed in the 'RoleCapabilities' folder of a valid PowerShell module.</span></span>
- <span data-ttu-id="190a7-111">È stato creato e verificato un file di configurazione sessione.</span><span class="sxs-lookup"><span data-stu-id="190a7-111">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="190a7-112">L'utente che registra la configurazione JEA ha diritti di amministratore sui sistemi.</span><span class="sxs-lookup"><span data-stu-id="190a7-112">The user registering the JEA configuration has administrator rights on the system(s).</span></span>

<span data-ttu-id="190a7-113">È anche necessario selezionare un nome per l'endpoint JEA.</span><span class="sxs-lookup"><span data-stu-id="190a7-113">You also need to select a name for your JEA endpoint.</span></span>
<span data-ttu-id="190a7-114">Il nome dell'endpoint JEA è necessario quando gli utenti vogliono connettersi al sistema tramite JEA.</span><span class="sxs-lookup"><span data-stu-id="190a7-114">The name of the JEA endpoint is required when users want to connect to the system using JEA.</span></span>
<span data-ttu-id="190a7-115">È possibile usare il cmdlet [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) per verificare i nomi degli endpoint esistenti nel sistema.</span><span class="sxs-lookup"><span data-stu-id="190a7-115">You can use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet to check the names of existing endpoints on the system.</span></span>
<span data-ttu-id="190a7-116">Gli endpoint che iniziano con "microsoft" sono in genere inclusi in Windows.</span><span class="sxs-lookup"><span data-stu-id="190a7-116">Endpoints that start with 'microsoft' are typically shipped with Windows.</span></span>
<span data-ttu-id="190a7-117">L'endpoint "microsoft.powershell" è l'endpoint predefinito usato per la connessione a un endpoint di PowerShell remoto.</span><span class="sxs-lookup"><span data-stu-id="190a7-117">The 'microsoft.powershell' endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="190a7-118">Dopo aver definito un nome appropriato per l'endpoint JEA, eseguire il comando seguente per registrare l'endpoint.</span><span class="sxs-lookup"><span data-stu-id="190a7-118">When you have determined an appropriate name for your JEA endpoint, run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="190a7-119">Il comando riportato di sopra riavvia il servizio WinRM nel sistema.</span><span class="sxs-lookup"><span data-stu-id="190a7-119">The above command restarts the WinRM service on the system.</span></span>
> <span data-ttu-id="190a7-120">Questo comando termina tutte le sessioni di comunicazione remota di PowerShell e anche eventuali configurazioni DSC in corso.</span><span class="sxs-lookup"><span data-stu-id="190a7-120">This terminates all PowerShell remoting sessions as well as any ongoing DSC configurations.</span></span>
> <span data-ttu-id="190a7-121">Per evitare di interrompere operazioni aziendali in corso, è consigliabile che ogni computer di produzione sia offline prima di eseguire il comando.</span><span class="sxs-lookup"><span data-stu-id="190a7-121">It is recommended that you take any production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="190a7-122">Se la registrazione ha esito positivo, è possibile [usare JEA](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="190a7-122">If registration is successful, you are ready to [use JEA](using-jea.md).</span></span>
<span data-ttu-id="190a7-123">È possibile eliminare il file di configurazione sessione in qualsiasi momento perché non viene più usato dopo la registrazione dell'endpoint.</span><span class="sxs-lookup"><span data-stu-id="190a7-123">You may delete the session configuration file at any time; it is not used after registration of the end point.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="190a7-124">Configurazione di più computer con DSC</span><span class="sxs-lookup"><span data-stu-id="190a7-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="190a7-125">Se si distribuisce JEA su più computer, il modello di distribuzione più semplice consiste nell'usare la risorsa [Desired State Configuration (DSC)](https://msdn.microsoft.com/powershell/dsc/overview) di JEA per distribuire rapidamente e in modo coerente JEA in ogni computer.</span><span class="sxs-lookup"><span data-stu-id="190a7-125">If you are deploying JEA on multiple machines, the simplest deployment model is to use the JEA [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="190a7-126">Per distribuire JEA con DSC, è necessario assicurarsi che siano soddisfatti i prerequisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="190a7-126">To deploy JEA with DSC, you need to ensure the following prerequisites are met:</span></span>
- <span data-ttu-id="190a7-127">Sono state create una o più funzionalità del ruolo e aggiunte a un modulo di PowerShell valido.</span><span class="sxs-lookup"><span data-stu-id="190a7-127">One or more role capabilities have been authored and added to a valid PowerShell module.</span></span>
- <span data-ttu-id="190a7-128">Il modulo di PowerShell che contiene i ruoli è archiviato in una condivisione di file (sola lettura) accessibile da ogni computer.</span><span class="sxs-lookup"><span data-stu-id="190a7-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="190a7-129">Le impostazioni per la configurazione sessione sono state determinate.</span><span class="sxs-lookup"><span data-stu-id="190a7-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="190a7-130">Non è necessario creare un file di configurazione sessione quando si usa la risorsa DSC di JEA.</span><span class="sxs-lookup"><span data-stu-id="190a7-130">You do not need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="190a7-131">Sono disponibili le credenziali che consentono di eseguire azioni amministrative in ogni computer o di avere accesso a un server di pull DSC usato per gestire i computer.</span><span class="sxs-lookup"><span data-stu-id="190a7-131">You have credentials that allow you to perform administrative actions on each machine, or have access to a DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="190a7-132">È stata scaricata la [risorse DSC di JEA](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span><span class="sxs-lookup"><span data-stu-id="190a7-132">You have downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span></span>

<span data-ttu-id="190a7-133">In un computer di destinazione (o in un server di pull, se usato), creare una configurazione DSC per l'endpoint JEA.</span><span class="sxs-lookup"><span data-stu-id="190a7-133">On a target machine (or pull server, if you are using one), create a DSC configuration for your JEA endpoint.</span></span>
<span data-ttu-id="190a7-134">In questa configurazione, si usa la risorsa DSC di Just Enough Administration (JEA) per impostare il file di configurazione sessione e la risorsa File per copiare le funzionalità di ruolo dalla condivisione file.</span><span class="sxs-lookup"><span data-stu-id="190a7-134">In this configuration, you use the JustEnoughAdministration DSC resource to set up the session configuration file and the File resource to copy over the role capabilities from the file share.</span></span>

<span data-ttu-id="190a7-135">Le proprietà seguenti possono essere configurate tramite la risorsa DSC:</span><span class="sxs-lookup"><span data-stu-id="190a7-135">The following properties are configurable using the DSC resource:</span></span>
- <span data-ttu-id="190a7-136">Definizioni dei ruoli</span><span class="sxs-lookup"><span data-stu-id="190a7-136">Role Definitions</span></span>
- <span data-ttu-id="190a7-137">Gruppi di account virtuali</span><span class="sxs-lookup"><span data-stu-id="190a7-137">Virtual Account groups</span></span>
- <span data-ttu-id="190a7-138">Nome account del servizio gestito del gruppo</span><span class="sxs-lookup"><span data-stu-id="190a7-138">Group Managed Service Account name</span></span>
- <span data-ttu-id="190a7-139">Directory delle trascrizioni</span><span class="sxs-lookup"><span data-stu-id="190a7-139">Transcript directory</span></span>
- <span data-ttu-id="190a7-140">Unità utente</span><span class="sxs-lookup"><span data-stu-id="190a7-140">User drive</span></span>
- <span data-ttu-id="190a7-141">Regole di accesso condizionale</span><span class="sxs-lookup"><span data-stu-id="190a7-141">Conditional access rules</span></span>
- <span data-ttu-id="190a7-142">Script di avvio per la sessione JEA</span><span class="sxs-lookup"><span data-stu-id="190a7-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="190a7-143">La sintassi per ognuna di queste proprietà in una configurazione DSC è coerente con il file di configurazione sessione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="190a7-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="190a7-144">Di seguito è riportato un esempio di configurazione DSC per un modulo di manutenzione generale del server.</span><span class="sxs-lookup"><span data-stu-id="190a7-144">Below is a sample DSC configuration for a general server maintenance module.</span></span>

<span data-ttu-id="190a7-145">Si presuppone che un modulo valido di PowerShell che contiene le funzionalità del ruolo in una sottocartella "RoleCapabilities" si trovi nella condivisione file "\\\\myfileshare\\JEA".</span><span class="sxs-lookup"><span data-stu-id="190a7-145">It assumes that a valid PowerShell module containing role capabilities in a 'RoleCapabilities' subfolder is located on the '\\\\myfileshare\\JEA' file share.</span></span>


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

<span data-ttu-id="190a7-146">Questa configurazione può quindi essere applicata in un sistema [chiamando direttamente Gestione configurazione locale](https://msdn.microsoft.com/powershell/dsc/metaconfig) o aggiornando la [configurazione server di pull](https://msdn.microsoft.com/powershell/dsc/pullserver).</span><span class="sxs-lookup"><span data-stu-id="190a7-146">This configuration can then be applied on a system by [directly invoking the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig) or updating the [pull server configuration](https://msdn.microsoft.com/powershell/dsc/pullserver).</span></span>

<span data-ttu-id="190a7-147">La risorsa DSC consente anche di sostituire l'endpoint di comunicazione remota Microsoft.PowerShell predefinito.</span><span class="sxs-lookup"><span data-stu-id="190a7-147">The DSC resource also allows you to replace the default Microsoft.PowerShell remoting endpoint.</span></span>
<span data-ttu-id="190a7-148">In questo caso, la risorsa registra automaticamente un endpoint di backup senza vincoli denominato "Microsoft.PowerShell.Restricted" con il valore predefinito WinRM ACL, consentendo così ai membri del gruppo Utenti gestione remota e Administrators locale di accedere all'endpoint.</span><span class="sxs-lookup"><span data-stu-id="190a7-148">If you do this, the resource automatically registers a backup unconstrained endpoint named "Microsoft.PowerShell.Restricted" which has the default WinRM ACL (allowing Remote Management Users and local Administrators group members to access it).</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="190a7-149">Annullamento delle configurazioni JEA</span><span class="sxs-lookup"><span data-stu-id="190a7-149">Unregistering JEA configurations</span></span>

<span data-ttu-id="190a7-150">Per rimuovere un endpoint JEA da un sistema, usare il cmdlet [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration).</span><span class="sxs-lookup"><span data-stu-id="190a7-150">To remove a JEA endpoint on a system, use the [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span></span>
<span data-ttu-id="190a7-151">L'annullamento della registrazione di un endpoint JEA impedisce ai nuovi utenti di creare sessioni JEA nuove nel sistema.</span><span class="sxs-lookup"><span data-stu-id="190a7-151">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span>
<span data-ttu-id="190a7-152">Ciò consente anche di aggiornare una configurazione JEA registrando di nuovo un file di configurazione sessione aggiornato con lo stesso nome di endpoint.</span><span class="sxs-lookup"><span data-stu-id="190a7-152">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="190a7-153">L'annullamento della registrazione di un endpoint JEA causa il riavvio del servizio WinRM.</span><span class="sxs-lookup"><span data-stu-id="190a7-153">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span>
> <span data-ttu-id="190a7-154">Questa operazione interrompe la maggior parte delle operazioni di gestione remota in corso, incluse altre sessioni di PowerShell, le chiamate WMI e alcuni strumenti di gestione.</span><span class="sxs-lookup"><span data-stu-id="190a7-154">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span>
> <span data-ttu-id="190a7-155">Annullare solo la registrazione degli endpoint di PowerShell nelle finestre di manutenzione pianificata.</span><span class="sxs-lookup"><span data-stu-id="190a7-155">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="190a7-156">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="190a7-156">Next steps</span></span>

- [<span data-ttu-id="190a7-157">Testare l'endpoint JEA</span><span class="sxs-lookup"><span data-stu-id="190a7-157">Test the JEA endpoint</span></span>](using-jea.md)
