---
ms.date: 07/10/2019
keywords: jea,powershell,sicurezza
title: Uso di JEA
ms.openlocfilehash: 8f3cc9186c61a2ae5b64eb3dc4f72ca83f1a58c5
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017752"
---
# <a name="using-jea"></a><span data-ttu-id="be518-103">Uso di JEA</span><span class="sxs-lookup"><span data-stu-id="be518-103">Using JEA</span></span>

<span data-ttu-id="be518-104">Questo articolo illustra i vari modi in cui è possibile connettersi e usare un endpoint JEA.</span><span class="sxs-lookup"><span data-stu-id="be518-104">This article describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="be518-105">Uso interattivo di JEA</span><span class="sxs-lookup"><span data-stu-id="be518-105">Using JEA interactively</span></span>

<span data-ttu-id="be518-106">Se si esegue il test della configurazione JEA oppure se gli utenti devono eseguire attività semplici, è possibile usare JEA allo stesso modo di una normale sessione di comunicazione remota di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="be518-106">If you're testing your JEA configuration or have simple tasks for users, you can use JEA the same way you would a regular PowerShell remoting session.</span></span> <span data-ttu-id="be518-107">Per le attività di comunicazione remota complesse, è consigliabile usare la [comunicazione remota implicita](#using-jea-with-implicit-remoting).</span><span class="sxs-lookup"><span data-stu-id="be518-107">For complex remoting tasks, it's recommended to use [implicit remoting](#using-jea-with-implicit-remoting).</span></span> <span data-ttu-id="be518-108">La comunicazione remota implicita consente agli utenti di operare con gli oggetti dati in locale.</span><span class="sxs-lookup"><span data-stu-id="be518-108">Implicit remoting allows users to operate with the data objects locally.</span></span>

<span data-ttu-id="be518-109">Per usare JEA in modo interattivo, sono necessari:</span><span class="sxs-lookup"><span data-stu-id="be518-109">To use JEA interactively, you need:</span></span>

- <span data-ttu-id="be518-110">Il nome del computer a cui si è connessi (può essere il computer locale)</span><span class="sxs-lookup"><span data-stu-id="be518-110">The name of the computer you're connecting to (can be the local machine)</span></span>
- <span data-ttu-id="be518-111">Il nome dell'endpoint JEA registrato nel computer</span><span class="sxs-lookup"><span data-stu-id="be518-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="be518-112">Le credenziali che hanno accesso all'endpoint JEA nel computer</span><span class="sxs-lookup"><span data-stu-id="be518-112">Credentials that have access to the JEA endpoint on that computer</span></span>

<span data-ttu-id="be518-113">Con queste informazioni a disposizione, è possibile avviare una sessione JEA usando i cmdlet [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) o [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="be518-113">Given that information, you can start a JEA session using the [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlets.</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="be518-114">Se l'account utente corrente ha accesso all'endopoint JEA, è possibile omettere il parametro **Credential**.</span><span class="sxs-lookup"><span data-stu-id="be518-114">If the current user account has access to the JEA endpoint, you can omit the **Credential** parameter.</span></span>

<span data-ttu-id="be518-115">Quando il prompt di PowerShell diventa `[localhost]: PS>` indica che si sta interagendo con la sessione remota JEA.</span><span class="sxs-lookup"><span data-stu-id="be518-115">When the PowerShell prompt changes to `[localhost]: PS>` you know that you're now interacting with the remote JEA session.</span></span> <span data-ttu-id="be518-116">È possibile eseguire `Get-Command` per verificare i comandi disponibili.</span><span class="sxs-lookup"><span data-stu-id="be518-116">You can run `Get-Command` to check which commands are available.</span></span> <span data-ttu-id="be518-117">Contattare l'amministratore per verificare se sono presenti eventuali limitazioni per i parametri disponibili o per i valori dei parametri consentiti.</span><span class="sxs-lookup"><span data-stu-id="be518-117">Consult with your administrator to learn if there are any restrictions on the available parameters or allowed parameter values.</span></span>

<span data-ttu-id="be518-118">Tenere presente che le sessioni JEA operano in modalità NoLanguage.</span><span class="sxs-lookup"><span data-stu-id="be518-118">Remember, JEA sessions operate in NoLanguage mode.</span></span> <span data-ttu-id="be518-119">È possibile che alcuni dei metodi con cui si usa generalmente PowerShell non siano disponibili.</span><span class="sxs-lookup"><span data-stu-id="be518-119">Some of the ways you typically use PowerShell may not be available.</span></span> <span data-ttu-id="be518-120">Ad esempio, non è possibile usare variabili per archiviare i dati o controllare le proprietà degli oggetti restituiti dai cmdlet.</span><span class="sxs-lookup"><span data-stu-id="be518-120">For instance, you can't use variables to store data or inspect the properties on objects returned from cmdlets.</span></span> <span data-ttu-id="be518-121">L'esempio seguente illustra due approcci per ottenere gli stessi comandi per lavorare in modalità NoLanguage.</span><span class="sxs-lookup"><span data-stu-id="be518-121">The following example shows two approaches to get the same commands to work in NoLanguage mode.</span></span>

```powershell
# Using variables is prohibited in NoLanguage mode. The following will not work:
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# You can also use parameter sets that don't require extra data to be passed in
Start-VM -VMName 'SQL01'
```

<span data-ttu-id="be518-122">Per chiamate di comandi più complesse che rendono difficile questo approccio, è consigliabile usare la [comunicazione remota implicita](#using-jea-with-implicit-remoting) o [creare funzioni personalizzate](role-capabilities.md#creating-custom-functions) che eseguono il wrapping della funzionalità desiderata.</span><span class="sxs-lookup"><span data-stu-id="be518-122">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you require.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="be518-123">Uso di JEA con comunicazione remota implicita</span><span class="sxs-lookup"><span data-stu-id="be518-123">Using JEA with implicit remoting</span></span>

<span data-ttu-id="be518-124">PowerShell ha un modello di comunicazione remota implicita che consente di importare cmdlet del proxy da un computer remoto e usarli come comandi locali.</span><span class="sxs-lookup"><span data-stu-id="be518-124">PowerShell has an implicit remoting model that lets you import proxy cmdlets from a remote machine and interact with them as if they were local commands.</span></span> <span data-ttu-id="be518-125">La comunicazione remota implicita è descritta in questo**Hey, Scripting Guy!**</span><span class="sxs-lookup"><span data-stu-id="be518-125">Implicit remoting is explained in this **Hey, Scripting Guy!**</span></span> <span data-ttu-id="be518-126">[post di blog](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) indirizzato agli autori di script.</span><span class="sxs-lookup"><span data-stu-id="be518-126">[blog post](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="be518-127">La comunicazione remota implicita è utile quando si usa JEA perché consente di usare i cmdlet JEA in una modalità di linguaggio completa.</span><span class="sxs-lookup"><span data-stu-id="be518-127">Implicit remoting is useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span> <span data-ttu-id="be518-128">È possibile usare il completamento tramite TAB, le variabili, modificare oggetti e usare anche script locali per automatizzare le operazioni in un endpoint JEA.</span><span class="sxs-lookup"><span data-stu-id="be518-128">You can use tab completion, variables, manipulate objects, and even use local scripts to automate tasks against a JEA endpoint.</span></span> <span data-ttu-id="be518-129">Ogni volta che si chiama un comando proxy, i dati vengono inviati all'endpoint JEA nel computer remoto ed eseguiti nel computer.</span><span class="sxs-lookup"><span data-stu-id="be518-129">Anytime you invoke a proxy command, the data is sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="be518-130">La comunicazione remota implicita importa i cmdlet da una sessione di PowerShell esistente.</span><span class="sxs-lookup"><span data-stu-id="be518-130">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span> <span data-ttu-id="be518-131">Facoltativamente, è possibile anteporre ai sostantivi di ogni cmdlet del proxy una stringa a scelta.</span><span class="sxs-lookup"><span data-stu-id="be518-131">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing.</span></span> <span data-ttu-id="be518-132">Il prefisso consente di distinguere i comandi per il sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="be518-132">The prefix allows you to distinguish the commands that are for the remote system.</span></span> <span data-ttu-id="be518-133">Un modulo di script temporaneo che contiene tutti i comandi proxy verrà creato e importato per la durata della sessione PowerShell locale.</span><span class="sxs-lookup"><span data-stu-id="be518-133">A temporary script module containing all the proxy commands is created and imported for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="be518-134">Alcuni sistemi potrebbero non essere in grado di importare un'intera sessione JEA a causa di vincoli nei cmdlet JEA predefiniti.</span><span class="sxs-lookup"><span data-stu-id="be518-134">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span> <span data-ttu-id="be518-135">Per evitare questo problema, importare dalla sessione JEA solo i comandi necessari, specificando in modo esplicito i loro nomi nel parametro `-CommandName`.</span><span class="sxs-lookup"><span data-stu-id="be518-135">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span> <span data-ttu-id="be518-136">Un futuro aggiornamento risolverà il problema con l'importazione di intere sessioni JEA nei sistemi interessati.</span><span class="sxs-lookup"><span data-stu-id="be518-136">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="be518-137">Se non si riesce a importare una sessione JEA a causa dei vincoli JEA nei parametri predefiniti, seguire questa procedura per filtrare i comandi predefiniti dal set importato.</span><span class="sxs-lookup"><span data-stu-id="be518-137">If you're unable to import a JEA session because of JEA constraints on the default parameters, follow the steps below to filter out the default commands from the imported set.</span></span> <span data-ttu-id="be518-138">Sebbene sia possibile continuare a usare alcuni comandi, ad esempio `Select-Object`, verrà usata solo la versione installata nel computer anziché la versione importata dalla sessione JEA remota.</span><span class="sxs-lookup"><span data-stu-id="be518-138">You can continue use commands like `Select-Object`, but you'll just use the local version installed on your computer instead of the one imported from the remote JEA session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Get a list of all the commands on the JEA endpoint
$commands = Invoke-Command -Session $jeasession -ScriptBlock { Get-Command }

# Filter out the default cmdlets
$jeaDefaultCmdlets = 'Clear-Host', 'Exit-PSSession', 'Get-Command', 'Get-FormatData', 'Get-Help', 'Measure-Object', 'Out-Default', 'Select-Object'
$filteredCommands = $commands.Name | Where-Object { $jeaDefaultCmdlets -notcontains $_ }

# Import only commands explicitly added in role capabilities and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA' -CommandName $filteredCommands
```

<span data-ttu-id="be518-139">È anche possibile salvare i cmdlet proxy da una comunicazione remota implicita tramite [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span><span class="sxs-lookup"><span data-stu-id="be518-139">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="be518-140">Per altre informazioni sulla comunicazione remota implicita, vedere la documentazione relativa a [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) e [Import-Module](/powershell/microsoft.powershell.core/import-module).</span><span class="sxs-lookup"><span data-stu-id="be518-140">For more information about implicit remoting, see the documentation for [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) and [Import-Module](/powershell/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="be518-141">Uso di JEA a livello di codice</span><span class="sxs-lookup"><span data-stu-id="be518-141">Using JEA programmatically</span></span>

<span data-ttu-id="be518-142">JEA può anche essere usato in sistemi di automazione e applicazioni utente, ad esempio app di supporto tecnico interno e siti Web.</span><span class="sxs-lookup"><span data-stu-id="be518-142">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and websites.</span></span> <span data-ttu-id="be518-143">L'approccio è uguale a quello per la creazione di app che comunicano con endpoint di PowerShell senza vincoli.</span><span class="sxs-lookup"><span data-stu-id="be518-143">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints.</span></span> <span data-ttu-id="be518-144">Assicurarsi che il programma sia progettato per funzionare con le limitazioni imposte da JEA.</span><span class="sxs-lookup"><span data-stu-id="be518-144">Ensure the program is designed to work with limitation imposed by JEA.</span></span>

<span data-ttu-id="be518-145">Per attività semplici e singole, è possibile usare [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) per eseguire comandi in una sessione JEA.</span><span class="sxs-lookup"><span data-stu-id="be518-145">For simple, one-off tasks, you can use [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) to run commands in a JEA session.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="be518-146">Per verificare i comandi disponibili durante la connessione a una sessione JEA, eseguire `Get-Command` e scorrere i risultati per vedere i parametri consentiti.</span><span class="sxs-lookup"><span data-stu-id="be518-146">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="be518-147">Se si compila un'app C#, è possibile creare uno spazio di esecuzione di PowerShell che si connette a una sessione JEA specificando il nome della configurazione in un oggetto [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo).</span><span class="sxs-lookup"><span data-stu-id="be518-147">If you're building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) object.</span></span>

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
// See https://docs.microsoft.com/dotnet/api/system.management.automation.pscredential
var creds        = // create a PSCredential object here

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
    false,                 // Use SSL
    computerName,          // Computer name
    5985,                  // WSMan Port
    "/wsman",              // WSMan Path
                           // Connection URI with config name
    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),
    creds);                // Credentials

// Now, use the connection info to create a runspace where you can run the commands
using (Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo))
{
    // Open the runspace
    runspace.Open();

    using (PowerShell ps = PowerShell.Create())
    {
        // Set the PowerShell object to use the JEA runspace
        ps.Runspace = runspace;

        // Now you can add and invoke commands
        ps.AddCommand("Get-Command");
        foreach (var result in ps.Invoke())
        {
            Console.WriteLine(result);
        }
    }

    // Close the runspace
    runspace.Close();
}
```

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="be518-148">Uso di JEA con PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="be518-148">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="be518-149">Hyper-V in Windows 10 e in Windows Server 2016 offre [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), una funzionalità che consente agli amministratori di Hyper-V di gestire le macchine virtuali con PowerShell, indipendentemente dalla configurazione di rete o dalle impostazioni di gestione remota della macchina virtuale.</span><span class="sxs-lookup"><span data-stu-id="be518-149">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), a feature that allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="be518-150">È possibile usare PowerShell Direct con JEA per concedere a un amministratore di Hyper-V accesso limitato alla macchina virtuale.</span><span class="sxs-lookup"><span data-stu-id="be518-150">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM.</span></span>
<span data-ttu-id="be518-151">Ciò può essere utile se si perde la connettività di rete alla macchina virtuale ed è necessario un amministratore del datacenter per correggere le impostazioni di rete.</span><span class="sxs-lookup"><span data-stu-id="be518-151">This can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="be518-152">Per usare JEA in PowerShell Direct non è richiesta alcuna configurazione aggiuntiva.</span><span class="sxs-lookup"><span data-stu-id="be518-152">No additional configuration is required to use JEA over PowerShell Direct.</span></span> <span data-ttu-id="be518-153">Tuttavia, il sistema operativo guest in esecuzione nella macchina virtuale deve essere Windows 10, Windows Server 2016 o versioni successive.</span><span class="sxs-lookup"><span data-stu-id="be518-153">However, the guest operating system running inside the virtual machine must be Windows 10, Windows Server 2016, or higher.</span></span> <span data-ttu-id="be518-154">L'amministratore di Hyper-V può connettersi all'endpoint JEA usando i parametri `-VMName` o `-VMId` nei cmdlet di PSRemoting:</span><span class="sxs-lookup"><span data-stu-id="be518-154">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="be518-155">Si consiglia di creare un account utente dedicato con i diritti minimi necessari per gestire il sistema per l'uso da parte di un amministratore di Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="be518-155">It's recommended you create a dedicated user account with the minimum rights needed to manage the system for use by a Hyper-V administrator.</span></span> <span data-ttu-id="be518-156">Tenere presente che anche un utente senza privilegi può accedere per impostazione predefinita a un computer Windows e usare PowerShell senza vincoli.</span><span class="sxs-lookup"><span data-stu-id="be518-156">Remember, even an unprivileged user can sign into a Windows machine by default, including using unconstrained PowerShell.</span></span> <span data-ttu-id="be518-157">Ciò consente all'utente di visualizzare il file system e altre informazioni sull'ambiente del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="be518-157">That allows them to browse the file system and learn more about your OS environment.</span></span> <span data-ttu-id="be518-158">Per limitare l'accesso di un amministratore di Hyper-V a una macchina virtuale tramite PowerShell Direct con JEA, è necessario negare i diritti di accesso locale all'account JEA dell'amministratore di Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="be518-158">To lock down a Hyper-V administrator and limit them to only access a VM using PowerShell Direct with JEA, you must deny local logon rights to the Hyper-V admin's JEA account.</span></span>
