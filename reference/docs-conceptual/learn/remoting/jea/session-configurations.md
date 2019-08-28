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
# <a name="jea-session-configurations"></a>Configurazioni della sessione JEA

Un endpoint JEA viene registrato in un sistema tramite la creazione e la registrazione di un file di configurazione di sessione di PowerShell. Le configurazioni di sessione determinano gli utenti che possono usare l'endpoint JEA e i ruoli ai quali possono avere accesso. Definiscono anche impostazioni globali che vengono applicate a tutti gli utenti della sessione JEA.

## <a name="create-a-session-configuration-file"></a>Creare un file di configurazione sessione

Per registrare un endpoint JEA è necessario specificare come è configurato. Vi sono diverse opzioni da prendere in considerazione. Le più importanti sono:

- Chi ha accesso all'endpoint JEA
- Quali sono i ruoli con cui vengono eseguiti gli accessi
- Quale identità JEA usa chi esegue l'accesso
- Il nome dell'endpoint JEA

Queste opzioni vengono definite in un file di dati PowerShell con estensione `.pssc`, ovvero in un file di configurazione di sessione. È possibile modificare il file di configurazione di sessione in qualsiasi editor di testo.

Eseguire il comando seguente per creare un file di configurazione modello vuoto.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Per impostazione predefinita, solo le opzioni di configurazione più comuni sono incluse nel file modello. Usare l'opzione `-Full` per includere tutte le impostazioni applicabili nel file PSSC generato.

Il campo `-SessionType RestrictedRemoteServer` indica che la configurazione di sessione viene usata da JEA per una gestione sicura. Le sessioni di questo tipo operano in modalità **NoLanguage** e hanno accesso solo ai comandi (e agli alias) predefiniti seguenti:

- Clear-Host (cls, clear)
- Exit-PSSession (exsn, exit)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- Measure-Object (measure)
- Out-Default
- Select-Object (select)

Non sono disponibili provider PowerShell e nemmeno programmi esterni (file eseguibili o script).

Per altre informazioni sulle modalità di linguaggio, vedere [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).

### <a name="choose-the-jea-identity"></a>Scegliere l'identità JEA

Alla base, JEA richiede un'identità (account) da usare durante l'esecuzione di comandi da parte dell'utente connesso.
L'utente decide quale identità JEA usare nel file di configurazione di sessione.

#### <a name="local-virtual-account"></a>Account virtuale locale

Gli account virtuali locali sono utili quando i ruoli definiti per l'endpoint JEA vengono tutti usati per gestire il computer locale, e l'account Administrator locale è sufficiente per eseguire i comandi correttamente.
Gli account virtuali sono account temporanei e univoci per un utente specifico. Sono validi solo per la durata della sessione di PowerShell. In un server membro o in una workstation gli account virtuali appartengono al gruppo **Administrators** del computer locale. In un controller di dominio Active Directory, gli account virtuali appartengono al gruppo **Domain Admins** del dominio.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Se i ruoli definiti dalla configurazione di sessione non richiedono privilegi amministrativi completi, è possibile specificare i gruppi di sicurezza a cui appartiene l'account virtuale. In un server membro o in una workstation, i gruppi di sicurezza specificati devono essere gruppi locali, non gruppi di un dominio.

Quando vengono specificati uno o più gruppi di sicurezza, l'account virtuale non viene assegnato al gruppo locale o degli amministratori di dominio.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> Agli account virtuali viene temporaneamente concesso il diritto relativo all'accesso come servizio nei criteri di sicurezza del server locale. Se a uno dei gruppi di account virtuali è già stato concesso questo diritto nei criteri, il singolo account virtuale non sarà più aggiunto né rimosso dai criteri. Può essere utile in alcuni scenari, ad esempio nei controller di dominio, dove le revisioni dei criteri di sicurezza dei controller di dominio sono sottoposte ad attenti controlli. Questa opzione è disponibile solo in Windows Server 2016 con l'aggiornamento cumulativo di Novembre 2018 o aggiornamento cumulativo successivo e in Windows Server 2019 con l'aggiornamento cumulativo di Gennaio 2019 o aggiornamento cumulativo successivo.

#### <a name="group-managed-service-account"></a>Account del servizio gestito del gruppo

