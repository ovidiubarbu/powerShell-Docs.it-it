---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Elenco di controllo per la creazione di risorse
ms.openlocfilehash: 85e0963d46358cd37cb87ea94fe6d1178a4f6a4a
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500620"
---
# <a name="resource-authoring-checklist"></a>Elenco di controllo per la creazione di risorse

Questo elenco di controllo è un elenco di procedure consigliate durante la creazione di una nuova risorsa DSC.

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a>Il modulo della risorsa contiene i file psd1 e schema.mof per ogni risorsa.

Verificare che la risorsa abbia una struttura corretta e contenga tutti i file necessari. Ogni modulo di risorsa deve contenere un file con estensione psd1 e per tutte le risorse non composite deve essere disponibile un file schema.mof.
Le risorse senza schema non verranno elencate da `Get-DscResource` e gli utenti non saranno in grado di usare IntelliSense durante la scrittura di codice in base a tali moduli in ISE. La struttura di directory per la risorsa xRemoteFile, che fa parte del [modulo della risorsa xPSDesiredStateConfiguration](https://github.com/PowerShell/xPSDesiredStateConfiguration), potrebbe avere questo aspetto:

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

## <a name="resource-and-schema-are-correct"></a>La risorsa e lo schema sono corretti

Verificare il file dello schema della risorsa (*. schema.mof). È possibile usare [Progettazione risorse DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) per sviluppare e testare lo schema. Assicurarsi che:

- I tipi di proprietà siano corretti (ad esempio, non usare il tipo String per proprietà che accettano valori numerici, ma usare invece UInt32 o altri tipi numerici)
- Gli attributi delle proprietà siano specificati correttamente, ad esempio [key], [required], [write], [read]
- Almeno un parametro dello schema deve essere contrassegnato come [key]
- La proprietà [read] non può coesistere con [required], [key] o [write]
- Se vengono specificati più qualificatori ad eccezione di [read], [key] ha la precedenza
- Se vengono specificati [write] e [required], [required] ha la precedenza
- Il qualificatore ValueMap è specificato dove appropriato. Esempio:

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- Il nome descrittivo è specificato ed è conforme alle convenzioni di denominazione DSC

  Esempio: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`

- Ogni campo ha una descrizione significativa. L'archivio GitHub di PowerShell include esempi utili, ad esempio [.schema.mof per xRemoteFile](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/DSCResources/DSC_xRemoteFile/DSC_xRemoteFile.schema.mof)

È inoltre consigliabile usare i cmdlet **Test-xDscResource** e **Test-xDscSchema** da [Progettazione risorse DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) per la verifica automatica della risorsa e dello schema:

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

Ad esempio:

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a>La risorsa viene caricata senza errori

Controllare se il modulo della risorse può essere caricato correttamente. È possibile farlo manualmente, eseguendo `Import-Module <resource_module> -force` e verificando che non si siano verificati errori oppure creando un'automazione dei test. In quest'ultimo caso, è possibile usare questa struttura nel test case:

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw "Module was not imported correctly. Errors returned: $error"
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a>La risorsa è idempotente in caso positivo

Una delle caratteristiche fondamentali delle risorse DSC è l'idempotenza. Ciò significa che l'applicazione di una configurazione DSC che include più volte la risorsa specifica darà sempre lo stesso risultato. Ad esempio, se si crea una configurazione che contiene la risorsa File seguente:

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

Dopo la prima applicazione, il file test.txt dovrebbe comparire nella cartella `C:\test`. Le esecuzioni successive della stessa configurazione, tuttavia, non dovrebbero modificare lo stato del computer (ad esempio, non dovrebbe essere creata alcuna copia del file `test.txt`). Per assicurarsi che una risorsa sia idempotente, è possibile chiamare ripetutamente `Set-TargetResource` quando si esegue un test diretto della risorsa oppure chiamare più volte `Start-DscConfiguration` quando si esegue un test end-to-end. Il risultato sarà lo stesso dopo ogni esecuzione.

## <a name="test-user-modification-scenario"></a>Scenario di modifica dell'utente test

È possibile verificare se `Set-TargetResource` e `Test-TargetResource` funzionano correttamente modificando lo stato del computer e quindi eseguendo nuovamente DSC. Ecco i passaggi necessari per eseguire questo test:

1. Iniziare con la risorsa che non si trova nello stato desiderato
2. Eseguire la configurazione della risorsa
3. Verificare `Test-DscConfiguration` restituisce true
4. Modificare lo stato dell'elemento configurato
5. Verificare `Test-DscConfiguration` restituisce false

Ecco un esempio più concreto con la risorsa Registro di sistema:

1. Iniziare con una chiave del Registro di sistema che non si trova nello stato desiderato
2. Eseguire `Start-DscConfiguration` con una configurazione per mettere la risorsa nello stato desiderato e verificare che il test venga superato.
3. Eseguire `Test-DscConfiguration` e verificare che restituisca true
4. Modificare il valore della chiave in modo che non si trovi più nello stato desiderato
5. Eseguire `Test-DscConfiguration` e verificare che restituisca false
6. La funzionalità `Get-TargetResource` è stata verificata con `Get-DscConfiguration`

`Get-TargetResource` dovrebbe restituire i dettagli dello stato corrente della risorsa. Assicurarsi di testarlo chiamando `Get-DscConfiguration` dopo aver applicato la configurazione e verificando che l'output rispecchi correttamente lo stato corrente del computer. È importante eseguire il test separatamente, poiché eventuali problemi in questa area non verranno visualizzati durante la chiamata di `Start-DscConfiguration`.

## <a name="call-getsettest-targetresource-functions-directly"></a>Chiamare direttamente le funzioni **Get/Set/Test-TargetResource**

Assicurarsi di testare le funzioni **Get/Set/Test-TargetResource** implementate nella risorsa chiamandole direttamente e verificando che funzionino come previsto.

## <a name="verify-end-to-end-using-start-dscconfiguration"></a>Eseguire un test end-to-end tramite **Start-DscConfiguration**

Testare le funzioni **Get/Set/Test-TargetResource** tramite chiamata diretta è importante, ma in questo modo non verranno individuati tutti i problemi. È consigliabile concentrare una parte significativa delle attività di test sull'uso di `Start-DscConfiguration` o del server di pull. Questo è in effetti il modo in cui gli utenti useranno la risorsa, quindi non sottovalutare l'importanza di questo tipo di test. Possibili tipi di problemi:

- Possibili comportamenti diversi delle credenziali e/o della sessione perché l'agente DSC viene eseguito come servizio. Assicurarsi di sottoporre qualsiasi funzionalità a test end-to-end.
- Gli errori restituiti da `Start-DscConfiguration` potrebbero essere diversi da quelli visualizzati quando si chiama la funzione `Set-TargetResource` direttamente.

## <a name="test-compatibility-on-all-dsc-supported-platforms"></a>Testare la compatibilità su tutte le piattaforme supportate da DSC

La risorsa dovrebbero funzionare in tutte le piattaforme supportate da DSC (Windows Server 2008 R2 e versioni successive). Installare la versione più recente di WMF (Windows Management Framework) nel sistema operativo per ottenere la versione più recente di DSC. Se la risorsa non funziona in alcune di queste piattaforme in base alla sua struttura di progettazione, verrà restituito un messaggio di errore specifico. Assicurarsi anche che la risorsa controlli che i cmdlet chiamati siano presenti nel computer specifico. In Windows Server 2012 sono stati aggiunti numerosi cmdlet nuovi, non disponibili in Windows Server 2008 R2 anche con WMF installato.

## <a name="verify-on-windows-client-if-applicable"></a>Verifiche nel client Windows (se applicabile)

Una mancanza molto comune dei test è verificare la risorsa solo nelle versioni server di Windows. Molte risorse sono progettate anche per il funzionamento su SKU client, quindi se questo è il caso, è importante non dimenticare di eseguire i test anche su queste piattaforme.

## <a name="get-dscresource-lists-the-resource"></a>Get-DSCResource elenca la risorsa

Dopo aver distribuito il modulo, la chiamata di `Get-DscResource` dovrebbe elencare nei risultati anche la risorsa in questione. Se non è possibile trovare la risorsa nell'elenco, verificare che esista il file schema.mof per la risorsa.

## <a name="resource-module-contains-examples"></a>Il modulo della risorsa contiene esempi

Creazione di esempi di qualità che consentono ad altri utenti di capirne l'uso. Ciò è fondamentale, soprattutto perché molti utenti usano il codice di esempio come documentazione.

- In primo luogo, è necessario determinare gli esempi da includere nel modulo. È opportuno offrire come minimo esempi per i casi d'uso più importanti per la risorsa:
- Se il modulo contiene varie risorse che devono essere usate insieme per uno scenario end-to-end, l'esempio end-to-end di base dovrebbe essere idealmente il primo.
- Gli esempi iniziali dovrebbero essere molto semplici e illustrare come iniziare a usare le risorse in piccoli blocchi gestibili, ad esempio la creazione di un nuovo VHD
- Gli esempi successivi dovrebbero continuare e ampliare quelli iniziali (ad esempio, creare una VM da un VHD, rimuovere una VM o modificare una VM) e illustrare le funzionalità avanzate (ad esempio, la creazione di una VM con memoria dinamica)
- Le configurazioni di esempio devono essere parametrizzate (tutti i valori devono essere passati come parametri alla configurazione, senza valori hardcoded):

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

- È buona norma includere un esempio di come chiamare la configurazione con i valori effettivi alla fine dello script di esempio, impostandolo come commento. Ad esempio, nella configurazione precedente non è così ovvio che il modo migliore per specificare UserAgent è:

  `UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In questo caso un commento può chiarire l'esecuzione della configurazione voluta:

  ```powershell
  <#
  Sample use (parameter values need to be changed according to your scenario):

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
  -userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
  #>
  ```

- Per ogni esempio, scrivere una breve descrizione per illustrarne le funzioni e indicare il significato dei parametri.
- Assicurarsi che siano disponibili esempi per la maggior parte degli scenari importanti per la risorsa e se non manca nulla, verificare che funzionino tutti e mettano il computer nello stato desiderato.

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a>I messaggi di errore sono facili da comprendere e aiutano gli utenti a risolvere i problemi

Per essere utili, i messaggi di errore devono essere:

- Presenti: il problema principale con i messaggi di errore è che spesso non esistono, quindi assicurarsi che ci siano.
- Facile da capire: messaggi leggibili evitando oscuri codici di errore
- Precisi: descrivere esattamente il problema
- Costruttivi: suggerire come risolvere il problema
- Cortesi: non incolpare l'utente o farlo sentire a disagio

Assicurarsi di verificare gli errori negli scenari end-to-end (con `Start-DscConfiguration`), in quanto potrebbero essere diversi da quelli restituiti quando si eseguono direttamente le funzioni della risorsa.

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a>I messaggi dei log sono facili da capire e informativi (inclusi i log -verbose, -debug ed ETW)

Assicurarsi che i log generati dalla risorsa siano facili da comprendere e offrano informazioni utili all'utente.
Le risorse dovrebbero offrire come output tutte le informazioni che potrebbero essere utili all'utente, ma non sempre la disponibilità di più log è un vantaggio. È consigliabile evitare la ridondanza e output di dati senza valore aggiunto, in modo da non costringere gli utenti a scorrere centinaia di voci di log per trovare quello che cercano. Naturalmente, anche l'assenza di log non è una soluzione accettabile per questo problema.

Durante il test, è necessario analizzare anche i log dettagliati e di debug (eseguendo `Start-DscConfiguration` con le opzioni `–Verbose` e `–Debug` in modo appropriato), oltre ai log ETW. Per visualizzare i log ETW di DSC, passare al Visualizzatore eventi e aprire la cartella seguente: Applicazioni e servizi - Microsoft - Windows - Desired State Configuration. Per impostazione predefinita è abilitato il canale operativo, ma assicurarsi di abilitare i canali analitico e debug prima di eseguire la configurazione. Per abilitare i canali Analitico/Debug, è possibile eseguire lo script riportato di seguito:

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

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a>L'implementazione della risorsa non contiene percorsi hardcoded

Assicurarsi che non siano presenti percorsi hardcoded nell'implementazione della risorsa, in particolare se presuppongono una lingua specifica (en-us) o quando possono essere usate variabili di sistema. Se la risorsa deve accedere a percorsi specifici, usare le variabili di ambiente invece di percorsi hardcoded, perché potrebbero variare in altri computer.

Esempio:

Anziché:

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

È possibile scrivere:

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a>L'implementazione della risorsa non contiene informazioni sull'utente

Assicurarsi che nel codice non siano presenti nomi di posta elettronica, informazioni su account o nomi di persone.

## <a name="resource-was-tested-with-validinvalid-credentials"></a>La risorsa è stata testata con credenziali valide e non valide

Se la risorsa accetta credenziali come parametro:

- Verificare che la risorsa funzioni quando l'account di sistema locale (o l'account computer per risorse remote) non ha accesso.
- Verificare che la risorsa funzioni quando vengono specificate credenziali per Get, Set e Test
- Se la risorsa accede a condivisioni, testare tutte le varianti che bisogna supportare, ad esempio:
  - Condivisioni Windows standard.
  - Condivisioni DFS.
  - Condivisioni SAMBA (se si vuole supportare Linux).

