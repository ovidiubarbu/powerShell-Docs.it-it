---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Configurazione di un client di pull usando nomi di configurazione
ms.openlocfilehash: dd0526b118b404854b1e9b445ca50bdaafdd01c7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="setting-up-a-pull-client-using-configuration-names"></a>Configurazione di un client di pull usando nomi di configurazione

> Si applica a: Windows PowerShell 5.0

Per ogni nodo di destinazione è necessario specificare che venga usata la modalità pull e fornire l'URL per contattare il server di pull da cui ottenere le configurazioni.
A tale scopo, è necessario configurare Gestione configurazione locale con le informazioni richieste.
Per configurare Gestione configurazione locale, è necessario creare un tipo speciale di configurazione usando l'attributo **DSCLocalConfigurationManager**.
Per altre informazioni sulla configurazione di Gestione configurazione locale, vedere [Configurazione di Gestione configurazione locale](metaConfig.md).

> **Nota**: questo argomento si applica a PowerShell 5.0.
Per informazioni sulla configurazione di un client di pull in PowerShell 4.0, vedere [Configurazione di un client di pull usando un ID configurazione in PowerShell 4.0](pullClientConfigID4.md).

Lo script seguente configura Gestione configurazione locale per il pull delle configurazioni da un server denominato "CONTOSO-PullSrv":

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
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
PullClientConfigNames
```

Nello script il blocco **ConfigurationRepositoryWeb** definisce il server di pull.
La proprietà **ServerURL** specifica l'endpoint per il server di pull.

La proprietà **RegistrationKey** è una chiave condivisa tra tutti i nodi client per un server di pull e il server di pull stesso.
Lo stesso valore viene archiviato in un file nel server di pull.

La proprietà **ConfigurationNames** è una matrice che specifica i nomi delle configurazioni per il nodo client.
Nel server di pull il file MOF di configurazione per il nodo client deve essere denominato *ConfigurationNames*.mof, dove *ConfigurationNames* corrisponde al valore della proprietà **ConfigurationNames** impostata in questa metaconfigurazione.

>**Nota:** se si specifica più di un valore in **ConfigurationNames**, è necessario specificare nella configurazione anche i blocchi di **PartialConfiguration**.
Per informazioni sulle configurazioni parziali, vedere [configurazioni parziali di PowerShell DSC](partialConfigs.md).

Dopo essere stato eseguito, questo script crea una nuova cartella di output denominata **PullClientConfigNames** e inserisce in questa cartella un file MOF di metaconfigurazione.
In questo caso, il file MOF di metaconfigurazione sarà denominato `localhost.meta.mof`.

Per applicare la configurazione, chiamare il cmdlet **Set-DscLocalConfigurationManager**, con il valore di **Path** impostato sul percorso del file MOF di metaconfigurazione.

```powershell
Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigNames –Verbose.
```

> **Nota**: le chiavi di registrazione funzionano solo con i server di pull Web.
Con un server di pull SMB è necessario usare **ConfigurationID**.
Per informazioni sulla configurazione di un server di pull usando **ConfigurationID**, vedere [Configurazione di un client di pull usando un ID configurazione](PullClientConfigNames.md).

## <a name="resource-and-report-servers"></a>Server delle risorse e di report

Se si specifica solo un blocco **ConfigurationRepositoryWeb** o **ConfigurationRepositoryShare** nella configurazione di Gestione configurazione locale, come nell'esempio precedente, il client di pull eseguirà il pull delle risorse dal server specificato, ma non invierà report al server.
È possibile usare un singolo server di pull per le configurazioni, le risorse e i report, ma è necessario creare un blocco **ReportRepositoryWeb** per configurare la creazione di report.
Nell'esempio seguente viene illustrata una metaconfigurazione che configura un client per il pull di configurazioni e risorse e per l'invio di dati di report a un singolo server di pull.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
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
PullClientConfigNames
```

È anche possibile specificare server di pull diversi per le risorse e i report.
Per specificare un server delle risorse, usare un blocco **ResourceRepositoryWeb** (per un server di pull Web) o **ResourceRepositoryShare** (per un server di pull SMB).
Per specificare un server di report, usare un blocco **ReportRepositoryWeb**.
Un server di report non può essere un server SMB.
La metaconfigurazione seguente configura un client di pull in modo da ottenere le configurazioni da **CONTOSO-PullSrv** e le risorse da **CONTOSO-ResourceSrv** e inviare i report sullo stato a **CONTOSO-ReportSrv**:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
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
            RegistrationKey = '6b392c6a-818c-4b24-bf38-47124f1e2f14'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a>Vedere anche

* [Configurazione di un client di pull usando un ID configurazione](PullClientConfigNames.md)
* [Configurazione di un server di pull Web DSC](pullServer.md)