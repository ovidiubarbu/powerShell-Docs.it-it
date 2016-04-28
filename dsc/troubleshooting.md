# Risoluzione dei problemi relativi a DSC

>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Questo argomento descrive i modi per eseguire gli script DSC (Desired State Configuration) senza errori. Usando i registri in modo efficace per tenere traccia degli errori e comprendendo come riciclare la cache per vedere i risultati immediati delle modifiche alle risorse, sarà possibile risolvere in modo più efficace i problemi relativi a DSC. Queste tecniche vengono illustrate in due sezioni:

* Lo script non viene eseguito: Uso di registri DSC per diagnosticare gli errori di script
* Le risorse non vengono aggiornate: Come reimpostare la cache

## Lo script non viene eseguito: Uso di registri DSC per diagnosticare gli errori di script

Come tutti i software Windows, DSC registra errori ed eventi in registri che possono essere visualizzati dal Visualizzatore eventi. Esaminando questi registri è possibile comprendere perché un'operazione specifica non è riuscita e come evitare l'errore in futuro. La scrittura di script di configurazione può essere complessa, quindi per rendere più semplice il rilevamento degli errori durante la scrittura è possibile usare la risorsa Log DSC per tenere traccia dello stato della configurazione nel registro eventi DSC Analytic.

## Dove sono i registri eventi DSC?

Nel Visualizzatore eventi gli eventi DSC si trovano in: Registri applicazioni e servizi/Microsoft/Windows/Desired State Configuration

Per visualizzare i registri eventi è anche possibile eseguire il cmdlet di PowerShell corrispondente, Get-WinEvent:

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message                                                                                                  
-----------                     -- ---------------- -------                                                                                                  
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
```

Come illustrato in precedenza, il nome del registro principale di DSC è Microsoft->Windows->DSC (gli altri nomi di registro in Windows non sono riportati per brevità). Il nome principale viene aggiunto al nome del canale per creare il nome completo del registro. Il motore DSC scrive principalmente in tre tipi di registri: registri di debug, operativo e analitico. Poiché i registri di debug e analitico sono disattivati per impostazione predefinita, è necessario abilitarli nel Visualizzatore eventi. A tale scopo, aprire il Visualizzatore eventi digitando Show-EventLog in Windows PowerShell oppure fare clic sul pulsante Start, scegliere Pannello di controllo, fare clic su Strumenti di amministrazione e quindi su Visualizzatore eventi. Scegliere Visualizza registri analitici e di debug dal menu Visualizza del Visualizzatore eventi. Il nome del registro per il canale analitico è Microsoft-Windows-Dsc/Analytic e per il canale di debug è Microsoft-Windows-Dsc/Debug. È anche possibile usare l'utilità wevtutil per abilitare i registri, come illustrato nell'esempio seguente.

```powershell
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
```

## Cosa contengono i registri DSC?

I registri DSC sono suddivisi in tre canali in base all'importanza del messaggio. Il registro operativo in DSC contiene tutti i messaggi di errore e può essere usato per identificare un problema. Il registro analitico include un volume maggiore di eventi e consente di identificare la posizione in cui si sono verificati gli errori. Questo canale contiene anche i messaggi dettagliati, se disponibili. Il registro di debug contiene registri che aiutano a capire come si sono verificati gli errori. I messaggi di evento DSC sono strutturati in modo che ogni messaggio inizi con un ID processo che rappresenta in modo univoco un'operazione DSC. Nell'esempio seguente si tenta di ottenere il messaggio dal primo evento registrato nel registro operativo DSC.

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
Consistency engine was run successfully. 
```

Gli eventi DSC vengono registrati in una struttura specifica che consente all'utente di aggregare gli eventi relativi a un processo DSC. La struttura è la seguente:

ID processo: <Guid>
**<Event Message>**

## Raccolta di eventi da una singola operazione DSC

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

È possibile estrarre i dati nella variabile `$SeparateDscOperations` usando Where-Object. Di seguito sono illustrati cinque scenari in cui è possibile estrarre i dati per la risoluzione dei problemi relativi a DSC:

### 1: Errori relativi alle operazioni

Tutti gli eventi hanno livelli di gravità. Queste informazioni possono essere usate per identificare gli eventi di errore:

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### 2: Dettagli delle operazioni eseguite nell'ultima mezz'ora

