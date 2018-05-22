---
ms.date: 06/12/2017
keywords: jea,powershell,sicurezza
title: Uso di JEA
ms.openlocfilehash: 891e4be4c3fadceeff5ede7ac5cab04a5f80e5c1
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
---
# <a name="using-jea"></a>Uso di JEA

> Si applica a: Windows PowerShell 5.0

Questo argomento illustra i vari modi in cui è possibile connettersi e usare un endpoint JEA.

## <a name="using-jea-interactively"></a>Uso interattivo di JEA

Se si esegue il test della configurazione JEA oppure se gli utenti devono eseguire attività semplici, è possibile usare JEA allo stesso modo di una sessione di comunicazione remota di PowerShell regolare.
Per attività di comunicazione remota complesse, è consigliabile invece usare la [comunicazione implicita](#using-jea-with-implicit-remoting) per renderla più semplice agli utenti consentendo di operare localmente con gli oggetti di dati.

Per usare JEA in modo interattivo, sono necessari:
- Il nome del computer a cui si è connessi (può essere il computer locale)
- Il nome dell'endpoint JEA registrato nel computer
- Le credenziali per i computer che hanno accesso all'endpoint JEA

Con queste informazioni a disposizione, è possibile avviare una sessione JEA tramite [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) o [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Se l'account con il quale si è attualmente connessi ha accesso all'endopoint JEA, è possibile omettere il parametro `-Credential`.

Quando il prompt di PowerShell diventa `[localhost]: PS>` indica che si sta ora interagendo con la sessione remota JEA.
È possibile eseguire `Get-Command` per verificare i comandi disponibili.
È necessario contattare l'amministratore per verificare se ci sono eventuali limitazioni per i parametri disponibili o per i valori dei parametri consentiti.

Si noti che le sessioni JEA non operano in modalità linguaggio, per cui alcuni dei modi in cui si usa generalmente PowerShell potrebbero non essere disponibili.
Ad esempio, non è possibile usare variabili per archiviare i dati o controllare le proprietà degli oggetti restituiti dai cmdlet.
L'esempio seguente illustra come è possibile usare PowerShell oggi e due approcci per ottenere lo stesso comando in modalità senza linguaggio.

```powershell
# Using variables in NoLanguage mode is disallowed, so the following will not work
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# Better yet, use parameter sets that don't require extra data to be passed in when possible
Start-VM -VMName 'SQL01'
```

Per chiamate di comandi più complesse che rendono difficile questo approccio, è consigliabile usare la [comunicazione remota implicita](#using-jea-with-implicit-remoting) o la [creazione di funzioni personalizzate](role-capabilities.md#creating-custom-functions) che eseguono il wrapping della funzionalità voluta.

## <a name="using-jea-with-implicit-remoting"></a>Uso di JEA con comunicazione remota implicita

PowerShell supporta un modello di comunicazione remota alternativa in cui è possibile importare i cmdlet del proxy da un computer remoto nel computer locale e usarli come se fossero comandi locali.
Questo modello viene chiamato comunicazione remota implicita ed è illustrato in maniera dettagliata in [questo *post di blog* Hey, Scripting Guy!](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/)
La comunicazione remota implicita è particolarmente utile quando si usa JEA perché consente di usare i cmdlet JEA in una modalità linguaggio completa.
Ciò significa che è possibile usare il completamento tramite TAB, variabili, modificare oggetti e usare anche script locali per automatizzare facilmente le operazioni in un endpoint JEA.
Ogni volta che si chiama un comando proxy, i dati vengono inviati all'endpoint JEA nel computer remoto ed eseguiti su questo computer.

La comunicazione remota implicita importa i cmdlet da una sessione di PowerShell esistente.
Facoltativamente, è possibile anteporre ai sostantivi di ogni cmdlet del proxy una stringa a scelta per distinguere i comandi per il sistema remoto.
Verrà creato un modulo di script temporaneo che contiene tutti i comandi proxy e questo modulo può essere usato per la durata della sessione PowerShell locale.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Alcuni sistemi potrebbero non essere in grado di importare un'intera sessione JEA a causa di vincoli nei cmdlet JEA predefiniti.
> Per evitare questo problema, importare dalla sessione JEA solo i comandi necessari, specificando in modo esplicito i loro nomi nel parametro `-CommandName`.
> Un futuro aggiornamento risolverà il problema con l'importazione di intere sessioni JEA nei sistemi interessati.

Se non si riesce a importare una sessione JEA a causa dei vincoli nei parametri JEA predefiniti, è possibile seguire la procedura seguente per filtrare i comandi predefiniti dal set importato.
Sarà comunque possibile usare alcuni comandi, ad esempio `Select-Object`. Si userà solo la versione installata nel computer locale anziché la versione remota nella sessione JEA.

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

È anche possibile salvare i cmdlet proxy da una comunicazione remota implicita tramite [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).
Per altre informazioni sulla comunicazione remota implicita, vedere la documentazione della Guida per [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) e [Import-Module](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/import-module).

## <a name="using-jea-programatically"></a>Uso di JEA in modo programmato

JEA può anche essere usato in sistemi di automazione e applicazioni utente, ad esempio app di supporto tecnico interno e siti Web.
L'approccio è simile alla compilazione di applicazioni che comunicano con gli endpoint di PowerShell non vincolati, tenendo presente che JEA limita i comandi che possono essere eseguiti nella sessione remota.

Per attività semplici e singole, è possibile usare [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) per eseguire un set di comandi tramite JEA.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Per verificare i comandi disponibili durante la connessione a una sessione JEA, eseguire `Get-Command` e scorrere i risultati per vedere i parametri consentiti.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Se si compila un'applicazione C#, è possibile creare uno spazio di esecuzione di PowerShell che connette a una sessione JEA specificando il nome della configurazione in un oggetto [WSManConnectionInfo](https://msdn.microsoft.com/en-us/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx).

```csharp

// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/en-us/library/system.management.automation.pscredential(v=vs.85).aspx)

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
                    false,                 // Use SSL
                    computerName,          // Computer name
                    5985,                  // WSMan Port
                    "/wsman",              // WSMan Path
                    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),  // Connection URI with config name
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

Hyper-V in Windows 10 e in Windows Server 2016 offre [PowerShell Direct](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/user_guide/vmsession), una funzionalità che consente agli amministratori di Hyper-V di gestire le macchine virtuali con PowerShell, indipendentemente dalla configurazione di rete o dalle impostazioni di gestione remota della macchina virtuale.

È possibile usare PowerShell Direct con JEA per concedere a un amministratore Hyper-V accesso limitato alla macchina virtuale. Ciò è utile quando si perde la connettività di rete nella macchina virtuale ed è necessario l'intervento di un amministratore del datacenter per modificare le impostazioni di rete.

Non è necessaria alcuna configurazione aggiuntiva per usare JEA in PowerShell Direct. Tuttavia, il sistema operativo eseguito nella macchina virtuale deve essere Windows 10 o Windows Server 2016.
L'amministratore di Hyper-V può connettersi all'endpoint JEA usando i parametri `-VMName` o `-VMId` nei cmdlet di PSRemoting:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

È consigliabile creare un utente locale dedicato senza diritti per gestire il sistema usato dagli amministratori di Hyper-V.
Si noti che anche un utente senza privilegi può accedere per impostazione predefinita a un computer Windows e può usare PowerShell non vincolato.
Ciò gli consente di vedere parte del contenuto del file system e altre informazioni sull'ambiente del sistema operativo.
Per limitare l'accesso di un amministratore di Hyper-V soltanto a una macchina virtuale tramite PowerShell Direct con JEA, è necessario rimuovere i diritti di accesso locale all'account JEA dell'amministratore di Hyper-V.