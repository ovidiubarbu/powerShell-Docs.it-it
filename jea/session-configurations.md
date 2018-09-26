---
ms.date: 06/12/2017
keywords: jea,powershell,sicurezza
title: Configurazioni della sessione JEA
ms.openlocfilehash: bdf3659357045203d90e8083613e51cce657da1a
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522961"
---
# <a name="jea-session-configurations"></a>Configurazioni della sessione JEA

> Si applica a: Windows PowerShell 5.0

Un endpoint JEA viene registrato in un sistema tramite la creazione e la registrazione di un file di configurazione sessione di PowerShell in un modo specifico.
Le configurazioni sessione determinano *chi* può usare l'endpoint JEA e a quali ruoli potranno avere accesso gli utenti.
Definiscono anche impostazioni globali che vengono applicate agli utenti di qualsiasi ruolo nella sessione JEA.

Questo argomento illustra come creare un file di configurazione sessione di PowerShell e registrare un endpoint JEA.

## <a name="create-a-session-configuration-file"></a>Creare un file di configurazione sessione

Per registrare un endpoint JEA, è necessario specificare come deve essere configurato l'endpoint.
Ci sono molte opzioni da tenere in considerazione, ma le più importanti sono relative agli utenti che devono avere accesso all'endpoint JEA, ai ruoli che verranno assegnati, a quale identità verrà usata da JEA in maniera invisibile e al nome dell'endpoint JEA.
Tutti questi elementi verranno definiti in un file di configurazione sessione di PowerShell, ovvero in un file di dati con estensione PSSC.

Per creare un file di struttura della configurazione sessione per gli endpoint JEA, eseguire il comando seguente.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Per impostazione predefinita, solo le opzioni di configurazione più comuni sono incluse nel file di struttura.
> Usare l'opzione `-Full` per includere tutte le impostazioni applicabili nel file PSSC generato.

