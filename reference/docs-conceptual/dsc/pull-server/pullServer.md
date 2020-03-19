---
ms.date: 01/08/2020
keywords: dsc,powershell,configurazione,installazione
title: Servizio di pull DSC
ms.openlocfilehash: cf2420e6889f63ac3b2859e5ee36fa888b728afc
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402438"
---
# <a name="desired-state-configuration-pull-service"></a>Servizio di pull DSC (Desired State Configuration)

> [!IMPORTANT]
> Il server di pull (funzionalità di Windows *servizio DSC*) è un componente supportato di Windows Server, tuttavia non si prevede di offrire nuove caratteristiche o funzionalità. È consigliabile avviare la transizione dei client gestiti ad [Automation DSC per Azure](/azure/automation/automation-dsc-getting-started) (include funzionalità superiori al server di pull in Windows Server) o a una delle soluzioni della community riportate [qui](pullserver.md#community-solutions-for-pull-service).

Gestione configurazione locale può essere gestito a livello centralizzato da una soluzione servizio di pull. Con questo approccio, il nodo gestito viene registrato con un servizio e gli viene assegnata una configurazione nelle impostazioni di Gestione configurazione locale. La configurazione e tutte le risorse DSC necessarie come dipendenze per la configurazione vengono scaricate nel computer e usate da Gestione configurazione locale per gestire la configurazione. Nel servizio vengono caricate informazioni sullo stato del computer gestito per la creazione di report. Questo concetto è noto come "servizio di pull".

Le opzioni correnti per il servizio di pull includono:

- Servizio DSC (Desired State Configuration) di Automazione di Azure
- Un servizio di pull in esecuzione in Windows Server
- Soluzioni open source gestite dalla community
- Una condivisione SMB

La scalabilità consigliata per ogni soluzione è la seguente:

|                   Soluzione                   |              Nodi client              |
| -------------------------------------------- | -------------------------------------- |
| Server di pull Windows con database MDB/ESENT | Fino a 500 nodi                        |
| Server di pull Windows con database SQL       | Fino a 3500 nodi                       |
| Automation DSC per Azure                         | Ambienti di piccole e grandi dimensioni      |

**La soluzione consigliata**, e l'opzione con il maggior numero di funzionalità disponibili, è [Automation DSC di Azure](/azure/automation/automation-dsc-getting-started). Non è stato identificato un limite massimo del numero di nodi per l'account di Automazione.

Il servizio di Azure può gestire i nodi in locale nei data center privati o in cloud pubblici, come Azure e AWS. Per gli ambienti privati in cui i server non possono connettersi direttamente a Internet, è consigliabile limitare il traffico in uscita esclusivamente all'intervallo di indirizzi IP di Azure pubblicato (vedere gli [intervalli di indirizzi IP dei data center di Azure](https://www.microsoft.com/download/details.aspx?id=41653)).

Le funzionalità del servizio online che non sono attualmente disponibili nel servizio di pull in Windows Server includono:

- Tutti i dati vengono crittografati in transito e quando inattivi
- I certificati client vengono creati e gestiti automaticamente
- Archivio dei segreti per la gestione centralizzata di [password/credenziali](/azure/automation/automation-credentials) o [variabili](/azure/automation/automation-variables) come nomi dei server o stringhe di connessione
- Gestione centralizzata della [configurazione di Gestione configurazione locale](../managing-nodes/metaConfig.md#basic-settings) del nodo
- Assegnazione centralizzata delle configurazioni ai nodi client
- Rilascio delle modifiche di configurazione a "gruppi canary" per i test prima della distribuzione in ambiente di produzione
- Creazione di report grafici
  - Dettagli sullo stato al livello di granularità delle risorse DSC
  - Messaggi di errore dettagliati dai computer client per la risoluzione dei problemi
- [Integrazione con Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) per gli avvisi, attività automatizzate, app Android o iOS per report e avvisi

## <a name="dsc-pull-service-in-windows-server"></a>Servizio di pull DSC in Windows Server 2016

È possibile configurare un servizio di pull per l'esecuzione in Windows Server. Si noti che la soluzione di servizio di pull inclusa in Windows Server contiene solo le funzionalità di archiviazione di configurazioni/moduli per il download e di acquisizione di dati di report in un database. Non include molte delle funzionalità offerte dal servizio in Azure e pertanto non rappresenta uno strumento ottimale per la valutazione delle modalità d'uso del servizio.

Il servizio di pull offerto in Windows Server è un servizio Web in IIS che usa un'interfaccia OData per rendere i file di configurazione DSC disponibili ai nodi di destinazione quando questi li richiedono.

Requisiti per l'uso di un server di pull:

- Un server che esegue:
  - WMF/PowerShell 4.0 o versioni successive
  - Ruolo del server IIS
  - Servizio DSC
- Idealmente, uno strumento per la generazione di un certificato, per proteggere le credenziali passate a Gestione configurazione locale nei nodi di destinazione

Il modo migliore per configurare Windows Server per ospitare un servizio di pull consiste nell'usare una configurazione DSC. Di seguito è disponibile un esempio di script.

### <a name="supported-database-systems"></a>Sistemi di database supportati

| WMF 4.0 |       WMF 5.0        |       WMF 5.1        | WMF 5.1 (Windows Server Insider Preview 17090) |
| ------- | -------------------- | -------------------- | ---------------------------------------------- |
| MDB     | ESENT (predefinito), MDB | ESENT (predefinito), MDB | ESENT (predefinito), SQL Server, MDB               |

A partire dalla versione 17090 di [Windows Server Insider Preview](https://www.microsoft.com/software-download/windowsinsiderpreviewserver), SQL Server è un'opzione supportata per il servizio di pull (funzionalità di Windows *servizio DSC*). In questo modo si rende disponibile una nuova opzione per il ridimensionamento di ambienti DSC di grandi dimensioni che non sono stati migrati ad [Automation DSC per Azure](/azure/automation/automation-dsc-getting-started).

> [!NOTE]
> il supporto per SQL Server non verrà aggiunto alle versioni precedenti di WMF 5.1 (o versioni precedenti) e sarà disponibile solo nelle versioni di Windows Server maggiori o uguali alla 17090.

Per configurare il server di pull per l'uso di SQL Server, impostare **SqlProvider** su `$true` e **SqlConnectionString** su una stringa di connessione di SQL Server valida. Per altre informazioni, vedere [Stringhe di connessione SqlClient](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).
Per un esempio di configurazione di SQL Server con **xDscWebService**, leggere prima [Uso della risorsa xDscWebService](#using-the-xdscwebservice-resource) e quindi vedere [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 in GitHub](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).

### <a name="using-the-xdscwebservice-resource"></a>Uso della risorsa xDscWebService

Il metodo più semplice per configurare un server di pull Web consiste nell'usare la risorsa **xDscWebService**, inclusa nel modulo **xPSDesiredStateConfiguration**. La procedura seguente descrive come usare la risorsa in un oggetto `Configuration` che imposta il servizio Web.

1. Chiamare il cmdlet [Install-Module](/reference/6/PowerShellGet/Install-Module.md) per installare il modulo **xPSDesiredStateConfiguration**.

   > [!NOTE]
   > Il cmdlet `Install-Module` è incluso nel modulo **PowerShellGet**, disponibile in PowerShell 5.0 o versioni successive.

1. Ottenere un certificato SSL per il server di pull DSC da un'Autorità di certificazione attendibile, all'interno dell'organizzazione o pubblica. Il certificato ricevuto dall'autorità è in genere in formato PFX.
1. Installare il certificato nel nodo che diventerà il server di pull DSC nel percorso predefinito, ossia `CERT:\LocalMachine\My`.
   - Prendere nota dell'identificazione personale del certificato.
1. Selezionare un GUID da usare come chiave di registrazione. Per generarne uno tramite PowerShell, immettere quanto segue al prompt di PowerShell e premere INVIO: `[guid]::newGuid()` oppure `New-Guid`. Questa chiave verrà usata dai nodi client come chiave condivisa per l'autenticazione durante la registrazione. Per altre informazioni, vedere la sezione Chiave di registrazione di seguito.
1. In PowerShell ISE avviare (<kbd>F5</kbd>) lo script di configurazione seguente, incluso nella cartella del modulo **xPSDesiredStateConfiguration** come `Sample_xDscWebServiceRegistration.ps1`. Questo script configura il server di pull.

    ```powershell
    configuration Sample_xDscWebServiceRegistration
    {
        param
        (
            [string[]]$NodeName = 'localhost',

            [ValidateNotNullOrEmpty()]
            [string] $certificateThumbPrint,

            [Parameter(HelpMessage='This should be a string with enough entropy (randomness) to protect the registration of clients to the pull server.  We will use new GUID by default.')]
            [ValidateNotNullOrEmpty()]
            [string] $RegistrationKey   # A guid that clients use to initiate conversation with pull server
        )

        Import-DSCResource -ModuleName PSDesiredStateConfiguration
        Import-DSCResource -ModuleName xPSDesiredStateConfiguration

        Node $NodeName
        {
            WindowsFeature DSCServiceFeature
            {
                Ensure = "Present"
                Name   = "DSC-Service"
            }

            xDscWebService PSDSCPullServer
            {
                Ensure                  = "Present"
                EndpointName            = "PSDSCPullServer"
                Port                    = 8080
                PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer"
                CertificateThumbPrint   = $certificateThumbPrint
                ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                State                   = "Started"
                DependsOn               = "[WindowsFeature]DSCServiceFeature"
                RegistrationKeyPath     = "$env:PROGRAMFILES\WindowsPowerShell\DscService"
                AcceptSelfSignedCertificates = $true
                UseSecurityBestPractices     = $true
                Enable32BitAppOnWin64   = $false
            }

            File RegistrationKeyFile
            {
                Ensure          = 'Present'
                Type            = 'File'
                DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
                Contents        = $RegistrationKey
            }
        }
    }
    ```

1. Eseguire la configurazione, passando l'identificazione personale del certificato SSL come parametro **certificateThumbPrint** e una chiave di registrazione GUID come parametro **RegistrationKey**:

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a>Chiave di registrazione

Per consentire ai nodi client di eseguire la registrazione nel server in modo da poter usare i nomi di configurazione invece di un ID configurazione, una chiave di registrazione creata dalla configurazione precedente viene salvata in un file denominato `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`. La chiave di registrazione funziona come segreto condiviso usato durante la registrazione iniziale dal client con il server di pull. Il client genererà un certificato autofirmato che viene usato per l'autenticazione univoca nel server di pull dopo il corretto completamento della registrazione. L'identificazione personale del certificato viene archiviata in locale e associata all'URL del server di pull.

> [!NOTE]
> Le chiavi di registrazione non sono supportate in PowerShell 4.0.

Per configurare un nodo per l'autenticazione nel server di pull, la chiave di registrazione deve essere inclusa nella metaconfigurazione per qualsiasi nodo di destinazione che si registrerà per questo server di pull. Tenere presente che **RegistrationKey** nella metaconfigurazione seguente viene rimosso dopo la registrazione del computer di destinazione e che il valore deve corrispondere al valore archiviato nel file `RegistrationKeys.txt` nel server di pull (in questo esempio, '140a952b-b9d6-406b-b416-e0f759c9c0e4'). Gestire sempre il valore della chiave di registrazione tenendo conto della sicurezza, perché qualsiasi computer di destinazione a conoscenza di questo valore può registrarsi nel server di pull.

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to set up pull server in previous configuration

        [ValidateNotNullOrEmpty()]
        [string] $ServerName = 'localhost' #node name of the pull server, same as $NodeName used in previous configuration
    )

    Node $NodeName
    {
        Settings
        {
            RefreshMode        = 'Pull'
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey    = $RegistrationKey
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey = $RegistrationKey
        }
    }
}

Sample_MetaConfigurationToRegisterWithLessSecurePullServer -RegistrationKey $RegistrationKey -OutputPath c:\Configs\TargetNodes
```

> [!NOTE]
> La sezione **ReportServerWeb** consente l'invio dei dati per la creazione di report al server di pull.

L'assenza della proprietà **ConfigurationID** nel file di metaconfigurazione significa implicitamente che il server di pull supporta la versione V2 del protocollo del server di pull e quindi è richiesta una registrazione iniziale. Al contrario, la presenza di un valore **ConfigurationID** significa che viene usata la versione V1 del protocollo del server di pull e non è prevista l'elaborazione della registrazione.

> [!NOTE]
> in uno scenario PUSH esiste un bug nella versione corrente che rende necessario definire una proprietà ConfigurationID nel file di metaconfigurazione per i nodi mai registrati in un server di pull. Verrà così forzato l'uso del protocollo V1 per il server di pull evitando messaggi di errori correlati alla registrazione.

## <a name="placing-configurations-and-resources"></a>Inserimento di configurazioni e risorse

Dopo il completamento della configurazione del server di pull, le cartelle definite dalle proprietà **ConfigurationPath** e **ModulePath** nella configurazione del server di pull si trovano nella posizione in cui verranno posizionati i moduli e le configurazioni disponibili per il pull dai nodi di destinazione. Questi file devono avere un formato specifico per consentire la corretta elaborazione dal server di pull.

### <a name="dsc-resource-module-package-format"></a>Formato del pacchetto dei moduli di risorse DSC

Ogni modulo di risorse deve essere compresso e denominato in base alla convenzione seguente `{Module Name}_{Module Version}.zip`.

Ad esempio, un modulo denominato **xWebAdminstration** con versione 3.1.2.0 viene denominato `xWebAdministration_3.1.2.0.zip`. Ogni versione di un modulo deve essere contenuta in un unico file ZIP.
Dato che esiste solo un'unica versione di una risorsa in ogni file ZIP, non è supportato il formato di modulo aggiunto in WMF 5.0 che supporta più versioni del modulo in una singola directory. Ciò significa che prima di creare un pacchetto per i moduli di risorse DSC da usare con il server di pull è necessario apportare una piccola modifica alla struttura di directory. Il formato predefinito dei moduli contenenti risorse DSC in WMF 5.0 è `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`. Prima di creare il pacchetto per il server di pull, rimuovere la cartella **{Versione modulo}** , in modo che il percorso diventi `{Module Folder}\DscResources\{DSC Resource Folder}\`. Con questa modifica, comprimere la cartella come descritto in precedenza e posizionare i file ZIP nella cartella **ModulePath**.

Usare `New-DscChecksum {module zip file}` per creare un file di checksum per il modulo appena aggiunto.

### <a name="configuration-mof-format"></a>Formato del file MOF di configurazione

Un file MOF di configurazione deve essere associato a un file di checksum in modo che Gestione configurazione locale in un nodo di destinazione possa convalidare la configurazione. Per creare un checksum, chiamare il cmdlet [New-DscChecksum](/reference/6/PSDesiredStateConfiguration/New-DSCCheckSum.md). Il cmdlet accetta un parametro **Path** che specifica la cartella in cui si trova il file MOF di configurazione. Il cmdlet crea un file di checksum denominato `ConfigurationMOFName.mof.checksum`, in cui `ConfigurationMOFName` è il nome del file MOF di configurazione. Se nella cartella specificata sono presenti più file MOF di configurazione, viene creato un checksum per ogni configurazione nella cartella. Posizionare i file MOF e i file di checksum associati nella cartella **ConfigurationPath**.

> [!NOTE]
> Se si modifica il file MOF di configurazione in qualsiasi modo, è anche necessario ricreare il file di checksum.

### <a name="tooling"></a>Strumenti

Per facilitare la configurazione, la convalida e la gestione del server di pull, gli strumenti seguenti sono inclusi come esempi nella versione più recente del modulo xPSDesiredStateConfiguration:

1. Un modulo che facilita la creazione di pacchetti per i moduli di risorse DSC e i file di configurazione per l'uso nel server di pull.
   [PublishModulesAndMofsToPullServer.psm1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetup.psm1).
   Ecco alcuni esempi:

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. Uno script che convalida la corretta configurazione del server di pull. [PullServerSetupTests.ps1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetupTest/DscPullServerSetupTest.ps1).

## <a name="community-solutions-for-pull-service"></a>Soluzioni della community per il servizio di pull

La community di DSC ha creato più soluzioni per implementare il protocollo del servizio di pull. Per gli ambienti locali, queste soluzioni offrono funzionalità del servizio di pull e la possibilità di offrire il proprio contributo alla community con miglioramenti incrementali.

- [Tug](https://github.com/powershellorg/tug)
- [DSC-TRÆK](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a>Configurazione dei client di pull

Gli argomenti seguenti descrivono in modo dettagliato la configurazione dei client di pull:

- [Configurare un client di pull DSC usando un ID configurazione](pullClientConfigID.md)
- [Configurare un client di pull DSC usando nomi di configurazione](pullClientConfigNames.md)
- [Configurazioni parziali](partialConfigs.md)

## <a name="see-also"></a>Vedere anche

- [Panoramica di PowerShell DSC](../overview/overview.md)
- [Applicazione delle configurazioni](enactingConfigurations.md)
- [Uso di un server di report DSC](reportServer.md)
- [[MS-DSCPM]: Protocollo del modello pull per la configurazione dello stato desiderato](https://docs.microsoft.com/openspecs/windows_protocols/ms-dscpm/ea744c01-51a2-4000-9ef2-312711dcc8c9)
- [[MS-DSCPM]: Protocollo del modello pull per la configurazione dello stato desiderato - Errori](https://docs.microsoft.com/openspecs/windows_protocols/ms-winerrata/f5fc7ae3-9172-41e8-ac6a-2a5a5b7bfaf5)
