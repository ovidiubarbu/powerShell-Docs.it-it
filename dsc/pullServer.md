# Configurazione di un server di pull Web DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Un server di pull Web DSC è un servizio Web in IIS che usa un'interfaccia OData per rendere i file di configurazione DSC disponibili ai nodi di destinazione quando questi li richiedono.

Requisiti per l'uso di un server di pull:

* Un server che esegue:
  - WMF/PowerShell 4.0 o versioni successive
  - Ruolo del server IIS
  - Servizio DSC
* Idealmente, uno strumento per la generazione di un certificato, per proteggere le credenziali passate a Gestione configurazione locale nei nodi di destinazione

Per aggiungere il ruolo del server IIS e il servizio DSC, è possibile usare l'Aggiunta guidata ruoli e funzionalità in Server Manager oppure PowerShell. Gli script di esempio inclusi in questo argomento gestiscono entrambi i passaggi automaticamente.

## Uso della risorsa xWebService
Il metodo più semplice per configurare un server di pull Web consiste nell'usare la risorsa xWebService, inclusa nel modulo xPSDesiredStateConfiguration. I passaggi seguenti descrivono come usare la risorsa in una configurazione che imposta il servizio Web.

1. Chiamare il cmdlet [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) per installare il modulo **xPSDesiredStateConfiguration**. **Nota**: il cmdlet **Install-Module** è incluso nel modulo **PowerShellGet**, disponibile in PowerShell 5.0. È possibile scaricare il modulo **PowerShellGet** per PowerShell 3.0 e 4.0 dalla pagina dell'[anteprima dei moduli PackageManagement di PowerShell](https://www.microsoft.com/en-us/download/details.aspx?id=49186). 
1. Creare un certificato autofirmato con l'oggetto `"CN=PSDSCPullServerCert"` nell'archivio `CERT:\LocalMachine\MY\`. A questo scopo, eseguire il comando `New-SelfSignedCertificate  -CertStoreLocation 'CERT:\LocalMachine\MY' -DnsName "PSDSCPullServerCert"`.
1. In PowerShell ISE avviare (F5) lo script di configurazione seguente (incluso nella cartella Example del modulo **xPSDesiredStateConfiguration** come Sample_xDscWebService.ps1). Questo script configura il server di pull e un server di conformità.
  
```powershell
configuration Sample_xDscWebService 
6 { 
7     param  
8     ( 
9         [string[]]$NodeName = 'localhost', 
10 
 
11         [ValidateNotNullOrEmpty()] 
12         [string] $certificateThumbPrint 
13     ) 
14 
 
15     Import-DSCResource -ModuleName xPSDesiredStateConfiguration 
16 
 
17     Node $NodeName 
18     { 
19         WindowsFeature DSCServiceFeature 
20         { 
21             Ensure = "Present" 
22             Name   = "DSC-Service"             
23         } 
24 
 
25         xDscWebService PSDSCPullServer 
26         { 
27             Ensure                  = "Present" 
28             EndpointName            = "PSDSCPullServer" 
29             Port                    = 8080 
30             PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer" 
31             CertificateThumbPrint   = $certificateThumbPrint          
32             ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules" 
33             ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"             
34             State                   = "Started" 
35             DependsOn               = "[WindowsFeature]DSCServiceFeature"                         
36         } 
```

1. Eseguire la configurazione, passando l'identificazione personale del certificato autofirmato creato come parametro **certificateThumbPrint**:

```powershell
PS:\>$myCert = Get-ChildItem CERT:\LocalMachine\My | Where-Object {$_.Subject -eq 'CN=PSDSCPullServerCert'}
PS:\>Sample_xDSCService -certificateThumbprint $myCert.Thumbprint 
```

## Chiave di registrazione
Per consentire ai nodi client di eseguire la registrazione con il server in modo da poter usare i nomi di configurazione invece di un ID configurazione, è necessario inserire una chiave di registrazione (ovvero un GUID noto sia al nodo server sia al nodo client) in un file denominato `RegistrationKeys.txt`. Per impostazione predefinita, il server di pull creato da questo esempio presuppone che il file si trovi in `C:\Program Files\WindowsPowerShell\DscService`. Creare un file di testo con una sola riga costituita dalla chiave di registrazione e salvarlo in questa cartella.
> **Nota**: le chiavi di registrazione non sono supportate in PowerShell 4.0. 

## Inserimento di configurazioni e risorse
Al termine della configurazione del server di pull, in `$env:PROGRAMFILES\WindowsPowerShell` sarà presente una nuova cartella denominata "DscService". Questa cartella contiene due cartelle, denominate "Modules" e "Configuration". Nella cartella "Modules" inserire tutte le risorse necessarie per le configurazioni di cui i nodi effettueranno il pull dal server. Nella cartella "Configuration" inserire i file MOF di configurazione per tutte le configurazioni di cui i nodi devono effettuare il pull. I nomi dei file MOF dipendono dal tipo di client di pull. Gli argomenti seguenti descrivono in modo dettagliato la configurazione dei client di pull:

* [Configurazione di un client di pull DSC usando un ID configurazione](pullClientConfigID.md)
* [Configurazione di un client di pull DSC usando nomi di configurazione](pullClientConfigNames.md)
* [Configurazioni parziali](partialConfigs.md)

## Creazione del checksum per il file MOF
Un file MOF di configurazione deve essere associato a un file di checksum in modo che Gestione configurazione locale in un nodo di destinazione possa convalidare la configurazione. Per creare un checksum, chiamare il cmdlet [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx). Il cmdlet accetta un parametro **Path** che specifica la cartella in cui si trova il file MOF di configurazione. Il cmdlet crea un file di checksum denominato `ConfigurationMOFName.mof.checksum`, in cui `ConfigurationMOFName` è il nome del file MOF di configurazione. Se nella cartella specificata sono presenti più file MOF di configurazione, viene creato un checksum per ogni configurazione nella cartella.

Il file di checksum deve essere presente nella stessa directory del file MOF di configurazione (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` per impostazione predefinita) e avere lo stesso nome, con estensione `.checksum`.

>**Nota**: se si modifica il file MOF di configurazione in qualsiasi modo, è necessario ricreare anche il file di checksum.

## Vedere anche
* [Panoramica di Windows PowerShell DSC (Desired State Configuration)](overview.md)
* [Applicazione delle configurazioni](enactingConfigurations.md)
* [Come recuperare le informazioni sui nodi dal server di pull DSC](retrieveNodeInfo.md)


<!--HONumber=Mar16_HO1-->


