---
title: Risoluzione dei problemi relativi a DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 99c1ea706ca5c3fb008065e98cc99fef463b1011
ms.openlocfilehash: caf661fe58faf8cf24c789b408505051429df3f4

---

# <a name="troubleshooting-dsc"></a>Risoluzione dei problemi relativi a DSC

>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Questo argomento illustra come risolvere eventuali problemi di DSC.

## <a name="using-getdscconfigurationstatus"></a>Uso di Get-DscConfigurationStatus

Il cmdlet [Get-DscConfigurationStatus](https://technet.microsoft.com/en-us/library/mt517868.aspx) ottiene informazioni di alto livello sullo stato di configurazione da un nodo di destinazione. Viene restituito un oggetto completo che include informazioni dettagliate sull'esito positivo o negativo dell'esecuzione della configurazione. È possibile esaminare l'oggetto per scoprire i dettagli sull'esecuzione della configurazione, ad esempio:

* Tutte le risorse con errori
* Qualsiasi risorsa che ha richiesto un riavvio
* Impostazioni di metaconfigurazione al momento dell'esecuzione della configurazione
* Altro.

Il set di parametri seguente restituisce informazioni sullo stato per l'ultima esecuzione della configurazione:

```powershell
Get-DscConfigurationStatus  [-CimSession <CimSession[]>] 
                            [-ThrottleLimit <int>] 
                            [-AsJob] 
                            [<CommonParameters>]
```
Il set di parametri seguente restituisce informazioni sullo stato per tutte le esecuzioni della configurazione precedenti:

```powershell
Get-DscConfigurationStatus  -All 
                            [-CimSession <CimSession[]>] 
                            [-ThrottleLimit <int>] 
                            [-AsJob] 
                            [<CommonParameters>]
```

## <a name="example"></a>Esempio

```powershell
PS C:\> $Status = Get-DscConfigurationStatus 

PS C:\> $Status

Status      StartDate               Type            Mode    RebootRequested     NumberOfResources
------      ---------               ----            ----    ---------------     -----------------
Failure     11/24/2015  3:44:56     Consistency     Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName       :   MyService
DependsOn               :   
ModuleName              :   PSDesiredStateConfiguration
ModuleVersion           :   1.1
PsDscRunAsCredential    :   
ResourceID              :   [File]ServiceDll
SourceInfo              :   c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds       :   0.19
Error                   :   SourcePath must be accessible for current configuration. The related file/directory is:
                            \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState              :   
InDesiredState          :   False
InitialState            :   
InstanceName            :   ServiceDll
RebootRequested         :   False
ReosurceName            :   File
StartDate               :   11/24/2015  3:44:56
PSComputerName          :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a>Lo script non viene eseguito: Uso di registri DSC per diagnosticare gli errori di script

Come tutti i software Windows, DSC registra errori ed eventi in [registri](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) che possono essere visualizzati dal [Visualizzatore eventi](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer). Esaminando questi registri è possibile comprendere perché un'operazione specifica non è riuscita e come evitare l'errore in futuro. La scrittura di script di configurazione può essere complessa, quindi per rendere più semplice il rilevamento degli errori durante la scrittura è possibile usare la risorsa Log DSC per tenere traccia dello stato della configurazione nel registro eventi DSC Analytic.

## <a name="where-are-dsc-event-logs"></a>Dove sono i registri eventi DSC?

Nel Visualizzatore eventi gli eventi DSC si trovano in: **Registri applicazioni e servizi/Microsoft/Windows/Desired State Configuration**

Per visualizzare i registri eventi è anche possibile eseguire il cmdlet di PowerShell corrispondente, [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx):

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message                                                                                                  
-----------                     -- ---------------- -------                                                                                                  
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
```

Come illustrato in precedenza, il nome del registro principale di DSC è **Microsoft->Windows->DSC** (gli altri nomi di registro in Windows non sono riportati per brevità). Il nome principale viene aggiunto al nome del canale per creare il nome completo del registro. Il motore DSC scrive principalmente in tre tipi di registri: [registri di debug, operativo e analitico](https://technet.microsoft.com/library/cc722404.aspx). Poiché i registri di debug e analitico sono disattivati per impostazione predefinita, è necessario abilitarli nel Visualizzatore eventi. A tale scopo, aprire il Visualizzatore eventi digitando Show-EventLog in Windows PowerShell oppure fare clic sul pulsante **Start**, scegliere **Pannello di controllo**, fare clic su **Strumenti di amministrazione** e quindi su **Visualizzatore eventi**. Scegliere **Visualizza registri analitici e di debug** dal menu **Visualizza** del Visualizzatore eventi. Il nome del registro per il canale analitico è **Microsoft-Windows-Dsc/Analytic** e per il canale di debug è **Microsoft-Windows-Dsc/Debug**. È anche possibile usare l'utilità [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) per abilitare i registri, come illustrato nell'esempio seguente.

```powershell
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a>Cosa contengono i registri DSC?

I registri DSC sono suddivisi in tre canali in base all'importanza del messaggio. Il registro operativo in DSC contiene tutti i messaggi di errore e può essere usato per identificare un problema. Il registro analitico include un volume maggiore di eventi e consente di identificare la posizione in cui si sono verificati gli errori. Questo canale contiene anche i messaggi dettagliati, se disponibili. Il registro di debug contiene registri che aiutano a capire come si sono verificati gli errori. I messaggi di evento DSC sono strutturati in modo che ogni messaggio inizi con un ID processo che rappresenta in modo univoco un'operazione DSC. Nell'esempio seguente si tenta di ottenere il messaggio dal primo evento registrato nel registro operativo DSC.

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
Consistency engine was run successfully. 
```

Gli eventi DSC vengono registrati in una struttura specifica che consente all'utente di aggregare gli eventi relativi a un processo DSC. La struttura è la seguente:

**ID processo: <Guid>**
**<Event Message>**

## <a name="gathering-events-from-a-single-dsc-operation"></a>Raccolta di eventi da una singola operazione DSC

I registri eventi DSC contengono eventi generati da diverse operazioni DSC. In genere, tuttavia, all'utente interessano i dettagli solo di un'operazione specifica. Tutti i registri DSC possono essere raggruppati in base alla proprietà ID processo, che è univoca per ogni operazione DSC. L'ID processo viene visualizzato come primo valore della proprietà in tutti gli eventi DSC. I passaggi seguenti illustrano come riunire tutti gli eventi in una struttura di matrice raggruppata.

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>
 
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
wevtutil.exe set-log “Microsoft-Windows-Dsc/Debug” /q:True /e:true
 
<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>
 
Get-DscLocalConfigurationManager
 
<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>
 
$DscEvents=[System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Debug" -Oldest)
 
 
<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations = $DscEvents | Group {$_.Properties[0].value}  
```

In questo caso la variabile `$SeparateDscOperations` contiene i registri raggruppati in base a ID processo. Ogni elemento della matrice di questa variabile rappresenta un gruppo di eventi registrati da un'operazione DSC diversa e consente l'accesso ad altre informazioni sui registri.

```
PS C:\> $SeparateDscOperations
 
Count Name                      Group                                                                     
----- ----                      -----                                                                     
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
PS C:\> $SeparateDscOperations[0].Group
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message                                               
-----------                     -- ---------------- -------                                               
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...       
```

È possibile estrarre i dati nella variabile `$SeparateDscOperations` usando [Where-Object](https://technet.microsoft.com/library/ee177028.aspx). Di seguito sono illustrati cinque scenari in cui è possibile estrarre i dati per la risoluzione dei problemi relativi a DSC:

### <a name="1-operations-failures"></a>1: Errori relativi alle operazioni

Tutti gli eventi hanno [livelli di gravità](https://msdn.microsoft.com/library/dd996917(v=vs.85)). Queste informazioni possono essere usate per identificare gli eventi di errore:

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a>2: Dettagli delle operazioni eseguite nell'ultima mezz'ora

`TimeCreated`, una proprietà di ogni evento di Windows, indica l'ora di creazione dell'evento. Il confronto tra questa proprietà e un oggetto di data/ora specifico consente di filtrare tutti gli eventi:

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}   
```

### <a name="3-messages-from-the-latest-operation"></a>3: Messaggi dell'operazione più recente

L'operazione più recente viene archiviata nel primo indice del gruppo di matrici `$SeparateDscOperations`. Eseguendo una query relativa ai messaggi del gruppo con indice 0, vengono restituiti tutti i messaggi per l'operazione più recente:

```powershelll
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} : 
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Displaying messages from built-in DSC resources:
 WMI channel 1 
 ResourceID:  
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Displaying messages from built-in DSC resources:
 WMI channel 1 
 ResourceID:  
 Message : [INCH-VM]:                            [] Consistency check completed. 
```

### <a name="4-error-messages-logged-for-recent-failed-operations"></a>4: Messaggi di errore registrati per operazioni recenti non riuscite

`$SeparateDscOperations[0].Group` contiene un set di eventi per l'operazione più recente. Eseguire il cmdlet `Where-Object` per filtrare gli eventi in base al nome visualizzato del livello. I risultati vengono archiviati nella variabile `$myFailedEvent`, che può essere analizzata più in dettaglio per ottenere il messaggio di evento:

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})
 
PS C:\> $myFailedEvent.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} : 
DSC Engine Error : 
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first. 
Error Code : 1 
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a>5: Tutti gli eventi generati per un ID processo specifico.

