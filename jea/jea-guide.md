# Just Enough Administration (JEA): Introduzione

## Sommario
Dopo aver letto questo documento, si sarà in grado di creare, distribuire, usare, gestire e controllare una distribuzione JEA (Just Enough Administration).
Di seguito sono riportati gli argomenti trattati in questa guida introduttiva:

1.  [Introduzione](#introduction): brevi considerazioni sul perché è opportuno prendere in considerazione JEA

2.  [Prerequisiti](#prerequisites): configurare l'ambiente

3.  [Uso di JEA](#using-jea): informazioni preliminari sull'esperienza dell'operatore con JEA

4.  [Ricreare la Demo](#remake-the-demo-endpoint): creare una configurazione di sessione JEA da zero

5.  [Capacità del ruolo](#role-capabilities): informazioni su come personalizzare le funzionalità JEA con i file di capacità del ruolo

6.  [End-to-end - Active Directory](#end-to-end---active-directory): creare un endpoint completamente nuovo per la gestione di Active Directory

7.  [Distribuzione e manutenzione di più computer](#multi-machine-deployment-and-maintenance): scoprire in che modo le modalità di distribuzione e creazione cambiano con le dimensioni

8.  [Creazione di report per JEA](#reporting-on-jea): informazioni su come controllare tutte le azioni e l'infrastruttura di JEA e creare i relativi report

9.  [Appendice](#appendix): competenze e punti di discussione importanti

## Introduzione

### Motivazione
Quando si concede a un utente l'accesso con privilegi ai propri sistemi, si estende il limite di trust a tale utente.
Questo è un rischio: gli amministratori sono una superficie di attacco.
Gli attacchi interni e le credenziali rubate sono sia reali che comuni.

Non è un problema nuovo.
Probabilmente si ha dimestichezza con il principio di privilegio minimo e si può utilizzare una forma di controllo di accesso basato sui ruoli (RBAC) con le applicazioni che la gestiscono.
Tuttavia, l'efficacia e la gestibilità di queste soluzioni spesso sono limitate a causa della vastità dell'ambito dall'imprecisione.
E la copertura RBAC presenta anche delle lacune.
In Windows, ad esempio, l'accesso con privilegi è sostanzialmente un commutatore binario, che forza la concessione di autorizzazioni non necessarie quando si aggiungono utenti al gruppo Administrators.

Just Enough Administration (JEA) offre una piattaforma RBAC attraverso la comunicazione remota di PowerShell.
*Consente a utenti specifici di eseguire attività amministrative specifiche sui server senza concedere loro diritti di amministratore.*
Ciò consente di colmare le lacune tra le soluzioni RBAC esistenti e semplifica la gestione delle impostazioni.

## Prerequisiti

### Stato iniziale
Prima di iniziare questa sezione, verificare quanto segue:

1. JEA è disponibile nel sistema. Verificare nel file [README](./README.md) quali sono i sistemi operativi attualmente supportati e i download necessari.
2. Si dispone di diritti amministrativi nel computer in cui verrà usato JEA.
3. Il computer fa parte di un dominio.
Vedere la sezione [Creazione di un controller di dominio](#creating-a-domain-controller) per configurare rapidamente un nuovo dominio in un server se non ancora disponibile.

### Comunicazione remota di PowerShell
La gestione con JEA avviene attraverso la comunicazione remota di PowerShell.
Eseguire il comando seguente in una finestra di PowerShell come amministratore per verificare che la funzionalità sia abilitata e configurata correttamente:

```PowerShell
Enable-PSRemoting 
```

Se non si ha familiarità con la comunicazione remota di PowerShell, è consigliabile eseguire `Get-Help about_Remote` per informazioni su questo concetto di fondamentale importanza.

### Identificare utenti o gruppi
Per visualizzare JEA in azione, è necessario identificare gli utenti e i gruppi non amministratori che si intende usare in questa guida.
  
Se si usa un dominio già esistente, identificare o creare alcuni gruppi e utenti senza privilegi.
Si concederà l'accesso a JEA a questi utenti non amministratori.
Ogni volta che viene visualizzata la variabile `$NonAdministrator` nella parte superiore di uno script, assegnarla ai propri utenti o gruppi non amministratori selezionati. 

Se è stato creato un nuovo dominio da zero, è molto più semplice.
Usare la sezione [Configurazione di utenti e gruppi](#set-up-users-and-groups) dell'appendice per creare utenti e gruppi non amministratori.
I valori predefiniti di `$NonAdministrator` saranno i gruppi creati in tale sezione.

### Configurare il file di capacità del ruolo per la manutenzione
Eseguire i comandi seguenti in PowerShell per creare il file di capacità del ruolo dimostrativo che verrà usato nella sezione successiva.
Le operazioni eseguite dal file sono illustrate più avanti in questa guida.

```PowerShell
# Fields in the role capability
$MaintenanceRoleCapabilityCreationParams = @{
    Author = 'Contoso Admin'
    CompanyName = 'Contoso'
    VisibleCmdlets = 'Restart-Service'
    FunctionDefinitions = 
            @{ Name = 'Get-UserInfo'; ScriptBlock = { $PSSenderInfo } }
}

# Create the demo module, which will contain the maintenance Role Capability File
New-Item -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module" -ItemType Directory
New-ModuleManifest -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\Demo_Module.psd1"
New-Item -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities" -ItemType Directory 

# Create the Role Capability file
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities\Maintenance.psrc" @MaintenanceRoleCapabilityCreationParams 
```
  
### Creare e registrare un file di configurazione di sessione dimostrativo
Eseguire i comandi seguenti per creare e registrare un file dimostrativo della configurazione di sessione che verrà usato per la sezione successiva.
Le operazioni eseguite dal file sono illustrate più avanti in questa guida.

```PowerShell
# Determine domain
$domain = (Get-CimInstance -ClassName Win32_ComputerSystem).Domain

# Replace with your non-admin group name
$NonAdministrator = "$domain\JEA_NonAdmin_Operator"

# Specify the settings for this JEA endpoint
# Note: You will not be able to use a virtual account if you are using WMF 5.0 on Windows 7 or Windows Server 2008 R2
$JEAConfigParams = @{
    SessionType = 'RestrictedRemoteServer'
    RunAsVirtualAccount = $true
    RoleDefinitions = @{
        $NonAdministrator = @{ RoleCapabilities = 'Maintenance' }
    }
    TranscriptDirectory = "$env:ProgramData\JEAConfiguration\Transcripts"
}

# Set up a folder for the Session Configuration files
if (-not (Test-Path "$env:ProgramData\JEAConfiguration"))
{
    New-Item -Path "$env:ProgramData\JEAConfiguration" -ItemType Directory
}

# Specify the name of the JEA endpoint
$sessionName = 'JEA_Demo'

if (Get-PSSessionConfiguration -Name $sessionName -ErrorAction SilentlyContinue)
{
    Unregister-PSSessionConfiguration -Name $sessionName -ErrorAction Stop
}

New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo.pssc" @JEAConfigParams

# Register the session configuration
Register-PSSessionConfiguration -Name $sessionName -Path "$env:ProgramData\JEAConfiguration\JEADemo.pssc"
```
 
### Abilitare la registrazione per i moduli di PowerShell (facoltativo)
La procedura seguente consente di registrare tutte le azioni di PowerShell nel sistema.
Questa opzione non è necessaria per il funzionamento di JEA, ma risulterà utile nella sezione [Creazione di report per JEA](#reporting-on-jea).

1. Aprire l'Editor criteri di gruppo locali
2. Passare a "Configurazione computer\Modelli amministrativi\Componenti di Windows\Windows PowerShell"
3. Fare doppio clic su "Attiva registrazione moduli"
4. Fare clic su "Abilitato".
5. Nella sezione Opzioni fare clic su "Mostra" accanto a Nomi moduli
6. Digitare "*" nella finestra popup. Ciò significa che PowerShell registrerà i comandi da tutti i moduli.
7. Fare clic su OK e applicare i criteri

Nota: è possibile abilitare la trascrizione PowerShell a livello di sistema anche con i criteri di gruppo.

**Complimenti, il computer ora è configurato con l'endpoint dimostrativo ed è possibile iniziare a usare JEA.**

## Uso di JEA
Questa sezione è incentrata sull'esperienza dell'utente finale *con JEA*.
Nella sezione dei prerequisiti è stato creato un endpoint JEA dimostrativo,
che verrà usato di seguito per illustrare il funzionamento di JEA.
Nelle sezioni successive della guida si procederà a ritroso, presentando le azioni e i file che hanno reso possibile l'esperienza utente descritta.

### Uso di JEA come utente non amministratore
Per visualizzare JEA in azione, è necessario usare la comunicazione remota di PowerShell come utente non amministratore.
Eseguire il comando seguente in una nuova finestra di PowerShell:   

```PowerShell
$NonAdminCred = Get-Credential
```

Immettere le credenziali per l'account non amministratore quando richiesto.
Se è stata seguita la sezione [Configurazione di utenti e gruppi](#set-up-users-and-groups), saranno:
-   Nome utente = "OperatorUser"
-   Password = "pa$$w0rd"

Quindi, eseguire il comando seguente per connettersi all'endpoint dimostrativo usando le credenziali specificate:

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred 
```

Viene avviata una sessione interattiva di PowerShell remota nel computer locale. Specificando il parametro "Credential", la connessione viene eseguita *come se l'utente fosse* OperatorUser (o qualsiasi account usato).
La modifica nella richiesta a `[localhost]: PS>` indica che si sta lavorando in una sessione remota.  

Per visualizzare i comandi disponibili, nel prompt dei comandi remoto eseguire:

```PowerShell
Get-Command 
```

Come si può vedere, si tratta di un subset molto limitato dei comandi disponibili in una normale finestra di PowerShell, che spesso può includere diverse migliaia di comandi.
In particolare, visualizza solo i 7 cmdlet JEA predefiniti (Clear-Host, Exit-PSSession, Get-Command, Get-FormatData, Get-Help, Measure-Object, Out-Default, Select-Object) e i due comandi inclusi in modo esplicito nel file di capacità del ruolo per la manutenzione.

Osservare quindi il contesto utente in cui opera questa sessione richiamando la funzione personalizzata inclusa nel file di capacità del ruolo per la manutenzione:

```PowerShell
Get-UserInfo
```
 
L'output di questa funzione indica un valore sia per "ConnectedUser" che per "RunAsUser".
L'utente connesso è l'account connesso alla sessione remota, ad esempio il proprio account.
Non è necessario che l'utente connesso abbia privilegi di amministratore.
L'account "RunAs" è l'account che effettivamente esegue le azioni con privilegi.
La possibilità di connettersi come utente normale e di eseguire operazioni come utente con privilegi consente agli utenti senza privilegi di eseguire specifiche attività amministrative senza avere diritti amministrativi.

Per vedere come funziona in pratica questo concetto, eseguire il comando seguente:

```PowerShell
Restart-Service -Name Spooler -Verbose
```

In genere, Restart-Service richiede privilegi di amministratore per essere eseguito.
Con l'account virtuale JEA, tuttavia, può essere eseguito usando credenziali senza privilegi.

Pertanto, JEA consente di svolgere il proprio lavoro usando i comandi già in uso.
Come vengono gestiti i comandi che *non si devono* usare?
Provare a eseguire un comando diverso nella sessione JEA, ad esempio `Restart-Computer`, e si noterà che JEA ne impedisce l'esecuzione.

```PowerShell
[localhost]: PS> Restart-Computer
The term 'Restart-Computer' is not recognized as the name of a cmdlet, function, script file, or
operable program. Check the spelling of the name, or if a path was included, verify that the path
is correct and try again.
    + CategoryInfo          : ObjectNotFound: (Restart-Computer:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException 
```

Per lasciare l'endpoint JEA vincolato, eseguire il comando seguente:

```PowerShell
Exit-PSSession
```

In questo modo l'utente viene disconnesso dalla sessione di PowerShell remota.

## Ricreare l'endpoint dimostrativo
Questa sezione spiega come generare una replica esatta dell'endpoint dimostrativo usato nella sezione precedente.
Verranno introdotti i concetti essenziali per la comprensione di JEA, incluse le configurazioni di sessione di PowerShell e le capacità del ruolo. 

### Configurazioni di sessione di PowerShell
Se è stato usato JEA nella sezione precedente, la procedura è iniziata con l'esecuzione di questo comando:

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

Benché nella maggior parte dei casi i parametri siano di chiara interpretazione, il parametro *ConfigurationName* inizialmente può generare confusione.
Il parametro specifica la configurazione di sessione di PowerShell a cui si è connessi. 

Il termine *configurazione di sessione di PowerShell* indica un endpoint di PowerShell.
In senso figurato, si tratta del "posto" in cui gli utenti si connettono e accedono alla funzionalità PowerShell.
In base all'impostazione della configurazione di sessione, offre funzionalità diverse per la connessione degli utenti.
Per JEA, le configurazioni di sessione vengono usate per circoscrivere PowerShell a un set limitato di funzionalità e per l'esecuzione come account virtuale con privilegi.

Nel computer sono già disponibili alcune configurazioni di sessione di PowerShell registrate, ognuna impostata in modo leggermente diverso.
La maggior parte di esse è inclusa in Windows, ma la configurazione di sessione "JEA_Demo" è stata impostata nella sezione dei [prerequisiti](#prerequisites).
Per visualizzare tutte le configurazioni di sessione registrate, eseguire il comando seguente in un prompt di PowerShell per amministratore:

```PowerShell
Get-PSSessionConfiguration
```

### File di configurazione di sessione di PowerShell
È possibile creare nuove configurazioni di sessione registrando nuovi *file di configurazione di sessione di PowerShell*.
I file di configurazione di sessione hanno estensione "pssc"
e possono essere creati con il cmdlet New-PSSessionConfigurationFile.

A questo punto è possibile creare e registrare una nuova configurazione di sessione per JEA. 

### Generare e modificare la configurazione di sessione di PowerShell
Eseguire il comando seguente per generare un file "scheletro" per la configurazione di sessione di PowerShell.

```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

> **Suggerimento:** per impostazione predefinita, solo le impostazioni di configurazione più comuni vengono incluse nel file scheletro.
> Usare il parametro `-Full` per includere tutte le impostazioni applicabili nel file PSSC generato.

Aprire il file in PowerShell ISE o in un editor di testo.

```PowerShell
ise "$env:ProgramData\JEAConfiguration\JEADemo2.pssc" 
```

Aggiornare i campi seguenti nel file con i valori riportati di seguito (ricordarsi di sostituire i valori nel proprio gruppo di sicurezza non amministratore): 

```PowerShell
# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: # RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{'CONTOSO\JEA_NonAdmin_Operator' = @{ RoleCapabilities =  'Maintenance' }}
```

Le voci hanno il significato seguente:

1.  Il campo *SessionType* definisce le impostazioni predefinite da usare con questo endpoint.
*RestrictedRemoteServer* definisce le impostazioni minime necessarie per la gestione remota. Per impostazione predefinita, un endpoint *RestrictedRemoteServer* espone Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clear-Host e Out-Default.
*ExecutionPolicy* viene impostato su *RemoteSigned* e *LanguageMode* su *NoLanguage*.
L'effetto di queste impostazioni è un punto di partenza minimo e sicuro per la configurazione dell'endpoint.

2.  Il campo *RoleDefinitions* assegna le capacità del ruolo a gruppi specifici.
Definisce chi fa cosa come un account con privilegi.
Con questo campo è possibile specificare le funzionalità disponibili per qualsiasi utente connesso in base all'appartenenza al gruppo.
Questo è l'elemento di base della funzionalità RBAC di JEA.
In questo esempio, si espone la capacità del ruolo "Demo" predefinita per i membri del gruppo "Contoso\JEA_NonAdmin_Operator".

3.  Il campo *RunAsVirtualAccount* indica che PowerShell deve "essere eseguito come" account virtuale per questo endpoint.
Per impostazione predefinita, l'account virtuale è un membro del gruppo Administrators incorporato.
In un controller di dominio è anche un membro del gruppo di amministratori del dominio per impostazione predefinita.
Più avanti in questa guida si apprenderà come personalizzare i privilegi dell'account virtuale.

4.  Il campo *TranscriptDirectory* indica dove vengono salvate le trascrizioni "over-the-shoulder" di PowerShell dopo ogni sessione remota.
Queste trascrizioni consentono di esaminare le azioni eseguite in ogni sessione in un formato leggibile.
Per altre informazioni sulle trascrizioni di PowerShell, vedere questo [post del blog](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).
Nota: anche la normale registrazione degli eventi di Windows acquisisce informazioni su ciò che ogni utente esegue con PowerShell.
Le trascrizioni sono semplicemente un po' più leggibili.

Infine, salvare le modifiche apportate a *JEADemo2.pssc*.

### Applicare la configurazione di sessione di PowerShell 

Per creare un endpoint da un file di configurazione di sessione, è necessario registrare il file.
Questa operazione richiede alcune informazioni:

1. Il percorso del file di configurazione della sessione.
2. Il nome della configurazione di sessione registrata. Si tratta dello stesso nome immesso dagli utenti per il parametro "ConfigurationName" quando si connettono all'endpoint con `Enter-PSSession` o `New-PSSession`.

Per registrare la configurazione di sessione nel computer locale, eseguire il comando seguente:

```PowerShell
Register-PSSessionConfiguration -Name 'JEADemo2' -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

Congratulazioni, l'impostazione dell'endpoint JEA è stata completata.

### Testare l'endpoint
Eseguire di nuovo i passaggi riportati nella sezione [Uso di JEA](#using-jea) per il nuovo endpoint per verificare se funziona come previsto.
Assicurarsi di usare il nome del nuovo endpoint (JEADemo2) quando si specifica il nome della configurazione per Enter-PSSession.

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
```

### Concetti chiave
**Configurazione di sessione di PowerShell**: detta anche *Endpoint di PowerShell*, è il "posto" in senso figurato dove gli utenti si connettono e accedono alle funzionalità di PowerShell.
Per visualizzare le configurazioni di sessione registrate nel sistema eseguire `Get-PSSessionConfiguration`.
Quando è configurata in modo specifico, una configurazione di sessione di PowerShell può essere definita *Endpoint JEA*.

**File di configurazione di sessione di PowerShell (con estensione pssc)**: un file che, quando è registrato, definisce le impostazioni per una configurazione di sessione di PowerShell.
Contiene le specifiche per i ruoli utente che possono connettersi all'endpoint, l'account virtuale "RunAs" e altro ancora.     

**Definizioni ruolo**: campo del file di configurazione di sessione che definisce le capacità del ruolo per la connessione degli utenti.
Definisce *chi* può fare *cosa* come account con privilegi.
Questo è l'elemento di base delle funzionalità RBAC di JEA.

**SessionType**: campo del file di configurazione di sessione che rappresenta le impostazioni predefinite per una configurazione di sessione.
Per gli endpoint JEA, deve essere impostato su RestrictedRemoteServer.

**Trascrizione PowerShell**: file contenente una visualizzazione "over-the-shoulder" di una sessione di PowerShell.
È possibile impostare PowerShell in modo che generi le trascrizioni per le sessioni JEA usando il campo TranscriptDirectory.
Per altre informazioni sulle trascrizioni, vedere questo [post del blog](https://technet.microsoft.com/en-us/magazine/ff687007.aspx).

## Capacità del ruolo

### Panoramica
Nella sezione precedente si è appreso che il campo "RoleDefinitions" definisce quali gruppi hanno accesso a quali capacità del ruolo.
Questa sezione spiega
che cosa sono le capacità del ruolo.  

## Introduzione alle capacità del ruolo di PowerShell
Le capacità del ruolo di PowerShell definiscono le operazioni che un utente può eseguire in corrispondenza di un endpoint JEA.
Indicano in dettaglio una serie di elementi, tra cui comandi visibili, applicazioni visibili e altro ancora.
Le capacità del ruolo vengono definite da file con estensione "psrc".

## Contenuto della capacità del ruolo
Per prima cosa è necessario esaminare e modificare il file di capacità del ruolo dimostrativo usato in precedenza.
Si supponga di aver distribuito la configurazione di sessione nel proprio ambiente, ma di aver ricevuto un feedback che indica che è necessario modificare le funzionalità esposte agli utenti.
Gli operatori devono avere la possibilità di riavviare i computer e vogliono essere in grado di ottenere informazioni sulle impostazioni di rete.
Gli addetti alla protezione hanno anche indicato che consentire agli utenti di eseguire "Restart-Service" senza restrizioni non è accettabile.
È necessario limitare i servizi che gli operatori possono riavviare.

Per apportare queste modifiche, eseguire PowerShell ISE come amministratore e aprire il file seguente:

```
C:\Program Files\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities\Maintenance.psrc
```

Ora individuare e aggiornare le righe seguenti nel file: 

```PowerShell
# OLD: VisibleCmdlets = 'Restart-Service'
VisibleCmdlets = 'Restart-Computer',
                 @{
                     Name = 'Restart-Service'
                     Parameters = @{ Name = 'Name'; ValidateSet = 'Spooler' }
                 },
                 'NetTCPIP\Get-*'

# OLD: VisibleExternalCommands = 'Item1', 'Item2'
VisibleExternalCommands = 'C:\Windows\system32\ipconfig.exe'
```

Il file contiene alcuni esempi interessanti:

1.  Restart-Service è stato limitato in modo che gli operatori possano usare Restart-Service solo con il parametro -Name e siano autorizzati solo a specificare "Spooler" come argomento per tale parametro.
Se necessario, è anche possibile limitare gli argomenti usando un'espressione regolare con "ValidatePattern" anziché "ValidateSet".

2.  Tutti i comandi con il verbo "Get" dal modulo NetTCPIP sono stati esposti.
Poiché i comandi "Get" in genere non modificano lo stato del sistema, si tratta di un'operazione relativamente sicura.
Detto questo, è assolutamente necessario esaminare ogni comando che si espone con JEA.

3.  È possibile esporre un eseguibile (ipconfig) usando VisibleExternalCommands.
Si possono anche esporre script completi di PowerShell con questo campo.
È importante specificare sempre il percorso completo per i comandi esterni per assicurarsi che non venga eseguito un programma con un nome simile, e potenzialmente dannoso, presente nel percorso dell'utente.

Salvare il file, quindi connettersi all'endpoint dimostrativo per verificare se le modifiche hanno avuto esito positivo.

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
Get-Command
```
Poiché è stato modificato solo il file di capacità del ruolo, non è necessario registrare nuovamente la configurazione di sessione.
PowerShell troverà automaticamente la capacità del ruolo aggiornata quando un utente si connette.
Poiché le capacità del ruolo vengono caricate all'avvio della sessione, le sessioni esistenti non sono interessate dagli aggiornamenti dei file di capacità del ruolo.

A questo punto, verificare se è possibile riavviare il computer eseguendo Restart-Computer con il parametro -WhatIf, a meno che non si voglia riavviare il computer.

```PowerShell
Restart-Computer -WhatIf 
```

Verificare che sia possibile eseguire "ipconfig"

```PowerShell
ipconfig
```

E infine verificare che Restart-Service funzioni solo per il servizio Spooler.

```PowerShell
Restart-Service Spooler # This should work
Restart-Service WSearch # This should fail 
```

Al termine, chiudere la sessione.

```PowerShell
Exit-PSSession 
```

### Creazione di capacità del ruolo
Nella sezione successiva verrà creato un endpoint JEA per gli utenti dell'help desk di Active Directory.
Per prima cosa verrà creato un file di capacità del ruolo vuoto da compilare in tale sezione.
Le capacità del ruolo devono essere create in una cartella "RoleCapabilities" all'interno di un modulo di PowerShell valido per poter essere risolte quando si avvia una sessione.

I moduli di PowerShell sono essenzialmente pacchetti di funzionalità di PowerShell.
Possono contenere funzioni di PowerShell, cmdlet, risorse DSC, capacità del ruolo e altro ancora.
È possibile trovare informazioni sui moduli eseguendo `Get-Help about_Modules` nella console di PowerShell.

Per creare un nuovo modulo di PowerShell con un file di capacità del ruolo vuoto, eseguire questi comandi:  

```PowerShell
# Create a new folder for the module.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module' -ItemType Directory

# Add a module manifest to contain metadata for this module.
New-ModuleManifest -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psd1' -RootModule Contoso_AD_Module.psm1

# Create a blank script module. You'll use this for custom functions in the next section.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1' -ItemType File 

# Create a RoleCapabilities folder in the AD_Module folder. PowerShell expects Role Capabilities to be located in a "RoleCapabilities" folder within a module.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities' -ItemType Directory

# Create a blank Role Capability in your RoleCapabilities folder. Running this command without any additional parameters just creates a blank template.
New-PSRoleCapabilityFile -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc' 
```

Il file di capacità del ruolo è stato creato
e potrà essere usato nella sezione successiva.

### Concetti chiave
**Capacità del ruolo (estensione psrc)**: file che definisce le operazioni che un utente può eseguire in corrispondenza di un endpoint JEA.
Indica in dettaglio una serie di elementi, tra cui comandi visibili, applicazioni visibili della console e altro ancora.
Per fare in modo che PowerShell rilevi le capacità del ruolo, è necessario inserirle in una cartella "RoleCapabilities" in un modulo di PowerShell valido.

**Modulo di PowerShell**: pacchetto di funzionalità di PowerShell.
Può contenere funzioni di PowerShell, cmdlet, risorse DSC, capacità del ruolo e altro ancora.
Per essere caricati automaticamente, i moduli di PowerShell devono trovarsi in un percorso in `$env:PSModulePath`. 

## End-to-end - Active Directory
Si supponga che l'ambito del programma sia aumentato
e di essere responsabili dell'aggiunta di JEA ai controller di dominio per eseguire azioni di Active Directory.
Il personale dell'help desk userà JEA per sbloccare gli account, reimpostare le password ed eseguire altre operazioni simili.

È necessario esporre un set di comandi completamente nuovo per un altro gruppo di persone.
In più, si dovrà esporre anche una serie di script di Active Directory già esistenti.
In questa sezione verrà illustrata la creazione di una configurazione di sessione e delle capacità del ruolo per questa attività.

### Prerequisiti
Per seguire le istruzioni dettagliate di questa sezione, è necessario lavorare su un controller di dominio.
Se non si ha accesso al proprio controller di dominio non è un problema.
Provare a seguire la procedura lavorando in un altro scenario o ruolo con cui si ha familiarità.
Per configurare rapidamente un nuovo controller di dominio, consultare l'appendice [Creazione di un controller di dominio](#creating-a-domain-controller).

### Procedura per la creazione di una nuova capacità del ruolo e una configurazione di sessione

Creare una nuova capacità del ruolo può essere scoraggiante all'inizio, ma l'operazione può essere suddivisa in passaggi abbastanza semplici:

1.  Identificare le attività che è necessario abilitare
2.  Limitare le attività secondo le esigenze
3.  Verificare che funzionino con JEA
4.  Inserirle in un file di capacità del ruolo
5.  Registrare una configurazione di sessione che espone la capacità del ruolo

### Passaggio 1: Identificare gli elementi da esporre
Prima di creare una nuova capacità del ruolo o configurazione di sessione, è necessario identificare tutte le attività che gli utenti dovranno svolgere attraverso l'endpoint JEA, nonché le modalità di gestione con PowerShell.
Questo comporta un discreto lavoro di ricerca e raccolta dei requisiti.
Il modo di procedere dipende dall'organizzazione e dagli obiettivi.
È importante sottolineare che la ricerca e la raccolta dei requisiti costituiscono una parte essenziale del processo reale.
Potrebbe trattarsi del passaggio più difficile del processo di adozione di JEA.

#### Reperire le risorse
Di seguito sono riportate alcune risorse online che potrebbero apparire nella ricerca in relazione alla creazione di un endpoint di gestione di Active Directory:
-   [Panoramica di Active Directory PowerShell](http://blogs.msdn.com/b/adpowershell/archive/2009/03/05/active-directory-powershell-overview.aspx) 
-   [Guida per il passaggio da CMD a PowerShell per Active Directory](http://blogs.technet.com/b/ashleymcglone/archive/2013/01/02/free-download-cmd-to-powershell-guide-for-ad.aspx)

#### Creare un elenco
Ecco una serie di dieci azioni che verranno usate più avanti in questa sezione.
Tenere presente che si tratta semplicemente di un esempio, i requisiti della propria organizzazione possono essere diversi:

|Azione                                                         |Comando di PowerShell                                             |
|---------------------------------------------------------------|---------------------------------------------------------------|
|Sblocco dell'account                                                 |`Unlock-ADAccount`                                             |
|Reimpostazione della password                                                 |`Set-ADAccountPassword` e `Set-ADUser -ChangePasswordAtLogon`|
|Modifica del titolo di un utente                                          |`Set-ADUser -Title`                                            |  
|Ricerca di account di Active Directory bloccati, disabilitati, inattivi e così via |`Search-ADAccount`                                             | 
|Aggiunta di un utente a un gruppo                                              |`Add-ADGroupMember -Identity (with whitelist) -Members`        | 
|Rimozione di un utente da un gruppo                                         |`Remove-ADGroupMember -Identity (with whitelist) -Members`     | 
|Abilitazione di un account utente                                          |`Enable-ADAccount`                                             |
|Disabilitazione di un account utente                                         |`Disable-ADAccount`                                            |

### Passaggio 2: Limitare le attività secondo le esigenze

Ora che si ha a disposizione un elenco di azioni, è necessario valutare la funzionalità di ogni comando.
Esistono due motivi principali per eseguire questa operazione:

1.  È facile esporre più funzionalità del previsto per gli utenti.
Ad esempio, `Set-ADUser` è un comando incredibilmente potente e flessibile.
È opportuno evitare di esporre tutto ciò che è in grado di fare agli utenti dell'help desk.  

2.  Peggio ancora, è possibile esporre comandi che consentono agli utenti di evitare le restrizioni di JEA.
In questo caso JEA smette di funzionare come limite di sicurezza.
Prestare attenzione quando si selezionano i comandi.
Ad esempio, Invoke-Expression consentirà agli utenti di eseguire codice senza restrizioni.
Per altre informazioni su questo argomento, vedere la sezione relativa alla limitazione dei comandi.

Dopo aver esaminato ogni comando, si decide di limitare quanto segue:

1.  `Set-ADUser` deve essere eseguito solo con il parametro "-Title" 

2.  `Add-ADGroupMember` e `Remove-ADGroupMember` deve funzionare solo con alcuni gruppi

### Passaggio 3: Verificare se le attività funzionano con JEA
Usare i cmdlet potrebbe non essere semplice nell'ambiente JEA con restrizioni.
JEA viene eseguito in modalità *NoLanguage* che, tra l'altro, impedisce agli utenti di usare le variabili.
Per garantire che gli utenti finali usufruiscano di un'esperienza ottimale, è importante verificare alcuni aspetti.

Ad esempio, considerare `Set-ADAccountPassword`.
Il parametro "-NewPassword" richiede una stringa sicura.
Spesso gli utenti creano un stringa sicura e la passano come variabile, come indicato di seguito:

```PowerShell
$newPassword = (Read-Host -Prompt "Specify a new password" -AsSecureString)
Set-ADAccountPassword -Identity mollyd -NewPassword $newPassword -Reset
```

La modalità NoLanguage impedisce l'uso delle variabili.
È possibile aggirare questa restrizione in due modi:

1.  È possibile richiedere agli utenti di eseguire il comando senza assegnare variabili.
La relativa configurazione è semplice, ma può diventare macchinosa per gli operatori che usano l'endpoint,
che ad ogni reimpostazione di una password dovrebbero digitare quanto segue:
```PowerShell
Set-ADAccountPassword -Identity mollyd -NewPassword (Read-Host -Prompt "Specify a new password" -AsSecureString) -Reset
```

2.  È possibile ridurre la complessità usando uno script o una funzione da esporre agli utenti finali.
Le funzioni e gli script esposti vengono eseguiti in un contesto senza restrizioni. È possibile scrivere funzioni che usano le variabili e chiamano altri comandi senza alcun problema.
Questo approccio semplifica l'esperienza dell'utente finale, impedisce gli errori, riduce la competenza necessaria con PowerShell ed evita che vengano esposte involontariamente funzionalità in eccesso.
L'unico svantaggio è costituito dai costi di creazione e gestione della funzione.

#### Approfondimento: Aggiunta di una funzione al modulo
Con l'approccio n. 2 si scrive una funzione di PowerShell denominata `Reset-ContosoUserPassword`.
Questa funzione dovrà eseguire tutte le operazioni necessarie quando si reimposta la password di un utente.
In un'organizzazione questo può significare dover svolgere attività elaborate e complesse.
Poiché si tratta semplicemente di un esempio, il comando si limiterà a reimpostare la password e a richiedere all'utente di cambiare la password all'accesso.
Il comando verrà inserito nel modulo Contoso_AD_Module creato nell'ultima sezione.

1. In PowerShell ISE aprire "Contoso_AD_Module.psm1"
```PowerShell
ISE 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1' 
```

2. Premere CTRL + J per aprire il menu dei frammenti di codice.

3. Premere la freccia in basso finché non appare "function" e premere INVIO.
In questo modo viene creato uno "scheletro" molto essenziale di funzione.

4. Rinominare la funzione "Reset-ContosoUserPassword".  

5. Rinominare uno dei parametri "Identity" ed eliminare il secondo.

6. Copiare quanto segue nel corpo della funzione.
```PowerShell
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
```

7. Salvare il file.
Il risultato dovrebbe essere simile al seguente:
```PowerShell
function Reset-ContosoUserPassword ($Identity)
{
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
} 
```
A questo punto, gli utenti possono semplicemente chiamare `Reset-ContosoUserPassword` senza dover ricordare la sintassi richiesta per creare una stringa sicura inline.

### Passaggio 4: Modificare il file di capacità del ruolo
Nella sezione [Creazione di capacità del ruolo](#role-capability-creation) è stato creato un file di capacità del ruolo vuoto.
In questa sezione verranno inseriti i valori nel file.

Per prima cosa, aprire il file di capacità del ruolo in ISE.
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc' 
```
Aggiornare il file con le seguenti modifiche:
```PowerShell
# OLD: VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleCmdlets =
    'Unlock-ADAccount',
    'Search-ADAccount',
    'Enable-ADAccount',
    'Disable-ADAccount',
    @{ Name = 'Set-ADUser'; Parameters = @{ Name = 'Title'; ValidateSet = 'Manager', 'Engineer' }},
    @{ Name = 'Add-ADGroupMember'; Parameters = 
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}},
    @{ Name = 'Remove-ADGroupMember'; Parameters = 
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}}
  
# OLD: VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }   
VisibleFunctions = 'Reset-ContosoUserPassword'
```

Riguardo al codice riportato sopra è necessario osservare quanto segue:
1.  PowerShell tenterà di caricare automaticamente i moduli necessari per la capacità del ruolo.
Può essere necessario indicare in modo esplicito i nomi dei moduli nel campo "ModulesToImport" se si riscontrano problemi con un modulo che non viene caricato automaticamente.

2.  Per verificare se un comando è un cmdlet o una funzione, eseguire `Get-Command` e controllare "CommandType"

3.  ValidatePattern consente di usare un'espressione regolare per limitare gli argomenti di parametro, nel caso in cui non sia facile definire un set di valori consentiti.
Non è possibile definire sia un valore ValidatePattern che un valore ValidateSet per un singolo parametro.

### Passaggio 5: Registrare una nuova configurazione di sessione
È necessario creare un nuovo file di configurazione di sessione che esporrà la capacità del ruolo ai membri del gruppo "JEA_NonAdmin_HelpDesk" di Active Directory. 

Per iniziare, creare e aprire un nuovo file di configurazione di sessione vuoto in PowerShell ISE.
```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc" 
ise "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
Modificare i campi seguenti nel file PSSC.
Se si lavora nel proprio ambiente, è necessario sostituire "CONTOSO\JEA_NonAdmins_Helpdesk" con il proprio utente o gruppo non amministratore.
```PowerShell
# OLD: Description = ''
Description = 'An endpoint for active directory tasks.' 

# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{ 'CONTOSO\JEA_NonAdmin_HelpDesk' = @{ RoleCapabilities =  'ADHelpDesk' }} 
```
Salvare e registrare la configurazione di sessione
```PowerShell
Register-PSSessionConfiguration -Name ADHelpDesk -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc" 
```
### Testare la configurazione
Ottenere le credenziali di utente non amministratore:
```PowerShell
$HelpDeskCred = Get-Credential
```
Se è stata seguita la sezione relativa alla configurazione di utenti e gruppi, saranno:
-   Username = "HelpDeskUser"
-   Password = "pa$$w0rd"

Accedere in remoto all'endpoint dell'help desk di Active Directory usando le credenziali di utente non amministratore:
```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName ADHelpDesk -Credential $HelpDeskCred 
```
Usare Set-ADUser per reimpostare il titolo di un utente.
```PowerShell
Set-ADUser -Identity OperatorUser -Title Engineer 
```
Verificare che il titolo è stato modificato.
```PowerShell
Get-ADUser -Identity OperatorUser -Property Title 
```
A questo punto, usare Add-ADGroupMember per aggiungere un utente al gruppo TestGroup.
Nota: verificare che TestGroup sia già stato creato.
```PowerShell
Add-ADGroupMember TestGroup -Member OperatorUser -Verbose 
```
Chiudere la sessione:
```PowerShell
Exit-PSSession
```
### Concetti chiave
**Modalità NoLanguage**: quando PowerShell è in modalità "NoLanguage", gli utenti possono solo eseguire i comandi e non possono usare elementi del linguaggio.
Per altre informazioni, eseguire `Get-Help about_Language_Modes`.

**Funzioni di PowerShell**: le funzioni di PowerShell sono parti di codice di PowerShell che è possibile chiamare in base al nome.
Per altre informazioni, eseguire `Get-Help about_Functions`.

**ValidateSet/ValidatePattern**: quando si espone un comando, è possibile limitare gli argomenti validi per parametri specifici.
ValidateSet indica un elenco specifico di comandi validi.
ValidatePattern è un'espressione regolare a cui gli argomenti per il parametro devono corrispondere.

## Distribuzione e manutenzione con più computer
A questo punto, JEA è stato distribuito più volte ai sistemi locali.
Poiché l'ambiente di produzione probabilmente è costituito da più di un computer, è importante esaminare i passaggi essenziali del processo di distribuzione che dovranno essere ripetuti in ogni computer.

### Passaggi di alto livello:
1.  Copiare i moduli (con capacità del ruolo) in ogni nodo.
2.  Copiare i file di configurazione di sessione in ogni nodo.
3.  Eseguire `Register-PSSessionConfiguration` con la configurazione di sessione.
4.  Conservare una copia della configurazione di sessione e dei toolkit in un luogo sicuro.
Quando si apportano modifiche, è opportuno usare un'unica "origine di dati reali".

### Script di esempio
Di seguito è riportato un esempio di script per la distribuzione.
Per usarlo nel proprio ambiente, è necessario usare i nomi o i percorsi dei moduli e delle condivisioni di file reali.
```PowerShell
# First, copy the session configuration and modules (containing role capability files) onto a file share you have access to.
Copy-Item -Path 'C:\Demo\Demo.pssc' -Destination '\\FileShare\JEA\Demo.pssc'
Copy-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\SomeModule\' -Recurse -Destination '\\FileShare\JEA\SomeModule'

# Next, author a setup script (C:\JEA\Deploy.ps1) to run on each individual node
    # Contents of C:\JEA\Deploy.ps1
    New-Item -ItemType Directory -Path C:\JEADeploy
    Copy-Item -Path '\\FileShare\JEA\Demo.pssc' -Destination 'C:\JEADeploy\'
    Copy-Item -Path '\\FileShare\JEA\SomeModule' -Recurse -Destination 'C:\Program Files\WindowsPowerShell\Modules' # Remember, Role Capability Files are found in modules
    if (Get-PSSessionConfiguration -Name JEADemo -ErrorAction SilentlyContinue)
    {
        Unregister-PSSessionConfiguration -Name JEADemo -ErrorAction Stop
    }

    Register-PSSessionConfiguration -Name JEADemo -Path 'C:\JEADeploy\Demo.pssc'
    Remove-Item -Path 'C:\JEADeploy' # Don't forget to clean up!

# Now, invoke the script on all of the target machines.
# Note: this requires PowerShell Remoting be enabled on each machine. Enabling PowerShell remoting is a requirement to use JEA as well.
# You may need to provide the "-Credential" parameter if your current user account does not have admin permissions on these machines.
Invoke-Command –ComputerName 'Node1', 'Node2', 'Node3', 'NodeN' -FilePath 'C:\JEA\Deploy.ps1'

# Finally, delete the session configuration and role capability files from the file share.
Remove-Item -Path '\\FileShare\JEA\Demo.pssc'
Remove-Item -Path '\\FileShare\JEA\SomeModule' -Recurse
```
### Modifica delle capacità
Quando si gestiscono molti computer, è importante che le modifiche vengano implementate in modo coerente.
Se per JEA è già disponibile una risorsa DSC, l'ambiente è sincronizzato.
In caso contrario, è consigliabile conservare una copia master delle configurazioni di sessione e distribuirla di nuovo ogni volta che si apporta una modifica.

### Rimozione delle capacità
Per rimuovere la configurazione JEA dai sistemi, usare il comando seguente in ogni computer:
```PowerShell
Unregister-PSSessionConfiguration -Name JEADemo 
```
## Creazione di report per JEA
Poiché JEA consente agli utenti senza privilegi l'esecuzione in un contesto con privilegi, la registrazione e il controllo sono estremamente importanti.
In questa sezione vengono illustrati gli strumenti che agevolano le procedure di registrazione e creazione di report.

### Creazione di report per azioni JEA
#### Trascrizione over-the-shoulder
Uno dei modi più rapidi per ottenere un riepilogo delle operazioni eseguite in una sessione di PowerShell è osservare da vicino l'attività dell'utente.
Vengono visualizzati i comandi in uso, l'output di tali comandi e tutto appare in ordine.
Oppure no, ma almeno si viene a sapere.
Le trascrizioni di PowerShell sono progettate in modo da offrire una visualizzazione simile al termine dell'attività.

Quando si usa il campo "TranscriptDirectory" nella configurazione di sessione, PowerShell registra automaticamente una trascrizione di tutte le azioni intraprese in una determinata sessione.
Le trascrizioni dalle sessioni sono contenute in questo documento: "$env: ProgramData\JEAConfiguration\Transcripts"

Come si può vedere, la trascrizione registra informazioni sull'utente "connesso", l'utente "RunAs", i comandi eseguiti nella sessione e altro ancora.
Per altre informazioni sulle trascrizioni di PowerShell, vedere questo [post del blog](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).

#### Registri eventi di PowerShell
Dopo aver attivato la registrazione dei moduli, anche tutte le azioni di PowerShell vengono registrate nei normali registri eventi di Windows.
Questa attività è leggermente più complessa da gestire rispetto alle trascrizioni, ma può essere utile il livello di dettaglio che offre.

Nel registro operativo "PowerShell", l'ID evento 4104 registrerà ogni comando richiamato se è stata abilitata la registrazione dei moduli.

#### Altri registri eventi
A differenza dei registri e delle trascrizioni di PowerShell, altri meccanismi di registrazione non acquisiscono l'utente "connesso".
È necessario stabilire una certa correlazione tra gli altri registri e i registri di PowerShell per la corrispondenza tra le azioni intraprese.

Nel registro operativo di "Gestione remota Windows", l'ID evento 193 registrerà il SID e il nome dell'utente connesso, nonché il SID dell'account virtuale RunAs per agevolare questa correlazione.
Come forse si è notato, il nome dell'account virtuale RunAs include alla fine il dominio e il nome utente dell'utente connesso.

### Creazione di report per la configurazione JEA
#### Get-PSSessionConfiguration
Per segnalare con precisione lo stato dell'ambiente, è importante sapere quanti endpoint JEA sono impostati sul computer.
`Get-PSSessionConfiguration` esegue questa operazione.
 
#### Get-PSSessionCapability
Creare manualmente report sulle capacità di ogni utente usando un endpoint JEA può essere molto complesso.
Potenzialmente occorre controllare diverse capacità del ruolo.
Fortunatamente il cmdlet "Get-PSSessionCapability" esegue questa operazione.

Per testarlo, eseguire il comando seguente dal prompt dei comandi di PowerShell come amministratore:
```PowerShell
Get-PSSessionCapability -Username 'CONTOSO\OperatorUser' -ConfigurationName JEADemo
```
## Conclusione 
Dopo aver completato questa guida, si hanno a disposizione gli strumenti e il vocabolario necessari per creare il proprio endpoint JEA. Grazie per aver letto questo documento.

## Appendice

## Concetti principali usati in questa guida
**Comunicazione remota di PowerShell**: consente di eseguire i comandi di PowerShell nei computer remoti.
È possibile lavorare con uno o più computer e usare connessioni temporanee o permanenti.
In questa demo la comunicazione remota viene eseguita nel computer locale con una sessione interattiva.
JEA limita le funzionalità disponibili attraverso la comunicazione remota di PowerShell.
Per altre informazioni sulla comunicazione remota di PowerShell, eseguire `Get-Help about_Remote`.

**Utente "RunAs"**: quando si usa JEA, un utente non amministratore viene eseguito come "account virtuale" con privilegi.
L'account virtuale esiste solo durante la sessione remota.
Vale a dire, viene creato quando un utente si connette all'endpoint ed eliminato quando l'utente termina la sessione.
Per impostazione predefinita, l'account virtuale è un membro del gruppo Administrators locale.
In un controller di dominio è un membro del gruppo Domain Admins.
Gli account virtuali sono locali nel computer in cui vengono creati e non usufruiscono di autorizzazioni di fuori di tale computer.
Ciò significa che non vengono registrati in Active Directory e che non viene assegnato alcun RID.
Inoltre, se un comando o script consentito tenta di accedere alle risorse esterne al computer locale, accederà a tali risorse con l'identità del computer, non l'identità dell'account virtuale.

**Utente "connesso"**: l'utente non amministratore che si connette all'endpoint JEA e a cui vengono assegnati i ruoli.
I comandi eseguiti da questo utente vengono eseguiti nel contesto dell'utente RunAs o dell'account virtuale.


### Creazione di un controller di dominio

In questo documento si presuppone che il computer faccia parte di un dominio.
Se non esiste un dominio a cui aggiungere il computer, questa sezione spiega come configurare rapidamente un controller di dominio con DSC.

#### Prerequisiti

1.  Il computer fa parte di una rete interna
2.  Il computer non è associato a un dominio esistente
3.  Il computer esegue Windows Server 2016 o ha WMF 5.0 installato

#### Installare xActiveDirectory
Se il computer ha una connessione attiva a Internet, eseguire il comando seguente in una finestra di PowerShell con privilegi elevati:
```PowerShell
Install-Module xActiveDirectory -Force 
```
Se non è presente una connessione a Internet, installare xActiveDirectory in un altro computer e quindi copiare la cartella xActiveDirectory nella cartella "C:\Programmi\WindowsPowerShell\Modules" nel computer in uso.

Per verificare se l'installazione ha avuto esito positivo, eseguire il comando seguente:
```PowerShell
Get-Module xActiveDirectory -ListAvailable
``` 

#### Configurare un dominio con DSC
Copiare il seguente script di PowerShell per impostare il computer in uso come controller di dominio in un nuovo dominio.
**NOTA DELL'AUTORE: ESISTE UN PROBLEMA NOTO CON LE CREDENZIALI SPECIFICATE E NON UTILIZZATE.  PER SICUREZZA, NON DIMENTICARE LA PASSWORD DI AMMINISTRATORE LOCALE.**

```PowerShell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value $env:COMPUTERNAME -Force 

# This "MetaConfiguration" sets the DSC Engine to automatically reboot if required
[DscLocalConfigurationManager()]
Configuration MetaConfiguration
{
    Node $env:Computername
    {
        Settings
        {
            RebootNodeIfNeeded = $true
        }
    }
    
}

MetaConfiguration
# Apply the MetaConfiguration
Set-DscLocalConfigurationManager .\MetaConfiguration

# Configure a domain controller of a new "Contoso" domain
configuration DomainController
{
    param
    (
        $node,
        $cred
    )
    Import-DscResource -ModuleName xActiveDirectory

    Node $node
    {
        WindowsFeature ADDS
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain Contoso
        {
            DomainName = 'contoso.com'
            DomainAdministratorCredential = $cred
            SafemodeAdministratorPassword = $cred
            DependsOn = '[WindowsFeature]ADDS'
        }

        file temp
        {
            DestinationPath = 'C:\temp.txt'
            Contents = 'Domain has been created'
            DependsOn = '[xADDomain]Contoso'
        }
    }
}

$ConfigData = @{
    AllNodes = @(
        @{
            NodeName = $env:Computername
            PSDscAllowPlainTextPassword = $true
        }
    )
}

# Enter your desired password for the domain administrator (note, this will be stored as plain text)
DomainController -cred (Get-Credential -Message "Enter desired credential for domain administrator") -node $env:Computername -configurationData $ConfigData

# Apply the configuration to create the domain controller
Start-DSCConfiguration -path .\DomainController -ComputerName $env:Computername -Wait -Force -Verbose
```
Il computer verrà riavviato più volte.
Il processo è completato quando viene visualizzato un file denominato "C:\temp.txt" che indica che il dominio è stato creato. 

#### Configurare utenti e gruppi
I comandi seguenti consentono di configurare i gruppi Operator e Helpdesk nel dominio e un utente non amministratore corrispondente che è membro dei gruppi.
```PowerShell
# Make Groups
$NonAdminOperatorGroup = New-ADGroup -Name "JEA_NonAdmin_Operator" -GroupScope DomainLocal -PassThru
$NonAdminHelpDeskGroup = New-ADGroup -Name "JEA_NonAdmin_HelpDesk" -GroupScope DomainLocal -PassThru
$TestGroup = New-ADGroup -Name "Test_Group" -GroupScope DomainLocal -PassThru

# Make Users
$OperatorUser = New-ADUser -Name "OperatorUser" -AccountPassword (ConvertTo-SecureString "pa`$`$w0rd" -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $OperatorUser

$HelpDeskUser = New-ADUser -name "HelpDeskUser" -AccountPassword (ConvertTo-SecureString "pa`$`$w0rd" -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $HelpDeskUser

# Add Users to Groups
Add-ADGroupMember -Identity $NonAdminOperatorGroup -Members $OperatorUser
Add-ADGroupMember -Identity $NonAdminHelpDeskGroup -Members $HelpDeskUser
```

### Blacklist
Dopo essersi esercitati con JEA, ci si potrebbe chiedere se è possibile disattivare i comandi.
Si tratta di una domanda legittima, ma l'operazione non è attualmente prevista per JEA per i motivi seguenti:

1.  JEA è stato progettato per limitare gli operatori solo alle azioni che devono svolgere.
La blacklist è un concetto opposto.

2.  Gli autori dei comandi di PowerShell non hanno progettato i comandi di PowerShell prendendo in considerazione JEA.
In una nuova installazione di Windows Server 2016 sono immediatamente disponibili circa 1520 comandi.
I modelli di rischio per questi comandi non includono la possibilità che un utente esegua i comandi come account con più privilegi.
Ad esempio, alcuni comandi consentono l'inserimento di codice a livello di progettazione (Add-Type e Invoke-Command nel modulo core di PowerShell).
JEA visualizza un avviso quando si espongono i comandi visti in precedenza, ma tutti gli altri comandi di Windows non sono stati nuovamente valutati in base al nuovo modello di rischio.
È necessario comprendere le capacità dei comandi che si espongono con JEA.  

3.  E anche se JEA blocca tutti i comandi con vulnerabilità tipo "code injection", non vi sono garanzie che un utente malintenzionato non sia in grado di eseguire un'azione inserita nella blacklist con un altro comando correlato.
Se non si comprendono tutti i comandi che si intende esporre, non è possibile garantire che una determinata operazione non venga eseguita.
L'impegno consiste nel comprendere i comandi esposti e se tali comandi usano una whitelist o una blacklist.
Il numero di comandi che possono essere esposti in base a una blacklist è da gestire, quindi JEA viene implementato usando invece delle whitelist.

### Considerazioni per la limitazione dei comandi
Questo passaggio richiede una puntualizzazione.
È essenziale che tutte le funzionalità esposte con JEA si trovino in aree con restrizioni di amministratore.
Gli utenti non amministratori non devono essere in grado di modificare gli script usati negli endpoint JEA.

Si noti che è fondamentale non concedere agli utenti di JEA la possibilità di sovrascrivere le configurazioni di JEA e gli script consentiti all'interno delle proprie sessioni di JEA.
Prestare particolare attenzione quando si espongono comandi come `Copy-Item`.

### Problemi comuni delle capacità del ruolo
È possibile incorrere in alcuni inconvenienti durante il processo.
Questa guida rapida illustra come identificare e risolvere tali inconvenienti quando si modifica o si crea un nuovo endpoint:

#### Funzioni e Cmdlet
I comandi di PowerShell scritti in PowerShell sono funzioni di PowerShell.
I comandi di PowerShell scritti come classi .NET specializzate sono cmdlet di PowerShell.
È possibile verificare il tipo di comando eseguendo `Get-Command`.

#### VisibleProviders 
È necessario esporre qualsiasi provider richiesto dai comandi.
Il più comune è il provider FileSystem, ma potrebbe essere necessario esporne altri, ad esempio il provider Registry.
Per un'introduzione ai provider, vedere il [post del blog Hey, Scripting Guy](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).
Prestare attenzione quando si espongono i provider: spesso è preferibile definire una propria funzione da usare con i provider sottostanti anziché esporre direttamente il provider in una sessione di JEA.
In questo modo, è comunque possibile consentire agli utenti di lavorare con file, chiavi del Registro di sistema e così via, mantenendo tuttavia il controllo su **quali* file e chiavi del Registro di sistema possono essere usati con la logica di convalida personalizzata.

<!--HONumber=Jun16_HO1-->


