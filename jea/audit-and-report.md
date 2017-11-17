---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: jea,powershell,sicurezza
title: Controllo e creazione di report in JEA
ms.openlocfilehash: 60bc7a4213c75735628207bb21078bf90f7b1ca3
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="bfba7-103">Controllo e creazione di report in JEA</span><span class="sxs-lookup"><span data-stu-id="bfba7-103">Auditing and Reporting on JEA</span></span>

> <span data-ttu-id="bfba7-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bfba7-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="bfba7-105">Dopo aver distribuito JEA, è possibile controllarne regolarmente la configurazione.</span><span class="sxs-lookup"><span data-stu-id="bfba7-105">After you've deployed JEA, you will want to regularly audit the JEA configuration.</span></span>
<span data-ttu-id="bfba7-106">Ciò consentirà di valutare se gli utenti corretti hanno accesso all'endpoint JEA e se i loro ruoli assegnati sono ancora appropriati.</span><span class="sxs-lookup"><span data-stu-id="bfba7-106">This will help you assess if the correct people have access to the JEA endpoint and if their assigned roles are still appropriate.</span></span>

<span data-ttu-id="bfba7-107">Questo argomento descrive i vari modi con cui è possibile controllare un endpoint JEA.</span><span class="sxs-lookup"><span data-stu-id="bfba7-107">This topic describes the various ways you can audit a JEA endpoint.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="bfba7-108">Trovare le sessioni JEA registrate in un computer</span><span class="sxs-lookup"><span data-stu-id="bfba7-108">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="bfba7-109">Per controllare quali sessioni JEA sono registrate in un computer, usare il cmdlet [Get-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration).</span><span class="sxs-lookup"><span data-stu-id="bfba7-109">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="bfba7-110">Le autorizzazioni effettive per l'endpoint sono elencate nella proprietà "Permission".</span><span class="sxs-lookup"><span data-stu-id="bfba7-110">The effective rights for the endpoint are listed in the "Permission" property.</span></span>
<span data-ttu-id="bfba7-111">Questi utenti hanno il diritto di connettersi all'endpoint JEA, ma i ruoli (e, di conseguenza, i comandi) a cui hanno accesso sono determinati dal campo "RoleDefinitions" nel [file di configurazione sessione](session-configurations.md) usato per registrare l'endpoint.</span><span class="sxs-lookup"><span data-stu-id="bfba7-111">These users have the right to connect to the JEA endpoint, but which roles (and, by extension, commands) they have access to is determined by the "RoleDefinitions" field in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span>

<span data-ttu-id="bfba7-112">È possibile valutare i mapping dei ruoli in un endpoint JEA registrato espandendo i dati nella proprietà "RoleDefinitions".</span><span class="sxs-lookup"><span data-stu-id="bfba7-112">You can evaluate the role mappings in a registered JEA endpoint by expanding the data in the "RoleDefinitions" property.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="bfba7-113">Trovare le funzionalità di ruolo disponibili nel computer</span><span class="sxs-lookup"><span data-stu-id="bfba7-113">Find available role capabilities on the machine</span></span>

