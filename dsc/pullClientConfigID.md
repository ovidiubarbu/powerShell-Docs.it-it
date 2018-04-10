---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Configurazione di un client di pull usando un ID configurazione
ms.openlocfilehash: 93e533fd4e729e1af0124ad69ca7e384e1cb3aa4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id"></a>Configurazione di un client di pull usando un ID configurazione

> Si applica a: Windows PowerShell 5.0

Per ogni nodo di destinazione è necessario specificare che venga usata la modalità pull e fornire l'URL per contattare il server di pull da cui ottenere le configurazioni. A tale scopo, è necessario configurare Gestione configurazione locale con le informazioni richieste. Per configurare Gestione configurazione locale, è necessario creare un tipo speciale di configurazione usando l'attributo **DSCLocalConfigurationManager**. Per altre informazioni sulla configurazione di Gestione configurazione locale, vedere [Configurazione di Gestione configurazione locale](metaConfig.md).

> **Nota**: questo argomento si applica a PowerShell 5.0. Per informazioni sulla configurazione di un client di pull in PowerShell 4.0, vedere [Configurazione di un client di pull usando un ID configurazione in PowerShell 4.0](pullClientConfigID4.md).

Lo script seguente configura Gestione configurazione locale per il pull delle configurazioni da un server denominato "CONTOSO-PullSrv".

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

Nello script il blocco **ConfigurationRepositoryWeb** definisce il server di pull. **ServerURL** rappresenta l'URL del server.

Dopo essere stato eseguito, questo script crea una nuova cartella di output denominata **PullClientConfigID** e inserisce in questa cartella un file MOF di metaconfigurazione. In questo caso, il file MOF di metaconfigurazione sarà denominato `localhost.meta.mof`.

Per applicare la configurazione, chiamare il cmdlet **Set-DscLocalConfigurationManager**, con il valore di **Path** impostato sul percorso del file MOF di metaconfigurazione. Ad esempio: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`

## <a name="configuration-id"></a>ID configurazione

Lo script imposta la proprietà **ConfigurationID** di Gestione configurazione locale su un GUID creato in precedenza per questo scopo (è possibile creare un GUID usando il cmdlet **New-Guid**). Il valore di **ConfigurationID** viene usato da Gestione configurazione locale per trovare la configurazione appropriata nel server di pull. Il file MOF di configurazione nel server di pull deve essere denominato _ConfigurationID.mof_, dove _ConfigurationID_ è il valore della proprietà **ConfigurationID** di Gestione configurazione locale del nodo di destinazione.

## <a name="smb-pull-server"></a>Server di pull SMB

Per configurare un client per il pull delle configurazioni da un server SMB, usare un blocco **ConfigurationRepositoryShare**. In un blocco **ConfigurationRepositoryShare** specificare il percorso del server impostando la proprietà **SourcePath**. La metaconfigurazione seguente consente di configurare il nodo di destinazione per il pull da un server di pull SMB denominato **SMBPullServer**.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\PullSource'

        }
    }
}
PullClientConfigID
```

## <a name="resource-and-report-servers"></a>Server delle risorse e di report

Se si specifica solo un blocco **ConfigurationRepositoryWeb** o **ConfigurationRepositoryShare** nella configurazione di Gestione configurazione locale, come nell'esempio precedente, il client di pull eseguirà il pull delle risorse dal server specificato, ma non invierà report al server. È possibile usare un singolo server di pull per le configurazioni, le risorse e i report, ma è necessario creare un blocco **ReportRepositoryWeb** per configurare la creazione di report.

Nell'esempio seguente viene illustrata una metaconfigurazione che configura un client per il pull di configurazioni e risorse e per l'invio di dati di report a un singolo server di pull.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }


        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

È anche possibile specificare server di pull diversi per le risorse e i report. Per specificare un server delle risorse, usare un blocco **ResourceRepositoryWeb** (per un server di pull Web) o **ResourceRepositoryShare** (per un server di pull SMB).
Per specificare un server di report, usare un blocco **ReportRepositoryWeb**. Un server di report non può essere un server SMB.
La metaconfigurazione seguente configura un client di pull in modo da ottenere le configurazioni da **CONTOSO-PullSrv** e le risorse da **CONTOSO-ResourceSrv** e inviare i report sullo stato a **CONTOSO-ReportSrv**:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

## <a name="see-also"></a>Vedere anche

* [Configurazione di un client di pull con nomi di configurazione](pullClientConfigNames.md)