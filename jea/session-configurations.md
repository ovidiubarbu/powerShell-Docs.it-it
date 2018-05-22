---
ms.date: 06/12/2017
keywords: jea,powershell,sicurezza
title: Configurazioni della sessione JEA
ms.openlocfilehash: 3e5a663be8e7aba09a2592c278224cd892c89a20
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
---
# <a name="jea-session-configurations"></a><span data-ttu-id="68557-103">Configurazioni della sessione JEA</span><span class="sxs-lookup"><span data-stu-id="68557-103">JEA Session Configurations</span></span>

> <span data-ttu-id="68557-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="68557-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="68557-105">Un endpoint JEA viene registrato in un sistema tramite la creazione e la registrazione di un file di configurazione sessione di PowerShell in un modo specifico.</span><span class="sxs-lookup"><span data-stu-id="68557-105">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file in a specific way.</span></span>
<span data-ttu-id="68557-106">Le configurazioni sessione determinano *chi* può usare l'endpoint JEA e a quali ruoli potranno avere accesso gli utenti.</span><span class="sxs-lookup"><span data-stu-id="68557-106">Session configurations determine *who* can use the JEA endpoint, and which role(s) they will have access to.</span></span>
<span data-ttu-id="68557-107">Definiscono anche impostazioni globali che vengono applicate agli utenti di qualsiasi ruolo nella sessione JEA.</span><span class="sxs-lookup"><span data-stu-id="68557-107">They also define global settings that apply to users of any role in the JEA session.</span></span>

<span data-ttu-id="68557-108">Questo argomento illustra come creare un file di configurazione sessione di PowerShell e registrare un endpoint JEA.</span><span class="sxs-lookup"><span data-stu-id="68557-108">This topic describes how to create a PowerShell session configuration file and register a JEA endpoint.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="68557-109">Creare un file di configurazione sessione</span><span class="sxs-lookup"><span data-stu-id="68557-109">Create a session configuration file</span></span>

<span data-ttu-id="68557-110">Per registrare un endpoint JEA, è necessario specificare come deve essere configurato l'endpoint.</span><span class="sxs-lookup"><span data-stu-id="68557-110">In order to register a JEA endpoint, you need to specify how that endpoint should be configured.</span></span>
<span data-ttu-id="68557-111">Ci sono molte opzioni da tenere in considerazione, ma le più importanti sono relative agli utenti che devono avere accesso all'endpoint JEA, ai ruoli che verranno assegnati, a quale identità verrà usata da JEA in maniera invisibile e al nome dell'endpoint JEA.</span><span class="sxs-lookup"><span data-stu-id="68557-111">There are many options to consider here, the most important of which being who should have access to the JEA endpoint, which roles will they be assigned, which identity will JEA use under the covers, and what will be the name of the JEA endpoint.</span></span>
<span data-ttu-id="68557-112">Tutti questi elementi verranno definiti in un file di configurazione sessione di PowerShell, ovvero in un file di dati con estensione PSSC.</span><span class="sxs-lookup"><span data-stu-id="68557-112">These are all defined in a PowerShell session configuration file, which is a PowerShell data file ending with a .pssc extension.</span></span>