`$SeparateDscOperations` è una matrice di gruppi, ognuno dei quali ha un nome che rappresenta l'ID processo univoco. Eseguendo il cmdlet `Where-Object`, è possibile estrarre i gruppi di eventi con un ID processo specifico:

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC
 
TimeCreated                     Id LevelDisplayName Message                                               
-----------                     -- ---------------- -------                                               
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...  
```

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a>Uso di xDscDiagnostics per analizzare i registri DSC

**xDscDiagnostics** è un modulo di PowerShell costituito da alcune funzioni che consentono di analizzare gli errori di DSC nel computer in uso. Queste funzioni possono aiutare a identificare tutti gli eventi locali delle operazioni DSC passate oppure gli eventi DSC in computer remoti (con credenziali valide). Il termine operazione DSC in questo ambito viene usato per definire una singola esecuzione di DSC univoca, dall'inizio alla fine. Ad esempio, `Test-DscConfiguration` sarebbe un'operazione DSC distinta. Allo stesso modo, ogni altro cmdlet in DSC (ad esempio `Get-DscConfiguration`, `Start-DscConfiguration` e così via) può essere identificato come operazione DSC distinta. Le funzioni vengono spiegate in [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics). La Guida è disponibile eseguendo `Get-Help <cmdlet name>`.

### <a name="getting-details-of-dsc-operations"></a>Acquisizione dei dettagli delle operazioni DSC 

La funzione `Get-xDscOperation` consente di trovare i risultati delle operazioni DSC eseguite in uno o più computer e restituisce un oggetto che contiene la raccolta di eventi generati da ogni operazione DSC. Nell'output seguente, ad esempio, sono stati eseguiti tre comandi. Il primo ha avuto esito positivo e gli altri due esito negativo. Questi risultati sono riepilogati nell'output di `Get-xDscOperation`.

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents            
------------   ---------- -----------           ------   -----                                 ---------            
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...

```

