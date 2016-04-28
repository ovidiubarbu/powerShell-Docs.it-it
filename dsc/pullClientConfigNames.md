# Configurazione di un client di pull usando nomi di configurazione

> Si applica a: Windows PowerShell 5.0

Per ogni nodo di destinazione è necessario specificare che venga usata la modalità pull e fornire l'URL per contattare il server di pull da cui ottenere le configurazioni. A tale scopo, è necessario configurare Gestione configurazione locale con le informazioni richieste. Per configurare Gestione configurazione locale, creare un tipo speciale di configurazione usando l'attributo **DSCLocalConfigurationManager**. Per altre informazioni sulla configurazione di Gestione configurazione locale, vedere [Configurazione di Gestione configurazione locale](metaConfig.md).

> **Nota**: questo argomento si applica a PowerShell 5.0. Per informazioni sulla configurazione di un client di pull in PowerShell 4.0, vedere [Configurazione di un client di pull usando un ID configurazione in PowerShell 4.0](pullClientConfigID4.md).

Lo script seguente configura Gestione configurazione locale per il pull delle configurazioni da un server denominato "CONTOSO-PullSrv":

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
            
        }      
    }
}
PullClientConfigID
```

Nello script il blocco **ConfigurationRepositoryWeb** definisce il server di pull. La proprietà **ServerURL** specifica l'endpoint per il server di pull.

La proprietà **RegistrationKey** è una chiave condivisa tra tutti i nodi client per un server di pull e il server di pull stesso. Lo stesso valore viene archiviato in un file nel server di pull. La proprietà **ConfigurationNames** specifica il nome della configurazione per il nodo client. Nel server di pull il file MOF di configurazione per il nodo client deve essere denominato *ConfigurationNames*.mof, dove *ConfigurationNames* corrisponde al valore della proprietà **ConfigurationNames** impostata in questa metaconfigurazione.

Dopo essere stato eseguito, questo script crea una nuova cartella di output denominata **PullClientConfigID** e inserisce in questa cartella un file MOF di metaconfigurazione. In questo caso, il file MOF di metaconfigurazione sarà denominato `localhost.meta.mof`.

Per applicare la configurazione, chiamare il cmdlet **Set-DscLocalConfigurationManager** con il valore **Path** impostato sul percorso del file MOF di metaconfigurazione. Ad esempio: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`

> **Nota**: le chiavi di registrazione funzionano solo con i server di pull Web. Con un server di pull SMB è necessario usare **ConfigurationID**. Per informazioni sulla configurazione di un server di pull usando **ConfigurationID**, vedere [Configurazione di un client di pull usando un ID configurazione](pullClientConfigID.md).

## Server delle risorse e di report

Se si specifica solo un blocco **ConfigurationRepositoryWeb** o **ConfigurationRepositoryShare** nella configurazione di Gestione configurazione locale (come nell'esempio precedente), il client di pull effettuerà il pull 
delle risorse dal server specificato, ma non invierà report a tale server. È possibile usare un singolo server di pull per le configurazioni, le risorse e i report, ma è necessario creare un blocco 
**ReportRepositoryWeb** per configurare la gestione dei report. Nell'esempio seguente viene illustrata una metaconfigurazione che configura un client per il pull di configurazioni e risorse e per l'invio dei dati di report a un singolo
server di pull.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
        
        

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```


È anche possibile specificare server di pull diversi per le risorse e i report. Per specificare un server delle risorse, usare un blocco **ResourceRepositoryWeb** (per un server di pull Web) o 
**ResourceRepositoryShare** (per un server di pull SMB).
Per specificare un server di report, usare un blocco **ReportRepositoryWeb**. Un server di report non può essere un server SMB.
La metaconfigurazione seguente configura un client di pull in modo da ottenere le configurazioni da **CONTOSO-PullSrv** e le risorse da **CONTOSO-ResourceSrv** e inviare i report sullo stato a **CONTOSO-ReportSrv**.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
        
        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-ResourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-ReportSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

## Vedere anche

* [Configurazione di un client di pull usando un ID configurazione](pullClientConfigID.md)
* [Configurazione di un server di pull Web DSC](pullServer.md)


<!--HONumber=Mar16_HO4-->