<span data-ttu-id="68557-113">Per creare un file di struttura della configurazione sessione per gli endpoint JEA, eseguire il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="68557-113">To create a skeleton session configuration file for JEA endpoints, run the following command.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="68557-114">Per impostazione predefinita, solo le opzioni di configurazione più comuni sono incluse nel file di struttura.</span><span class="sxs-lookup"><span data-stu-id="68557-114">Only the most common configuration options are included in the skeleton file by default.</span></span>
> <span data-ttu-id="68557-115">Usare l'opzione `-Full` per includere tutte le impostazioni applicabili nel file PSSC generato.</span><span class="sxs-lookup"><span data-stu-id="68557-115">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="68557-116">È possibile aprire il file di configurazione sessione in qualsiasi editor di testo.</span><span class="sxs-lookup"><span data-stu-id="68557-116">You can open the session configuration file in any text editor.</span></span>
<span data-ttu-id="68557-117">Il campo `-SessionType RestrictedRemoteServer` indica che la configurazione sessione verrà usata da JEA per una gestione sicura.</span><span class="sxs-lookup"><span data-stu-id="68557-117">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration will be used by JEA for secure management.</span></span>
<span data-ttu-id="68557-118">Le sessioni configurate in questo modo funzioneranno in [modalità NoLanguage](https://technet.microsoft.com/library/dn433292.aspx) e hanno disponibili solo gli 8 comandi (e alias) predefiniti seguenti:</span><span class="sxs-lookup"><span data-stu-id="68557-118">Sessions configured this way will operate in [NoLanguage mode](https://technet.microsoft.com/library/dn433292.aspx) and only have the following 8 default commands (and aliases) available:</span></span>

- <span data-ttu-id="68557-119">Clear-Host (cls, clear)</span><span class="sxs-lookup"><span data-stu-id="68557-119">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="68557-120">Exit-PSSession (exsn, exit)</span><span class="sxs-lookup"><span data-stu-id="68557-120">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="68557-121">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="68557-121">Get-Command (gcm)</span></span>
- <span data-ttu-id="68557-122">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="68557-122">Get-FormatData</span></span>
- <span data-ttu-id="68557-123">Get-Help</span><span class="sxs-lookup"><span data-stu-id="68557-123">Get-Help</span></span>
- <span data-ttu-id="68557-124">Measure-Object (measure)</span><span class="sxs-lookup"><span data-stu-id="68557-124">Measure-Object (measure)</span></span>
- <span data-ttu-id="68557-125">Out-Default</span><span class="sxs-lookup"><span data-stu-id="68557-125">Out-Default</span></span>
- <span data-ttu-id="68557-126">Select-Object (select)</span><span class="sxs-lookup"><span data-stu-id="68557-126">Select-Object (select)</span></span>

<span data-ttu-id="68557-127">Non sono disponibili provider PowerShell e nemmeno programmi esterni (file eseguibili, script e così via).</span><span class="sxs-lookup"><span data-stu-id="68557-127">No PowerShell providers are available, nor are any external programs (executables, scripts, etc.).</span></span>

<span data-ttu-id="68557-128">Molti altri campi possono essere configurati per la sessione JEA.</span><span class="sxs-lookup"><span data-stu-id="68557-128">There are several other fields you will want to configure for the JEA session.</span></span>
<span data-ttu-id="68557-129">Questi verranno illustrati nelle sezioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="68557-129">They are covered in the following sections.</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="68557-130">Scegliere l'identità JEA</span><span class="sxs-lookup"><span data-stu-id="68557-130">Choose the JEA identity</span></span>

<span data-ttu-id="68557-131">Alla base, JEA richiede un'identità (account) da usare durante l'esecuzione di comandi da parte dell'utente connesso.</span><span class="sxs-lookup"><span data-stu-id="68557-131">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="68557-132">L'utente decide quale identità JEA userà nel file di configurazione sessione.</span><span class="sxs-lookup"><span data-stu-id="68557-132">You decide which identity JEA will use in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="68557-133">Account virtuale locale</span><span class="sxs-lookup"><span data-stu-id="68557-133">Local Virtual Account</span></span>

<span data-ttu-id="68557-134">Se i ruoli supportati da questo endpoint JEA sono tutti usati per gestire il computer locale, e l'account di amministratore locale è sufficiente per eseguire i comandi correttamente, è necessario configurare JEA per usare un account virtuale locale.</span><span class="sxs-lookup"><span data-stu-id="68557-134">If the roles supported by this JEA endpoint are all used to manage the local machine, and a local administrator account is sufficient to run the commands succesfully, you should configure JEA to use a local virtual account.</span></span>
<span data-ttu-id="68557-135">Gli account virtuali sono account temporanei e univoci per un utente specifico. Sono validi solo per la durata della sessione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="68557-135">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span>
<span data-ttu-id="68557-136">In un server membro o in una workstation, gli account virtuali appartengono al gruppo **Administrators** del computer locale e hanno accesso alla maggior parte delle risorse di sistema.</span><span class="sxs-lookup"><span data-stu-id="68557-136">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group, and have access to most system resources.</span></span>
<span data-ttu-id="68557-137">In un controller di dominio Active Directory, gli account virtuali appartengono al gruppo **Domain Admins** del dominio.</span><span class="sxs-lookup"><span data-stu-id="68557-137">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="68557-138">Se i ruoli supportati dalla configurazione sessione non richiedono privilegi estesi, è possibile specificare facoltativamente i gruppi di sicurezza a cui appartiene l'account virtuale.</span><span class="sxs-lookup"><span data-stu-id="68557-138">If the roles supported by the session configuration do not require such broad privileges, you can optionally specify the security groups to which the virtual account will belong.</span></span>
<span data-ttu-id="68557-139">In un server membro o in una workstation, i gruppi di sicurezza specificati devono essere gruppi locali, non gruppi di un dominio.</span><span class="sxs-lookup"><span data-stu-id="68557-139">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="68557-140">Quando si specifica uno o più gruppi di sicurezza, l'account virtuale non apparterrà più al gruppo locale o Domain Administrators.</span><span class="sxs-lookup"><span data-stu-id="68557-140">When one or more security groups is specified, the virtual account will no longer belong to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a><span data-ttu-id="68557-141">Account del servizio gestito del gruppo</span><span class="sxs-lookup"><span data-stu-id="68557-141">Group Managed Service Account</span></span>


<span data-ttu-id="68557-142">Per gli scenari che richiedono all'utente JEA di accedere alle risorse di rete, ad esempio altri computer o i servizi Web, un account del servizio gestito del gruppo (gMSA) è un'identità più appropriata da usare.</span><span class="sxs-lookup"><span data-stu-id="68557-142">For scenarios requiring the JEA user to access network resources such as other machines or web services, a group managed service account (gMSA) is a more appropriate identity to use.</span></span>
<span data-ttu-id="68557-143">Gli account gMSA offrono un'identità di dominio che può essere usata per eseguire l'autenticazione alle risorse di tutti i computer all'interno del dominio.</span><span class="sxs-lookup"><span data-stu-id="68557-143">gMSA accounts give you a domain identity which can be used to authenticate against resources on any machine within the domain.</span></span>
<span data-ttu-id="68557-144">I diritti offerti dall'account gMSA sono determinati dalle risorse a cui si accede.</span><span class="sxs-lookup"><span data-stu-id="68557-144">The rights the gMSA account gives you is determined by the resources you are accessing.</span></span>
<span data-ttu-id="68557-145">Non si hanno automaticamente diritti di amministratore su tutti i computer o servizi, se l'amministratore del computer/servizio non ha esplicitamente concesso i privilegi di amministratore all'account gMSA.</span><span class="sxs-lookup"><span data-stu-id="68557-145">You will not automatically have admin rights on any machines or services unless the machine/service administrator has explicitly granted the gMSA account admin privileges.</span></span>

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

<span data-ttu-id="68557-146">Gli account gMSA dovrebbero essere usati solo quando è necessario accedere alle risorse di rete per alcuni motivi:</span><span class="sxs-lookup"><span data-stu-id="68557-146">gMSA accounts should only be used when access to network resources are required for a few reasons:</span></span>

- <span data-ttu-id="68557-147">È molto difficile tracciare le azioni di un utente quando si usa un account gMSA perché ogni utente condivide la stessa identità RunAs.</span><span class="sxs-lookup"><span data-stu-id="68557-147">It is harder to trace back actions to a user when using a gMSA account since every user shares the same run-as identity.</span></span> <span data-ttu-id="68557-148">È necessario esaminare le trascrizioni della sessione di PowerShell e i log per correlare gli utenti con le relative azioni.</span><span class="sxs-lookup"><span data-stu-id="68557-148">You will need to consult PowerShell session transcripts and logs to correlate users with their actions.</span></span>

- <span data-ttu-id="68557-149">L'account gMSA potrebbe avere accesso a numerose risorse di rete a cui l'utente che si connette non ha bisogno di accedere.</span><span class="sxs-lookup"><span data-stu-id="68557-149">The gMSA account may have access to many network resources which the connecting user does not need access to.</span></span> <span data-ttu-id="68557-150">Limitare sempre le autorizzazioni effettive in una sessione JEA per seguire il principio del privilegio minimo.</span><span class="sxs-lookup"><span data-stu-id="68557-150">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="68557-151">Gli account del servizio gestito del gruppo sono disponibili solo in Windows PowerShell 5.1 o versione successiva e nei computer uniti in un dominio.</span><span class="sxs-lookup"><span data-stu-id="68557-151">Group managed service accounts are only available in Windows PowerShell 5.1 or newer and on domain-joined machines.</span></span>


#### <a name="more-information-about-run-as-users"></a><span data-ttu-id="68557-152">Altre informazioni su utenti RunAs</span><span class="sxs-lookup"><span data-stu-id="68557-152">More information about run as users</span></span>

<span data-ttu-id="68557-153">Altre informazioni sulle identità RunAs e su come influenzano la sicurezza di una sessione JEA sono reperibili nell'articolo relativo alle [considerazioni sulla sicurezza](security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="68557-153">Additional information about run as identities and how they factor into the security of a JEA session can be found in the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="68557-154">Trascrizioni di sessione</span><span class="sxs-lookup"><span data-stu-id="68557-154">Session transcripts</span></span>

<span data-ttu-id="68557-155">È consigliabile configurare il file di configurazione sessione JEA per registrare automaticamente le trascrizioni delle sessioni degli utenti.</span><span class="sxs-lookup"><span data-stu-id="68557-155">It is recommended that you configure a JEA session configuration file to automatically record transcripts of users' sessions.</span></span>
<span data-ttu-id="68557-156">Le trascrizioni delle sessione di PowerShell contengono informazioni sull'utente che si connette, sulle identità RunAs assegnate e sui comandi eseguiti dall'utente.</span><span class="sxs-lookup"><span data-stu-id="68557-156">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span>
<span data-ttu-id="68557-157">Queste informazioni possono essere utili a un gruppo di controllo che ha bisogno di sapere chi ha eseguito una modifica specifica a un sistema.</span><span class="sxs-lookup"><span data-stu-id="68557-157">They can be useful to an auditing team who needs to understand who performed a specific change to a system.</span></span>

<span data-ttu-id="68557-158">Per configurare la trascrizione automatica nel file di configurazione sessione, specificare il percorso a una cartella in cui le trascrizioni devono essere archiviate.</span><span class="sxs-lookup"><span data-stu-id="68557-158">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="68557-159">La cartella specificata deve essere configurata per impedire agli utenti di modificare o eliminare i dati contenuti.</span><span class="sxs-lookup"><span data-stu-id="68557-159">The specified folder should be configured to prevent users from modifying or deleting any data in it.</span></span>
<span data-ttu-id="68557-160">Le trascrizioni vengono scritte nella cartella dall'account del sistema locale, che richiede l'accesso in lettura e scrittura alla directory.</span><span class="sxs-lookup"><span data-stu-id="68557-160">Transcripts are written to the folder by the Local System account, which requires read and write access to the directory.</span></span>
<span data-ttu-id="68557-161">Gli utenti standard non devono avere accesso alla cartella e solo un set limitato di amministratori della sicurezza dovrebbe avere accesso per controllare le trascrizioni.</span><span class="sxs-lookup"><span data-stu-id="68557-161">Standard users should have no access to the folder, and a limited set of security administrators should have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="68557-162">Unità utente</span><span class="sxs-lookup"><span data-stu-id="68557-162">User drive</span></span>

<span data-ttu-id="68557-163">Se gli utenti che si connettono hanno bisogno di copiare file dal e nell'endpoint JEA per eseguire un comando, è possibile abilitare l'unità utente nel file di configurazione sessione.</span><span class="sxs-lookup"><span data-stu-id="68557-163">If your connecting users will need to copy files to/from the JEA endpoint in order to run a command, you can enable the user drive in the session configuration file.</span></span>
<span data-ttu-id="68557-164">L'unità utente è una [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) con mapping a una cartella univoca per ogni utente che si connette.</span><span class="sxs-lookup"><span data-stu-id="68557-164">The user drive is a [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) that is mapped to a unique folder for each connecting user.</span></span>
<span data-ttu-id="68557-165">Questa cartella ha lo scopo di offrire uno spazio agli utenti per copiare file nel e dal sistema senza concedere accesso al sistema intero o al provider del file system.</span><span class="sxs-lookup"><span data-stu-id="68557-165">This folder serves as a space for them to copy files to/from the system, without giving them access to the full file system or exposing the FileSystem provider.</span></span>
<span data-ttu-id="68557-166">Il contenuto dell'unità utente è persistente tra le sessioni per consentire situazioni in cui la connettività di rete viene interrotta.</span><span class="sxs-lookup"><span data-stu-id="68557-166">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="68557-167">Per impostazione predefinita, l'unità utente consente di archiviare massimo 50 MB di dati per ogni utente.</span><span class="sxs-lookup"><span data-stu-id="68557-167">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span>
<span data-ttu-id="68557-168">È possibile limitare la quantità di dati utilizzabile da un utente tramite il campo *UserDriveMaximumSize*.</span><span class="sxs-lookup"><span data-stu-id="68557-168">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="68557-169">Se si preferisce che i dati nell'unità utente non siano persistenti, è possibile configurare un'attività pianificata nel sistema per pulire automaticamente la cartella ogni notte.</span><span class="sxs-lookup"><span data-stu-id="68557-169">If you do not want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="68557-170">L'unità utente è solo disponibile in Windows PowerShell 5.1 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="68557-170">The user drive is only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="role-definitions"></a><span data-ttu-id="68557-171">Definizioni dei ruoli</span><span class="sxs-lookup"><span data-stu-id="68557-171">Role definitions</span></span>

<span data-ttu-id="68557-172">Le definizioni dei ruoli in un file di configurazione sessione definiscono il mapping degli *utenti* ai *ruoli*.</span><span class="sxs-lookup"><span data-stu-id="68557-172">Role definitions in a session configuration file define the mapping of *users* to *roles*.</span></span>
<span data-ttu-id="68557-173">A ogni utente o gruppo incluso in questo campo verrà automaticamente concessa l'autorizzazione per l'endpoint JEA alla registrazione.</span><span class="sxs-lookup"><span data-stu-id="68557-173">Every user or group included in this field will automatically be granted permission to the JEA endpoint when it is registered.</span></span>
<span data-ttu-id="68557-174">Ogni utente o gruppo può essere incluso come chiave nella tabella hash solo una volta, ma gli possono essere assegnati più ruoli.</span><span class="sxs-lookup"><span data-stu-id="68557-174">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span>
<span data-ttu-id="68557-175">Il nome della funzionalità del ruolo deve essere il nome del file delle funzionalità del ruolo, senza l'estensione PSRC.</span><span class="sxs-lookup"><span data-stu-id="68557-175">The name of the role capability should be the name of the role capability file, without the .psrc extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="68557-176">Se un utente appartiene a più gruppi nella definizione del ruolo, avrà accesso ai ruoli di ogni gruppo.</span><span class="sxs-lookup"><span data-stu-id="68557-176">If a user belongs to more than one group in the role definition, they will get access to the roles of each.</span></span>
<span data-ttu-id="68557-177">Se due ruoli concedono l'accesso agli stessi cmdlet, il set di parametri più permissivo verrà concesso all'utente.</span><span class="sxs-lookup"><span data-stu-id="68557-177">If two roles grant access to the same cmdlets, the most permissive parameter set will be granted to the user.</span></span>

<span data-ttu-id="68557-178">Quando si specificano utenti o gruppi locali nel campo delle definizioni di ruolo, assicurarsi di usare il nome del computer (non *localhost* o *.*) prima della barra rovesciata.</span><span class="sxs-lookup"><span data-stu-id="68557-178">When specifying local users or groups in the role definitions field, be sure to use the computer name (not *localhost* or *.*) before the backslash.</span></span>
<span data-ttu-id="68557-179">È possibile verificare il nome del computer controllando la variabile `$env:computername`.</span><span class="sxs-lookup"><span data-stu-id="68557-179">You can check the computer name by inspecting the `$env:computername` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="68557-180">Ordine di ricerca delle funzionalità del ruolo</span><span class="sxs-lookup"><span data-stu-id="68557-180">Role capability search order</span></span>
<span data-ttu-id="68557-181">Come illustrato nell'esempio precedente, le funzionalità del ruolo vengono indicate dal nome flat (nome file senza estensione) del file delle funzionalità del ruolo.</span><span class="sxs-lookup"><span data-stu-id="68557-181">As shown in the example above, role capabilities are referenced by the flat name (filename without the extension) of the role capability file.</span></span>
<span data-ttu-id="68557-182">Se più funzionalità del ruolo sono disponibili nel sistema con lo stesso nome flat, PowerShell userà l'ordine di ricerca implicito per selezionare il file delle funzionalità del ruolo effettivo.</span><span class="sxs-lookup"><span data-stu-id="68557-182">If multiple role capabilities are available on the system with the same flat name, PowerShell will use its implicit search order to select the effective role capability file.</span></span>
<span data-ttu-id="68557-183">**Non** concederà accesso a tutti i file delle funzionalità del ruolo con lo stesso nome.</span><span class="sxs-lookup"><span data-stu-id="68557-183">It will **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="68557-184">JEA usa la variabile di ambiente `$env:PSModulePath` per determinare i percorsi in cui cercare i file delle funzionalità di ruolo.</span><span class="sxs-lookup"><span data-stu-id="68557-184">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span>
<span data-ttu-id="68557-185">All'interno di ognuno di questi percorsi, JEA cercherà moduli di PowerShell validi che contengono una sottocartella "RoleCapabilities".</span><span class="sxs-lookup"><span data-stu-id="68557-185">Within each of those paths, JEA will look for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span>
<span data-ttu-id="68557-186">Come per l'importazione dei moduli, JEA preferisce le funzionalità di ruolo fornite con Windows rispetto alle funzionalità di ruolo personalizzate con lo stesso nome.</span><span class="sxs-lookup"><span data-stu-id="68557-186">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>
<span data-ttu-id="68557-187">Per tutti gli altri conflitti di nome, la precedenza è determinata dall'ordine in cui Windows enumera i file nella directory (non necessariamente alfabetico).</span><span class="sxs-lookup"><span data-stu-id="68557-187">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory (not guaranteed to be alphabetically).</span></span>
<span data-ttu-id="68557-188">Il primo file di funzionalità di ruolo trovato che corrisponde al nome desiderato verrà usato per l'utente che si connette.</span><span class="sxs-lookup"><span data-stu-id="68557-188">The first role capability file found that matches the desired name will be used for the connecting user.</span></span>

<span data-ttu-id="68557-189">Dato che l'ordine di ricerca delle funzionalità di ruolo non è deterministico quando due o più funzionalità di ruolo hanno lo stesso nome, è **consigliabile** assicurarsi che le funzionalità di ruolo abbiano nomi univoci nel computer in uso.</span><span class="sxs-lookup"><span data-stu-id="68557-189">Since the role capability search order is not deterministic when two or more role capabilities share the same name, it is **strongly recommended** that you ensure role capabilities have unique names on your machine.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="68557-190">Regole di accesso condizionale</span><span class="sxs-lookup"><span data-stu-id="68557-190">Conditional access rules</span></span>

<span data-ttu-id="68557-191">A tutti gli utenti e gruppi inclusi nel campo RoleDefinitions viene concesso automaticamente l'accesso agli endpoint JEA.</span><span class="sxs-lookup"><span data-stu-id="68557-191">All users and groups included in the RoleDefinitions field are automatically granted access to JEA endpoints.</span></span>
<span data-ttu-id="68557-192">Le regole di accesso condizionale consentono di ottimizzare l'accesso e richiedono che gli utenti appartengano ai gruppi di sicurezza aggiuntivi che non incidono sui ruoli ai quali sono stati assegnati.</span><span class="sxs-lookup"><span data-stu-id="68557-192">Conditional access rules allow you to refine this access and require users to belong to additional security groups which do not impact the roles which they are assigned.</span></span>
<span data-ttu-id="68557-193">Ciò può essere utile se si vuole integrare una soluzione di gestione di accesso privilegiato "Just in Time", l'autenticazione smart card o altra soluzione di autenticazione a più fattori con JEA.</span><span class="sxs-lookup"><span data-stu-id="68557-193">This can be useful if you want to integrate a "just in time" privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="68557-194">Le regole di accesso condizionale sono definite nel campo RequiredGroups di un file di configurazione sessione.</span><span class="sxs-lookup"><span data-stu-id="68557-194">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="68557-195">In questo file è possibile specificare una tabella hash (facoltativamente nidificata) che usi le chiavi "And" e "Or" per costruire le regole.</span><span class="sxs-lookup"><span data-stu-id="68557-195">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="68557-196">Di seguito sono riportati alcuni esempi di come usare questo campo:</span><span class="sxs-lookup"><span data-stu-id="68557-196">Here are some examples of how to leverage this field:</span></span>

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
> <span data-ttu-id="68557-197">Le regole di accesso condizionale sono disponibili solo in Windows PowerShell 5.1 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="68557-197">Conditional access rules are only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="68557-198">Altre proprietà</span><span class="sxs-lookup"><span data-stu-id="68557-198">Other properties</span></span>
<span data-ttu-id="68557-199">I file di configurazione sessione consentono di eseguire tutte le operazioni di un file delle funzionalità del ruolo, ma non possono offrire agli utenti che si connettono accesso ai diversi comandi.</span><span class="sxs-lookup"><span data-stu-id="68557-199">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span>
<span data-ttu-id="68557-200">Se si vuole concedere agli utenti l'accesso a specifici cmdlet, funzioni o provider, è possibile impostarlo direttamente nel file di configurazione sessione.</span><span class="sxs-lookup"><span data-stu-id="68557-200">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="68557-201">Per un elenco completo delle proprietà supportate nel file di configurazione sessione, eseguire `Get-Help New-PSSessionConfigurationFile -Full`.</span><span class="sxs-lookup"><span data-stu-id="68557-201">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="68557-202">Test di un file di configurazione sessione</span><span class="sxs-lookup"><span data-stu-id="68557-202">Testing a session configuration file</span></span>

<span data-ttu-id="68557-203">È possibile testare una configurazione sessione tramite il cmdlet [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile).</span><span class="sxs-lookup"><span data-stu-id="68557-203">You can test a session configuration using the [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span>
<span data-ttu-id="68557-204">È consigliabile testare il file di configurazione sessione se è stato modificato il file PSSC manualmente in un editor di testo per assicurarsi che la sintassi usata sia corretta.</span><span class="sxs-lookup"><span data-stu-id="68557-204">It is strongly recommended that you test your session configuration file if you have edited the pssc file manually using a text editor to ensure the syntax is correct.</span></span>
<span data-ttu-id="68557-205">Se un file di configurazione sessione non supera il test, non sarà registrato correttamente nel sistema.</span><span class="sxs-lookup"><span data-stu-id="68557-205">If a session configuration file does not pass this test, it will not be able to be successfully registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="68557-206">File di configurazione sessione d'esempio</span><span class="sxs-lookup"><span data-stu-id="68557-206">Sample session configuration file</span></span>

<span data-ttu-id="68557-207">Di seguito viene visualizzato un esempio completo che illustra come creare e convalidare una configurazione sessione per JEA.</span><span class="sxs-lookup"><span data-stu-id="68557-207">Below is a complete example showing how to create and validate a session configuration for JEA.</span></span>
<span data-ttu-id="68557-208">Si noti che le definizioni del ruolo vengono create e archiviate nella variabile `$roles` per motivi di praticità e leggibilità.</span><span class="sxs-lookup"><span data-stu-id="68557-208">Note that the role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span>
<span data-ttu-id="68557-209">Non è un requisito obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="68557-209">It is not a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="68557-210">Aggiornamento dei file di configurazione sessione</span><span class="sxs-lookup"><span data-stu-id="68557-210">Updating session configuration files</span></span>

<span data-ttu-id="68557-211">Se è necessario modificare le proprietà di una configurazione sessione JEA, tra cui il mapping degli utenti ai ruoli, è necessario [annullare la registrazione](register-jea.md#unregistering-jea-configurations) e [registrare di nuovo](register-jea.md) la configurazione sessione JEA.</span><span class="sxs-lookup"><span data-stu-id="68557-211">If you need to change properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations) and [re-register](register-jea.md) the JEA session configuration.</span></span>
<span data-ttu-id="68557-212">Quando si registra di nuovo la configurazione sessione JEA, usare un file di configurazione sessione PowerShell aggiornato che includa le modifiche volute.</span><span class="sxs-lookup"><span data-stu-id="68557-212">When you re-register the JEA session configuration, use an updated PowerShell session configuration file that includes your desired changes.</span></span>

## <a name="next-steps"></a><span data-ttu-id="68557-213">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="68557-213">Next steps</span></span>

- [<span data-ttu-id="68557-214">Registrare una configurazione JEA</span><span class="sxs-lookup"><span data-stu-id="68557-214">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="68557-215">Creare ruoli JEA</span><span class="sxs-lookup"><span data-stu-id="68557-215">Author JEA roles</span></span>](role-capabilities.md)