È anche possibile specificare che vengano restituiti solo i risultati relativi alle operazioni più recenti usando il parametro `Newest`:

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation -Newest 5
ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents            
------------   ---------- -----------           ------   -----                                 ---------            
SRV1   1          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   2          6/23/2016 4:36:54 PM  Success  5c06402b-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   3          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   4          6/23/2016 4:36:54 PM  Success  5c06402a-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   5          6/23/2016 4:36:51 PM  Success                                        {@{Message=; TimeC...
```

### <a name="getting-details-of-dsc-events"></a>Acquisizione dei dettagli degli eventi DSC

Il cmdlet `Trace-xDscOperation` restituisce un oggetto contenente una raccolta di eventi, i relativi tipi e l'output del messaggio generato da un'operazione DSC specifica. In genere, quando viene individuato un errore in un'operazione tramite `Get-xDscOperation`, è necessario tracciare tale operazione per determinare gli eventi che hanno causato l'errore.

Usare il parametro `SequenceID` per ottenere gli eventi per un'operazione specifica in un computer specifico. Ad esempio, se si specifica 9 come `SequenceID`, `Trace-xDscOperaion` ottiene la traccia per l'operazione DSC al nono posto dopo l'ultima operazione:

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -SequenceID 9

ComputerName   EventType    TimeCreated           Message                                                                                             
------------   ---------    -----------           -------                                                                                             
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.                
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Running consistency engine.                                                                         
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM The local configuration manager is updating the PSModulePath to WindowsPowerShell\Modules;C:\Prog...
SRV1   OPERATIONAL  6/24/2016 10:51:53 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer. 
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Consistency engine was run successfully.                                                            
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Job runs under the following LCM setting. ...                                                       
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Operation Consistency Check or Pull completed successfully. 
```

Passare il **GUID** assegnato a una specifica operazione DSC, come restituito dal cmdlet `Get-xDscOperation`, per ottenere i dettagli degli eventi per l'operazione DSC:

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -JobID 9e0bfb6b-3a3a-11e6-9165-00155d390509

ComputerName   EventType    TimeCreated           Message                                                                                             
------------   ---------    -----------           -------                                                                                             
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.                
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof                             
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.                                                                         
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Starting consistency engine.                          
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Current.mof.                          
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.                                                                 
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer. 
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCServiceFeature]                      
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with resource name [WindowsFeature]DSC...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCServiceFeature]                      
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCServiceFeature] True in 0.3130 sec...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCServiceFeature]                      
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCPullServer]                        
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with resource name [xDSCWebService]P...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCPullServer]                        
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Ensure           
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Port             
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Physical Path ...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check State            
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Get Full Path for We...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCPullServer] True in 0.0160 seconds.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCPullServer]                        
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Consistency check completed.                          
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof                             
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.                                                            
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...                                                       
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.                                         
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
```

Si noti che, poiché `Trace-xDscOperation` aggrega gli eventi dei registri di debug, operativo e analitico, verrà chiesto di abilitare questi registri, come descritto in precedenza.

In alternativa, è possibile raccogliere informazioni sugli eventi salvando l'output di `Trace-xDscOperation` in una variabile. È possibile usare i comandi seguenti per visualizzare tutti gli eventi per un'operazione DSC specifica.

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

In questo modo, verranno visualizzati gli stessi risultati del cmdlet `Get-WinEvent`, come nell'output seguente:

```powershell
   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message                                                                                           
