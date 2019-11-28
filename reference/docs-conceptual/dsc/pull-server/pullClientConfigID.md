---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Configurare un client di pull usando ID configurazione in PowerShell 5.0 e versioni successive
ms.openlocfilehash: bd173a1079b916c450a0292dca7a595a9bcff985
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417242"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>Configurare un client di pull usando ID configurazione in PowerShell 5.0 e versioni successive

> Si applica a: Windows PowerShell 5.0

> [!IMPORTANT]
> Il server di pull (funzionalità di Windows *servizio DSC*) è un componente supportato di Windows Server, tuttavia non si prevede di offrire nuove caratteristiche o funzionalità. È consigliabile avviare la transizione dei client gestiti ad [Automation DSC per Azure](/azure/automation/automation-dsc-getting-started) (include funzionalità superiori al server di pull in Windows Server) o a una delle soluzioni della community riportate [qui](pullserver.md#community-solutions-for-pull-service).

Prima di configurare un client di pull, è necessario configurare un server di pull. Anche se quest'ordine non è obbligatorio, facilita la risoluzione dei problemi e agevola la riuscita della registrazione. Per configurare un server di pull, è possibile usare le guide seguenti:

- [Configurare un server di pull SMB DSC](pullServerSmb.md)
- [Configurare un server di pull HTTP DSC](pullServer.md)

Ogni nodo di destinazione può essere configurato in modo che possa scaricare configurazioni e risorse e persino segnalare il proprio stato. Le sezioni seguenti illustrano come configurare un client di pull con una condivisione SMB o on server di pull DSC HTTP. Quando Gestione configurazione locale del nodo si aggiorna, contatta la posizione configurata per scaricare tutte le configurazioni assegnate. Se una o più risorse necessarie non sono presenti nel nodo, le scarica automaticamente dalla posizione configurata. Se il nodo è configurato con un [server di report](reportServer.md), segnala quindi lo stato dell'operazione.

> [!NOTE]
> Questo argomento si applica a PowerShell 5.0. Per informazioni sulla configurazione di un client di pull in PowerShell 4.0, vedere [Configurazione di un client di pull usando un ID configurazione in PowerShell 4.0](pullClientConfigID4.md).

## <a name="configure-the-pull-client-lcm"></a>Configurare Gestione configurazione locale del client di pull

L'esecuzione di uno degli esempi che seguono crea una nuova cartella di output denominata **PullClientConfigID** e inserisce in questa cartella un file MOF di metaconfigurazione. In questo caso, il file MOF di metaconfigurazione sarà denominato `localhost.meta.mof`.

Per applicare la configurazione, chiamare il cmdlet **Set-DscLocalConfigurationManager**, con il valore di **Path** impostato sul percorso del file MOF di metaconfigurazione. Ad esempio:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>ID configurazione

Gli esempi che seguono impostano la proprietà **ConfigurationID** di Gestione configurazione locale su un **GUID** creato in precedenza per questo scopo. Il valore di **ConfigurationID** viene usato da Gestione configurazione locale per trovare la configurazione appropriata nel server di pull. Il file MOF di configurazione nel server di pull deve essere denominato `ConfigurationID.mof`, dove *ConfigurationID* è il valore della proprietà **ConfigurationID** di Gestione configurazione locale del nodo di destinazione. Per altre informazioni, vedere [Pubblicare le configurazioni in un server di pull (v4/v5)](publishConfigs.md).

È possibile creare un **GUID** casuale usando l'esempio che segue o tramite il cmdlet [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid).

```powershell
[System.Guid]::NewGuid()
```

Per altre informazioni sull'uso di **GUID** nell'ambiente in uso, vedere [Pianificare per i GUID](/powershell/scripting/dsc/secureserver#guids).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configurare un client di pull per scaricare configurazioni

Ogni client deve essere configurato in modalità **Pull** e deve ricevere l'URL del server di pull in cui è archiviata la sua configurazione. A tale scopo, è necessario configurare Gestione configurazione locale con le informazioni richieste. Per configurare Gestione configurazione locale, è necessario creare un tipo speciale di configurazione usando l'attributo **DSCLocalConfigurationManager**. Per altre informazioni sulla configurazione di Gestione configurazione locale, vedere [Configurazione di Gestione configurazione locale](../managing-nodes/metaConfig.md).

### <a name="http-dsc-pull-server"></a>Server di pull DSC HTTP

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

Nello script il blocco **ConfigurationRepositoryWeb** definisce il server di pull. **ServerUrl** specifica l'URL del pull DSC

### <a name="smb-share"></a>Condivisione SMB

Lo script seguente configura Gestione configurazione locale per il pull delle configurazioni dalla condivisione SMB `\\SMBPullServer\Pull`.

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

Nello script, il blocco **ConfigurationRepositoryShare** definisce il server di pull, che in questo caso è una condivisione SMB.

## <a name="set-up-a-pull-client-to-download-resources"></a>Configurare un client di pull per scaricare risorse

Se nella configurazione di Gestione configurazione locale si specifica solo il blocco **ConfigurationRepositoryWeb** o il blocco **ConfigurationRepositoryShare**, come negli esempi precedenti, il client di pull eseguirà il pull delle risorse dalla stessa posizione da cui recupera le proprie configurazioni. È anche possibile specificare posizioni distinte per le risorse. Per specificare una posizione per le risorse come server separato, usare il blocco **ResourceRepositoryWeb**. Per specificare una posizione per le risorse come condivisione SMB, usare il blocco **ResourceRepositoryShare**.

> [!NOTE]
> È possibile combinare **ConfigurationRepositoryWeb** con **ResourceRepositoryShare** oppure **ConfigurationRepositoryShare** con **ResourceRepositoryWeb** . Di seguito non sono riportati esempi di queste combinazioni.

### <a name="http-dsc-pull-server"></a>Server di pull DSC HTTP

La metaconfigurazione seguente configura un client di pull in modo che ottenga le configurazioni da **CONTOSO-PullSrv** e le risorse da **CONTOSO-ResourceSrv**.

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

### <a name="smb-share"></a>Condivisione SMB

L'esempio seguente illustra una metaconfigurazione che configura un client per il pull di configurazioni dalla condivisione SMB `\\SMBPullServer\Configurations` e per il pull di risorse dalla condivisione SMB `\\SMBPullServer\Resources`.

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

#### <a name="automatically-download-resources-in-push-mode"></a>Scaricare automaticamente le risorse in modalità Push

A partire da PowerShell 5.0, i client di pull possono scaricare moduli da una condivisione SMB, anche quando sono configurati per la modalità **Push**. Ciò è particolarmente utile negli scenari in cui non si vuole configurare un server di pull. È possibile usare il blocco **ResourceRepositoryShare** senza specificare un blocco **ConfigurationRepositoryShare**. L'esempio seguente illustra una metaconfigurazione che configura un client per il pull di risorse dalla condivisione SMB `\\SMBPullServer\Resources`. Quando il nodo **riceve il push** di una configurazione, scarica automaticamente tutte le risorse necessarie dalla condivisione specificata.

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

## <a name="set-up-a-pull-client-to-report-status"></a>Configurare un client di pull per la segnalazione dello stato

Per impostazione predefinita, i nodi non inviano report a un server di pull configurato. È possibile usare un singolo server di pull per le configurazioni, le risorse e i report, ma è necessario creare un blocco **ReportRepositoryWeb** per configurare la creazione di report.

### <a name="http-dsc-pull-server"></a>Server di pull DSC HTTP

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

### <a name="smb-share"></a>Condivisione SMB

Un server di report non può fungere da condivisione SMB.

## <a name="next-steps"></a>Passaggi successivi

Dopo la configurazione del client di pull, per eseguire i passaggi successivi è possibile usare le guide seguenti:

- [Pubblicare le configurazioni in un server di pull (v4/v5)](publishConfigs.md)
- [Creare un pacchetto e caricare le risorse in un server di pull (v4)](package-upload-resources.md)

## <a name="see-also"></a>Vedere anche

* [Configurazione di un client di pull con nomi di configurazione](pullClientConfigNames.md)