## <a name="resource-does-not-require-interactive-input"></a>La risorsa non richiede input interattivo

Le funzioni **Get/Set/Test-TargetResource** dovrebbero essere eseguite automaticamente e non devono attendere l'input dell'utente in alcuna fase dell'esecuzione. Ad esempio, è consigliabile non usare `Get-Credential` all'interno di queste funzioni. Se è necessario fornire l'input dell'utente, è consigliabile passarlo alla configurazione come parametro durante la fase di compilazione.

## <a name="resource-functionality-was-thoroughly-tested"></a>La funzionalità della risorsa è stata accuratamente testata

Questo elenco di controllo contiene gli elementi che è importante testare e/o che vengono spesso dimenticati. Ci sono molti test, principalmente funzionali, specifici della risorsa da testare e che non sono menzionati in questo articolo. Non dimenticarsi dei test case negativi.

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a>Procedura consigliata: il modulo della risorsa contiene una cartella Test con lo script ResourceDesignerTests.ps1

È buona norma creare una cartella "Test" all'interno del modulo della risorsa, creare il file `ResourceDesignerTests.ps1` e aggiungere i test con **Test-xDscResource** e **Test-xDscSchema** per tutte le risorse nel modulo specificato. In questo modo è possibile convalidare rapidamente gli schemi di tutte le risorse da moduli specifici ed eseguire test di integrità prima della pubblicazione. Per xRemoteFile, `ResourceTests.ps1` potrebbe essere semplice come:

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a>Procedura consigliata: la cartella della risorsa contiene uno script di progettazione della risorsa per la generazione dello schema