Un account del servizio gestito del gruppo è l'identità appropriata per gli utenti JEA quando devono accedere a risorse di rete come ad esempio condivisioni di file e servizi Web. Gli account del servizio gestito del gruppo offrono un'identità di dominio che può essere usata per eseguire l'autenticazione alle risorse di tutti i computer all'interno del dominio. I diritti specificati da un account del servizio gestito del gruppo vengono determinati in base alle risorse a cui si accede. Non si hanno diritti di amministratore sui computer o i servizi, a meno che l'amministratore del computer o del servizio abbia garantito esplicitamente tali diritti all'account del servizio gestito del gruppo.

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

Gli account del servizio gestito del gruppo devono essere usati solo quando è necessario:

- È difficile risalire alle azioni di un utente quando si usa un account del servizio gestito del gruppo. Ogni utente condivide la stessa identità Esegui come. È necessario esaminare le trascrizioni e i log della sessione di PowerShell per correlare i singoli utenti con le relative azioni.

- L'account del servizio gestito del gruppo può avere accesso a numerose risorse di rete a cui l'utente che si connette non ha bisogno di accedere. Limitare sempre le autorizzazioni effettive in una sessione JEA per seguire il principio del privilegio minimo.

> [!NOTE]
> Gli account del servizio gestito del gruppo sono disponibili solo in computer aggiunti a un dominio con PowerShell 5.1 o versione successiva.

Per altre informazioni sulla protezione di una sessione JEA, vedere l'articolo [Considerazioni sulla sicurezza](security-considerations.md).

### <a name="session-transcripts"></a>Trascrizioni di sessione

È consigliabile configurare un endpoint JEA per registrare automaticamente le trascrizioni delle sessioni degli utenti. Le trascrizioni delle sessione di PowerShell contengono informazioni sull'utente che si connette, sulle identità RunAs assegnate e sui comandi eseguiti dall'utente. Queste informazioni possono essere utili a un gruppo di controllo che ha bisogno di sapere chi ha eseguito una modifica specifica a un sistema.

Per configurare la trascrizione automatica nel file di configurazione sessione, specificare il percorso a una cartella in cui le trascrizioni devono essere archiviate.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

Le trascrizioni vengono scritte nella cartella dall'account **di sistema locale**, che richiede l'accesso in lettura e scrittura alla directory. Gli utenti standard non devono avere accesso alla cartella. Limitare il numero di amministratori della sicurezza che hanno accesso alla cartella per controllare le trascrizioni.

### <a name="user-drive"></a>Unità utente

Se gli utenti che si connettono hanno bisogno di copiare file dal e nell'endpoint JEA, è possibile abilitare l'unità utente nel file di configurazione di sessione. L'unità utente è una **PSDrive** con mapping a una cartella univoca per ogni utente che si connette. Questa cartella consente agli utenti di copiare file nel e dal sistema senza che abbiano accesso all'intero file system e senza esporre il provider FileSystem. Il contenuto dell'unità utente è persistente tra le sessioni per consentire situazioni in cui la connettività di rete viene interrotta.

```powershell
MountUserDrive = $true
```

Per impostazione predefinita, l'unità utente consente di archiviare massimo 50 MB di dati per ogni utente. È possibile limitare la quantità di dati utilizzabile da un utente tramite il campo *UserDriveMaximumSize*.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Se si preferisce che i dati nell'unità utente non siano persistenti, è possibile configurare un'attività pianificata nel sistema per pulire automaticamente la cartella ogni notte.

> [!NOTE]
> L'unità utente è disponibile solo in PowerShell 5.1 o versione successiva.

Per altre informazioni sulle PSDrive, vedere [Gestione delle unità di PowerShell](/powershell/scripting/samples/managing-windows-powershell-drives).

### <a name="role-definitions"></a>Definizioni dei ruoli

Le definizioni dei ruoli in un file di configurazione sessione definiscono il mapping degli **utenti** ai **ruoli**. A ogni utente o gruppo incluso in questo campo viene automaticamente concessa l'autorizzazione per l'endpoint JEA alla registrazione.
Ogni utente o gruppo può essere incluso come chiave nella tabella hash solo una volta, ma gli possono essere assegnati più ruoli. Il nome della funzionalità del ruolo deve essere il nome del file delle funzionalità del ruolo, senza l'estensione `.psrc`.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Se un utente appartiene a più gruppi nella definizione del ruolo, avrà accesso ai ruoli di ogni gruppo. Se due ruoli concedono l'accesso agli stessi cmdlet, all'utente viene concesso il set di parametri più permissivo.