-----------                     -- ---------------- -------                                                                                           
6/23/2016 1:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 1:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 2:07:00 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 2:07:01 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 2:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 2:36:56 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 3:06:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 3:06:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 3:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 3:36:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 4:06:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 4:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 4:36:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 4:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 5:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 5:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 5:36:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 5:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 6:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 6:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 6:36:56 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 6:36:57 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 7:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 7:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 7:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 7:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 8:06:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
```

Idealmente, è consigliabile usare prima di tutto `Get-xDscOperation` per elencare le ultime esecuzioni della configurazione DSC nei computer. In seguito, è possibile esaminare qualsiasi singola operazione (usando il campo SequenceID o JobID) con `Trace-xDscOperation` per determinare le azioni eseguite in background.

### <a name="getting-events-for-a-remote-computer"></a>Acquisizione degli eventi per un computer remoto

Utilizzare il parametro `ComputerName` del cmdlet `Trace-xDscOperation` per acquisire i dettagli dell'evento in un computer remoto. Prima di procedere, è necessario creare una regola firewall per consentire l'amministrazione remota nel computer remoto:

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```
Ora è possibile specificare il computer nella chiamata a `Trace-xDscOperation`:

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -ComputerName SRV2 -Credential Get-Credential -SequenceID 5

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 f...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Starting consistency...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Curr...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature,...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCSer...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with re...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCP...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with ...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Consistency check co...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
```

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a>Le risorse non vengono aggiornate: Come reimpostare la cache

Il motore DSC memorizza nella cache le risorse implementate come modulo di PowerShell, per garantire maggiore efficienza. Tuttavia, ciò può provocare problemi quando si crea una risorsa e contemporaneamente la si testa, perché DSC carica la versione memorizzata nella cache fino a quando non viene riavviato il processo. Per fare in modo che DSC carichi la versione più recente, è necessario terminare in modo esplicito il processo che ospita il motore DSC.

Analogamente, quando si esegue `Start-DscConfiguration`, dopo l'aggiunta e la modifica di una risorsa personalizzata, la modifica potrebbe non venire applicata fino a quando il computer non viene riavviato. Ciò avviene perché DSC viene eseguito nel processo host del provider WMI (WmiPrvSE) e in genere ci sono molte istanze di WmiPrvSE in esecuzione contemporaneamente. Quando si riavvia, il processo host viene riavviato e la cache viene cancellata.

Per riciclare la configurazione e cancellare la cache senza riavviare il computer, è necessario arrestare e quindi riavviare il processo host. Questa operazione può essere eseguita per ogni istanza, identificando il processo, arrestandolo e riavviandolo. In alternativa, è possibile usare `DebugMode`, come illustrato di seguito, per ricaricare la risorsa PowerShell DSC.

Per identificare il processo che ospita il motore DSC e arrestarlo per ogni istanza, è possibile elencare l'ID processo di WmiPrvSE che ospita il motore DSC. Quindi, per aggiornare il provider, arrestare il processo WmiPrvSE usando i comandi seguenti ed eseguire **Start-DscConfiguration** di nuovo.

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers | 
Where-Object {$_.provider -like 'dsccore'} | 
Select-Object -ExpandProperty HostProcessIdentifier 

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## <a name="using-debugmode"></a>Uso di DebugMode

È possibile configurare Gestione configurazione locale per DSC in modo da usare `DebugMode` per cancellare sempre la cache quando il processo host viene riavviato. Se l'impostazione è **TRUE**, il motore ricarica sempre la risorsa PowerShell DSC. Dopo aver terminato di scrivere la risorsa, è possibile impostare di nuovo il valore su **FALSE** per ripristinare il comportamento del motore in base a cui i moduli vengono memorizzati nella cache.

Di seguito è illustrato in che modo `DebugMode` può aggiornare automaticamente la cache. Si analizzi prima di tutto la configurazione predefinita:

```
PS C:\> Get-DscLocalConfigurationManager
 
 
AllowModuleOverwrite           : False
CertificateID                  : 
ConfigurationID                : 
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     : 
DebugMode                      : False
DownloadManagerCustomData      : 
DownloadManagerName            : 
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :  
```

È possibile vedere che `DebugMode` è impostato su **FALSE**.

Per la dimostrazione di `DebugMode`, usare la risorsa di PowerShell seguente:

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1" | Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
} 
```

