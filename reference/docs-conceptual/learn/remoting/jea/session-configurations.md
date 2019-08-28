---
ms.date: 07/10/2019
keywords: jea,powershell,sicurezza
title: Configurazioni della sessione JEA
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017732"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="ebfd0-103">Configurazioni della sessione JEA</span><span class="sxs-lookup"><span data-stu-id="ebfd0-103">JEA Session Configurations</span></span>

<span data-ttu-id="ebfd0-104">Un endpoint JEA viene registrato in un sistema tramite la creazione e la registrazione di un file di configurazione di sessione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-104">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file.</span></span> <span data-ttu-id="ebfd0-105">Le configurazioni di sessione determinano gli utenti che possono usare l'endpoint JEA e i ruoli ai quali possono avere accesso.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-105">Session configurations define who can use the JEA endpoint and which roles they have access to.</span></span> <span data-ttu-id="ebfd0-106">Definiscono anche impostazioni globali che vengono applicate a tutti gli utenti della sessione JEA.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-106">They also define global settings that apply to all users of the JEA session.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="ebfd0-107">Creare un file di configurazione sessione</span><span class="sxs-lookup"><span data-stu-id="ebfd0-107">Create a session configuration file</span></span>

<span data-ttu-id="ebfd0-108">Per registrare un endpoint JEA è necessario specificare come è configurato.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-108">To register a JEA endpoint, you must specify how that endpoint is configured.</span></span> <span data-ttu-id="ebfd0-109">Vi sono diverse opzioni da prendere in considerazione.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-109">There are many options to consider.</span></span> <span data-ttu-id="ebfd0-110">Le più importanti sono:</span><span class="sxs-lookup"><span data-stu-id="ebfd0-110">The most important options are:</span></span>

- <span data-ttu-id="ebfd0-111">Chi ha accesso all'endpoint JEA</span><span class="sxs-lookup"><span data-stu-id="ebfd0-111">Who has access to the JEA endpoint</span></span>
- <span data-ttu-id="ebfd0-112">Quali sono i ruoli con cui vengono eseguiti gli accessi</span><span class="sxs-lookup"><span data-stu-id="ebfd0-112">Which roles they be assigned</span></span>
- <span data-ttu-id="ebfd0-113">Quale identità JEA usa chi esegue l'accesso</span><span class="sxs-lookup"><span data-stu-id="ebfd0-113">Which identity JEA uses under the covers</span></span>
- <span data-ttu-id="ebfd0-114">Il nome dell'endpoint JEA</span><span class="sxs-lookup"><span data-stu-id="ebfd0-114">The name of the JEA endpoint</span></span>

<span data-ttu-id="ebfd0-115">Queste opzioni vengono definite in un file di dati PowerShell con estensione `.pssc`, ovvero in un file di configurazione di sessione.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-115">These options are defined in a PowerShell data file with a `.pssc` extension known as a PowerShell session configuration file.</span></span> <span data-ttu-id="ebfd0-116">È possibile modificare il file di configurazione di sessione in qualsiasi editor di testo.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-116">The session configuration file can be edited using any text editor.</span></span>

<span data-ttu-id="ebfd0-117">Eseguire il comando seguente per creare un file di configurazione modello vuoto.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-117">Run the following command to create a blank template configuration file.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="ebfd0-118">Per impostazione predefinita, solo le opzioni di configurazione più comuni sono incluse nel file modello.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-118">Only the most common configuration options are included in the template file by default.</span></span> <span data-ttu-id="ebfd0-119">Usare l'opzione `-Full` per includere tutte le impostazioni applicabili nel file PSSC generato.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-119">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="ebfd0-120">Il campo `-SessionType RestrictedRemoteServer` indica che la configurazione di sessione viene usata da JEA per una gestione sicura.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-120">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration is used by JEA for secure management.</span></span> <span data-ttu-id="ebfd0-121">Le sessioni di questo tipo operano in modalità **NoLanguage** e hanno accesso solo ai comandi (e agli alias) predefiniti seguenti:</span><span class="sxs-lookup"><span data-stu-id="ebfd0-121">Sessions of this type operate in **NoLanguage** mode and only have access to the following default commands (and aliases):</span></span>