Quando si specificano utenti o gruppi locali nel campo delle definizioni di ruolo, assicurarsi di usare il nome del computer, non **localhost** o caratteri jolly. È possibile verificare il nome del computer controllando la variabile `$env:COMPUTERNAME`.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Ordine di ricerca delle funzionalità del ruolo

Come illustrato nell'esempio precedente, viene fatto riferimento alle funzionalità del ruolo tramite il nome di base del file delle funzionalità del ruolo. Il nome di base di un file è il nome file senza estensione. Se nel sistema sono disponibili più funzionalità del ruolo con lo stesso nome, PowerShell usa l'ordine di ricerca implicito per selezionare il file delle funzionalità del ruolo effettivo. JEA **non** concede accesso a tutti i file delle funzionalità del ruolo con lo stesso nome.

JEA usa la variabile di ambiente `$env:PSModulePath` per determinare i percorsi in cui cercare i file delle funzionalità di ruolo. All'interno di ognuno di questi percorsi JEA cerca moduli di PowerShell validi che contengono una sottocartella "RoleCapabilities". Come per l'importazione dei moduli, JEA preferisce le funzionalità di ruolo fornite con Windows rispetto alle funzionalità di ruolo personalizzate con lo stesso nome.

Per tutti gli altri conflitti di nome, la precedenza è determinata dall'ordine in cui Windows enumera i file nella directory. L'ordine non è necessariamente alfabetico. Il primo file di funzionalità del ruolo trovato che corrisponde al nome specificato viene usato per l'utente che si connette. Poiché l'ordine di ricerca delle funzionalità del ruolo non è deterministico, **è consigliabile** che le funzionalità del ruolo abbiano nomi file univoci.

### <a name="conditional-access-rules"></a>Regole di accesso condizionale

A tutti gli utenti e gruppi inclusi nel campo **RoleDefinitions** viene concesso automaticamente l'accesso agli endpoint JEA. Le regole di accesso condizionale consentono di ottimizzare l'accesso e richiedono che gli utenti appartengano ai gruppi di sicurezza aggiuntivi che non incidono sui ruoli ai quali sono stati assegnati. Ciò può essere utile se si vuole integrare una soluzione di gestione di accesso privilegiato just-in-time, l'autenticazione smart card o altra soluzione di autenticazione a più fattori con JEA.

Le regole di accesso condizionale sono definite nel campo RequiredGroups di un file di configurazione sessione.
In questo file è possibile specificare una tabella hash (facoltativamente nidificata) che usi le chiavi "And" e "Or" per costruire le regole. Di seguito sono riportati alcuni esempi di come usare questo campo:

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
> Le regole di accesso condizionale sono disponibili solo in PowerShell 5.1 o versione successiva.

### <a name="other-properties"></a>Altre proprietà

I file di configurazione sessione consentono di eseguire tutte le operazioni di un file delle funzionalità del ruolo, ma non possono offrire agli utenti che si connettono accesso ai diversi comandi. Se si vuole concedere agli utenti l'accesso a specifici cmdlet, funzioni o provider, è possibile impostarlo direttamente nel file di configurazione sessione.
Per un elenco completo delle proprietà supportate nel file di configurazione sessione, eseguire `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Test di un file di configurazione sessione

È possibile testare una configurazione sessione tramite il cmdlet [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile). È consigliabile testare il file di configurazione di sessione se il file `.pssc` è stato modificato manualmente. Il test garantisce che la sintassi sia corretta. Se un file di configurazione di sessione ha esito negativo in seguito al test, non può essere registrato nel sistema.

## <a name="sample-session-configuration-file"></a>File di configurazione sessione d'esempio

L'esempio seguente illustra come creare e convalidare una configurazione di sessione per JEA. Le definizioni del ruolo vengono create e archiviate nella variabile `$roles` per motivi di praticità e leggibilità. Non è un requisito obbligatorio.

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a>Aggiornamento dei file di configurazione sessione

Per modificare le proprietà di una configurazione di sessione JEA, tra cui il mapping degli utenti ai ruoli, è necessario [annullare la registrazione](register-jea.md#unregistering-jea-configurations). In seguito [registrare nuovamente](register-jea.md) la configurazione di sessione JEA usando un file di configurazione di sessione aggiornato.

## <a name="next-steps"></a>Passaggi successivi

- [Registrare una configurazione JEA](register-jea.md)
- [Creare ruoli JEA](role-capabilities.md)