`TimeCreated`, una proprietà di ogni evento di Windows, indica l'ora di creazione dell'evento. Il confronto tra questa proprietà e un oggetto di data/ora specifico consente di filtrare tutti gli eventi:

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}   
```

### 3: Messaggi dell'operazione più recente

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

### 4: Messaggi di errore registrati per operazioni recenti non riuscite

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

### 5: Tutti gli eventi generati per un ID processo specifico.

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

## Uso di xDscDiagnostics per analizzare i registri DSC

xDscDiagnostics è un modulo di PowerShell costituito da due semplici funzioni che consentono di analizzare gli errori di DSC nel computer in uso: `Get-xDscOperation` e `Trace-xDscOperation`. Queste funzioni possono aiutare a identificare tutti gli eventi locali delle operazioni DSC passate oppure gli eventi DSC in computer remoti (con credenziali valide). Il termine operazione DSC in questo ambito viene usato per definire una singola esecuzione di DSC univoca, dall'inizio alla fine. Ad esempio, `Test-DscConfiguration` sarebbe un'operazione DSC distinta. Allo stesso modo, ogni altro cmdlet in DSC (ad esempio `Get-DscConfiguration`, `Start-DscConfiguration` e così via) può essere identificato come operazione DSC distinta. Le due funzioni sono illustrate nel modulo xDscDiagnostics di PowerShell (DSC Resource Kit) e in dettaglio più avanti. La Guida è disponibile eseguendo `Get-Help <cmdlet name>`.

## Get-xDscOperation

Questa funzione consente di trovare i risultati delle operazioni DSC eseguite in uno o più computer e restituisce un oggetto che contiene la raccolta di eventi generati da ogni operazione DSC. Nell'output seguente, ad esempio, sono stati eseguiti tre comandi. Il primo ha avuto esito positivo e gli altri due esito negativo. Questi risultati sono riepilogati nell'output di `Get-xDscOperation`.

TODO: Sostituire questa immagine che mostra l'output di Get-xDscOperation

### Parametri

* Newest: accetta un valore intero che indica il numero di operazioni da visualizzare. Per impostazione predefinita, vengono restituite le 10 operazioni più recenti. Ad esempio:
  TODO: Mostrare Get-xDscOperation -Newest 5
* ComputerName: parametro che accetta una matrice di stringhe, ognuna delle quali contiene il nome di un computer da cui raccogliere dati del registro eventi DSC. Per impostazione predefinita, vengono raccolti i dati dal computer locale. Per abilitare questa funzionalità, è necessario eseguire il comando seguente nei computer remoti, in modalità con privilegi elevati in modo che sia consentita la raccolta di eventi.
```powershell
  New-NetFirewallRule -Name "Service RemoteAdmin" -Action Allow