- <span data-ttu-id="ebfd0-122">Clear-Host (cls, clear)</span><span class="sxs-lookup"><span data-stu-id="ebfd0-122">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="ebfd0-123">Exit-PSSession (exsn, exit)</span><span class="sxs-lookup"><span data-stu-id="ebfd0-123">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="ebfd0-124">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="ebfd0-124">Get-Command (gcm)</span></span>
- <span data-ttu-id="ebfd0-125">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="ebfd0-125">Get-FormatData</span></span>
- <span data-ttu-id="ebfd0-126">Get-Help</span><span class="sxs-lookup"><span data-stu-id="ebfd0-126">Get-Help</span></span>
- <span data-ttu-id="ebfd0-127">Measure-Object (measure)</span><span class="sxs-lookup"><span data-stu-id="ebfd0-127">Measure-Object (measure)</span></span>
- <span data-ttu-id="ebfd0-128">Out-Default</span><span class="sxs-lookup"><span data-stu-id="ebfd0-128">Out-Default</span></span>
- <span data-ttu-id="ebfd0-129">Select-Object (select)</span><span class="sxs-lookup"><span data-stu-id="ebfd0-129">Select-Object (select)</span></span>

<span data-ttu-id="ebfd0-130">Non sono disponibili provider PowerShell e nemmeno programmi esterni (file eseguibili o script).</span><span class="sxs-lookup"><span data-stu-id="ebfd0-130">No PowerShell providers are available, nor are any external programs (executables or scripts).</span></span>

