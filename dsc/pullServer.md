# Configurazione di un server di pull Web DSC

> Si applica a: Windows PowerShell 5.0

Un server di pull Web DSC è un servizio Web in IIS che usa un'interfaccia OData per rendere i file di configurazione DSC disponibili ai nodi di destinazione quando questi li richiedono.

Requisiti per l'uso di un server di pull:

* Un server che esegue:
  - WMF/PowerShell 5.0 o versioni successive
  - Ruolo del server IIS
  - Servizio DSC
* Idealmente, uno strumento per la generazione di un certificato, per proteggere le credenziali passate a Gestione configurazione locale nei nodi di destinazione

Per aggiungere il ruolo del server IIS e il servizio DSC, è possibile usare l'Aggiunta guidata ruoli e funzionalità in Server Manager oppure PowerShell. Gli script di esempio inclusi in questo argomento gestiscono entrambi i passaggi automaticamente.

## Uso della risorsa xWebService
Il metodo più semplice per configurare un server di pull Web consiste nell'usare la risorsa xWebService, inclusa nel modulo xPSDesiredStateConfiguration. I passaggi seguenti descrivono come usare la risorsa in una configurazione che imposta il servizio Web.

1. Chiamare il cmdlet [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) per installare il modulo **xPSDesiredStateConfiguration**. **Nota**: il cmdlet **Install-Module** è incluso nel modulo **PowerShellGet**, disponibile in PowerShell 5.0. È possibile scaricare il modulo **PowerShellGet** per PowerShell 3.0 e 4.0 dalla pagina dell'[anteprima dei moduli PackageManagement di PowerShell](https://www.microsoft.com/en-us/download/details.aspx?id=49186).. 
1. Ottenere un certificato SSL per il server di pull DSC da un'Autorità di certificazione disponibile nell'elenco locale, all'interno dell'organizzazione o pubblica. Il certificato ricevuto dall'autorità è in genere in formato PFX. Installare il certificato nel nodo che diventerà il server di pull DSC nel percorso predefinito, ossia CERT: \LocalMachine\My. Prendere nota dell'identificazione personale del certificato.
1. Selezionare un GUID da usare come chiave di registrazione. Per generarne una tramite PowerShell, immettere il comando seguente al prompt di PowerShell e premere INVIO: '``` [guid]::newGuid()```'. Questa chiave verrà usata dai nodi client come chiave condivisa per l'autenticazione durante la registrazione. Per altre informazioni, vedere la sezione [Chiave di registrazione](#RegKey) di seguito.
1. In PowerShell ISE avviare (F5) lo script di configurazione seguente (incluso nella cartella Example del modulo **xPSDesiredStateConfiguration** come Sample_xDscWebService.ps1). Questo script configura il server di pull.
  
```powershell
configuration Sample_xDscPullServer
{ 
    param  
    ( 
            [string[]]$NodeName = 'localhost', 
            
            [ValidateNotNullOrEmpty()] 
            [string] $certificateThumbPrint,
            
            [Parameter(Mandatory)]
            [ValidateNotNullOrEmpty()]
            [string] $RegistrationKey 
     ) 
 
 
     Import-DSCResource -ModuleName xPSDesiredStateConfiguration 

     Node $NodeName 
     { 
         WindowsFeature DSCServiceFeature 
         { 
             Ensure = 'Present'
             Name   = 'DSC-Service'             
         } 
 
         xDscWebService PSDSCPullServer 
         { 
             Ensure                  = 'Present' 
             EndpointName            = 'PSDSCPullServer' 
             Port                    = 8080 
             PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer" 
             CertificateThumbPrint   = $certificateThumbPrint          
             ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules" 
             ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration" 
             State                   = 'Started'
             DependsOn               = '[WindowsFeature]DSCServiceFeature'                         
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
# To find the Thumbprint for an installed SSL certificate for use with the pull server list all certifcates in your local store 
# and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
dir Cert:\LocalMachine\my

# Then include this thumbprint when running the configuration
Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutpuPath c:\Configs\PullServer

# Run the compiled configuration to make the target node a DSC Pull Server
Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
```

## Chiave di registrazione
Per consentire ai nodi client di eseguire la registrazione nel server in modo da poter usare i nomi di configurazione invece di un ID configurazione, una chiave di registrazione creata dalla configurazione precedente viene salvata in un file denominato `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`. La chiave di registrazione funziona come segreto condiviso usato durante la registrazione iniziale dal client con il server di pull. Il client genererà un certificato autofirmato che viene usato per l'autenticazione univoca nel server di pull dopo il corretto completamento della registrazione. L'identificazione personale del certificato viene archiviata in locale e associata all'URL del server di pull.
> **Nota**: le chiavi di registrazione non sono supportate in PowerShell 4.0. 

