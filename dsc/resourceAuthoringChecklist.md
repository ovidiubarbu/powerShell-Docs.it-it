---
title: Elenco di controllo per la creazione di risorse
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: bd6af2cbf746e71aa59f509eae14664e647a1b05

---

# Elenco di controllo per la creazione di risorse
Questo elenco di controllo è un elenco di procedure consigliate durante la creazione di una nuova risorsa DSC
## Il modulo della risorsa contiene i file psd1 e schema.mof per ogni risorsa. 
Per prima cosa, è necessario verificare che la risorsa abbia la struttura corretta e contenga tutti i file necessari. Ogni modulo di risorsa deve contenere un file con estensione psd1 e per tutte le risorse non composite deve essere disponibile un file schema.mof. Le risorse senza schema non verranno elencate da **Get-DscResource** e gli utenti non saranno in grado di usare IntelliSense durante la scrittura di codice in base a tali moduli in ISE. La struttura di directory di esempio per la risorsa xRemoteFile, che fa parte del modulo della risorsa xPSDesiredStateConfiguration, potrebbe avere questo aspetto:


```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## La risorsa e lo schema sono corretti e sono stati verificati con i cmdlet di DscResourceDesigner ##
Un altro aspetto importante è verificare il file di schema della risorsa (*.schema.mof). Verificare che:
-   I tipi di proprietà siano corretti (ad esempio, non usare il tipo String per proprietà che accettano valori numerici, ma usare invece UInt32 o altri tipi numerici)
-   Gli attributi delle proprietà siano specificati correttamente ([key], [required], [write], [read])


- Almeno un parametro dello schema deve essere contrassegnato come [key]


- Una proprietà [read] non può coesistere con [required], [key] o [write]


- Se vengono specificati più qualificatori ad eccezione di [read], [key] ha la precedenza. Se vengono specificati [write] e [required], [required] ha la precedenza
-   Il qualificatore ValueMap è specificato dove appropriato

Esempio:
```
[Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
```

-   Il nome descrittivo è specificato ed è conforme alle convenzioni di denominazione DSC

Esempio:
```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```

-   Ogni campo ha una descrizione significativa

Di seguito è possibile trovare un buon esempio del file di schema della risorsa (questo è lo schema effettivo della risorsa xRemoteFile dal DSC Resource Kit)
```
[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]
class MSFT_xRemoteFile : OMI_BaseResource
{
    [Key, Description("Path under which downloaded or copied file should be accessible after operation.")] String DestinationPath;
    [Required, Description("Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.")] String Uri;
    [Write, Description("User agent for the web request.")] String UserAgent;
    [Write, EmbeddedInstance("MSFT_KeyValuePair"), Description("Headers of the web request.")] String Headers[];
    [Write, EmbeddedInstance("MSFT_Credential"), Description("Specifies a user account that has permission to send the request.")] String Credential;
    [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
}; 
```
È inoltre consigliabile usare i cmdlet **Test-xDscResource** e **Test-xDscSchema** da DscResourceDesigner per la verifica automatica di risorsa e schema:
```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```
Ad esempio:
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## La risorsa viene caricata senza errori ##
Dopo avere verificato che la risorsa contenga tutti i file necessari e averli verificati tramite DscResourceDesigner, è necessario controllare se il modulo della risorsa può essere caricato correttamente.
È possibile farlo manualmente, eseguendo `Import-Module <resource_module> -force ` e verificando che non si siano verificati errori oppure tramite l'automazione del test. In quest'ultimo caso, è possibile usare questa struttura nel test case:
```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```
4   La risorsa è idempotente in caso positivo. Una delle caratteristiche fondamentali di tutte le risorse DSC è l'idempotenza. Questo significa che è possibile applicare una configurazione DSC contenente la risorsa più volte senza modificare il risultato dopo l'applicazione iniziale. Ad esempio, se si crea una configurazione che contiene la risorsa File seguente:
```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
} 
```
Dopo la prima applicazione, il file test.txt dovrebbe comparire nella cartella C:\test. Le esecuzioni successive della stessa configurazione, tuttavia, non dovrebbero modificare lo stato del computer (ad esempio, non dovrebbe essere creata alcuna copia del file test.txt).
Per assicurarsi che la risorsa sia idempotente, è possibile chiamare ripetutamente **Set-TargetResource** in caso di test diretto della risorsa oppure chiamare più volte **Start-DscConfiguration** per l'esecuzione di test end-to-end. Il risultato sarà lo stesso dopo ogni esecuzione. 


## Lo scenario di modifica utente è stato testato ##
La modifica dell'utente è un altro scenario comune, che vale la pena di testare. Consente di verificare che **Set-TargetResource** e **Test-TargetResource** funzionino correttamente. Ecco i passaggi necessari per questo test:
1.  Iniziare con la risorsa che non si trova nello stato desiderato
2.  Eseguire la configurazione della risorsa
3.  Verificare che **Test-DscConfiguration** restituisca True
4.  Modificare la risorsa in modo che non si trovi più nello stato desiderato
5.  Verificare che il valore restituito da **Test-DscConfiguration** sia false. Ecco un esempio più concreto che usa la risorsa Registry:
1.  Iniziare con una chiave del Registro di sistema che non si trova nello stato desiderato
2.  Eseguire **Start-DscConfiguration** con una configurazione per mettere la risorsa nello stato desiderato e verificare che il test venga superato.
3.  Eseguire **Test-DscConfiguration** e verificare che restituisca True
4.  Modificare il valore della chiave in modo che non si trovi più nello stato desiderato
5.  Eseguire **Test-DscConfiguration** e verificare che restituisca False
6.  La funzionalità Get-TargetResource è stata verificata con Get-DscConfiguration

Get-TargetResource dovrebbe restituire i dettagli dello stato corrente della risorsa. Assicurarsi di testarla chiamando Get-DscConfiguration dopo aver applicato la configurazione e verificando che l'output rispecchi correttamente lo stato corrente del computer. È importante eseguire il test separatamente, poiché eventuali problemi in questa area non verranno visualizzati durante la chiamata di Start-DscConfiguration.

## La risorsa è stata verificata chiamando direttamente le funzioni **Get/Set/Test-TargetResource** ##

Assicurarsi di testare le funzioni **Get/Set/Test-TargetResource** implementate nella risorsa chiamandole direttamente e verificando che funzionino come previsto.

## La risorsa è stata sottoposta a una verifica end-to-end tramite **Start-DscConfiguration** ##

Testare le funzioni **Get/Set/Test-TargetResource** tramite chiamata diretta è importante, ma in questo modo non verranno individuati tutti i problemi. È consigliabile concentrare una parte significativa delle attività di test sull'uso di **Start-DscConfiguration** o del server di pull. Questo è in effetti il modo in cui gli utenti useranno la risorsa, quindi non sottovalutare l'importanza di questo tipo di test. Possibili tipi di problemi:
-   Possibili comportamenti diversi delle credenziali e/o della sessione perché l'agente DSC viene eseguito come servizio.  Assicurarsi di sottoporre qualsiasi funzionalità a test end-to-end.
-   Verificare che i messaggi di errore visualizzati dalla risorsa abbiano senso. Ad esempio, gli errori restituiti da **Start-DscConfiguration** potrebbero essere diversi da quelli visualizzati in seguito alla chiamata diretta della funzione **Set-TargetResource**.

## La risorsa si comporta correttamente in tutte le piattaforme supportate da DSC (o in caso contrario restituisce un errore specifico) ##
La risorsa dovrebbero funzionare in tutte le piattaforme supportate da DSC (Windows Server 2008 R2 e versioni successive). Assicurarsi di installare la versione più recente di WMF (Windows Management Framework) nel sistema operativo per ottenere la versione più recente di DSC. Se la risorsa non funziona in alcune di queste piattaforme da progettazione, deve essere restituito un messaggio di errore specifico. Assicurarsi anche che la risorsa controlli che i cmdlet chiamati siano presenti nel computer specifico. In Windows Server 2012 sono stati aggiunti numerosi cmdlet nuovi, non disponibili in Windows Server 2008 R2 anche con WMF installato. 

## Il funzionamento della risorsa è stato verificato nel client Windows (se applicabile) ##
Una mancanza molto comune dei test è verificare la risorsa solo nelle versioni server di Windows. Molte risorse sono progettate anche per il funzionamento su SKU client, quindi se questo è il caso, è importante non dimenticare di eseguire i test anche su queste piattaforme. 
## Get-DSCResource elenca la risorsa ##
Dopo aver distribuito il modulo nel computer, la chiamata di Get-DscResource dovrebbe elencare anche la risorsa in questione tra le altre nei risultati. Se non è possibile trovare la risorsa nell'elenco, verificare che esista il file schema.mof per la risorsa. 
## Il modulo della risorsa contiene esempi ##
Se si prevede di condividere la risorsa (come auspicabile), è consigliabile creare esempi di qualità che possano aiutare gli altri utenti a capire come usarla. Ciò è fondamentale, soprattutto perché molti utenti usano il codice di esempio come documentazione. 
-   In primo luogo, è necessario determinare gli esempi da includere nel modulo. È opportuno offrire come minimo esempi per i casi d'uso più importanti per la risorsa:
-   Se il modulo contiene varie risorse che devono essere usate insieme per uno scenario end-to-end, l'esempio end-to-end di base dovrebbe essere idealmente il primo.
-   Gli esempi iniziali dovrebbero essere molto semplici e illustrare come iniziare a usare le risorse in piccoli blocchi gestibili, ad esempio la creazione di un nuovo VHD
-   Gli esempi successivi dovrebbero continuare e ampliare quelli iniziali (ad esempio, creare una VM da un VHD, rimuovere una VM o modificare una VM) e illustrare le funzionalità avanzate (ad esempio, la creazione di una VM con memoria dinamica)
-   Le configurazioni di esempio devono essere parametrizzate (tutti i valori devono essere passati come parametri alla configurazione, senza valori hardcoded):
```powershell
configuration Sample_xRemoteFile_DownloadFile
{
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
} 
```
-   È buona norma includere un esempio di come chiamare la configurazione con i valori effettivi alla fine dello script di esempio, impostandolo come commento. Ad esempio, nella configurazione precedente non sarà evidente per tutti gli utenti che è il modo migliore per specificare UserAgent è:

`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer`  
Per questo motivo è consigliabile includere un commento con l'esecuzione di esempio della configurazione:
```
<# 
Sample use (parameter values need to be changed according to your scenario):

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
-userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
#>  
```
-   Per ogni esempio, scrivere una breve descrizione per illustrarne le funzioni e indicare il significato dei parametri. 
-   Assicurarsi che siano disponibili esempi per la maggior parte degli scenari importanti per la risorsa e se non manca nulla, verificare che funzionino tutti e mettano il computer nello stato desiderato.  

## I messaggi di errore sono facili da comprendere e aiutano gli utenti a risolvere i problemi ##
Per essere utili, i messaggi di errore devono essere:
-   Presenti: il problema principale con i messaggi di errore è che spesso non esistono, quindi assicurarsi che ci siano. 
-   Facili da capire: messaggi leggibili evitando oscuri codici di errore
-   Precisi: descrivere esattamente il problema
-   Costruttivi: suggerire come risolvere il problema
-   Cortesi: non incolpare l'utente o farlo sentire stupido. Assicurarsi di verificare gli errori negli scenari end-to-end, con **Start-DscConfiguration**, in quanto potrebbero essere diversi da quelli restituiti quando si eseguono direttamente le funzioni della risorsa. 

## I messaggi dei log sono facili da capire e informativi (inclusi i log -verbose, -debug ed ETW) ##
Assicurarsi che i log generati dalla risorsa siano facili da comprendere e offrano informazioni utili all'utente. Le risorse dovrebbero offrire come output tutte le informazioni che potrebbero essere utili all'utente, ma non sempre la disponibilità di più log è un vantaggio. È consigliabile evitare la ridondanza e output di dati senza valore aggiunto, in modo da non costringere gli utenti a scorrere centinaia di voci di log per trovare quello che cercano. Naturalmente, anche l'assenza di log non è una soluzione accettabile per questo problema. 

Durante il test, è necessario analizzare anche i log dettagliati e di debug (eseguendo **Start-DscConfiguration** con le opzioni -verbose e -debug in modo appropriato), oltre ai log ETW. Per visualizzare i log ETW di DSC, nel Visualizzatore eventi aprire la cartella seguente: Registri applicazioni e servizi - Microsoft - Windows - Desired State Configuration.  Per impostazione predefinita è visualizzato il canale Operativo, ma assicurarsi di abilitare i canali Analitico e Debug prima di eseguire la configurazione. Per abilitare i canali Analitico/Debug, è possibile eseguire lo script riportato di seguito:
```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug" 
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}     
Invoke-Expression $commandToExecute 
```
## L'implementazione della risorsa non contiene percorsi hardcoded ##
Assicurarsi che non siano presenti percorsi hardcoded nell'implementazione della risorsa, in particolare se presuppongono una lingua specifica (en-us) o quando possono essere usate variabili di sistema.
Se la risorsa deve accedere a percorsi specifici, usare le variabili di ambiente invece di percorsi hardcoded, perché potrebbero variare in altri computer.

Esempio:

Invece di:
```
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
 ```
È possibile scrivere:
```
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)} 
```
## L'implementazione della risorsa non contiene informazioni sull'utente ##
Assicurarsi che nel codice non siano presenti nomi di posta elettronica, informazioni su account o nomi di persone.
## La risorsa è stata testata con credenziali valide e non valide ##
Se la risorsa accetta credenziali come parametro:
-   Verificare che la risorsa funzioni quando l'account di sistema locale (o l'account computer per risorse remote) non ha accesso.
-   Verificare che la risorsa funzioni quando vengono specificate credenziali per Get, Set e Test 
-   Se la risorsa accede a condivisioni, testare tutte le varianti che occorre supportare.  
Ad esempio:
- Condivisioni Windows standard.
- Condivisioni DFS.
- Condivisioni SAMBA (se si vuole supportare Linux).

## La risorsa non usa cmdlet che richiedono input interattivo ##
Le funzioni **Get/Set/Test-TargetResource** dovrebbero essere eseguite automaticamente e non devono attendere l'input dell'utente in alcuna fase dell'esecuzione. Ad esempio, è consigliabile non usare **Get-Credential** all'interno di queste funzioni. Se è necessario fornire l'input dell'utente, è consigliabile passarlo alla configurazione come parametro durante la fase di compilazione. 
## La funzionalità della risorsa è stata accuratamente testata ##
Lo sviluppatore ha la responsabilità di assicurarsi che il comportamento della risorsa sia corretto, quindi è necessario testarne le funzionalità manualmente o, meglio ancora, scrivere codice di automazione dei test. Questo elenco di controllo contiene gli elementi che è importante testare e/o che vengono spesso dimenticati. Ci sono molti test, principalmente funzionali, specifici della risorsa da testare e che non sono menzionati in questo articolo. Non dimenticarsi dei test case negativi. Questi rappresenteranno probabilmente la parte più onerosa a livello di tempo dei test della risorsa. 
## Procedura consigliata: il modulo della risorsa contiene una cartella Test con lo script ResourceDesignerTests.ps1 ##
È buona norma creare una cartella "Test" all'interno del modulo della risorsa, creare il file ResourceDesignerTests.ps1 e aggiungere i test con **Test-xDscResource** e **Test-xDscSchema** per tutte le risorse nel modulo specificato. In questo modo è possibile convalidare rapidamente gli schemi di tutte le risorse da moduli specifici ed eseguire test di integrità prima della pubblicazione.
Per xRemoteFile, il file ResourceTests.ps1 potrebbe essere semplice come questo:
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof 
```
**Procedura consigliata: la cartella delle risorse contiene lo script di progettazione delle risorse per la generazione dello schema** Ogni risorsa deve contenere uno script di progettazione delle risorse per la generazione di uno schema MOF della risorsa. Questo file deve essere inserito in <ResourceName>\ResourceDesignerScripts e denominato Generate<ResourceName>Schema.ps1 Per la risorsa xRemoteFile il file è denominato GenerateXRemoteFileSchema.ps1 e contiene:
```powershell 
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.' 
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile 
```
22  Procedura consigliata: la risorsa supporta -whatif. Se la risorsa esegue operazioni "pericolose", è consigliabile implementare la funzionalità -whatif. Verificare poi che l'output di whatif descriva correttamente le operazioni che verrebbero eseguite se il comando venisse eseguito senza l'opzione whatif.
Verificare anche che le operazioni non vengono eseguite, ovvero non vengano apportate modifiche allo stato del nodo, quando è presente l'opzione -whatif. Si supponga, ad esempio, di dover eseguire il test della risorsa File. Quella che segue è una configurazione semplice che crea il file "test.txt" con il contenuto "test":
```powershell
configuration config
{
    node localhost 
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config 
```
Se si compila e poi si esegue la configurazione con l'opzione -whatif, l'output indica le esatte conseguenze dell'esecuzione della configurazione. La configurazione stessa non viene però eseguita e il file test.txt non viene creato.
```powershell 
Start-DscConfiguration -path .\config -ComputerName localhost -wait -verbose -whatif
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

Questo conclude l'elenco di controllo. Tenere presente che questo elenco non è esaustivo, ma tiene conto di molti importanti problemi riscontrati durante la progettazione, lo sviluppo e il test di risorse DSC. L'elenco di controllo è utile per assicurarsi di non dimenticare questi aspetti e viene effettivamente usato da Microsoft durante lo sviluppo di risorse DSC. Gli sviluppatori che hanno elaborato linee guida e procedure consigliate per la scrittura e il test di risorse DSC sono invitati a condividerle.




<!--HONumber=Jun16_HO4-->


