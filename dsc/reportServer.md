# Uso di un server di report DSC

> Si applica a: Windows PowerShell 5.0

> **Nota:** il server di report descritto in questo argomento non è disponibile in PowerShell 4.0. Per la creazione di report in PowerShell 4.0, vedere l'argomento relativo all'uso di un server di conformità DSC.

È possibile configurare Gestione configurazione locale in un nodo per inviare report sullo stato della configurazione a un server di pull, su cui è quindi possibile eseguire query per recuperare i dati. Ogni volta che il nodo controlla e applica
una configurazione, invia un report al server di report. Questi report vengono archiviati in un database nel server e possono essere recuperati chiamando il servizio Web di gestione dei report. Ogni report contiene
informazioni come le configurazioni applicate e l'esito dell'applicazione, le risorse usate, eventuali errori generati e le ore di inizio e fine.

## Configurazione di un nodo per l'invio di report

Per richiedere a un nodo di inviare report a un server, è possibile usare un blocco **ReportServerWeb** nella configurazione di Gestione configurazione locale del nodo (per informazioni sulla configurazione di Gestione configurazione locale,
 vedere [Configurazione di Gestione configurazione locale](metaConfig.md)). Il server a cui il nodo invia i report deve essere configurato come server di pull Web (non è possibile inviare report
 a una condivisione SMB). Per informazioni sulla configurazione di un server di pull, vedere [Configurazione di un server di pull Web DSC](pullServer.md). Il server di report può corrispondere al servizio da cui
 il nodo effettua il pull delle configurazioni e ottiene le risorse oppure può essere un servizio diverso.
 
 Nel blocco **ReportServerWeb** specificare l'URL del servizio pull
 e una chiave di registrazione nota al server.
 
  La configurazione seguente consente di impostare un nodo per il pull delle configurazioni da un servizio e l'invio di report
 a un servizio in un server diverso. 
 
```powershell
[DSCLocalConfigurationManager()]
configuration ReportClientConfig
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
            ServerURL          = 'https://CONTOSO-PULL:8080/PSDSCPullServer.svc'
            RegistrationKey    = 'bbb9778f-43f2-47de-b61e-a0daff474c6d'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL               = 'http://CONTOSO-REPORT:8080/PSDSCReportServer.svc'
            RegistrationKey         = 'ba39daaa-96c5-4f2f-9149-f95c46460faa'
            AllowUnsecureConnection = $true
        }
    }
}
PullClientConfigID
```

## Recupero dei dati dei report

I report inviati al server di pull vengono immessi in un database nel server. I report sono disponibili tramite chiamate al servizio Web. Per recuperare i report per un nodo specifico, 
inviare una richiesta HTTP al servizio Web di report nel formato seguente:
`http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentID = MyNodeAgentId)/Reports` 
dove `MyNodeAgentId` è il valore di AgentId del nodo per cui ottenere i report. È possibile ottenere il valore di AgentID per un nodo chiamando [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx)
in tale nodo.

I report vengono restituiti come matrice di oggetti JSON.

Lo script seguente restituisce i report per il nodo in cui viene eseguito:

```powershell
function GetReport
{
    param($AgentId = "$((glcm).AgentId)", $serviceURL = "http://CONTOSO-REPORT:8080/PSDSCReportServer.svc")
    $requestUri = "$serviceURL/Nodes(AgentId= '$AgentId')/Reports"
    $request = Invoke-WebRequest -Uri $requestUri  -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" `
               -UseBasicParsing -Headers @{Accept = "application/json";ProtocolVersion = "2.0"} `
               -ErrorAction SilentlyContinue -ErrorVariable ev
    $object = ConvertFrom-Json $request.content
    return $object.value
}
```
    
## Visualizzazione dei dati dei report

Se si imposta una variabile sul risultato della funzione **GetReport**, è possibile visualizzare i singoli campi in un elemento della matrice restituita:

```powershell
$reports = GetReport
$reports[1]

JobId                : 71515ae8-7294-40a3-8137-fc85bf4b678f
OperationType        : Consistency
RefreshMode          : 
Status               : 
ReportFormatVersion  : 1.0
ConfigurationVersion : 2.0.0
StartTime            : 02/08/2016 01:28:54
EndTime              : 02/08/2016 01:28:57
RebootRequested      : False
Errors               : {}
StatusData           : {{"NumberOfResources":"2","Locale":"en-US","ResourcesInDesiredState":[{"ResourceId":"[WindowsFeature]MyFeatureInstance","SourceI
                       nfo":"C:\\ReportTest\\ClientConfig.ps1::4::9::WindowsFeature","ModuleName":"PsDesiredStateConfiguration","ModuleVersion":"1.0","
                       ConfigurationName":"ClientConfig","ResourceName":"WindowsFeature"},{"ResourceId":"[WindowsFeature]My2ndFeatureInstance","SourceI
                       nfo":"C:\\ReportTest\\ClientConfig.ps1::8::9::WindowsFeature","ModuleName":"PsDesiredStateConfiguration","ModuleVersion":"1.0","
                       ConfigurationName":"ClientConfig","ResourceName":"WindowsFeature"}]}}
```

Si noti che il campo **StatusData** è un oggetto con tre proprietà: **NumberOfResources**, **Locale** e **ResourcesInDesiredState**. La proprietà **ResourcesInDesiredState**
è una matrice di oggetti ognuno dei quali ha diverse proprietà. Lo script seguente accetta un singolo report come parametro, scorre la matrice **ResourcesInDesiredState**
e quindi scrive nella console:
 
```powershell
function GetStatusData
{
    param ($Report)
    $statusData = $Report.StatusData | ConvertFrom-Json

    $Resources = $statusData.ResourcesInDesiredState

    Foreach ($Resource in $Resources)
    {
        Write-Host 'ResourceId: ' $Resource.ResourceId
        Write-Host 'SourceInfo: ' $Resource.SourceInfo
        Write-Host 'ModuleName: ' $Resource.ModuleName
        Write-Host 'ModuleVersion: ' $Resource.ModuleVersion
        Write-Host 'ConfigurationName: ' $Resource.ConfigurationName
        Write-Host 'ResourceName: ' $Resource.ResourceName
        Write-Host
    }
}
```

Ecco un esempio di output dopo la chiamata della funzione **GetStatusData**:

```powershell
GetStatusData -Report $report[1]

ResourceId:  [WindowsFeature]MyFeatureInstance
SourceInfo:  C:\ReportTest\ClientConfig.ps1::4::9::WindowsFeature
ModuleName:  PsDesiredStateConfiguration
ModuleVersion:  1.0
ConfigurationName:  ClientConfig
ResourceName:  WindowsFeature

ResourceId:  [WindowsFeature]My2ndFeatureInstance
SourceInfo:  C:\ReportTest\ClientConfig.ps1::8::9::WindowsFeature
ModuleName:  PsDesiredStateConfiguration
ModuleVersion:  1.0
ConfigurationName:  ClientConfig
ResourceName:  WindowsFeature
```

Si noti che questi esempi servono solo per dare un'idea di cosa è possibile fare con i dati dei report. Per informazioni introduttive sull'uso di JSON in PowerShell, vedere il post di blog
[Playing with JSON and PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).

## Vedere anche
>[Configurazione di Gestione configurazione locale](metaConfig.md)
>[Configurazione di un server di pull Web DSC](pullServer.md)
>[Configurazione di un client di pull usando nomi di configurazione](pullClientConfigNames.md)
<!--HONumber=Feb16_HO4-->