Per configurare un nodo per l'autenticazione nel server di pull, la chiave di registrazione deve essere inclusa nella metaconfigurazione per qualsiasi nodo di destinazione che si registrerà per questo server di pull. Tenere presente che **RegistrationKey** nella metaconfigurazione seguente viene rimosso dopo la registrazione del computer di destinazione e che il valore '140a952b-b9d6-406b-b416-e0f759c9c0e4' deve corrispondere al valore archiviato nel file RegistrationKeys.txt nel server di pull. Gestire sempre il valore della chiave di registrazione tenendo conto della sicurezza, perché qualsiasi computer di destinazione a conoscenza di questo valore può registrarsi nel server di pull.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded   = $true
        }
        
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey    = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }   
        
        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
        }
    }
}

PullClientConfigID -OutputPath c:\Configs\TargetNodes
```
> **Nota**: la sezione **ReportServerWeb** consente l'invio dei dati di report al server di pull. 

L'assenza della proprietà **ConfigurationID** nel file di metaconfigurazione significa implicitamente che il server di pull supporta la versione V2 del protocollo del server di pull e quindi è richiesta una registrazione iniziale. Al contrario, la presenza di un valore **ConfigurationID** significa che viene usata la versione V1 del protocollo del server di pull e non è prevista l'elaborazione della registrazione.

>**Nota**: in uno scenario PUSH esiste un bug nella versione corrente che rende necessario definire una proprietà ConfigurationID nel file di metaconfigurazione per i nodi mai registrati in un server di pull. Verrà così forzato l'uso del protocollo V1 per il server di pull evitando messaggi di errori correlati alla registrazione.

## Inserimento di configurazioni e risorse
Dopo il completamento della configurazione del server di pull, le cartelle definite dalle proprietà **ConfigurationPath** e **ModulePath** nella configurazione del server di pull si trovano nella posizione in cui verranno posizionati i moduli e le configurazioni disponibili per il pull dai nodi di destinazione. Questi file devono avere un formato specifico per consentire la corretta elaborazione dal server di pull. 

### Formato del pacchetto dei moduli di risorse DSC
Ogni modulo di risorse deve essere compresso e denominato in base a questa convenzione **{Nome modulo}_{Versione modulo}.zip**. Ad esempio, un modulo denominato xWebAdminstration con versione 3.1.2.0 verrebbe denominato 'xWebAdministration_3.2.1.0.zip'. Ogni versione di un modulo deve essere contenuta in un unico file ZIP. Dato che esiste solo un'unica versione di una risorsa in ogni file ZIP, non è supportato il formato di modulo aggiunto in WMF 5.0 che supporta più versioni del modulo in una singola directory. Ciò significa che prima di creare un pacchetto per i moduli di risorse DSC da usare con il server di pull è necessario apportare una piccola modifica alla struttura di directory. Il formato predefinito dei moduli contenenti risorse DSC WMF 5.0 è '{Cartella modulo}\{Versione modulo}\DscResources\{Cartella risorsa DSC}\'. Prima di creare il pacchetto per il server di pull, rimuovere semplicemente la cartella **{Versione modulo}** in modo che il percorso diventi '{Cartella modulo}\DscResources\{Cartella risorsa DSC}\'. Con questa modifica, comprimere la cartella come descritto in precedenza e posizionare i file ZIP nella cartella **ModulePath**.

### Formato del file MOF di configurazione 
Un file MOF di configurazione deve essere associato a un file di checksum in modo che Gestione configurazione locale in un nodo di destinazione possa convalidare la configurazione. Per creare un checksum, chiamare il cmdlet [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx). Il cmdlet accetta un parametro **Path** che specifica la cartella in cui si trova il file MOF di configurazione. Il cmdlet crea un file di checksum denominato `ConfigurationMOFName.mof.checksum`, in cui `ConfigurationMOFName` è il nome del file MOF di configurazione. Se nella cartella specificata sono presenti più file MOF di configurazione, viene creato un checksum per ogni configurazione nella cartella. Posizionare i file MOF e i file di checksum associati nella cartella **ConfigurationPath**.

>**Nota**: se si modifica il file MOF di configurazione in qualsiasi modo, è necessario ricreare anche il file di checksum.

## Strumenti
Per facilitare la configurazione, la convalida e la gestione del server di pull, gli strumenti seguenti sono inclusi come esempi nella versione più recente del modulo xPSDesiredStateConfiguration:
1. Un modulo che facilita la creazione di pacchetti per i moduli di risorse DSC e i file di configurazione per l'uso nel server di pull. [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1). Ecco alcuni esempi:

```powershell
    # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
     $moduleList = @("xWebAdministration", "xPhp") 
     Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 
     
     # Example 2 - Package modules and mof documents from c:\LocalDepot
     Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
```

1. Uno script che convalida la corretta configurazione del server di pull. [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/Examples/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).


## Configurazione dei client di pull 
Gli argomenti seguenti descrivono in modo dettagliato la configurazione dei client di pull:

* [Configurazione di un client di pull DSC usando un ID configurazione](pullClientConfigID.md)
* [Configurazione di un client di pull DSC usando nomi di configurazione](pullClientConfigNames.md)
* [Configurazioni parziali](partialConfigs.md)


## Vedere anche
* [Panoramica di Windows PowerShell DSC (Desired State Configuration)](overview.md)
* [Applicazione delle configurazioni](enactingConfigurations.md)
* [Uso di un server di report DSC](reportServer.md)


<!--HONumber=May16_HO1-->


