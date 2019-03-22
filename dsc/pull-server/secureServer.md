---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Procedure consigliate per i server di pull
ms.openlocfilehash: fe483a487f85f2e4edb0928fccfe98746ae11231
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2019
ms.locfileid: "58057706"
---
# <a name="pull-server-best-practices"></a>Procedure consigliate per i server di pull

Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Il server di pull (funzionalità di Windows *servizio DSC*) è un componente supportato di Windows Server, tuttavia non si prevede di offrire nuove caratteristiche o funzionalità. È consigliabile avviare la transizione dei client gestiti ad [Automation DSC per Azure](/azure/automation/automation-dsc-getting-started) (include funzionalità superiori al server di pull in Windows Server) o a una delle soluzioni della community riportate [qui](pullserver.md#community-solutions-for-pull-service).

Riepilogo: questo documento illustra processi ed estendibilità per supportare i tecnici che preparano la soluzione. I dettagli inclusi offrono procedure consigliate identificate dai clienti e validate dal team del prodotto per garantire che le indicazioni siano stabili e valide per il futuro.

| |Informazioni sul documento|
|:---|:---|
Autore | Michael Greene
Revisori | Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic
Pubblicato | Aprile 2015

## <a name="abstract"></a>Contenuto

Questo documento è designato a offrire procedure ufficiali a coloro che pianificano di implementare un server di pull per la configurazione dello stato desiderato tramite Windows PowerShell. Un server di pull è un servizio semplice, la cui distribuzione dovrebbe impiegare solo alcuni minuti. Sebbene questo documento includa procedure tecniche che possono essere usate in una distribuzione, il suo scopo è di essere un riferimento per procedure consigliate e per gli elementi da considerare prima di eseguire una distribuzione.
I lettori devono avere una conoscenza di base di DSC e dei termini usati per descrivere i componenti inclusi in una distribuzione DSC. Per altre informazioni, vedere [Panoramica di Windows PowerShell DSC (Desired State Configuration)](/powershell/dsc/overview).
Poiché si presuppone che DSC evolverà presto verso una cadenza cloud, la tecnologia che sta alla base, inclusi i server di pull, evolverà e presenterà nuove funzionalità. Questo documento include nell'appendice una tabella delle versioni, che offre riferimenti a versioni precedenti e a soluzioni future per incoraggiare la creazione di strutture che guardano al futuro.

Le due sezioni principali di questo documento sono:

- Pianificazione della configurazione
- Guida all'installazione

### <a name="versions-of-the-windows-management-framework"></a>Versioni di Windows Management Framework

Le informazioni contenute in questo documento sono applicabili a Windows Management Framework 5.0. Anche se WMF 5.0 non è necessario per la distribuzione e l'operatività di un server di pull, in questo documento si fa riferimento alla versione 5.0.

### <a name="windows-powershell-desired-state-configuration"></a>Configurazione dello stato desiderato tramite Windows PowerShell

La configurazione dello stato desiderato (DSC) è una piattaforma di gestione che consente la distribuzione e la gestione dei dati di configurazione usando una sintassi standard, denominata Managed Object Format (MOF) per descrivere Common Information Model (CIM). Un progetto open source, Open Management Infrastructure (OMI), è disponibile per altri sviluppi di tali standard tra piattaforme, ad esempio Linux e sistemi operativi per hardware di rete. Per altre informazioni, vedere la [pagina DMTF con il collegamento alle specifiche MOF](https://www.dmtf.org/standards/cim) e la pagina che elenca i [documenti e le origine OMI](https://collaboration.opengroup.org/omi/documents.php).

Windows PowerShell offre un set di estensioni del linguaggio per la configurazione dello stato desiderato che è possibile usare per creare e gestire configurazioni dichiarative.

### <a name="pull-server-role"></a>Ruolo del server di pull

Un server di pull offre un servizio centralizzato per archiviare le configurazioni che saranno accessibili per i nodi di destinazione.

Il ruolo del server di pull può essere distribuito come istanza del server Web o come condivisione di file SMB. La funzionalità del server Web include un'interfaccia OData e può facoltativamente includere funzionalità per i nodi di destinazione per restituire la conferma di un esito positivo o negativo quando vengono applicate le configurazioni. Questa funzionalità è utile in ambienti in cui è presente un numero elevato di nodi di destinazione.
Dopo la configurazione di un nodo di destinazione (noto anche come client) verso il server di pull, vengono scaricati e applicati i dati della configurazione più recente e gli script necessari. Questa operazione può essere eseguita come distribuzione singola o come processo ripetuto. Ciò rende il server di pull un'importante risorsa per la gestione di modifiche su larga scala. Per altre informazioni, vedere [Windows PowerShell Desired State Configuration Pull Servers](/powershell/dsc/pullServer) (Server di pull per la configurazione dello stato desiderato tramite Windows PowerShell) e

[Push and Pull Configuration Modes](/powershell/dsc/pullServer) (Modalità di configurazione push e pull).

## <a name="configuration-planning"></a>Pianificazione della configurazione

Per la distribuzione di software aziendale, alcune informazioni possono essere raccolte in anticipo per supportare la pianificazione dell'architettura appropriata e per essere pronti ai passaggi necessari per completare la distribuzione. Le sezioni seguenti includono informazioni su come preparare la distribuzione e le connessioni organizzative che dovranno probabilmente essere eseguite in anticipo.

### <a name="software-requirements"></a>Requisiti software

La distribuzione di un server di pull richiede la funzionalità del servizio DSC di Windows Server. Questa funzionalità è stata introdotta in Windows Server 2012 ed è stata aggiornata tramite le versioni in corso di Windows Management Framework (WMF).

### <a name="software-downloads"></a>Download del software

Oltre a installare i contenuti più recenti da Windows Update, per distribuire un server di pull DSC è consigliabile scaricare la versione più recente di Windows Management Framework e un modulo DSC per automatizzare il provisioning del server di pull.

### <a name="wmf"></a>WMF

Windows Server 2012 R2 include una funzionalità denominata servizio DSC. La caratteristica servizio DSC offre la funzionalità del server di pull, inclusi i file binari che supportano l'endpoint OData.
WMF è incluso in Windows Server e viene aggiornato regolarmente tra le versioni di Windows Server. Le [nuove versioni di WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616) possono includere aggiornamenti per la funzionalità del servizio DSC. Per questo motivo, è consigliabile scaricare la versione più recente di WMF ed esaminare le note sulla versione per determinare se la versione include un aggiornamento per la funzionalità servizio DSC. È anche necessario esaminare la sezione delle note sulla versione che indica se lo stato di progettazione per uno scenario o per un aggiornamento è elencato come stabile o sperimentale.
Per consentire un ciclo di versioni agile, le singole funzionalità possono essere dichiarate stabili, ovvero sono pronte per essere usate in un ambiente di produzione, anche se WMF viene rilasciato in anteprima.
Altre funzionalità che storicamente sono state aggiornate dalle versioni di WMF (per altre informazioni, vedere le note sulla versione WMF):

- Windows PowerShell Integrated Scripting Environment (ISE)
- Servizi Web di Windows PowerShell (Estensione IIS OData gestione)
- Configurazione dello stato desiderato tramite Windows PowerShell (DSC)
- Gestione remota Windows (WinRM) Strumentazione gestione Windows (WMI)

### <a name="dsc-resource"></a>Risorsa DSC

Una distribuzione del server di pull può essere semplificata dal provisioning del servizio tramite uno script di configurazione DSC. Questo documento include gli script di configurazione che possono essere usati per distribuire un nodo server pronto per la produzione. Per usare gli script di configurazione, è necessario un modulo DSC non incluso in Windows Server. Il nome del modulo necessario è **xPSDesiredStateConfiguration**, il quale include la risorsa DSC **xDscWebService**. È possibile scaricare il modulo xPSDesiredStateConfiguration [qui](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).

Usare il cmdlet `Install-Module` dal modulo **PowerShellGet**.

```powershell
Install-Module xPSDesiredStateConfiguration
```

Il modulo **PowerShellGet** scaricherà il modulo in:

`C:\Program Files\Windows PowerShell\Modules`

Pianificazione dell'attività|
---|
Si ha accesso ai file di installazione di Windows Server 2012 R2?|
L'ambiente di distribuzione ha accesso a Internet per scaricare WMF e il modulo dalla raccolta online?|
Come si installeranno gli aggiornamenti più recenti dopo l'installazione del sistema operativo?|
L'ambiente avrà accesso a Internet per ottenere gli aggiornamenti oppure avrà un server locale Windows Server Update Services (WSUS)?|
Si ha accesso ai file di installazione di Windows Server che includono già gli aggiornamenti tramite un'aggiunta offline?|

### <a name="hardware-requirements"></a>Requisiti hardware

Le distribuzioni di server di pull sono supportate nei server fisici e virtuali. I requisiti di dimensioni per il server di pull si allineano con i requisiti per Windows Server 2012 R2.

CPU: processore a 64 bit da 1,4 GHz Memoria: 512 MB Spazio su disco: 32 GB Rete: scheda Gigabit Ethernet

Pianificazione dell'attività|
---|
La distribuzione verrà eseguita in hardware fisico o su una piattaforma di virtualizzazione?|
Qual è il processo per richiedere un nuovo server per l'ambiente di destinazione?|
Qual è il tempo medio necessario a un server per essere disponibile?|
Quali dimensioni del server saranno richieste?|

### <a name="accounts"></a>Account

Non sono previsti requisiti di account di servizio per distribuire un'istanza del server di pull.
Ci sono tuttavia scenari in cui il sito Web può essere eseguito nel contesto di un account utente locale.
Ad esempio, se è necessario accedere a una condivisione di archiviazione per il contenuto del sito Web e Windows Server o il dispositivo che ospita la condivisione di archiviazione non sono aggiunti a un dominio.

### <a name="dns-records"></a>Record DNS

È necessario avere un nome di server quando si configurano i client che usano un ambiente server di pull.
In ambienti di test, viene in genere usato il nome host del server oppure può essere usato l'indirizzo IP per il server se la risoluzione dei nomi DNS non è disponibile.
Negli ambienti di produzione o in un ambiente lab che ha lo scopo di rappresentare una distribuzione di produzione, la procedura consigliata consiste nel creare un record CNAME DNS.

Un CNAME DNS consente di creare un alias come riferimento al record dell'host (A).
Lo scopo del record del nome aggiuntivo è incrementare la flessibilità, se dovesse essere necessaria una modifica in futuro.
Un CNAME consente di isolare la configurazione del client in modo che le modifiche all'ambiente di server, ad esempio la sostituzione di un server di pull o l'aggiunta di altri server di pull, non richiedano una modifica corrispondente alla configurazione del client.

Quando si sceglie un nome per il record DNS, tenere presente l'architettura della soluzione.
Se si usa il bilanciamento del carico, il certificato usato per proteggere il traffico su HTTPS deve condividere lo stesso nome del record DNS.

Scenario |Procedura consigliata
:---|:---
Ambiente di test |Riprodurre l'ambiente di produzione pianificato, se possibile. Un nome host del server è adatto per configurazioni semplici. Se DNS non è disponibile, può essere usato un indirizzo IP anziché un nome host.|
Distribuzione di un nodo singolo |Creare un record CNAME DNS che punta al nome host del server.|

Per altre informazioni, vedere [Configuring DNS Round Robin in Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)) (Configurazione del round robin DNS in Windows Server).

Pianificazione dell'attività|
---|
Si sa a chi rivolgersi per avere i record DNS creati e modificati?|
Qual è il tempo medio per una richiesta di un record DNS?|
È necessario richiedere record di nome host (A) statici per i server?|
Cosa verrà richiesto come CNAME?|
Se necessario, quale tipo di soluzione di bilanciamento del carico verrà usato? (vedere la sezione Bilanciamento del carico per informazioni dettagliate)|

### <a name="public-key-infrastructure"></a>Infrastruttura a chiave pubblica (PKI)

La maggior parte delle organizzazioni richiedono oggi che il traffico di rete, in particolare il traffico che include dati sensibili, ad esempio la configurazione dei server, debba essere validato e/o crittografato durante il trasferimento.
Sebbene sia possibile distribuire un server di pull tramite HTTP che facilita le richieste client in testo non crittografato, è consigliabile proteggere il traffico tramite HTTPS. Il servizio può essere configurato per l'uso di HTTPS tramite un set di parametri nella risorsa DSC **xPSDesiredStateConfiguration**.

I requisiti del certificato per proteggere il traffico HTTPS per il server di pull non sono diversi da quelli per la protezione di qualsiasi altro sito Web HTTPS. Il modello **Web Server** in Servizi certificati di Windows Server soddisfa le funzionalità necessarie.

Pianificazione dell'attività|
---|
Se le richieste di certificati non sono automatiche, a chi è necessario rivolgersi per richiedere un certificato?|
Qual è il tempo medio di elaborazione della richiesta?|
Come verrà trasferito il file del certificato all'utente?|
Come verrà trasferita la chiave privata del certificato all'utente?|
Qual è il periodo di tempo predefinito prima della scadenza?|
È stato definito un nome DNS per l'ambiente del server del pull, che è possibile usare per il nome certificato?|

### <a name="choosing-an-architecture"></a>Scelta di un'architettura

Un server di pull può essere distribuito tramite un servizio Web ospitato in IIS o tramite una condivisione file SMB. Nella maggior parte dei casi, l'uso del servizio Web offre maggiore flessibilità. Non è insolito che il traffico HTTPS oltrepassi i limiti di rete, mentre il traffico SMB è spesso filtrato o bloccato tra le reti. Il servizio Web offre anche l'opzione di includere un server di conformità o Gestione rapporti Web (entrambi gli argomenti verranno trattati in una versione futura di questo documento) che offrono ai client un meccanismo di restituire lo stato a un server per una visibilità centralizzata.
SMB offre un'opzione per alcuni ambienti in cui i criteri indicano che un server Web non debba essere usato e per altri ambienti che rendono il ruolo del server Web indesiderato.
In entrambi i casi, è necessario valutare i requisiti per la firma e la crittografia del traffico. HTTPS, firma SMB e criteri IPSEC sono tutte opzioni da considerare.

#### <a name="load-balancing"></a>Bilanciamento del carico

I client che interagiscono con il servizio Web eseguono una richiesta di informazioni restituita in una risposta singola. Nessuna richiesta sequenziale è obbligatoria, pertanto non è necessario assicurarsi che per la piattaforma del bilanciamento del carico siano sempre mantenute le sessioni in un server singolo.

Pianificazione dell'attività|
---|
Quale soluzione verrà usata per il traffico del bilanciamento del carico tra server?|
Se si usa un bilanciamento del carico hardware, chi prenderà la richiesta per aggiungere una nuova configurazione al dispositivo?|
Qual è il tempo medio di elaborazione di una richiesta per configurare un nuovo servizio Web con carico bilanciato?|
Quali informazioni sono necessarie per la richiesta?|
Sarà necessario richiedere un indirizzo IP aggiuntivo o il team responsabile del bilanciamento del carico gestirà l'operazione?|
Si hanno i record DNS necessari? Questa disponibilità verrà richiesta dal team responsabile della configurazione della soluzione di bilanciamento del carico?|
La soluzione di bilanciamento del carico richiede che PKI sia gestito dal dispositivo o può bilanciare il carico del traffico HTTPS se non ci sono requisiti di sessione?|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a>Gestione temporanea di configurazioni e moduli nel server di pull

Come parte della pianificazione della configurazione, è necessario determinare quali moduli e configurazioni DSC verranno ospitati dal server di pull. Ai fini della pianificazione della configurazione è importante avere una conoscenza di base su come preparare e distribuire contenuto a un server di pull.

In futuro, questa sezione verrà estesa e inclusa in una guida operativa per il server di pull DSC.  La guida illustrerà il processo quotidiano per la gestione di moduli e configurazioni nel tempo con l'automazione.

#### <a name="dsc-modules"></a>Moduli DSC

I client che richiedono una configurazione avranno bisogno dei moduli DSC richiesti. Una funzionalità del server di pull consiste nell'automatizzare la distribuzione su richiesta dei moduli DSC ai client. Se si distribuisce un server di pull per la prima volta, ad esempio come lab o modello di verifica, probabilmente si dipenderà dai moduli DSC che sono disponibili nei repository pubblici, ad esempio la raccolta di PowerShell o i repository GitHub di PowerShell.org per i moduli DSC.

È fondamentale ricordare che anche per le origini online attendibile, ad esempio PowerShell Gallery, ogni modulo che viene scaricato da un repository pubblico deve essere esaminato da un utente con esperienza in PowerShell e conoscenza dell'ambiente in cui i moduli verranno usati prima di essere usati nell'ambiente di produzione. Durante il completamento di questa attività, è consigliabile verificare la presenza di eventuali payload aggiuntivi nel modulo che possono essere rimossi, ad esempio gli script di esempio e la documentazione. Ciò riduce la larghezza di banda di rete per ogni client durante la prima richiesta, quando i moduli verranno scaricati nella rete dal server al client.

Ogni modulo deve essere compresso in un formato specifico, ovvero un file ZIP denominato nomemodulo_versione.zip, che contenga il payload del modulo. Dopo che il file viene copiato nel server, è necessario creare un file di checksum. Quando i client si connettono al server, viene usato il checksum per verificare che il contenuto del modulo DSC non è stato modificato dopo la pubblicazione.

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

Pianificazione dell'attività|
---|
Se si pianifica un ambiente di test o lab, quali sono gli scenari fondamentali da convalidare?|
Sono disponibili pubblicamente i moduli che contengono le risorse necessarie per coprire tutto ciò che è necessario o si devono creare le proprie risorse?|
L'ambiente avrà accesso a Internet per recuperare i moduli pubblici?|
Chi sarà responsabile della revisione dei moduli DSC?|
Se si pianifica un ambiente di produzione, che cosa verrà usato come repository locale per l'archiviazione dei moduli DSC?|
Un team centrale accetterà moduli DSC provenienti dai team dell'applicazione? Quale sarà il processo?|
Verranno automatizzati l'assemblaggio, la copia e la creazione di un checksum per i moduli DSC pronti alla produzione dal repository di origine al server?|
Il team sarà anche responsabile per la gestione della piattaforma di automazione?|

#### <a name="dsc-configurations"></a>Configurazioni DSC

Lo scopo di un server di pull è fornire un meccanismo centralizzato per la distribuzione delle configurazioni DSC ai nodi client. Le configurazioni sono archiviate nel server come documenti MOF.
Ogni documento verrà denominato con un identificatore univoco globale (**GUID**). Quando i client vengono configurati per la connessione a un server di pull, viene assegnato l'identificatore **GUID** per la configurazione che i client devono richiedere. Questo sistema di riferimento a configurazioni da identificatori **GUID** garantisce l'univocità globale ed è flessibile al punto che può essere applicata una configurazione con granularità per nodo o come configurazione del ruolo che si estende su più server che devono avere configurazioni identiche.

#### <a name="guids"></a>Identificatori univoci globali (GUID)

La pianificazione della configurazione degli identificatori **GUID** richiede ulteriore attenzione nel caso di una distribuzione di server di pull. Non esistono requisiti specifici su come gestire gli identificatori **GUID** e il processo è probabilmente univoco per ogni ambiente. Il processo può variare da semplice a complesso, ad esempio un file CSV archiviato centralmente, una semplice tabella SQL, un database CMDB o una soluzione complessa che richiede l'integrazione con un altro strumento o soluzione software. I processi seguono due approcci generali:

- **Assegnazione di identificatori GUID per server**: questo approccio garantisce che ogni configurazione del server venga controllata individualmente. Ciò offre un livello di precisione per gli aggiornamenti e funziona efficientemente in ambienti con pochi server.
- **Assegnazione di identificatori GUID per ruolo del server**: tutti i server che eseguono la stessa funzione, ad esempio i server Web, usano lo stesso identificatore GUID come riferimento ai dati di configurazione necessari.  Tenere presente che se molti server condividono lo stesso identificatore GUID, tutti i server verranno contemporaneamente aggiornati quando cambia la configurazione.

  L'identificatore GUID è un elemento da considerare come informazione sensibile perché potrebbe essere usato a proprio vantaggio da utenti malintenzionati che vogliono conoscere come sono distribuiti e configurati i server nell'ambiente. Per altre informazioni, vedere [Securely allocating Guids in PowerShell Desired State Configuration Pull Mode](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/) (Allocazione sicura degli identificatori GUID nella modalità pull di configurazione dello stato desiderato tramite Windows PowerShell).

Pianificazione dell'attività|
---|
Chi sarà responsabile per copiare le configurazioni nella cartella del server di pull quando sono pronte?|
Se le configurazioni vengono create da un team di applicazione, quale sarà il processo per consegnarle?|
Verrà usato un repository per archiviare le configurazioni mentre vengono create, tra i team?|
Verrà automatizzato il processo di copia delle configurazione nel server e di creazione di un checksum quando sono pronte?|
Come verrà eseguito il mapping degli identificatori GUID ai server o ai ruoli e dove verrà archiviato?|
Quale processo verrà usato per configurare i computer client e come si integrerà con il processo di creazione e archiviazione degli identificatori GUID di configurazione?|

## <a name="installation-guide"></a>Guida all'installazione

*Gli script illustrati in questo documento sono esempi stabili. Esaminare sempre gli script con attenzione prima di eseguirli in un ambiente di produzione.*

### <a name="prerequisites"></a>Prerequisiti

Per verificare la versione di PowerShell nel server usare il comando seguente.

```powershell
$PSVersionTable.PSVersion
```

Se possibile, eseguire l'aggiornamento alla versione più recente di Windows Management Framework.
Successivamente, scaricare il modulo `xPsDesiredStateConfiguration` con il comando seguente.

```powershell
Install-Module xPSDesiredStateConfiguration
```

Il comando chiederà conferma prima di scaricare il modulo.

### <a name="installation-and-configuration-scripts"></a>Script di installazione e configurazione

Il metodo migliore per distribuire un server di pull DSC è usare uno script di configurazione DSC. Questo documento illustra script che includono impostazioni di base per configurare solo il servizio Web DSC e impostazioni avanzate per configurare completamente Windows Server, incluso il servizio Web DSC.

Nota:  attualmente il modulo DSC `xPSDesiredStateConfiguration` richiede che il server sia configurato su impostazioni locali EN-US.

### <a name="basic-configuration-for-windows-server-2012"></a>Configurazione di base per Windows Server 2012

```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a>Configurazione avanzata per Windows Server 2012 R2

```powershell
# This is an advanced Configuration example for Pull Server production deployments on Windows Server 2012 R2.
# Many of the features demonstrated are optional and provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority, complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider modifying the default port, possibly leveraging port 443 in environments where that is enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }

PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```

### <a name="verify-pull-server-functionality"></a>Verificare la funzionalità del server di pull

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a>Configurare i client

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}

PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```

## <a name="additional-references-snippets-and-examples"></a>Riferimenti aggiuntivi, frammenti di codice ed esempi

Questo esempio illustra come avviare manualmente una connessione client (richiede WMF5) per il test.

```powershell
Update-DscConfiguration –Wait -Verbose
```

Il cmdlet [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) viene usato per aggiungere un tipo di record CNAME a una zona DNS.

La funzione di PowerShell per [creare un checksum e pubblicare MOF DSC al Server di Pull SMB](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) genera automaticamente il checksum necessario e quindi copia la configurazione MOF e i file di checksum nel server di pull SMB.

## <a name="appendix---understanding-odata-service-data-file-types"></a>Appendice - Informazioni sui tipi di file di dati del servizio ODATA

Un file di dati viene archiviato per creare informazioni durante la distribuzione di un server di pull che include il servizio Web OData. Il tipo di file dipende dal sistema operativo, come specificato di seguito.

- **Windows Server 2012** Il tipo di file sarà sempre MDB
- **Windows Server 2012 R2** Il tipo di file predefinito è EDB a meno che non venga specificato un file con estensione MDB nella configurazione

Nello [script di esempio avanzato](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) per installare un server di pull è incluso anche un esempio di come controllare automaticamente le impostazioni del file web.config per evitare qualsiasi possibilità di errore causato dal tipo di file.