È possibile aprire il file di configurazione sessione in qualsiasi editor di testo.
Il campo `-SessionType RestrictedRemoteServer` indica che la configurazione sessione verrà usata da JEA per una gestione sicura.
Le sessioni configurate in questo modo funzioneranno in [modalità NoLanguage](https://technet.microsoft.com/library/dn433292.aspx) e hanno disponibili solo gli 8 comandi (e alias) predefiniti seguenti:

- Clear-Host (cls, clear)
- Exit-PSSession (exsn, exit)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- Measure-Object (measure)
- Out-Default
- Select-Object (select)

Non sono disponibili provider PowerShell e nemmeno programmi esterni (file eseguibili, script e così via).

Molti altri campi possono essere configurati per la sessione JEA.
Questi verranno illustrati nelle sezioni seguenti.

### <a name="choose-the-jea-identity"></a>Scegliere l'identità JEA

Alla base, JEA richiede un'identità (account) da usare durante l'esecuzione di comandi da parte dell'utente connesso.
L'utente decide quale identità JEA userà nel file di configurazione sessione.

#### <a name="local-virtual-account"></a>Account virtuale locale

Se i ruoli supportati da questo endpoint JEA sono tutti usati per gestire il computer locale, e l'account di amministratore locale è sufficiente per eseguire i comandi correttamente, è necessario configurare JEA per usare un account virtuale locale.
Gli account virtuali sono account temporanei e univoci per un utente specifico. Sono validi solo per la durata della sessione di PowerShell.
In un server membro o in una workstation, gli account virtuali appartengono al gruppo **Administrators** del computer locale e hanno accesso alla maggior parte delle risorse di sistema.
In un controller di dominio Active Directory, gli account virtuali appartengono al gruppo **Domain Admins** del dominio.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Se i ruoli supportati dalla configurazione sessione non richiedono privilegi estesi, è possibile specificare facoltativamente i gruppi di sicurezza a cui appartiene l'account virtuale.
In un server membro o in una workstation, i gruppi di sicurezza specificati devono essere gruppi locali, non gruppi di un dominio.

Quando si specifica uno o più gruppi di sicurezza, l'account virtuale non apparterrà più al gruppo locale o Domain Administrators.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a>Account del servizio gestito del gruppo


Per gli scenari che richiedono all'utente JEA di accedere alle risorse di rete, ad esempio altri computer o i servizi Web, un account del servizio gestito del gruppo (gMSA) è un'identità più appropriata da usare.
Gli account gMSA offrono un'identità di dominio che può essere usata per eseguire l'autenticazione alle risorse di tutti i computer all'interno del dominio.
I diritti offerti dall'account gMSA sono determinati dalle risorse a cui si accede.
Non si hanno automaticamente diritti di amministratore su tutti i computer o servizi, se l'amministratore del computer/servizio non ha esplicitamente concesso i privilegi di amministratore all'account gMSA.

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

Gli account gMSA dovrebbero essere usati solo quando è necessario accedere alle risorse di rete per alcuni motivi:

- È molto difficile tracciare le azioni di un utente quando si usa un account gMSA perché ogni utente condivide la stessa identità RunAs. È necessario esaminare le trascrizioni della sessione di PowerShell e i log per correlare gli utenti con le relative azioni.

- L'account gMSA potrebbe avere accesso a numerose risorse di rete a cui l'utente che si connette non ha bisogno di accedere. Limitare sempre le autorizzazioni effettive in una sessione JEA per seguire il principio del privilegio minimo.

> [!NOTE]
> Gli account del servizio gestito del gruppo sono disponibili solo in Windows PowerShell 5.1 o versione successiva e nei computer uniti in un dominio.


#### <a name="more-information-about-run-as-users"></a>Altre informazioni su utenti RunAs

Altre informazioni sulle identità RunAs e su come influenzano la sicurezza di una sessione JEA sono reperibili nell'articolo relativo alle [considerazioni sulla sicurezza](security-considerations.md).

### <a name="session-transcripts"></a>Trascrizioni di sessione

È consigliabile configurare il file di configurazione sessione JEA per registrare automaticamente le trascrizioni delle sessioni degli utenti.
Le trascrizioni delle sessione di PowerShell contengono informazioni sull'utente che si connette, sulle identità RunAs assegnate e sui comandi eseguiti dall'utente.
Queste informazioni possono essere utili a un gruppo di controllo che ha bisogno di sapere chi ha eseguito una modifica specifica a un sistema.

Per configurare la trascrizione automatica nel file di configurazione sessione, specificare il percorso a una cartella in cui le trascrizioni devono essere archiviate.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

La cartella specificata deve essere configurata per impedire agli utenti di modificare o eliminare i dati contenuti.
Le trascrizioni vengono scritte nella cartella dall'account del sistema locale, che richiede l'accesso in lettura e scrittura alla directory.
Gli utenti standard non devono avere accesso alla cartella e solo un set limitato di amministratori della sicurezza dovrebbe avere accesso per controllare le trascrizioni.

### <a name="user-drive"></a>Unità utente

Se gli utenti che si connettono hanno bisogno di copiare file dal e nell'endpoint JEA per eseguire un comando, è possibile abilitare l'unità utente nel file di configurazione sessione.
L'unità utente è una [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) con mapping a una cartella univoca per ogni utente che si connette.
Questa cartella ha lo scopo di offrire uno spazio agli utenti per copiare file nel e dal sistema senza concedere accesso al sistema intero o al provider del file system.
Il contenuto dell'unità utente è persistente tra le sessioni per consentire situazioni in cui la connettività di rete viene interrotta.

```powershell
MountUserDrive = $true
```

Per impostazione predefinita, l'unità utente consente di archiviare massimo 50 MB di dati per ogni utente.
È possibile limitare la quantità di dati utilizzabile da un utente tramite il campo *UserDriveMaximumSize*.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Se si preferisce che i dati nell'unità utente non siano persistenti, è possibile configurare un'attività pianificata nel sistema per pulire automaticamente la cartella ogni notte.

> [!NOTE]
> L'unità utente è solo disponibile in Windows PowerShell 5.1 o versione successiva.

### <a name="role-definitions"></a>Definizioni dei ruoli

Le definizioni dei ruoli in un file di configurazione sessione definiscono il mapping degli *utenti* ai *ruoli*.
A ogni utente o gruppo incluso in questo campo verrà automaticamente concessa l'autorizzazione per l'endpoint JEA alla registrazione.
Ogni utente o gruppo può essere incluso come chiave nella tabella hash solo una volta, ma gli possono essere assegnati più ruoli.
Il nome della funzionalità del ruolo deve essere il nome del file delle funzionalità del ruolo, senza l'estensione PSRC.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Se un utente appartiene a più gruppi nella definizione del ruolo, avrà accesso ai ruoli di ogni gruppo.
Se due ruoli concedono l'accesso agli stessi cmdlet, il set di parametri più permissivo verrà concesso all'utente.

Quando si specificano utenti o gruppi locali nel campo delle definizioni di ruolo, assicurarsi di usare il nome del computer (non *localhost* o *.*) prima della barra rovesciata.
È possibile verificare il nome del computer controllando la variabile `$env:computername`.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Ordine di ricerca delle funzionalità del ruolo
Come illustrato nell'esempio precedente, le funzionalità del ruolo vengono indicate dal nome flat (nome file senza estensione) del file delle funzionalità del ruolo.
Se più funzionalità del ruolo sono disponibili nel sistema con lo stesso nome flat, PowerShell userà l'ordine di ricerca implicito per selezionare il file delle funzionalità del ruolo effettivo.
**Non** concederà accesso a tutti i file delle funzionalità del ruolo con lo stesso nome.

JEA usa la variabile di ambiente `$env:PSModulePath` per determinare i percorsi in cui cercare i file delle funzionalità di ruolo.
All'interno di ognuno di questi percorsi, JEA cercherà moduli di PowerShell validi che contengono una sottocartella "RoleCapabilities".
Come per l'importazione dei moduli, JEA preferisce le funzionalità di ruolo fornite con Windows rispetto alle funzionalità di ruolo personalizzate con lo stesso nome.
Per tutti gli altri conflitti di nome, la precedenza è determinata dall'ordine in cui Windows enumera i file nella directory (non necessariamente alfabetico).
Il primo file di funzionalità di ruolo trovato che corrisponde al nome desiderato verrà usato per l'utente che si connette.

Dato che l'ordine di ricerca delle funzionalità di ruolo non è deterministico quando due o più funzionalità di ruolo hanno lo stesso nome, è **consigliabile** assicurarsi che le funzionalità di ruolo abbiano nomi univoci nel computer in uso.

### <a name="conditional-access-rules"></a>Regole di accesso condizionale

A tutti gli utenti e gruppi inclusi nel campo RoleDefinitions viene concesso automaticamente l'accesso agli endpoint JEA.
Le regole di accesso condizionale consentono di ottimizzare l'accesso e richiedono che gli utenti appartengano ai gruppi di sicurezza aggiuntivi che non incidono sui ruoli ai quali sono stati assegnati.
Ciò può essere utile se si vuole integrare una soluzione di gestione di accesso privilegiato "Just in Time", l'autenticazione smart card o altra soluzione di autenticazione a più fattori con JEA.

Le regole di accesso condizionale sono definite nel campo RequiredGroups di un file di configurazione sessione.
In questo file è possibile specificare una tabella hash (facoltativamente nidificata) che usi le chiavi "And" e "Or" per costruire le regole.
Di seguito sono riportati alcuni esempi di come usare questo campo:

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
> Le regole di accesso condizionale sono disponibili solo in Windows PowerShell 5.1 o versione successiva.

### <a name="other-properties"></a>Altre proprietà
I file di configurazione sessione consentono di eseguire tutte le operazioni di un file delle funzionalità del ruolo, ma non possono offrire agli utenti che si connettono accesso ai diversi comandi.
Se si vuole concedere agli utenti l'accesso a specifici cmdlet, funzioni o provider, è possibile impostarlo direttamente nel file di configurazione sessione.
Per un elenco completo delle proprietà supportate nel file di configurazione sessione, eseguire `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Test di un file di configurazione sessione

È possibile testare una configurazione sessione tramite il cmdlet [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile).
È consigliabile testare il file di configurazione sessione se è stato modificato il file PSSC manualmente in un editor di testo per assicurarsi che la sintassi usata sia corretta.
Se un file di configurazione sessione non supera il test, non sarà registrato correttamente nel sistema.

## <a name="sample-session-configuration-file"></a>File di configurazione sessione d'esempio

Di seguito viene visualizzato un esempio completo che illustra come creare e convalidare una configurazione sessione per JEA.
Si noti che le definizioni del ruolo vengono create e archiviate nella variabile `$roles` per motivi di praticità e leggibilità.
Non è un requisito obbligatorio.

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

Se è necessario modificare le proprietà di una configurazione sessione JEA, tra cui il mapping degli utenti ai ruoli, è necessario [annullare la registrazione](register-jea.md#unregistering-jea-configurations) e [registrare di nuovo](register-jea.md) la configurazione sessione JEA.
Quando si registra di nuovo la configurazione sessione JEA, usare un file di configurazione sessione PowerShell aggiornato che includa le modifiche volute.

## <a name="next-steps"></a>Passaggi successivi

- [Registrare una configurazione JEA](register-jea.md)
- [Creare ruoli JEA](role-capabilities.md)