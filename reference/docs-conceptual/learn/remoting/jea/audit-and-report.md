---
ms.date: 07/10/2019
keywords: jea,powershell,sicurezza
title: Controllo e creazione di report in JEA
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "70017792"
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="6bc9f-103">Controllo e creazione di report in JEA</span><span class="sxs-lookup"><span data-stu-id="6bc9f-103">Auditing and Reporting on JEA</span></span>

<span data-ttu-id="6bc9f-104">Dopo aver distribuito JEA, è necessario controllarne regolarmente la configurazione.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-104">After you've deployed JEA, you need to regularly audit the JEA configuration.</span></span> <span data-ttu-id="6bc9f-105">Ciò consente di valutare se gli utenti corretti hanno accesso all'endpoint JEA e se i loro ruoli assegnati sono ancora appropriati.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-105">Auditing helps you assess that the correct people have access to the JEA endpoint and their assigned roles are still appropriate.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="6bc9f-106">Trovare le sessioni JEA registrate in un computer</span><span class="sxs-lookup"><span data-stu-id="6bc9f-106">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="6bc9f-107">Per controllare quali sessioni JEA sono registrate in un computer, usare il cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration).</span><span class="sxs-lookup"><span data-stu-id="6bc9f-107">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }
```

```Output
Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed,
                CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="6bc9f-108">Le autorizzazioni effettive per l'endpoint sono elencate nella proprietà **Permission**.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-108">The effective rights for the endpoint are listed in the **Permission** property.</span></span> <span data-ttu-id="6bc9f-109">Questi utenti hanno il diritto di connettersi all'endpoint JEA.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-109">These users have the right to connect to the JEA endpoint.</span></span> <span data-ttu-id="6bc9f-110">I ruoli e, di conseguenza, i comandi a cui hanno accesso sono tuttavia determinati dalla proprietà **RoleDefinitions** nel [file di configurazione sessione](session-configurations.md) usato per registrare l'endpoint.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-110">However, the roles and commands they have access to is determined by the **RoleDefinitions** property in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span> <span data-ttu-id="6bc9f-111">Espandere la proprietà **RoleDefinitions** per valutare i mapping dei ruoli in un endpoint JEA registrato.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-111">Expand the **RoleDefinitions** property to evaluate the role mappings in a registered JEA endpoint.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="6bc9f-112">Trovare le funzionalità di ruolo disponibili nel computer</span><span class="sxs-lookup"><span data-stu-id="6bc9f-112">Find available role capabilities on the machine</span></span>