<span data-ttu-id="ebfd0-131">Per altre informazioni sulle modalità di linguaggio, vedere [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span><span class="sxs-lookup"><span data-stu-id="ebfd0-131">For more information about language modes, see [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="ebfd0-132">Scegliere l'identità JEA</span><span class="sxs-lookup"><span data-stu-id="ebfd0-132">Choose the JEA identity</span></span>

<span data-ttu-id="ebfd0-133">Alla base, JEA richiede un'identità (account) da usare durante l'esecuzione di comandi da parte dell'utente connesso.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-133">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="ebfd0-134">L'utente decide quale identità JEA usare nel file di configurazione di sessione.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-134">You define which identity JEA uses in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="ebfd0-135">Account virtuale locale</span><span class="sxs-lookup"><span data-stu-id="ebfd0-135">Local Virtual Account</span></span>

<span data-ttu-id="ebfd0-136">Gli account virtuali locali sono utili quando i ruoli definiti per l'endpoint JEA vengono tutti usati per gestire il computer locale, e l'account Administrator locale è sufficiente per eseguire i comandi correttamente.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-136">Local virtual accounts are useful when all roles defined for the JEA endpoint are used to manage the local machine and a local administrator account is sufficient to run the commands successfully.</span></span>
<span data-ttu-id="ebfd0-137">Gli account virtuali sono account temporanei e univoci per un utente specifico. Sono validi solo per la durata della sessione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-137">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span> <span data-ttu-id="ebfd0-138">In un server membro o in una workstation gli account virtuali appartengono al gruppo **Administrators** del computer locale.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-138">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group.</span></span> <span data-ttu-id="ebfd0-139">In un controller di dominio Active Directory, gli account virtuali appartengono al gruppo **Domain Admins** del dominio.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-139">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="ebfd0-140">Se i ruoli definiti dalla configurazione di sessione non richiedono privilegi amministrativi completi, è possibile specificare i gruppi di sicurezza a cui appartiene l'account virtuale.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-140">If the roles defined by the session configuration don't require full administrative privilege, you can specify the security groups to which the virtual account will belong.</span></span> <span data-ttu-id="ebfd0-141">In un server membro o in una workstation, i gruppi di sicurezza specificati devono essere gruppi locali, non gruppi di un dominio.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-141">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="ebfd0-142">Quando vengono specificati uno o più gruppi di sicurezza, l'account virtuale non viene assegnato al gruppo locale o degli amministratori di dominio.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-142">When one or more security groups are specified, the virtual account isn't assigned to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> <span data-ttu-id="ebfd0-143">Agli account virtuali viene temporaneamente concesso il diritto relativo all'accesso come servizio nei criteri di sicurezza del server locale.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-143">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span> <span data-ttu-id="ebfd0-144">Se a uno dei gruppi di account virtuali è già stato concesso questo diritto nei criteri, il singolo account virtuale non sarà più aggiunto né rimosso dai criteri.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-144">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span> <span data-ttu-id="ebfd0-145">Può essere utile in alcuni scenari, ad esempio nei controller di dominio, dove le revisioni dei criteri di sicurezza dei controller di dominio sono sottoposte ad attenti controlli.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-145">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span> <span data-ttu-id="ebfd0-146">Questa opzione è disponibile solo in Windows Server 2016 con l'aggiornamento cumulativo di Novembre 2018 o aggiornamento cumulativo successivo e in Windows Server 2019 con l'aggiornamento cumulativo di Gennaio 2019 o aggiornamento cumulativo successivo.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-146">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="ebfd0-147">Account del servizio gestito del gruppo</span><span class="sxs-lookup"><span data-stu-id="ebfd0-147">Group-managed service account</span></span>

<span data-ttu-id="ebfd0-148">Un account del servizio gestito del gruppo è l'identità appropriata per gli utenti JEA quando devono accedere a risorse di rete come ad esempio condivisioni di file e servizi Web.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-148">A group-managed service account (GMSA) is the appropriate identity to use when JEA users need to access network resources such as file shares and web services.</span></span> <span data-ttu-id="ebfd0-149">Gli account del servizio gestito del gruppo offrono un'identità di dominio che può essere usata per eseguire l'autenticazione alle risorse di tutti i computer all'interno del dominio.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-149">GMSAs give you a domain identity that is used to authenticate with resources on any machine within the domain.</span></span> <span data-ttu-id="ebfd0-150">I diritti specificati da un account del servizio gestito del gruppo vengono determinati in base alle risorse a cui si accede.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-150">The rights that a GMSA provides are determined by the resources you're accessing.</span></span> <span data-ttu-id="ebfd0-151">Non si hanno diritti di amministratore sui computer o i servizi, a meno che l'amministratore del computer o del servizio abbia garantito esplicitamente tali diritti all'account del servizio gestito del gruppo.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-151">You don't have admin rights on any machines or services unless the machine or service administrator has explicitly granted those rights to the GMSA.</span></span>

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

<span data-ttu-id="ebfd0-152">Gli account del servizio gestito del gruppo devono essere usati solo quando è necessario:</span><span class="sxs-lookup"><span data-stu-id="ebfd0-152">GMSAs should only be used when necessary:</span></span>

- <span data-ttu-id="ebfd0-153">È difficile risalire alle azioni di un utente quando si usa un account del servizio gestito del gruppo.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-153">It's difficult to trace back actions to a user when using a GMSA.</span></span> <span data-ttu-id="ebfd0-154">Ogni utente condivide la stessa identità Esegui come.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-154">Every user shares the same run-as identity.</span></span> <span data-ttu-id="ebfd0-155">È necessario esaminare le trascrizioni e i log della sessione di PowerShell per correlare i singoli utenti con le relative azioni.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-155">You must review PowerShell session transcripts and logs to correlate individual users with their actions.</span></span>

- <span data-ttu-id="ebfd0-156">L'account del servizio gestito del gruppo può avere accesso a numerose risorse di rete a cui l'utente che si connette non ha bisogno di accedere.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-156">The GMSA may have access to many network resources that the connecting user doesn't need access to.</span></span> <span data-ttu-id="ebfd0-157">Limitare sempre le autorizzazioni effettive in una sessione JEA per seguire il principio del privilegio minimo.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-157">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="ebfd0-158">Gli account del servizio gestito del gruppo sono disponibili solo in computer aggiunti a un dominio con PowerShell 5.1 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-158">Group managed service accounts are only available on domain-joined machines using PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="ebfd0-159">Per altre informazioni sulla protezione di una sessione JEA, vedere l'articolo [Considerazioni sulla sicurezza](security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="ebfd0-159">For more information about securing a JEA session, see the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="ebfd0-160">Trascrizioni di sessione</span><span class="sxs-lookup"><span data-stu-id="ebfd0-160">Session transcripts</span></span>

<span data-ttu-id="ebfd0-161">È consigliabile configurare un endpoint JEA per registrare automaticamente le trascrizioni delle sessioni degli utenti.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-161">It's recommended that you configure a JEA endpoint to automatically record transcripts of users' sessions.</span></span> <span data-ttu-id="ebfd0-162">Le trascrizioni delle sessione di PowerShell contengono informazioni sull'utente che si connette, sulle identità RunAs assegnate e sui comandi eseguiti dall'utente.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-162">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span> <span data-ttu-id="ebfd0-163">Queste informazioni possono essere utili a un gruppo di controllo che ha bisogno di sapere chi ha eseguito una modifica specifica a un sistema.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-163">They can be useful to an auditing team who needs to understand who made a specific change to a system.</span></span>

<span data-ttu-id="ebfd0-164">Per configurare la trascrizione automatica nel file di configurazione sessione, specificare il percorso a una cartella in cui le trascrizioni devono essere archiviate.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-164">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="ebfd0-165">Le trascrizioni vengono scritte nella cartella dall'account **di sistema locale**, che richiede l'accesso in lettura e scrittura alla directory.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-165">Transcripts are written to the folder by the **Local System** account, which requires read and write access to the directory.</span></span> <span data-ttu-id="ebfd0-166">Gli utenti standard non devono avere accesso alla cartella.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-166">Standard users should have no access to the folder.</span></span> <span data-ttu-id="ebfd0-167">Limitare il numero di amministratori della sicurezza che hanno accesso alla cartella per controllare le trascrizioni.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-167">Limit the number of security administrators that have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="ebfd0-168">Unità utente</span><span class="sxs-lookup"><span data-stu-id="ebfd0-168">User drive</span></span>

<span data-ttu-id="ebfd0-169">Se gli utenti che si connettono hanno bisogno di copiare file dal e nell'endpoint JEA, è possibile abilitare l'unità utente nel file di configurazione di sessione.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-169">If your connecting users need to copy files to or from the JEA endpoint, you can enable the user drive in the session configuration file.</span></span> <span data-ttu-id="ebfd0-170">L'unità utente è una **PSDrive** con mapping a una cartella univoca per ogni utente che si connette.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-170">The user drive is a **PSDrive** that is mapped to a unique folder for each connecting user.</span></span> <span data-ttu-id="ebfd0-171">Questa cartella consente agli utenti di copiare file nel e dal sistema senza che abbiano accesso all'intero file system e senza esporre il provider FileSystem.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-171">This folder allows users to copy files to or from the system without giving them access to the full file system or exposing the FileSystem provider.</span></span> <span data-ttu-id="ebfd0-172">Il contenuto dell'unità utente è persistente tra le sessioni per consentire situazioni in cui la connettività di rete viene interrotta.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-172">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="ebfd0-173">Per impostazione predefinita, l'unità utente consente di archiviare massimo 50 MB di dati per ogni utente.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-173">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span> <span data-ttu-id="ebfd0-174">È possibile limitare la quantità di dati utilizzabile da un utente tramite il campo *UserDriveMaximumSize*.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-174">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="ebfd0-175">Se si preferisce che i dati nell'unità utente non siano persistenti, è possibile configurare un'attività pianificata nel sistema per pulire automaticamente la cartella ogni notte.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-175">If you don't want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="ebfd0-176">L'unità utente è disponibile solo in PowerShell 5.1 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-176">The user drive is only available in PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="ebfd0-177">Per altre informazioni sulle PSDrive, vedere [Gestione delle unità di PowerShell](/powershell/scripting/samples/managing-windows-powershell-drives).</span><span class="sxs-lookup"><span data-stu-id="ebfd0-177">For more information about PSDrives, see [Managing PowerShell drives](/powershell/scripting/samples/managing-windows-powershell-drives).</span></span>

### <a name="role-definitions"></a><span data-ttu-id="ebfd0-178">Definizioni dei ruoli</span><span class="sxs-lookup"><span data-stu-id="ebfd0-178">Role definitions</span></span>

<span data-ttu-id="ebfd0-179">Le definizioni dei ruoli in un file di configurazione sessione definiscono il mapping degli **utenti** ai **ruoli**.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-179">Role definitions in a session configuration file define the mapping of **users** to **roles**.</span></span> <span data-ttu-id="ebfd0-180">A ogni utente o gruppo incluso in questo campo viene automaticamente concessa l'autorizzazione per l'endpoint JEA alla registrazione.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-180">Every user or group included in this field is granted permission to the JEA endpoint when it's registered.</span></span>
<span data-ttu-id="ebfd0-181">Ogni utente o gruppo può essere incluso come chiave nella tabella hash solo una volta, ma gli possono essere assegnati più ruoli.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-181">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span> <span data-ttu-id="ebfd0-182">Il nome della funzionalità del ruolo deve essere il nome del file delle funzionalità del ruolo, senza l'estensione `.psrc`.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-182">The name of the role capability should be the name of the role capability file, without the `.psrc` extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="ebfd0-183">Se un utente appartiene a più gruppi nella definizione del ruolo, avrà accesso ai ruoli di ogni gruppo.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-183">If a user belongs to more than one group in the role definition, they get access to the roles of each.</span></span> <span data-ttu-id="ebfd0-184">Se due ruoli concedono l'accesso agli stessi cmdlet, all'utente viene concesso il set di parametri più permissivo.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-184">When two roles grant access to the same cmdlets, the most permissive parameter set is granted to the user.</span></span>

<span data-ttu-id="ebfd0-185">Quando si specificano utenti o gruppi locali nel campo delle definizioni di ruolo, assicurarsi di usare il nome del computer, non **localhost** o caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-185">When specifying local users or groups in the role definitions field, be sure to use the computer name, not **localhost** or wildcards.</span></span> <span data-ttu-id="ebfd0-186">È possibile verificare il nome del computer controllando la variabile `$env:COMPUTERNAME`.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-186">You can check the computer name by inspecting the `$env:COMPUTERNAME` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="ebfd0-187">Ordine di ricerca delle funzionalità del ruolo</span><span class="sxs-lookup"><span data-stu-id="ebfd0-187">Role capability search order</span></span>

<span data-ttu-id="ebfd0-188">Come illustrato nell'esempio precedente, viene fatto riferimento alle funzionalità del ruolo tramite il nome di base del file delle funzionalità del ruolo.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-188">As shown in the example above, role capabilities are referenced by the base name of the role capability file.</span></span> <span data-ttu-id="ebfd0-189">Il nome di base di un file è il nome file senza estensione.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-189">The base name of a file is the filename without the extension.</span></span> <span data-ttu-id="ebfd0-190">Se nel sistema sono disponibili più funzionalità del ruolo con lo stesso nome, PowerShell usa l'ordine di ricerca implicito per selezionare il file delle funzionalità del ruolo effettivo.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-190">If multiple role capabilities are available on the system with the same name, PowerShell uses its implicit search order to select the effective role capability file.</span></span> <span data-ttu-id="ebfd0-191">JEA **non** concede accesso a tutti i file delle funzionalità del ruolo con lo stesso nome.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-191">JEA does **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="ebfd0-192">JEA usa la variabile di ambiente `$env:PSModulePath` per determinare i percorsi in cui cercare i file delle funzionalità di ruolo.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-192">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span> <span data-ttu-id="ebfd0-193">All'interno di ognuno di questi percorsi JEA cerca moduli di PowerShell validi che contengono una sottocartella "RoleCapabilities".</span><span class="sxs-lookup"><span data-stu-id="ebfd0-193">Within each of those paths, JEA looks for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span> <span data-ttu-id="ebfd0-194">Come per l'importazione dei moduli, JEA preferisce le funzionalità di ruolo fornite con Windows rispetto alle funzionalità di ruolo personalizzate con lo stesso nome.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-194">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>

<span data-ttu-id="ebfd0-195">Per tutti gli altri conflitti di nome, la precedenza è determinata dall'ordine in cui Windows enumera i file nella directory.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-195">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory.</span></span> <span data-ttu-id="ebfd0-196">L'ordine non è necessariamente alfabetico.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-196">The order isn't guaranteed to be alphabetical.</span></span> <span data-ttu-id="ebfd0-197">Il primo file di funzionalità del ruolo trovato che corrisponde al nome specificato viene usato per l'utente che si connette.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-197">The first role capability file found that matches the specified name is used for the connecting user.</span></span> <span data-ttu-id="ebfd0-198">Poiché l'ordine di ricerca delle funzionalità del ruolo non è deterministico, **è consigliabile** che le funzionalità del ruolo abbiano nomi file univoci.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-198">Since the role capability search order isn't deterministic, it's **strongly recommended** that role capabilities have unique filenames.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="ebfd0-199">Regole di accesso condizionale</span><span class="sxs-lookup"><span data-stu-id="ebfd0-199">Conditional access rules</span></span>

<span data-ttu-id="ebfd0-200">A tutti gli utenti e gruppi inclusi nel campo **RoleDefinitions** viene concesso automaticamente l'accesso agli endpoint JEA.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-200">All users and groups included in the **RoleDefinitions** field are automatically granted access to JEA endpoints.</span></span> <span data-ttu-id="ebfd0-201">Le regole di accesso condizionale consentono di ottimizzare l'accesso e richiedono che gli utenti appartengano ai gruppi di sicurezza aggiuntivi che non incidono sui ruoli ai quali sono stati assegnati.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-201">Conditional access rules allow you to refine this access and require users to belong to additional security groups that don't impact the roles to which they're assigned.</span></span> <span data-ttu-id="ebfd0-202">Ciò può essere utile se si vuole integrare una soluzione di gestione di accesso privilegiato just-in-time, l'autenticazione smart card o altra soluzione di autenticazione a più fattori con JEA.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-202">This is useful when you want to integrate a just-in-time privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="ebfd0-203">Le regole di accesso condizionale sono definite nel campo RequiredGroups di un file di configurazione sessione.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-203">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="ebfd0-204">In questo file è possibile specificare una tabella hash (facoltativamente nidificata) che usi le chiavi "And" e "Or" per costruire le regole.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-204">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="ebfd0-205">Di seguito sono riportati alcuni esempi di come usare questo campo:</span><span class="sxs-lookup"><span data-stu-id="ebfd0-205">Here are some examples of how to use this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> <span data-ttu-id="ebfd0-206">Le regole di accesso condizionale sono disponibili solo in PowerShell 5.1 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-206">Conditional access rules are only available in PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="ebfd0-207">Altre proprietà</span><span class="sxs-lookup"><span data-stu-id="ebfd0-207">Other properties</span></span>

<span data-ttu-id="ebfd0-208">I file di configurazione sessione consentono di eseguire tutte le operazioni di un file delle funzionalità del ruolo, ma non possono offrire agli utenti che si connettono accesso ai diversi comandi.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-208">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span> <span data-ttu-id="ebfd0-209">Se si vuole concedere agli utenti l'accesso a specifici cmdlet, funzioni o provider, è possibile impostarlo direttamente nel file di configurazione sessione.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-209">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="ebfd0-210">Per un elenco completo delle proprietà supportate nel file di configurazione sessione, eseguire `Get-Help New-PSSessionConfigurationFile -Full`.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-210">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="ebfd0-211">Test di un file di configurazione sessione</span><span class="sxs-lookup"><span data-stu-id="ebfd0-211">Testing a session configuration file</span></span>

<span data-ttu-id="ebfd0-212">È possibile testare una configurazione sessione tramite il cmdlet [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile).</span><span class="sxs-lookup"><span data-stu-id="ebfd0-212">You can test a session configuration using the [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span> <span data-ttu-id="ebfd0-213">È consigliabile testare il file di configurazione di sessione se il file `.pssc` è stato modificato manualmente.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-213">It's recommended that you test your session configuration file if you've manually edited the `.pssc` file.</span></span> <span data-ttu-id="ebfd0-214">Il test garantisce che la sintassi sia corretta.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-214">Testing ensures the syntax is correct.</span></span> <span data-ttu-id="ebfd0-215">Se un file di configurazione di sessione ha esito negativo in seguito al test, non può essere registrato nel sistema.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-215">If a session configuration file fails this test, it can't be registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="ebfd0-216">File di configurazione sessione d'esempio</span><span class="sxs-lookup"><span data-stu-id="ebfd0-216">Sample session configuration file</span></span>

<span data-ttu-id="ebfd0-217">L'esempio seguente illustra come creare e convalidare una configurazione di sessione per JEA.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-217">The following example shows how to create and validate a session configuration for JEA.</span></span> <span data-ttu-id="ebfd0-218">Le definizioni del ruolo vengono create e archiviate nella variabile `$roles` per motivi di praticità e leggibilità.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-218">The role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span> <span data-ttu-id="ebfd0-219">Non è un requisito obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-219">It isn't a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="ebfd0-220">Aggiornamento dei file di configurazione sessione</span><span class="sxs-lookup"><span data-stu-id="ebfd0-220">Updating session configuration files</span></span>

<span data-ttu-id="ebfd0-221">Per modificare le proprietà di una configurazione di sessione JEA, tra cui il mapping degli utenti ai ruoli, è necessario [annullare la registrazione](register-jea.md#unregistering-jea-configurations).</span><span class="sxs-lookup"><span data-stu-id="ebfd0-221">To change the properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations).</span></span> <span data-ttu-id="ebfd0-222">In seguito [registrare nuovamente](register-jea.md) la configurazione di sessione JEA usando un file di configurazione di sessione aggiornato.</span><span class="sxs-lookup"><span data-stu-id="ebfd0-222">Then, [re-register](register-jea.md) the JEA session configuration using an updated session configuration file.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ebfd0-223">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="ebfd0-223">Next steps</span></span>

- [<span data-ttu-id="ebfd0-224">Registrare una configurazione JEA</span><span class="sxs-lookup"><span data-stu-id="ebfd0-224">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="ebfd0-225">Creare ruoli JEA</span><span class="sxs-lookup"><span data-stu-id="ebfd0-225">Author JEA roles</span></span>](role-capabilities.md)