Ogni risorsa dovrebbe contenere uno script di progettazione della risorsa che genera uno schema MOF della risorsa. Questo file deve essere inserito `<ResourceName>\ResourceDesignerScripts` e denominato `<ResourceName>Schema.ps1`. Per la risorsa xRemoteFile questo file deve essere denominato `GenerateXRemoteFileSchema.ps1` e contenere:

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

## <a name="best-practice-resource-supports--whatif"></a>Procedura consigliata: la risorsa supporta - WhatIf

Se la risorsa esegue operazioni "pericolose", è consigliabile implementare la funzionalità `-WhatIf`. Verificare poi che l'output di `-WhatIf` descriva correttamente le operazioni che verrebbero eseguite se il comando venisse eseguito senza l'opzione `-WhatIf`. Verificare anche che le operazioni non vengano eseguite, ovvero non vengano apportate modifiche allo stato del nodo, quando è presente l'opzione `–WhatIf`. Si supponga, ad esempio, di dover eseguire il test della risorsa File. Quella che segue è una configurazione semplice che crea il file `test.txt` con il contenuto "test":

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

Se si compila e poi si esegue la configurazione con l'opzione `-WhatIf`, l'output indica le esatte conseguenze dell'esecuzione della configurazione. La configurazione stessa non viene però eseguita e il file `test.txt` non viene creato.

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```Output
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

Questo elenco non è esaustivo, ma tiene conto di molti importanti problemi riscontrati durante la progettazione, lo sviluppo e il test di risorse DSC.