<span data-ttu-id="6bc9f-113">JEA ottiene le funzionalità del ruolo dai file `.psrc` archiviati nella cartella **RoleCapabilities** all'interno di un modulo di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-113">JEA gets role capabilities from the `.psrc` files stored in the **RoleCapabilities** folder inside a PowerShell module.</span></span> <span data-ttu-id="6bc9f-114">La funzione seguente consente di trovare tutte le funzionalità del ruolo disponibili in un computer.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-114">The following function finds all role capabilities available on a computer.</span></span>

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
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{
        Name = 'Path'; Expression = { $_.FullName }
    } | Sort-Object Name
}
```

> [!NOTE]
> <span data-ttu-id="6bc9f-115">L'ordine dei risultati di questa funzione non è necessariamente l'ordine in cui verranno selezionate le funzionalità di ruolo se più funzionalità di ruolo condividono lo stesso nome.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-115">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="6bc9f-116">Controllare le autorizzazioni effettive per un utente specifico</span><span class="sxs-lookup"><span data-stu-id="6bc9f-116">Check effective rights for a specific user</span></span>

<span data-ttu-id="6bc9f-117">Il cmdlet [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) enumera tutti i comandi disponibili in un endpoint JEA in base alle appartenenze ai gruppi di un utente.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-117">The [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet enumerates all the commands available on a JEA endpoint based on a user's group memberships.</span></span>
<span data-ttu-id="6bc9f-118">L'output di `Get-PSSessionCapability` è identico a quello dell'utente specificato che esegue `Get-Command -CommandType All` in una sessione JEA.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-118">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="6bc9f-119">Se gli utenti non sono membri permanenti di gruppi che concedono diritti JEA aggiuntivi, questo cmdlet potrebbe non tenere in considerazione le autorizzazioni aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-119">If your users aren't permanent members of groups that would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span> <span data-ttu-id="6bc9f-120">Ciò avviene quando si usano sistemi di gestione di accesso con privilegi just-in-time (JIT) per consentire agli utenti di far temporaneamente parte di un gruppo di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-120">This happens when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span> <span data-ttu-id="6bc9f-121">Valutare con attenzione il mapping degli utenti ai ruoli e alle funzionalità per fare in modo che gli utenti ottengano solo il livello di accesso necessario per svolgere correttamente il proprio lavoro.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-121">Carefully evaluate the mapping of users to roles and capabilities to ensure that users only get the level of access needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="6bc9f-122">Log eventi di PowerShell</span><span class="sxs-lookup"><span data-stu-id="6bc9f-122">PowerShell event logs</span></span>

<span data-ttu-id="6bc9f-123">Se è stata abilitata la registrazione blocco di script o moduli nel sistema, sarà possibile individuare gli eventi nei log eventi Windows per ogni comando eseguito in una sessione JEA.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-123">If you enabled module or script block logging on the system, you can see events in the Windows event logs for each command a user runs in a JEA session.</span></span> <span data-ttu-id="6bc9f-124">Per trovare questi eventi, aprire il log eventi **Microsoft-Windows-PowerShell/Operational** e cercare gli eventi con ID evento **4104**.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-124">To find these events, open **Microsoft-Windows-PowerShell/Operational** event log and look for events with event ID **4104**.</span></span>

<span data-ttu-id="6bc9f-125">Ogni voce del log eventi include informazioni sulla sessione in cui è stato eseguito il comando.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-125">Each event log entry includes information about the session in which the command was run.</span></span> <span data-ttu-id="6bc9f-126">Per le sessioni JEA, l'evento include informazioni su **ConnectedUser** e **RunAsUser**.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-126">For JEA sessions, the event includes information about the **ConnectedUser** and the **RunAsUser**.</span></span> <span data-ttu-id="6bc9f-127">**ConnectedUser** è l'utente effettivo che ha creato la sessione JEA.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-127">The **ConnectedUser** is the actual user who created the JEA session.</span></span> <span data-ttu-id="6bc9f-128">**RunAsUser** è l'account JEA usato per eseguire il comando.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-128">The **RunAsUser** is the account JEA used to execute the command.</span></span>

<span data-ttu-id="6bc9f-129">Nei log eventi dell'applicazione vengono visualizzate le modifiche apportate da **RunAsUser**.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-129">Application event logs show changes being made by the **RunAsUser**.</span></span> <span data-ttu-id="6bc9f-130">È quindi necessario abilitare la registrazione di moduli e script per poter tracciare una chiamata al comando specifico di **ConnectedUser**.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-130">So having module and script logging enabled is required to trace a specific command invocation back to the **ConnectedUser**.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="6bc9f-131">Log eventi dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="6bc9f-131">Application event logs</span></span>

<span data-ttu-id="6bc9f-132">I comandi eseguiti in una sessione JEA che interagiscono con applicazioni o servizi esterni potrebbero registrare eventi nei propri log eventi.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-132">Commands run in a JEA session that interact with external applications or services may log events to their own event logs.</span></span> <span data-ttu-id="6bc9f-133">A differenza dei log e delle trascrizioni di PowerShell, gli altri meccanismi di registrazione non memorizzano l'utente connesso alla sessione JEA.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-133">Unlike PowerShell logs and transcripts, other logging mechanisms don't capture the connected user of the JEA session.</span></span> <span data-ttu-id="6bc9f-134">Tali applicazioni registrano invece solo l'utente virtuale RunAs.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-134">Instead, those applications only log the virtual run-as user.</span></span>
<span data-ttu-id="6bc9f-135">Per determinare l'utente che ha eseguito il comando, è necessario vedere una [trascrizione di sessione](#session-transcripts) o correlare i log eventi di PowerShell con l'ora e l'utente indicato nel log eventi dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-135">To determine who ran the command, you need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="6bc9f-136">Il log di WinRM consente anche di correlare utenti RunAs con l'utente che si connette in un log eventi dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-136">The WinRM log can also help you correlate run-as users to the connecting user in an application event log.</span></span> <span data-ttu-id="6bc9f-137">L'ID evento **193** nel log **Microsoft-Windows-Windows Remote Management/Operational** registra l'ID di sicurezza (SID) e il nome account dell'utente che si connette e dell'utente RunAs per ogni nuova sessione JEA.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-137">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user for every new JEA session.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="6bc9f-138">Trascrizioni di sessione</span><span class="sxs-lookup"><span data-stu-id="6bc9f-138">Session transcripts</span></span>

<span data-ttu-id="6bc9f-139">Se è stato configurato JEA per creare una trascrizione per ogni sessione utente, una copia in formato testo di tutte le azioni dell'utente verrà archiviata nella cartella specificata.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-139">If you configured JEA to create a transcript for each user session, a text copy of every user's actions are stored in the specified folder.</span></span>

<span data-ttu-id="6bc9f-140">Il comando seguente (come amministratore) consente di trovare tutte le directory di trascrizione.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-140">The following command (as an administrator) finds all transcript directories.</span></span>

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="6bc9f-141">Ogni trascrizione inizia con informazioni sul tempo di avvio della sessione, sull'utente connesso alla sessione e sull'identità JEA assegnata.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-141">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="6bc9f-142">Il corpo della trascrizione contiene informazioni su ogni comando chiamato dall'utente.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-142">The body of the transcript contains information about each command the user invoked.</span></span> <span data-ttu-id="6bc9f-143">La sintassi esatta del comando usato non è disponibile nelle sessioni JEA a causa del modo in cui i comandi vengono trasformati per la comunicazione remota di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-143">The exact syntax of the command used is unavailable in JEA sessions because of the way commands are transformed for PowerShell remoting.</span></span> <span data-ttu-id="6bc9f-144">È tuttavia possibile determinare il comando effettivo che è stato eseguito.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-144">However, you can still determine the effective command that was executed.</span></span> <span data-ttu-id="6bc9f-145">Di seguito viene illustrato un frammento di trascrizione di esempio da un utente che esegue `Get-Service Dns` in una sessione JEA:</span><span class="sxs-lookup"><span data-stu-id="6bc9f-145">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="6bc9f-146">Viene scritta una riga **CommandInvocation** per ogni comando eseguito da un utente.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-146">A **CommandInvocation** line is written for each command a user runs.</span></span> <span data-ttu-id="6bc9f-147">**ParameterBindings** registra ogni parametro e valore specificato con il comando.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-147">**ParameterBindings** record each parameter and value supplied with the command.</span></span> <span data-ttu-id="6bc9f-148">Nell'esempio precedente si può osservare che nel parametro **Name** è stato specificato il valore **Dns** per il cmdlet `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-148">In the previous example, you can see that the parameter **Name** was supplied the with value **Dns** for the `Get-Service` cmdlet.</span></span>

<span data-ttu-id="6bc9f-149">L'output di ogni comando genera anche un **CommandInvocation**, in genere per `Out-Default`.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-149">The output of each command also triggers a **CommandInvocation**, usually to `Out-Default`.</span></span> <span data-ttu-id="6bc9f-150">**InputObject** di `Out-Default` è l'oggetto PowerShell restituito dal comando.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-150">The **InputObject** of `Out-Default` is the PowerShell object returned from the command.</span></span> <span data-ttu-id="6bc9f-151">I dettagli di tale oggetto vengono aggiunti in alcune righe di sotto, emulando strettamente ciò che avrebbe visto l'utente.</span><span class="sxs-lookup"><span data-stu-id="6bc9f-151">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="6bc9f-152">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6bc9f-152">See also</span></span>

[<span data-ttu-id="6bc9f-153">Post di blog sulla sicurezza di *PowerShell ♥ the Blue Team*</span><span class="sxs-lookup"><span data-stu-id="6bc9f-153">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