```
* Credential: parametro di tipo PSCredential, che consente l'accesso ai computer specificati nel parametro ComputerName.

### Oggetto restituito

Il cmdlet restituisce una matrice di oggetti, ognuno di tipo Microsoft.PowerShell.xDscDiagnostics.GroupedEvents. Ogni oggetto nella matrice si riferisce a un'operazione DSC distinta. La visualizzazione predefinita per questo oggetto ha le proprietà seguenti:
* SequenceID: specifica il numero incrementale assegnato all'operazione DSC in base a quando viene eseguita. Ad esempio, l'ultima operazione eseguita ha un valore SequenceID pari a 1, la penultima operazione DSC ha un valore SequenceID pari a 2 e così via. Questo numero è un altro identificatore per ogni oggetto nella matrice restituita.
* TimeCreated: valore DateTime che indica quando è iniziata l'operazione DSC.
* ComputerName: nome del computer da cui vengono aggregati i risultati.
* Result: stringa con valore Failure o Success, che indica se l'operazione DSC ha restituito un errore o meno.
* AllEvents: oggetto che rappresenta una raccolta di eventi generati dall'operazione DSC.

Ad esempio, l'output seguente mostra i risultati dell'ultima operazione da più computer:
  TODO: Sostituire l'immagine per Get-xDscOperation per visualizzare i registri dei computer remoti

## Trace-xDscOperation

Questo cmdlet restituisce un oggetto contenente una raccolta di eventi, i relativi tipi e l'output del messaggio generato da un'operazione DSC specifica. In genere, quando viene individuato un errore in un'operazione tramite `Get-xDscOperation`, è necessario tracciare tale operazione per determinare gli eventi che hanno causato l'errore.

### Parametri

* SequenceID: valore intero assegnato a qualsiasi operazione, relativamente a un computer specifico. Specificando, ad esempio, un ID di sequenza pari a 4, l'output restituito corrisponde alla traccia per la quartultima operazione DSC.

Trace-xDscOperation con ID di sequenza specificato
* JobID: valore GUID assegnato da xDscOperation di Gestione configurazione locale per identificare in modo univoco un'operazione. Quando viene specificato un valore JobID, l'output è costituito dalla traccia dell'operazione DSC corrispondente.
  TODO: Sostituire l'immagine per Trace-xDscOperation con un parametro JobID
* ComputerName e Credential: questi parametri consentono di raccogliere la traccia dai computer remoti:
```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -Action Allow
```
  TODO: Sostituire l'immagine per Trace-xDscOperation in esecuzione in un computer diverso

Si noti che, poiché `Trace-xDscOperation` aggrega gli eventi dei registri di debug, operativo e analitico, verrà chiesto di abilitare questi registri, come descritto in precedenza.

### Oggetto restituito

Questo cmdlet restituisce una matrice di oggetti, ognuno di tipo `Microsoft.PowerShell.xDscDiagnostics.TraceOutput`. Ogni oggetto in questa matrice contiene i campi seguenti:
* ComputerName: nome del computer da cui vengono raccolti i registri.
* EventType: campo di tipo enumeratore che contiene informazioni sul tipo di evento. I tipi possibili sono i seguenti:
  - Operational: l'evento è incluso nel registro operativo.
  - Analytic: l'evento è incluso nel registro analitico.
  - Debug: l'evento è incluso nel registro di debug.
  - Verbose: l'output degli eventi è costituito da messaggi dettagliati durante l'esecuzione. I messaggi dettagliati semplificano l'identificazione della sequenza di eventi pubblicati.
  - Error: eventi di errore. Cercando gli eventi di errore, in genere è possibile trovare rapidamente la causa dell'errore.
* TimeCreated: valore DateTime che indica quando è stato registrato l'evento da DSC.
* Message: messaggio registrato da DSC nei registri eventi.

Di seguito sono illustrati i campi di questo oggetto che è possibile usare per ottenere altre informazioni sull'evento, ma che non sono visualizzati per impostazione predefinita:

* JobID: ID processo (in formato GUID) specifico dell'operazione DSC.
* SequenceID: valore SequenceID univoco dell'operazione DSC nel computer.
* Event: evento effettivo registrato da DSC, di tipo `System.Diagnostics.Eventing.Reader.EventLogRecord`. È possibile ottenere questo elemento anche eseguendo il cmdlet `Get-WinEvent`. Sono incluse informazioni aggiuntive, ad esempio attività, ID e livello dell'evento.

In alternativa, è possibile raccogliere informazioni sugli eventi salvando l'output di `Trace-xDscOperation` in una variabile. È possibile usare il comando seguente per visualizzare tutti gli eventi per un'operazione DSC specifica:

```powershell
(Trace-xDscOperation -SequenceID 3).Event
```

In questo modo, verranno visualizzati gli stessi risultati del cmdlet `Get-WinEvent`, come nell'output seguente:
  TODO: Quale output?

Idealmente, è consigliabile usare prima di tutto `Get-xDscOperation` per elencare le ultime esecuzioni della configurazione DSC nei computer. In seguito, è possibile esaminare qualsiasi singola operazione (usando il campo SequenceID o JobID) con `Trace-xDscOperation` per determinare le azioni eseguite in background.

## Le risorse non vengono aggiornate: Come reimpostare la cache

Il motore DSC memorizza nella cache le risorse implementate come modulo di PowerShell, per garantire maggiore efficienza. Tuttavia, ciò può provocare problemi quando si crea una risorsa e contemporaneamente la si testa, perché DSC carica la versione memorizzata nella cache fino a quando non viene riavviato il processo. Per fare in modo che DSC carichi la versione più recente, è necessario terminare in modo esplicito il processo che ospita il motore DSC.

Analogamente, quando si esegue `Start-DscConfiguration`, dopo l'aggiunta e la modifica di una risorsa personalizzata, la modifica potrebbe non venire applicata fino a quando il computer non viene riavviato. Ciò avviene perché DSC viene eseguito nel processo host del provider WMI (WmiPrvSE) e in genere ci sono molte istanze di WmiPrvSE in esecuzione contemporaneamente. Quando si riavvia, il processo host viene riavviato e la cache viene cancellata.

Per riciclare la configurazione e cancellare la cache senza riavviare il computer, è necessario arrestare e quindi riavviare il processo host. Questa operazione può essere eseguita per ogni istanza, identificando il processo, arrestandolo e riavviandolo. In alternativa, è possibile usare `DebugMode`, come illustrato di seguito, per ricaricare la risorsa PowerShell DSC.

Per identificare il processo che ospita il motore DSC e arrestarlo per ogni istanza, è possibile elencare l'ID processo di WmiPrvSE che ospita il motore DSC. Quindi, per aggiornare il provider, arrestare il processo WmiPrvSE usando i comandi seguenti ed eseguire Start-DscConfiguration di nuovo.

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

## Uso di DebugMode

È possibile configurare Gestione configurazione locale per DSC in modo da usare `DebugMode` per cancellare sempre la cache quando il processo host viene riavviato. Se l'impostazione è TRUE, il motore ricarica sempre la risorsa PowerShell DSC. Dopo aver terminato di scrivere la risorsa, è possibile impostare di nuovo il valore su FALSE per ripristinare il comportamento del motore in base a cui i moduli vengono memorizzati nella cache.

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

È possibile vedere che `DebugMode` è impostato su FALSE.

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

È possibile notare che il contenuto del file: "$env:SystemDrive\OutputFromTestProviderDebugMode.txt" è 1.

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

Questo script genera un numero casuale e aggiorna di conseguenza il codice del provider. Con `DebugMode` impostato su false, il contenuto del file "$env:SystemDrive\OutputFromTestProviderDebugMode.txt" non viene mai modificato.

A questo punto, impostare `DebugMode` su TRUE nello script di configurazione:

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

## Vedere anche

### Riferimento
* [Risorsa Log DSC](logResource.md)

### Concetti
* [Creare risorse Windows PowerShell DSC (Desired State Configuration) personalizzate](authoringResource.md)

### Risorse aggiuntive
* [Cmdlet di Windows PowerShell DSC (Desired State Configuration)](https://technet.microsoft.com/en-us/library/dn521624(v=wps.630).aspx)


<!--HONumber=Mar16_HO1-->


