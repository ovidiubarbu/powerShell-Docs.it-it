---
ms.date: 07/10/2019
keywords: jea,powershell,sicurezza
title: Uso di JEA
ms.openlocfilehash: 1c424eb4a476dd0db3cc69c0e6f14c89a3c523ba
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500509"
---
# <a name="using-jea"></a>Uso di JEA

Questo articolo illustra i vari modi in cui è possibile connettersi e usare un endpoint JEA.

## <a name="using-jea-interactively"></a>Uso interattivo di JEA

Se si esegue il test della configurazione JEA oppure se gli utenti devono eseguire attività semplici, è possibile usare JEA allo stesso modo di una normale sessione di comunicazione remota di PowerShell. Per le attività di comunicazione remota complesse, è consigliabile usare la [comunicazione remota implicita](#using-jea-with-implicit-remoting). La comunicazione remota implicita consente agli utenti di operare con gli oggetti dati in locale.

Per usare JEA in modo interattivo, sono necessari:

- Il nome del computer a cui si è connessi (può essere il computer locale)
- Il nome dell'endpoint JEA registrato nel computer
- Le credenziali che hanno accesso all'endpoint JEA nel computer

Con queste informazioni a disposizione, è possibile avviare una sessione JEA usando i cmdlet [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) o [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Se l'account utente corrente ha accesso all'endopoint JEA, è possibile omettere il parametro **Credential**.

Quando il prompt di PowerShell diventa `[localhost]: PS>` indica che si sta interagendo con la sessione remota JEA. È possibile eseguire `Get-Command` per verificare i comandi disponibili. Contattare l'amministratore per verificare se sono presenti eventuali limitazioni per i parametri disponibili o per i valori dei parametri consentiti.

Tenere presente che le sessioni JEA operano in modalità NoLanguage. È possibile che alcuni dei metodi con cui si usa generalmente PowerShell non siano disponibili. Ad esempio, non è possibile usare variabili per archiviare i dati o controllare le proprietà degli oggetti restituiti dai cmdlet. L'esempio seguente illustra due approcci per ottenere gli stessi comandi per lavorare in modalità NoLanguage.

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

Per chiamate di comandi più complesse che rendono difficile questo approccio, è consigliabile usare la [comunicazione remota implicita](#using-jea-with-implicit-remoting) o [creare funzioni personalizzate](role-capabilities.md#creating-custom-functions) che eseguono il wrapping della funzionalità desiderata.

## <a name="using-jea-with-implicit-remoting"></a>Uso di JEA con comunicazione remota implicita

PowerShell ha un modello di comunicazione remota implicita che consente di importare cmdlet del proxy da un computer remoto e usarli come comandi locali. La comunicazione remota implicita è descritta in questo**Hey, Scripting Guy!** [post di blog](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) indirizzato agli autori di script.
La comunicazione remota implicita è utile quando si usa JEA perché consente di usare i cmdlet JEA in una modalità di linguaggio completa. È possibile usare il completamento tramite TAB, le variabili, modificare oggetti e usare anche script locali per automatizzare le operazioni in un endpoint JEA. Ogni volta che si chiama un comando proxy, i dati vengono inviati all'endpoint JEA nel computer remoto ed eseguiti nel computer.

La comunicazione remota implicita importa i cmdlet da una sessione di PowerShell esistente. Facoltativamente, è possibile anteporre ai sostantivi di ogni cmdlet del proxy una stringa a scelta. Il prefisso consente di distinguere i comandi per il sistema remoto. Un modulo di script temporaneo che contiene tutti i comandi proxy verrà creato e importato per la durata della sessione PowerShell locale.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Alcuni sistemi potrebbero non essere in grado di importare un'intera sessione JEA a causa di vincoli nei cmdlet JEA predefiniti. Per evitare questo problema, importare dalla sessione JEA solo i comandi necessari, specificando in modo esplicito i loro nomi nel parametro `-CommandName`. Un futuro aggiornamento risolverà il problema con l'importazione di intere sessioni JEA nei sistemi interessati.

Se non si riesce a importare una sessione JEA a causa dei vincoli JEA nei parametri predefiniti, seguire questa procedura per filtrare i comandi predefiniti dal set importato. Sebbene sia possibile continuare a usare alcuni comandi, ad esempio `Select-Object`, verrà usata solo la versione installata nel computer anziché la versione importata dalla sessione JEA remota.

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

È anche possibile salvare i cmdlet proxy da una comunicazione remota implicita tramite [Export-PSSession](/powershell/module/microsoft.powershell.utility/Export-PSSession).
Per altre informazioni sulla comunicazione remota implicita, vedere la documentazione relativa a [Import-PSSession](/powershell/module/microsoft.powershell.utility/import-pssession) e [Import-Module](/powershell/module/microsoft.powershell.core/import-module).

## <a name="using-jea-programmatically"></a>Uso di JEA a livello di codice

JEA può anche essere usato in sistemi di automazione e applicazioni utente, ad esempio app di supporto tecnico interno e siti Web. L'approccio è uguale a quello per la creazione di app che comunicano con endpoint di PowerShell senza vincoli. Assicurarsi che il programma sia progettato per funzionare con le limitazioni imposte da JEA.

Per attività semplici e singole, è possibile usare [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) per eseguire comandi in una sessione JEA.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Per verificare i comandi disponibili durante la connessione a una sessione JEA, eseguire `Get-Command` e scorrere i risultati per vedere i parametri consentiti.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Se si compila un'app C#, è possibile creare uno spazio di esecuzione di PowerShell che si connette a una sessione JEA specificando il nome della configurazione in un oggetto [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo).

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
    string.Format(CultureInfo.InvariantCulture, "https://schemas.microsoft.com/powershell/{0}", configName),
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

## <a name="using-jea-with-powershell-direct"></a>Uso di JEA con PowerShell Direct

Hyper-V in Windows 10 e in Windows Server 2016 offre [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), una funzionalità che consente agli amministratori di Hyper-V di gestire le macchine virtuali con PowerShell, indipendentemente dalla configurazione di rete o dalle impostazioni di gestione remota della macchina virtuale.

È possibile usare PowerShell Direct con JEA per concedere a un amministratore di Hyper-V accesso limitato alla macchina virtuale.
Ciò può essere utile se si perde la connettività di rete alla macchina virtuale ed è necessario un amministratore del datacenter per correggere le impostazioni di rete.

Per usare JEA in PowerShell Direct non è richiesta alcuna configurazione aggiuntiva. Tuttavia, il sistema operativo guest in esecuzione nella macchina virtuale deve essere Windows 10, Windows Server 2016 o versioni successive. L'amministratore di Hyper-V può connettersi all'endpoint JEA usando i parametri `-VMName` o `-VMId` nei cmdlet di PSRemoting:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

Si consiglia di creare un account utente dedicato con i diritti minimi necessari per gestire il sistema per l'uso da parte di un amministratore di Hyper-V. Tenere presente che anche un utente senza privilegi può accedere per impostazione predefinita a un computer Windows e usare PowerShell senza vincoli. Ciò consente all'utente di visualizzare il file system e altre informazioni sull'ambiente del sistema operativo. Per limitare l'accesso di un amministratore di Hyper-V a una macchina virtuale tramite PowerShell Direct con JEA, è necessario negare i diritti di accesso locale all'account JEA dell'amministratore di Hyper-V.