<span data-ttu-id="bfba7-114">I file delle funzionalità del ruolo verranno usati da JEA solo se sono archiviati in una cartella "RoleCapabilities" all'interno di un modulo di PowerShell valido.</span><span class="sxs-lookup"><span data-stu-id="bfba7-114">Role capability files will only be used by JEA if they are stored in a "RoleCapabilities" folder inside a valid PowerShell module.</span></span>
<span data-ttu-id="bfba7-115">È possibile trovare tutte le funzionalità di ruolo disponibili in un computer eseguendo una ricerca nell'elenco dei moduli disponibili.</span><span class="sxs-lookup"><span data-stu-id="bfba7-115">You can find all role capabilities available on a computer by searching the list of available modules.</span></span>

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{ Name = 'Path'; Expression = { $_.FullName }} | Sort-Object Name
}
```

> [!NOTE]
> <span data-ttu-id="bfba7-116">L'ordine dei risultati di questa funzione non è necessariamente l'ordine in cui verranno selezionate le funzionalità di ruolo se più funzionalità di ruolo condividono lo stesso nome.</span><span class="sxs-lookup"><span data-stu-id="bfba7-116">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="bfba7-117">Controllare le autorizzazioni effettive per un utente specifico</span><span class="sxs-lookup"><span data-stu-id="bfba7-117">Check effective rights for a specific user</span></span>

<span data-ttu-id="bfba7-118">Dopo aver impostato un endpoint JEA, è possibile verificare quali comandi sono disponibili per un utente specifico in una sessione JEA.</span><span class="sxs-lookup"><span data-stu-id="bfba7-118">Once you have set up a JEA endpoint, you may want to check which commands are available to a specific user in a JEA session.</span></span>
<span data-ttu-id="bfba7-119">È possibile usare [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) per enumerare tutti i comandi applicabili a utenti se devono avviare una sessione JEA con l'appartenenza al gruppo corrente.</span><span class="sxs-lookup"><span data-stu-id="bfba7-119">You can use [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) to enumerate all of the commands applicable to a user if they were to start a JEA session with their current group memberships.</span></span>
<span data-ttu-id="bfba7-120">L'output di `Get-PSSessionCapability` è identico a quello dell'utente specificato che esegue `Get-Command -CommandType All` in una sessione JEA.</span><span class="sxs-lookup"><span data-stu-id="bfba7-120">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="bfba7-121">Se gli utenti non sono membri permanenti di gruppi che concedono diritti JEA aggiuntivi, questo cmdlet potrebbe non tenere in considerazione le autorizzazioni aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="bfba7-121">If your users are not permanent members of groups which would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span>
<span data-ttu-id="bfba7-122">Ciò avviene in genere quando si usano sistemi di gestione di accesso con privilegi just-in-time (JIT) per consentire agli utenti di far temporaneamente parte di un gruppo di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="bfba7-122">This is typically the case when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span>
<span data-ttu-id="bfba7-123">Valutare sempre il mapping degli utenti ai ruoli e il contenuto di ogni ruolo per assicurarsi che gli utenti ottengano accesso solo al numero minimo di comandi necessari per svolgere il proprio lavoro.</span><span class="sxs-lookup"><span data-stu-id="bfba7-123">Always carefully evaluate the mapping of users to roles and the contents of each role to ensure users are only getting access to the least amount of commands needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="bfba7-124">Log eventi di PowerShell</span><span class="sxs-lookup"><span data-stu-id="bfba7-124">PowerShell event logs</span></span>

<span data-ttu-id="bfba7-125">Se è stata abilitata la registrazione blocco di script e/o moduli nel sistema, sarà possibile trovare gli eventi nei log eventi Windows per ogni comando eseguito nelle sessioni JEA.</span><span class="sxs-lookup"><span data-stu-id="bfba7-125">If you enabled module and/or script block logging on the system, you will be able to find events in the Windows event logs for each command a user ran in their JEA sessions.</span></span>
<span data-ttu-id="bfba7-126">Per trovare questi eventi, aprire il Visualizzatore eventi di Windows, passare al log eventi **Microsoft-Windows-PowerShell/Operational** e cercare gli eventi con ID evento **4104**.</span><span class="sxs-lookup"><span data-stu-id="bfba7-126">To find these events, open the Windows Event Viewer, navigate to the **Microsoft-Windows-PowerShell/Operational** event log, and look for events with event ID **4104**.</span></span>

<span data-ttu-id="bfba7-127">Ogni voce del log eventi include informazioni sulla sessione in cui è stato eseguito il comando.</span><span class="sxs-lookup"><span data-stu-id="bfba7-127">Each event log entry will include information about the session in which the command was run.</span></span>
<span data-ttu-id="bfba7-128">Per le sessioni JEA, la voce include informazioni importanti su **ConnectedUser**, che corrisponde all'utente che ha creato la sessione JEA, e su **RunAsUser**, che identifica l'account JEA usato per eseguire il comando.</span><span class="sxs-lookup"><span data-stu-id="bfba7-128">For JEA sessions, this includes important information about the **ConnectedUser**, which is the actual user who created the JEA session, as well as the **RunAsUser** which identifies the account JEA used to execute the command.</span></span>
<span data-ttu-id="bfba7-129">I log eventi dell'applicazione includono le modifiche eseguite da RunAsUser, pertanto è molto importante abilitare la registrazione di moduli/script per poter tracciare una chiamata al comando specifico di un utente.</span><span class="sxs-lookup"><span data-stu-id="bfba7-129">Application event logs will show changes being made by the RunAsUser, so having transcripts or module/script logging enabled is crucial to be able to trace a specific command invocation back to a user.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="bfba7-130">Log eventi dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="bfba7-130">Application event logs</span></span>

<span data-ttu-id="bfba7-131">Quando si esegue un comando in una sessione JEA che interagisce con applicazioni esterne o con un servizio, tali applicazioni potrebbero registrare eventi nei propri log eventi.</span><span class="sxs-lookup"><span data-stu-id="bfba7-131">When you run a command in a JEA session that interacts with an external application or service, those applications may log events to their own event logs.</span></span>
<span data-ttu-id="bfba7-132">Diversamente dalle trascrizioni e dai log di PowerShell, gli altri meccanismi di registrazione non memorizzano l'utente connesso alla sessione JEA e registrano invece solo l'utente virtuale RunAs o l'account del servizio gestito del gruppo.</span><span class="sxs-lookup"><span data-stu-id="bfba7-132">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the connected user of the JEA session, and will instead only log the virtual run-as user or group managed service account.</span></span>
<span data-ttu-id="bfba7-133">Per determinare l'utente che ha eseguito il comando, è necessario vedere una [trascrizione di sessione](#session-transcripts) o correlare i log eventi di PowerShell con l'ora e l'utente indicato nel log eventi dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="bfba7-133">In order to determine who ran the command, you will need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="bfba7-134">Il log di WinRM consente anche di correlare utenti RunAs in un log eventi dell'applicazione con l'utente che si connette.</span><span class="sxs-lookup"><span data-stu-id="bfba7-134">The WinRM log can also help you correlate run as users in an application event log with the connecting user.</span></span>
<span data-ttu-id="bfba7-135">L'ID evento **193** nel log **Microsoft-Windows-Windows Remote Management/Operational** registra l'ID di sicurezza (SID) e il nome account dell'utente che si connette e dell'utente RunAs, ogni volta che viene creata una sessione JEA.</span><span class="sxs-lookup"><span data-stu-id="bfba7-135">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user every time a JEA session is created.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="bfba7-136">Trascrizioni di sessione</span><span class="sxs-lookup"><span data-stu-id="bfba7-136">Session transcripts</span></span>

<span data-ttu-id="bfba7-137">Se è stato configurato JEA per creare una trascrizione per ogni sessione utente, una copia in formato testo di tutte le azioni dell'utente verrà archiviata nella cartella specificata.</span><span class="sxs-lookup"><span data-stu-id="bfba7-137">If you configured JEA to create a transcript for each user session, a text copy of every user's actions will be stored in the specified folder.</span></span>

<span data-ttu-id="bfba7-138">Per trovare tutte le directory di trascrizione, eseguire il comando seguente con privilegi di amministratore nel computer configurato con JEA:</span><span class="sxs-lookup"><span data-stu-id="bfba7-138">To find all transcript directories, run the following command as an administrator on the computer configured with JEA:</span></span>

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="bfba7-139">Ogni trascrizione inizia con informazioni sul tempo di avvio della sessione, sull'utente connesso alla sessione e sull'identità JEA assegnata.</span><span class="sxs-lookup"><span data-stu-id="bfba7-139">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="bfba7-140">Nel corpo della trascrizione, vengono registrate informazioni su ogni comando chiamato dall'utente.</span><span class="sxs-lookup"><span data-stu-id="bfba7-140">In the body of the transcript, information is logged about each command the user invoked.</span></span>
<span data-ttu-id="bfba7-141">La sintassi esatta del comando che è stato eseguito dall'utente non è disponibile nelle sessioni JEA a causa del modo in cui i comandi vengono trasformati per la comunicazione remota di PowerShell, comunque è sempre possibile determinare il comando eseguito.</span><span class="sxs-lookup"><span data-stu-id="bfba7-141">The exact syntax of the command the user ran is unavailable in JEA sessions due to the way commands are transformed for PowerShell remoting, however you can still determine the effective command that was executed.</span></span>
<span data-ttu-id="bfba7-142">Di seguito viene illustrato un frammento di trascrizione di esempio da un utente che esegue `Get-Service Dns` in una sessione JEA:</span><span class="sxs-lookup"><span data-stu-id="bfba7-142">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="bfba7-143">Per ogni comando eseguito da un utente, viene scritta una riga "CommandInvocation", che descrive il cmdlet o la funzione chiamata dall'utente.</span><span class="sxs-lookup"><span data-stu-id="bfba7-143">For each command a user runs, a "CommandInvocation" line will be written, describing the cmdlet or function the user invoked.</span></span>
<span data-ttu-id="bfba7-144">ParameterBindings segue ogni CommandInvocation per specificare informazioni su ogni parametro e valore usato con il comando.</span><span class="sxs-lookup"><span data-stu-id="bfba7-144">ParameterBindings follow each CommandInvocation to tell you about each parameter and value that was supplied with the command.</span></span>
<span data-ttu-id="bfba7-145">Nell'esempio precedente, è possibile notare che nel parametro "Name" è stato specificato il valore "Dns" per il cmdlet "Get-Service".</span><span class="sxs-lookup"><span data-stu-id="bfba7-145">In the above example, you can see that the parameter "Name" was supplied the value "Dns" for the "Get-Service" cmdlet.</span></span>

<span data-ttu-id="bfba7-146">L'output di ogni comando genera anche un CommandInvocation, in genere per Out-Default.</span><span class="sxs-lookup"><span data-stu-id="bfba7-146">The output of each command will also trigger a CommandInvocation, usually to Out-Default.</span></span> <span data-ttu-id="bfba7-147">InputObject di Out-Default è l'oggetto PowerShell restituito dal comando.</span><span class="sxs-lookup"><span data-stu-id="bfba7-147">The InputObject of Out-Default is the PowerShell object returned from the command.</span></span>
<span data-ttu-id="bfba7-148">I dettagli di tale oggetto vengono aggiunti in alcune righe di sotto, emulando strettamente ciò che avrebbe visto l'utente.</span><span class="sxs-lookup"><span data-stu-id="bfba7-148">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="bfba7-149">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bfba7-149">See also</span></span>

- [<span data-ttu-id="bfba7-150">Controllare le azioni dell'utente in una sessione JEA</span><span class="sxs-lookup"><span data-stu-id="bfba7-150">Audit user actions in a JEA session</span></span>](audit-and-report.md)
- [<span data-ttu-id="bfba7-151">Post di blog sulla sicurezza di *PowerShell ♥ the Blue Team*</span><span class="sxs-lookup"><span data-stu-id="bfba7-151">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)