Creare quindi una configurazione usando la risorsa precedente denominata `TestProviderDebugMode`:

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

È possibile notare che contenuto del file: "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" è **1**.

Aggiornare quindi il codice del provider usando lo script seguente:

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput" | Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

Questo script genera un numero casuale e aggiorna di conseguenza il codice del provider. Con `DebugMode` impostato su false, i contenuti del file "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" non vengono mai modificati.

A questo punto, impostare `DebugMode` su **TRUE** nello script di configurazione:

```powershell
LocalConfigurationManager
{
    DebugMode = $true
} 
```

Quando si esegue di nuovo lo script precedente, si noterà che il contenuto del file è diverso ogni volta. È possibile eseguire `Get-DscConfiguration` per verificare. Di seguito è riportato il risultato di due esecuzioni aggiuntive (quando si esegue lo script, i risultati potrebbero essere diversi):

```powershell
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)
 
onlyProperty                            PSComputerName                         
------------                            --------------                         
20                                      localhost                              
 
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)
 
onlyProperty                            PSComputerName                         
------------                            --------------                         
14                                      localhost
```

## <a name="see-also"></a>Vedere anche

### <a name="reference"></a>Riferimento
* [Risorsa Log DSC](logResource.md)

### <a name="concepts"></a>Concetti
* [Creare risorse Windows PowerShell DSC (Desired State Configuration) personalizzate](authoringResource.md)

### <a name="other-resources"></a>Risorse aggiuntive
* [Cmdlet di Windows PowerShell DSC (Desired State Configuration)](https://technet.microsoft.com/en-us/library/dn521624(v=wps.630).aspx)




<!--HONumber=Oct16_HO4-->


