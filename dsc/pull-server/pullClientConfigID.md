---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Configurare un Client di Pull usando un ID configurazione in PowerShell 5.0 e versioni successive
ms.openlocfilehash: 8d8cf478f9127e1b7005d1b9e832e84b11612c9c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680872"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>Configurare un Client di Pull usando un ID configurazione in PowerShell 5.0 e versioni successive

> Si applica a: Windows PowerShell 5.0

> [!IMPORTANT]
> Il server di pull (funzionalità di Windows *servizio DSC*) è un componente supportato di Windows Server, tuttavia non si prevede di offrire nuove caratteristiche o funzionalità. È consigliabile avviare la transizione dei client gestiti ad [Automation DSC per Azure](/azure/automation/automation-dsc-getting-started) (include funzionalità superiori al server di pull in Windows Server) o a una delle soluzioni della community riportate [qui](pullserver.md#community-solutions-for-pull-service).

Prima di configurare un client di pull, è necessario configurare un server di pull. Anche se quest'ordine non sia obbligatorio, consente la risoluzione dei problemi e consente di assicurarsi che la registrazione è riuscita. Per configurare un server di pull, è possibile usare le guide seguenti:

- [Configurare un server di pull SMB DSC](pullServerSmb.md)
- [Configurare un server di pull HTTP DSC](pullServer.md)

Ogni nodo di destinazione può essere configurato per scaricare le configurazioni, risorse e anche segnalare lo stato. Le sezioni seguenti illustrano come configurare un client di pull con una condivisione SMB o HTTP Server di Pull DSC. Quando Gestione configurazione locale del nodo viene aggiornato, ti contatterà per il percorso configurato per scaricare eventuali configurazioni assegnate. Se tutte le risorse necessarie non sono presenti nel nodo, verrà automaticamente scaricato li dal percorso configurato. Se il nodo è configurato con un [Server di Report](reportServer.md), quindi segnala lo stato dell'operazione.

> **Nota**: Questo argomento si applica a PowerShell 5.0. Per informazioni sulla configurazione di un client di pull in PowerShell 4.0, vedere [Configurazione di un client di pull usando un ID configurazione in PowerShell 4.0](pullClientConfigID4.md).

## <a name="configure-the-pull-client-lcm"></a>Configurare il client di pull Gestione configurazione locale

L'esecuzione di uno degli esempi seguenti viene creata una nuova cartella di output denominata **PullClientConfigID** e inserisce un file MOF di metaconfigurazione esiste. In questo caso, il file MOF di metaconfigurazione sarà denominato `localhost.meta.mof`.

Per applicare la configurazione, chiamare il cmdlet **Set-DscLocalConfigurationManager**, con il valore di **Path** impostato sul percorso del file MOF di metaconfigurazione. Ad esempio:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>ID configurazione

Gli esempi seguenti set il **ConfigurationID** proprietà di Gestione configurazione locale per un **Guid** che fosse stato creato in precedenza per questo scopo. Il valore di **ConfigurationID** viene usato da Gestione configurazione locale per trovare la configurazione appropriata nel server di pull. Il file MOF di configurazione nel server di pull deve essere denominato `ConfigurationID.mof`, dove *ConfigurationID* è il valore della proprietà **ConfigurationID** di Gestione configurazione locale del nodo di destinazione. Per altre informazioni, vedere [pubblicare le configurazioni a un Server di Pull (v4/v5)](publishConfigs.md).

È possibile creare uno casuale **Guid** usando l'esempio sotto, o tramite il [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.

```powershell
[System.Guid]::NewGuid()
```

Per altre informazioni sull'uso **GUID** nell'ambiente in uso, vedere [pianificare GUID](/powershell/dsc/secureserver#guids).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configurare un Client di Pull per scaricare le configurazioni

Ogni client deve essere configurato **Pull** modalità e fornire l'url di server di pull in cui la configurazione viene archiviata. A tale scopo, è necessario configurare Gestione configurazione locale con le informazioni richieste. Per configurare Gestione configurazione locale, è necessario creare un tipo speciale di configurazione usando l'attributo **DSCLocalConfigurationManager**. Per altre informazioni sulla configurazione di Gestione configurazione locale, vedere [Configurazione di Gestione configurazione locale](../managing-nodes/metaConfig.md).

### <a name="http-dsc-pull-server"></a>Server di Pull DSC HTTP

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

Nello script il blocco **ConfigurationRepositoryWeb** definisce il server di pull. Il **ServerUrl** specifica l'url di pull DSC

### <a name="smb-share"></a>SMB Share

Lo script seguente configura Gestione configurazione locale per il pull delle configurazioni da una condivisione SMB `\\SMBPullServer\Pull`.

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
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

Nello script, il **ConfigurationRepositoryShare** blocco definisce il server di pull, in questo caso, è sufficiente una condivisione SMB.

## <a name="set-up-a-pull-client-to-download-resources"></a>Configurare un Client di Pull per scaricare le risorse

Se si specifica solo le **ConfigurationRepositoryWeb** oppure **ConfigurationRepositoryShare** nella configurazione di Gestione configurazione locale (come negli esempi precedenti), il client di pull effettuerà il pull delle risorse dallo stesso percorso recupera le configurazioni. È anche possibile specificare posizioni distinte per le risorse. Per specificare un percorso della risorsa come un server separato, usare il **ResourceRepositoryWeb** blocco. Per specificare un percorso della risorsa come una condivisione SMB, usare il **ResourceRepositoryShare** blocco.

> [!NOTE]
> È possibile combinare **ConfigurationRepositoryWeb** con **ResourceRepositoryShare** oppure **ConfigurationRepositoryShare** con **ResourceRepositoryWeb** . Esempi di questo oggetto non vengono visualizzati sotto.

### <a name="http-dsc-pull-server"></a>Server di Pull DSC HTTP

La metaconfigurazione seguente configura un client di pull per ottenere le configurazioni da **CONTOSO-PullSrv** e le relative risorse dalla **CONTOSO-ResourceSrv**.

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
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>SMB Share

Nell'esempio seguente viene illustrata una metaconfigurazione che configura un client per il pull delle configurazioni da una condivisione SMB `\\SMBPullServer\Configurations`e le risorse da una condivisione SMB `\\SMBPullServer\Resources`.

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
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a>Scarica automaticamente le risorse in modalità Push

A partire da PowerShell 5.0, i client di pull possono scaricare i moduli da una condivisione SMB, anche quando sono configurati per la **Push** modalità. Ciò è particolarmente utile negli scenari in cui non si desidera configurare un Server di Pull. Il **ResourceRepositoryShare** blocco può essere usato senza specificare un **ConfigurationRepositoryShare**. Nell'esempio seguente viene illustrata una metaconfigurazione che configura un client per recuperare le risorse da una condivisione SMB `\\SMBPullServer\Resources`. Quando il nodo è **PUSHED** una configurazione, verrà automaticamente scaricato tutte le risorse necessarie, dalla condivisione specificata.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a>Configurare un Client di Pull per segnalare lo stato

Per impostazione predefinita, i nodi non invierà report a un Server di Pull configurato. È possibile usare un singolo server di pull per le configurazioni, le risorse e i report, ma è necessario creare un blocco **ReportRepositoryWeb** per configurare la creazione di report.

### <a name="http-dsc-pull-server"></a>Server di Pull DSC HTTP

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

### <a name="smb-share"></a>SMB Share

Un server di report non può essere una condivisione SMB.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver configurato il client di pull, è possibile utilizzare le guide seguenti per eseguire i passaggi successivi:

- [Pubblicare le configurazioni in un server di pull (v4/v5)](publishConfigs.md)
- [Creare un pacchetto e caricare le risorse in un server di pull (v4)](package-upload-resources.md)

## <a name="see-also"></a>Vedere anche

* [Configurazione di un client di pull con nomi di configurazione](pullClientConfigNames.md)
